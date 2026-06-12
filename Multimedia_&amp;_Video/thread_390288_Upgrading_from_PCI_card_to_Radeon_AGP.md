---
title: "Upgrading from PCI card to Radeon AGP"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by mikeglaz on 2007-03-21
I had to install Ubuntu 6.10 using an old Trident Microsystems Blade 3D PCI card with 2MB memory.  I normally use my ATI Radeon 9800 Pro (AGP) but the Ubuntu installation would hang with this card.  Now I have Ubuntu installed and running but how do I switch back to my ATI Radeon card?  If I just try swapping cards and rebooting I get X-Window errors.  So I'm guessing I somehow have to modify my xorg.conf file and install the ATI driver??

thanx,
mike

---

### Post by mikeglaz on 2007-03-21
Well, did it myself.  Just followed these instructions to install an ATI driver:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.34.8_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.34.8_Driver_Manually)
Then shut-down, replaced cards, and my Radeon is going strong with 3D enabled!  (knock on wood)

---

