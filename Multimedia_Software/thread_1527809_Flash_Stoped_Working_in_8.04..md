---
title: "Flash Stoped Working in 8.04."
date: 2010-07-09
forum: Multimedia Software
---

### Post by NobleSavage on 2010-07-09
I'm still using the last LTS 8.04.  Getting ready to upgrade to the newest version 

Flash was working perfect until one of the last software updates. Now all I get is "The Adobe Flash plugin has crashed." 

I tried running:

sudo apt-get install flashplugin-installer and got the following message"

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer


If anyone has any advice it would be much appreciated.  I'd really like to get Flash working again before I build a new box and upgrade to 10.04.

Thanks

---

### Post by lovinglinux on 2010-07-09
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by NobleSavage on 2010-07-10
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

Ok, I followed your instructions and this is what I get for Shockwave Flash:


    File: /home/noble/.mozilla/plugins/libflashplayer.so
    Version: 
    Shockwave Flash 9.0 r48


Thanks again for any help with its. :D

---

### Post by lovinglinux on 2010-07-10
> **NobleSavage said:**
> Ok, I followed your instructions and this is what I get for Shockwave Flash:


    File: /home/noble/.mozilla/plugins/libflashplayer.so
    Version: 
    Shockwave Flash 9.0 r48


Thanks again for any help with its. :D

Download the tar.gz flash 10.1 version from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Extract it and move to /home/noble/.mozilla/plugins/

---

### Post by NobleSavage on 2010-07-10
That worked perfect lovinglinux! Thanks!

---

### Post by lovinglinux on 2010-07-10
> **NobleSavage said:**
> That worked perfect lovinglinux! Thanks!

You are welcome.

---

