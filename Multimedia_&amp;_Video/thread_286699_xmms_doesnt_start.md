---
title: "xmms doesnt start"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by ShirishAg75 on 2006-10-28
Hi all,
         I just upgraded from Ubuntu 6.06 to Ubuntu 6.10 . xmms doesnt start & reports this failure :-

```

Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2493 error_code 8 request_code 72 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2494 error_code 8 request_code 72 minor_code 0

```while looking at the version of xmms it gives as 

```
shirish@shirish-desktop:~$ xmms --version
xmms 1.2.10
``` On digging a little further, found there is .xmms folder in my home directory which has 3 files & 2 folders namely config, menurc, xmm.m3u & 2 folders namely Plugins & Skins perhaps tht has to do something with it.

 Lastly how do I change to show tht im now a Ubuntu 6.10 user. Thnx in advance.

---

### Post by ShirishAg75 on 2006-10-28
Hi all,
       I deleted the .xmms folder thinking tht it might solve the problem as I understand tht most of the .files are configurations tht I have made xmms. Tht didnt effect much & although I was able to see xmms, all the things Menu names had disappeared. Then I decided to uninstall & install xmms all over again, thinking tht might put things right. Now I get the following errors

```
Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory
Message: device: default

```

---

### Post by ShirishAg75 on 2006-10-30
come on guys somebody plz. respond :(

---

### Post by odin277 on 2006-10-30
> **shirishag75 said:**
> come on guys somebody plz. respond :(

Having the same problem. Hope someone can help. Tried re-installing xmms but still can't see it. Visualization GOOM2 comes on though.

---

### Post by BLTicklemonster on 2006-10-30
Odd, on dapper, if I try to use xmms, it locks up and won't work at all. Just recently started doing this.

---

### Post by odin277 on 2006-10-30
> **shirishag75 said:**
> come on guys somebody plz. respond :(

try this string 
[http://www.ubuntuforums.org/showthread.php?t=285915&highlight=xmms](http://www.ubuntuforums.org/showthread.php?t=285915&highlight=xmms)

---

