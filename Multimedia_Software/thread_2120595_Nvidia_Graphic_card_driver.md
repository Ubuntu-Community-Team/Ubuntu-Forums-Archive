---
title: "Nvidia Graphic card driver"
date: 2013-02-26
forum: Multimedia Software
---

### Post by harimodel007 on 2013-02-26
i have ASUS K55VJ laptop comes with[COLOR=Red] Nvidia 635M [/COLOR]Graphics.

Do i need to install drivers for this in[COLOR=Red] ubuntu 12.04 [/COLOR]in order to get better resource utilization and system performance ?
please reply. 
):P

---

### Post by harimodel007 on 2013-02-26
[B]somebody help me.
[/B]
i've downloaded the suitable driver from nvidia anyway. its in .run format.
cant install it. :(

---

### Post by nwalkey on 2013-02-27
You need to make it executable...

```
sudo chmod 755 /pathtofile/file
```Or you could do it the long way: right click on the file, go to properties, and change permissions to execute. Also you may need to use bumblebee and run programs that you want to actually use the graphics from terminal using optirun... either that or set it to only use the 635m which I highly recommend you do not do. There are lots of resources out there for installing bumblebee and nvidia drivers. Just search 'nvidia 635m driver ubuntu' or something similar on google. Good luck!

---

### Post by Bucky Ball on 2013-02-27
*Thread moved to **Multimedia & Video**.*

---

### Post by MAFoElffen on 2013-02-27
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

I followed this over here from Installations & Upgrades... Where it was actually an appropriate question there. (Being it was a graphics layer problem...)

Please read this post for the latest instructions on installing nVidia binary drivers on Ubuntu branches:
[http://ubuntuforums.org/showpost.php?p=12487320&postcount=1126](http://ubuntuforums.org/showpost.php?p=12487320&postcount=1126)

Or you could install the nvidia-current driver from the repo's.

I'll follow this thread to see how it goes and answer any questions.

---

### Post by Bucky Ball on 2013-02-27
@ MAFoElffen: FYI, from the description of Installation & Upgrades:

> **Installation & Upgrades** For questions about *_upgrading and installation of your new Ubuntu OS._*

This thread clearly does not ask any question about installing or upgrading the OS but *does* ask a question about graphics.

> **Multimedia & Video** Have multimedia question? ATI, Nvidia, Sound cards. Just ask here.

Quite clear. Thanks. ;)

---

