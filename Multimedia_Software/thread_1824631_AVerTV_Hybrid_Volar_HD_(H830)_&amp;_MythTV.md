---
title: "AVerTV Hybrid Volar HD (H830) &amp; MythTV"
date: 2011-08-14
forum: Multimedia Software
---

### Post by BrownWarrior on 2011-08-14
[SIZE=1]Hi
  Can anyone please help me to set up my usb, digital TV Tuner, an [AVerTV Hybrid Volar HD (H830) ]("http://www.avermedia.com/avertv/product/productdetail.aspx?id=501&tab=APDriver"), to work with MythTV?


 I note that the 'MythTV backend set-up', only refers TV Tuner cards, not usb sticks. Nevertheless, the link above provides a 'Linux x86' driver for my computer – a .tar.gz file. The link also provides an accompanying text file that asserts 'This package is tested with MythTV against Ubuntu 10.04'. I've recently installed Ubuntu 11.04.The accompanying text gives its pre-requisites as  [/SIZE]   [SIZE=1]
 [/SIZE][FONT=Arial][SIZE=1]a. support linux kernel 2.6.29 or later.[/SIZE][/FONT][FONT=Arial][SIZE=1] b.  make sure /lib/modules/`uname -r`/build exists[/SIZE][/FONT][SIZE=1]
 [/SIZE][FONT=Arial][SIZE=1]c. make sure "dvb_frontend.h" exist in your Ubuntu. d. kernel modules dependency: videodev, video buf-core, v4l2-common.[/SIZE][/FONT][SIZE=1] 

For (b), my computer shows the following path  /lib/modules/2.6.38-10-generic/build$  I'm note sure what (c) means with 'in your Ubuntu' 

 Needless to say, its later instruction doesn't work [/SIZE][SIZE=1]
 Install driver to system
              $ sudo ./xxx_LinuxDrv_x86_vxxx-beta_Install.sh 

 I'm told that this 'command not found' [/SIZE]

---

### Post by mac_is_mac on 2011-08-25
Yes. You should install linux-headers-2.6.38. 

If this don't work, you can also read the page I wrote after my Debian install:

[http://www.iecn.u-nancy.fr/~garet/linux/notes_installation_av830_debian.php]("http://www.iecn.u-nancy.fr/%7Egaret/linux/notes_installation_av830_debian.php")

Good luck !

---

