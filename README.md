# Django Orderless Cache Middleware

## Because order shouldn't matter!

Most of this is copied verbatim from the Django Cache Middleware and cache_page wrappers
What this does is make sure that ?q=1&q=2&a=4&a=6 gets the same cache key as ?a=6&a=4&a=2&q=1
and thus is cached regardless of the order of the querystring parameters. It will sort alphabetically
the GET parameters and then sort alphabetically their values to compute the querystring.


#Installation

For now add the cache.py file into one of your apps :)

#Configuration

Replace in the middleware UpdateCacheMiddleware with orderless.cache.OrderlessUpdateCacheMiddleware
and FetchFromCacheMiddleware with orderless.cache.OrderlessFetchFromCacheMiddleware

#View Decorator Replacement

You can also use orderless_cache_page(my_view, 3600) or orderless_cache_page(MyGenericView.as_view(), 3600) as a replacement for the view decorator
