---
title: "Duplicate Xine Plugins"
date: 2010-01-01
forum: Multimedia Software
---

### Post by watchpocket on 2010-01-01
"about: plugins" shows that I have 2 identical xine plugin entries in (64-bit) Firefox-3.5.6. 

 Tools -> Add-ons -> Plugins shows only one.

The actual "xineplugin.so" file is in:
```
/usr/lib/xine-plugin/xineplugin.so
```But I have 3 symlinks (diversions?) pointing to that file:

```
/usr/lib64/firefox/plugins/xineplugin.so -> ../../xine-plugin/xineplugin.so

/usr/lib64/mozilla-firefox/plugins/xineplugin.so -> ../../xine-plugin/xineplugin.so


/usr/lib64/xulrunner-1.9.1.6/plugins/xineplugin.so -> ../../xine-plugin/xineplugin.so
```( /usr/lib64 points to lib/ )

Anyone know why about: plugins is showing 2 of them? 

Do I need to remove one (or more) of the symlinks?  If so, which one(s)?

---

### Post by watchpocket on 2010-01-02
**I meant** ```
/usr/lib/xulrunner-addons/plugins/...
```**not**

```
/usr/lib64/xulrunner-1.9.1.6/plugins/xineplugin.so -> ../../xine-plugin/xineplugin.so
```Still wondering about this.

 I've moved all three of the symlinks and I can only seem to get both listings of the xine plugin, or none . . . .

 Thanks for any suggestions.

---

