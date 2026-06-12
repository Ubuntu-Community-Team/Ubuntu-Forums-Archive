---
title: "How do I tell my Openchrome drivers to load?"
date: 2006-07-03
forum: Multimedia &amp; Video
---

### Post by jeeves on 2006-07-03
A few weeks ago I compiled the openchrome drivers for my VIA/S3G Unichrome Pro Integrated Graphics Processor. **How do I tell them to load?** From looking at my xorg.0.log ,it appears that the old **Unichrome** drivers that come with Dapper are loading instead.

Here is what I have in my xorg.conf:

> Section "Device"
Identifier "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
Driver "via"
BusID "PCI:1:0:0"
Option "DisableIRQ"
Option "EnableAGPDMA"

EndSection

---

### Post by encompass on 2006-07-03
You have a newer driver your trying to work with?  I would try to stick with the old driver as it would need updating everytime you upgrade your kernel.
If you are looking for 3d support it should have it by default for the s3 serious if I am not mistaken.

---

### Post by jeeves on 2006-07-03
Yes I had originally planned to use the via driver supplied with Dapper, however it does not appear to support the VN800 chipset (which is my chipset AFAIK). Everytime I attempt to start X I get the following message in my Xorg.0.log:

[B](II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400
(II) Primary Device is: PCI 01:00:0
(EE) [COLOR="Red"]No devices detected.[/COLOR][/B]

*So I am guessing from the message that Dappers supplied Unichrome driver will not support the VN800 chipset. While it appears that Openchrome drivers will support VN800.*

---

### Post by encompass on 2006-07-03
I am sure you have already done it, but try this... 
sudo dpkg-reconfigure xserver-xorg
I think...
That should start up the reconfigure program for your graphical environ.  try to find a better driver.  I swear I used to use the unichrome driver before.  Try the savage driver.  or as a last resort the vesa fb driver.
Sorry for not being able to help you much more.

---

### Post by jeeves on 2006-07-03
[QUOTE=encompass]I am sure you have already done it, but try this... 
sudo dpkg-reconfigure xserver-xorg
I think...
That should start up the reconfigure program for your graphical environ.  try to find a better driver.  I swear I used to use the unichrome driver before.  Try the savage driver.  or as a last resort the vesa fb driver.
Sorry for not being able to help you much more.[/QUOTE]
Thanks - I'll give it another try. **Anyone know what is the designation in the xorg.conf for the *Openchrome* drivers? **It can't be "via" since that is what I used for the *Unichrome* drivers included in Dapper. 

Am I right in assuming that the xorg.conf is what tells Ubuntu what graphics driver to load?

---

### Post by acojlo on 2006-07-03
[QUOTE=jeeves]Thanks - I'll give it another try. **Anyone know what is the designation in the xorg.conf for the *Openchrome* drivers? **It can't be "via" since that is what I used for the *Unichrome* drivers included in Dapper. 

Am I right in assuming that the xorg.conf is what tells Ubuntu what graphics driver to load?[/QUOTE]

Acctualy, you can use allready compiled binaries for VN800. Drivers supplied with 6.06 installation do not support VN800. For HOW-To read two threads at this forum:

1. [http://ubuntuforums.org/showthread.php?t=206594]("http://ubuntuforums.org/showthread.php?t=206594")
2. [http://ubuntuforums.org/showthread.php?t=184512]("http://ubuntuforums.org/showthread.php?t=184512")

You have to put drivers at standard predefined locations. Maybe you can change this predefined locations but I'm also new at linux comunity so I do not know how to and maybe it is not good to mess that way. Please read the threads I suggested and then do the job. You have two drivers - one for standard behaviour of the video chip and second for DRI (games and hardware video acceleration).

---

### Post by encompass on 2006-07-04
acojlo
phew thanks... I was getting lost there.

---

