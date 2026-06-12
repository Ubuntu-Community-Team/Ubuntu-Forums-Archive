---
title: "Pinnacle and tvtime"
date: 2009-11-28
forum: Multimedia Software
---

### Post by tvks on 2009-11-28
Hi,

I had Ubuntu 8.5 earlier and had used the following link to configure my Pinnacle tv tuner with tvtime

[http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html](http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html)

Right now I have formatted my system and come down to Karmic 9.10. Now I am having the problem of configuration. My tvtime does not seem to work. This is my lspci command output.

[PHP]
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
[/PHP]

When I run tvtime it says 

[PHP]
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/kumar/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

[/PHP]

On googling I find many recommendations that the problem will be fixed on changing xorg.conf in /etc/X11 but in 9.10 I do not find any such file also. It is neither possible to guess a few files and create it as it might affect my display on reboot completely.

Kindly help.

Regards,

tvks

---

