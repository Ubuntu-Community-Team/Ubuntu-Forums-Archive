---
title: "OGMRip configure Errors on Edgy"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by Nerdy on 2006-12-06
Hi all,

I am trying to configure OGMRip and end up with these errors.

[INDENT]checking for OGMRIP... configure: error: Package requirements (glib-2.0 >= 2.6.0 gobject-2.0 >= 2.6.0 libxml-2.0) were not met:

No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OGMRIP_CFLAGS
and OGMRIP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/INDENT] 

Any help greatly appreciated.

---

### Post by pay on 2006-12-06
Do as it says, install glib-2.0 >= 2.6.0 gobject-2.0 >= 2.6.0 libxml-2.0

---

### Post by Nerdy on 2006-12-06
Sorry, should have been clearer.
I have already checked that these packages are installed under synaptic.

---

### Post by pay on 2006-12-06
Add "deb-src [http://www.bigbob.org.uk/debian](http://www.bigbob.org.uk/debian) dapper/" to /etc/apt/sources.list
Run the following commands:
```
sudo apt-get update
sudo apt-get build-dep ogmrip
fakeroot apt-get --build source ogmrip
sudo dpkg -i ogmrip*deb
```Don't worry that it says dapper because you are compilling from source anyway.

---

### Post by Nerdy on 2006-12-07
Cheers Pay, will give it a go tonight.

---

