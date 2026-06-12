---
title: "Component Video Out on Asus M2NPV-VM"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by douglaseg1 on 2006-12-25
Hello,

I am trying to get the component video out on my ASUS M2NPV-VM motherboard working with Edgy. My basic setup -

M2NPV-VM
AMD 64 3800+ X2
1 Gb RAM

Edgy Server (AMD64)

I'm trying to setup a MythTV box but can only get the display on my computer monitor. I'm basically new to linux/ubuntu so any help would be appreciated. I want to get the video output sent over to my HDTV via the component video out on the motherboard. I followed the mythtv setup wiki for a combined backend / frontend myth tv server box.

From what I've read, I think that I need to edit my xorg.conf file. I must admit that I have no idea what to edit.

Thanks!

---

### Post by jimholt3 on 2007-02-01
I have the same set up.  I was able to get video out over the component output, but you must not have a monitor plugged into the vga port.  The system will detect which output is being used at boot and only send to that device.
The trouble I have is that the output is very blue.  It is like one of the component connections is not working.  I did swap cables and the startup Ubuntu splash screen show a good orange color, so I believe it must be the X11 driver.

Were you able to resolve your problem?

---

### Post by klueless on 2007-03-14
I have the M2NPV-VM as well.  Everything looks fine on VGA and DVI outputs, but the component output is blue.  Has anyone figured out how to fix this problem yet?

I tried various settings but no luck.
Option "TVStandard" "HD480i"
#Option "TVStandard" "HD480p"
#Option "TVStandard" "HD720p"
#Option "TVStandard" "HD1080i"

Anyone?

---

