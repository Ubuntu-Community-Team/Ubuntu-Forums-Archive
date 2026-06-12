---
title: "Rhythmbox missing lib in Hardy"
date: 2010-04-06
forum: Multimedia Software
---

### Post by justanotherhandle on 2010-04-06
Rhythmbox went missing. How long ago I'm not sure as I don't use often.  When starting I get them error:

```
$ rhythmbox
rhythmbox: error while loading shared libraries: libtotem-plparser.so.10: cannot open shared object file: No such file or directory
```

I uninstalled and reinstalled Rhythmbox, but that didn't help.

How can I fix?

Many thanks.

---

### Post by justanotherhandle on 2010-04-25
After installing, purging, uninstalling, and reinstalling almost everything that seemed even vaguely likely to contain the missing lib I found the missing file, or at least a symbolic link to the missing file, in the mozilla plugin directory

```
/usr/lib/mozilla/plugins/libtotem-plparser.so.10 -> libtotem-plparser.so.10.1.1
```

In the /usr/lib directory itself I found these orphan links
```
libtotem-plparser-mini.so -> libtotem-plparser-mini.so.10.1.1
libtotem-plparser.so -> libtotem-plparser.so.10.1.1
```

So I copied the libtotem-plparser.so.10.1.1 from the /usr/lib/mozilla/plugins directory to the /usr/lib directory and made a symbolic link named libtotem-plparser.so.10 pointing to the newly relocated libtotem-plparser.so.10.1.1

Voila, I have rhythmbox back.

HTH sombody.

---

