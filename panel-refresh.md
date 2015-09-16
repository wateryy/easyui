### jQuery EasyUI 1.4.3 版本
```javascript
$("#panel").panel("refresh"); // 无效
$("#panel").panel("refresh", "_abc.html"); // 有效
```

想要都生效，需要修改源码
```javascript
if (!opts.href) {
    return;
}
```
修改为:
```javascript
if (!opts.href) {
    if (opts.content) {
        if (!_22c.isLoaded) {
            $(_22a).panel("clear");
            $(_22a).html(opts.content);
            $.parser.parse($(_22a));
            opts.onLoad.apply(_22a);
            _22c.isLoaded = true;
        }
    }
    return;
}
```
