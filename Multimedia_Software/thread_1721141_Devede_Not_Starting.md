---
title: "Devede Not Starting"
date: 2011-04-04
forum: Multimedia Software
---

### Post by coolglobal on 2011-04-04
**devede not starting, here is the terminal output**

xxxx@xxxx:~$ devede

(process:2250): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
DeVeDe 3.16.9
Locale: en_AU
Using package-installed files
Traceback (most recent call last):
  File "/usr/bin/devede", line 138, in <module>
    locale.setlocale(locale.LC_ALL,"")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
xxxx@xxxx:~$

---

### Post by howefield on 2011-04-04
Try running the terminal command

```
sudo dpkg-reconfigure locales 
```

---

### Post by coolglobal on 2011-04-04
it just started working!!!???

---

