---
title: "Nvidia Geforce 6200 issues"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by S1nn3r on 2006-09-01
Hi all,

Haveing a huge problem getting this 6200 working right in my system -
Intel P4 3.2Ghz
Nvidia Nforce4 Intel Ed.
1GB Ram
200GB PATA HD
Nvidia Geforce 6200 TC

Followed the install instuctions for the nvidia drivers on the ubuntu help, and everything installs without errors seemingly. However I can not, even if it is the only video mode entered in xorg.conf get X to set resolution to 1280x1024, it always stays at 1024x768 regardless of what I do. Also glxgears framerate is very low (600fps ish) this dispite the output of glxinfo indicateing that direct rendering is on, and everything looking to be in order in the nvidia-settings panel.

All in all on paper everything should be working fine but for some reason it is not.. and I nor people I spoke to on the IRC channel could work out why.

---

### Post by xboxer21 on 2006-09-01
I was having problems as well with the 6200 and finally returned it back to the store. Switched back to the old integrated sis vga, the only reason I bought the nvidia was to get xgl working :(

---

### Post by tseliot on 2006-09-01
> **S1nn3r said:**
> Hi all,

Haveing a huge problem getting this 6200 working right in my system -
Intel P4 3.2Ghz
Nvidia Nforce4 Intel Ed.
1GB Ram
200GB PATA HD
Nvidia Geforce 6200 TC

Followed the install instuctions for the nvidia drivers on the ubuntu help, and everything installs without errors seemingly. However I can not, even if it is the only video mode entered in xorg.conf get X to set resolution to 1280x1024, it always stays at 1024x768 regardless of what I do. Also glxgears framerate is very low (600fps ish) this dispite the output of glxinfo indicateing that direct rendering is on, and everything looking to be in order in the nvidia-settings panel.

All in all on paper everything should be working fine but for some reason it is not.. and I nor people I spoke to on the IRC channel could work out why.

Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by S1nn3r on 2006-09-01
Ive tryed doing all those things, and it still doesnt work right.

---

