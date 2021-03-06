# Routing by Convention

The default route which is declared for you in the `Routes.cfm` is:

```js
addRoute(pattern=":handler/:action?");
```

The URL pattern in the default route includes two special position holders:

* `:handler` - The handler to relocate to (It can include Package and Module)
* `:action` - The action to relocate to or a RESTFul map (We will see later)

With one route you can potentially write an entire application because once a route is deteceted, any extra name-value pair in the URL will be translated to variables in the request collection for you.

```js
http://localhost/general -> event=general.index
http://localhost/general/index -> event=general.index
http://localhost/general/index/id/2 -> event=general.index&id=2
// If 'admin' is a package in the handlers directory
http://localhost/admin/general/index -> event=admin.general.index 
// If 'admin' is a module
http://localhost/admin/general/index/id/4/page/2 -> event=admin:general.index&id=4&page=2
```

However, the problem is that your routing URLs depend too much in the name of your handlers and actions. Thus, if you refactor, your URLs change and that's not very nice. That's why we encourage you to create more routes so this can be avoided especially on public sites.