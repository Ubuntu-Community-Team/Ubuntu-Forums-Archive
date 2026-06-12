---
title: "openshot errors 10.04"
date: 2011-05-03
forum: Multimedia Software
---

### Post by ddarsow on 2011-05-03
I have been running OpenShot for video editing for some time on 10.04, as of yesterday the app fails to launch at all from the launcher. If I attempt to open it from the terminal I get the following errors:

```
$ openshot

(process:2858): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
--------------------------------
   OpenShot (version 1.2.2)
--------------------------------
Process no longer exists: 2834.  Creating new pid lock file.
Traceback (most recent call last):
  File "/usr/bin/openshot", line 57, in <module>
    main()
  File "/usr/lib/pymodules/python2.6/openshot/openshot.py", line 52, in main
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
```

Any idea what the locale setting error is? (or what else the problem may be?)

Thanks,
Dave

---

