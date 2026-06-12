---
title: "Mozilla Minefield in Ubuntu"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by turinturambar on 2009-02-09
As a recent Windows refugee, I'm really missing the speed of Minefield.  Does anyone know how to install it?

Thanks

---

### Post by cb951303 on 2009-02-09
is this the firefox development release? if so [http://getswiftfox.com/](http://getswiftfox.com/) would do the job:popcorn:

---

### Post by turinturambar on 2009-02-13
Thanks--is this the official mozilla release?

---

### Post by zika on 2009-02-13
> **turinturambar said:**
> As a recent Windows refugee, I'm really missing the speed of Minefield.  Does anyone know how to install it? Thanks
simply.
this is for the Terminal (CLI), similar is for nautilus (GUI).
download file according to Your install from the nightly archive:
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)
put the file in the directory where You want Minefield directory to be.
go to that directory.
unpack it with: ```
 sudo tar -xvf firefox(whatever is the name for Your install)...tar.bz2
```edit the line with moz_libdir in file (wherever You've put it)/firefox/firefox
 ```
sudo nano (wherever You've put it)/firefox/firefox
```so that it reads: moz_libdir=(wherever You've put it)/firefox/
and make a launcher with command line: (wherever You've put it)/firefox/firefox
and You're done.
You can even make it a default by changing it in System->Preferences->Preffered_Applications->Browser->Custom->(wherever You've put it)/firefox/firefox ...

I'm using it and, even though I've tried to get used to 3.0.6 or even 3.1beta nightly, I'm always coming back the same day to this nightly, updated every day ... :)

---

### Post by zika on 2009-02-13
> **turinturambar said:**
> Thanks--is this the official mozilla release?
NO, see my previous post.

---

### Post by turinturambar on 2009-08-15
thanks, do you know if it updates on it's own, or do I have to download and unpack it again every time I want an update?

---

