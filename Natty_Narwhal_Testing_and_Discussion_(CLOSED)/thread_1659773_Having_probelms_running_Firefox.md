---
title: "Having probelms running Firefox"
date: 2011-01-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by davideotape on 2011-01-04
So, I can't seem to start Firefox at all as of 4b8. ```
$ firefox
``` does nothing, but ```
$ firefox -h
/usr/lib/firefox-4.0b8/firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

      -g or --debug       Start within /usr/bin/gdb (Must be first)

``` may help.

I have firefox 4.0~b8+nobinonly-0ubuntu2 installed, with both xulrunner 1.9.2.13+build3+nobinonly-0ubuntu2 and 2.0~b8+build1+nobinonly-0ubuntu2 installed. And finally, libxul.so exists in /usr/lib/xulrunner-2.0b8/ and /usr/lib/xulrunner-1.9.2.13/

Anyone got any ideas what's going on?

---

### Post by mc4man on 2011-01-04
I know very little about firefox in ubuntu, though it seems that for whatever reason you're trying to open firefox (firefox-bin) directly, rather than whatever slightly twisted path it should follow
(/usr/bin/firefox > /usr/lib/firefox-4.0b8/firefox.sh > ??

Worst case you may want to try purging firefox and re-installing (though maybe wait for more informed reply

Don't believe those xul packages are involved at all

---

### Post by lidex on 2011-01-04
You sure that's all you have?
```
locate libxul.so
[COLOR="Red"]/usr/lib/firefox-4.0b8/libxul.so[/COLOR]
/usr/lib/xulrunner-1.9.2.13/libxul.so
/usr/lib/xulrunner-2.0b8/libxul.so
/usr/lib/xulrunner-devel-2.0b8/sdk/lib/libxul.so

```
Try copying it to the directory in red.

---

### Post by rburkartjo on 2011-01-05
it worked out of the box for me

---

### Post by davideotape on 2011-01-05
I seem to have it everywhere:

```
$ locate libxul.so
/home/david/Downloads/firefox/libxul.so
/usr/lib/firefox-4.0b8/libxul.so
/usr/lib/xulrunner-1.9.2.13/libxul.so
/usr/lib/xulrunner-2.0b8/libxul.so
/usr/lib/xulrunner-devel-2.0b8/sdk/lib/libxul.so

```

---

### Post by mc4man on 2011-01-05
Check for the proper path as mentioned or remove and re-install.

Were or are you using a non natty repo version of firefox.
(anyone can get the same error from firefox -h or if trying to run firefox-bin directly ( /usr/lib/firefox-4.0b8/firefox-bin

---

### Post by davideotape on 2011-01-05
> **mc4man said:**
> Check for the proper path as mentioned or remove and re-install.

Were or are you using a non natty repo version of firefox.
(anyone can get the same error from firefox -h or if trying to run firefox-bin directly ( /usr/lib/firefox-4.0b8/firefox-bin

I was using a non-repo version at one point, but after 4b7 came I deleted the local version and 4b7 was working fine. It's only since 4b8 was uploaded that I can't launch it.

---

