---
title: "Encore ENPWI-G installation"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by manro on 2006-06-01
Hi, I just install the final release of Ubuntu, Ubuntu 6.06 LTS but I cannot make my Encore wireless pcmcia card to work ](*,) ... here's the link to the card webpage: [http://www.encore-usa.com/product.php?id=95&lang=]("http://www.encore-usa.com/product.php?id=95&lang=") ... please let me know what kind of feedback you need from me so you can give me some help!

Thanks to everyone!!! :D 

Regards!  ;)

---

### Post by manro on 2006-06-20
Someone please!?

---

### Post by noname101 on 2006-06-20
What does lspci say? 
What does iwconfig say?

---

### Post by manro on 2006-07-01
[QUOTE=noname101]What does lspci say? 
What does iwconfig say?[/QUOTE]

I think it's almost done...but I can't get it to work with my linksys AP. The AP has WAP Personal and TKIP security.

Any ideas?

Here's the lspci and iwconfig:

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)



manro@ubuntu-laptop:~$ iwconfig lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

manro@ubuntu-laptop:~$

---

### Post by macabro22 on 2007-05-06
I have the same wireless card. I can detect the networks and sometimes connect to them but I cannot access the great computer network.

Good grief...

---

### Post by macabro22 on 2007-05-19
Manro!

I found a solution. Read it up in here:

[http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g](http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g)

---

### Post by manro on 2007-06-30
> **macabro22 said:**
> Manro!

I found a solution. Read it up in here:

[http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g](http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g)

Thanks a lot really...this just work great!

MaNRo :D

---

### Post by macabro22 on 2007-07-01
Welcome =]

---

