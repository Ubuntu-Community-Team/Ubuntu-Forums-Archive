---
title: "3 soundcards in one computer(Ubuntu 9.04)"
date: 2009-04-24
forum: Multimedia Software
---

### Post by kristensson.jonas on 2009-04-24
Hello!
Im trying to configure a computer that is going to act as a media center. I will use pulseaudio when i have configured my soundcards properly. However i have bumped into some problems while installing them. The cards are:

Sweex 5.1 with  CM8738  chipset
Creative Labs SB X-Fi
and integrated ICH5 (asrock p4i65G motherboard)

I have run the sweex card on another computer before so it is a simple installation with the command:
> modprobe snd-cmipci;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
So when i tried this command this time it worked aswell. Showed up nicely both in the mixer and using sudo asoundconf list.
Then i tried to install the creative labs card with drivers downloaded from creatives homepage.
I typed:
> 
sudo make
sudo make install

But something went wrong and now i cant find my sweex card anymore either. This is the output from make install:
> 
Copy module files...
Update module dependency relationships...
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Error inserting ctxfi (/lib/modules/2.6.28-11-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
jonas@jonas-media:~/XFiDrv_Linux_Public_US_1.00$ sudo modprobe ctxfi
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Error inserting ctxfi (/lib/modules/2.6.28-11-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And when i again tried to atleast fix the sweex card again with the command i usually use i get the following error:

> 
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module snd_cmipci not found.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.


I have updated alsa to the latest version and it has had no effect. So my questions are:
How do i get my sweex card to function again?
How do I install the creative card without getting this error?
And how do i get the built in hda-intel ICH5 to work?

Oh one other thing if you need it, this is the output from lspci:

> 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900XT] (rev a1)
02:01.0 Multimedia audio controller: Creative Labs SB X-Fi
02:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Best regards
Jonas

---

### Post by markbuntu on 2009-04-24
The basic problem is the X-fi. The driver has not been updated for the latest kernel which no longer uses modprobe.conf but puts configs in /etc/modeprobe.d/. You can file a bug with creative and wait for them to fix it or you can get another c-media card which would be a cheap and easy solution.

---

