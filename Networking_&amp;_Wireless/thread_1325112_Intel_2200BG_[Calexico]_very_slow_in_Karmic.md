---
title: "Intel 2200BG [Calexico] very slow in Karmic"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by manoman67 on 2009-11-13
Hi all,
I have a Dell latitude D600 laptop with a PCI wireless card that shows in the NetworkManager Applet as Intel PRO/Wireless 2200BG [Calexico2]. I can connect to my home wireless network using this interface, but the connection is too slow to work with (< 1 kbps ). When I plug in a USB Wireless connector (SMC EZ Connect) everything works fine & fast, but I need to manually disable the 2200BG to prevent e.g. Firefox sessions using the slow interface and becoming unresponsive.

Anybody know how I can improve the speed of the 2200BG?
Or otherwise how I can disable it more permanently? I prefer not to remove it physically since I use it when I boot into Windows.

Setup detail:

mano@mano-laptop:/etc$ lsb_release -d
Description:    Ubuntu 9.10

mano@mano-laptop:/etc$ uname -mr
2.6.31-14-generic i686

mano@mano-laptop:/etc$ lspci | grep Wireless
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

mano@mano-laptop:/etc$ iwconfig eth1
eth1      unassociated  Mode:Managed  Frequency=2.432 GHz  
          Access Point: Not-Associated   Bit Rate:0 kb/s   Tx-Power=20 dBm   
          Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mano@mano-laptop:/etc$ dmesg | grep Wireless
[   10.686432] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   10.686624] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

---

### Post by clayd62 on 2009-11-23
Manoman,
I had the exact same problem (same laptop, same wifi card, slow to no wifi connection).  Problem started happening right after I upgraded to Ubuntu 9.10.  Made a boot disk with Ubuntu 9.04 and the wifi started working, even from the boot.  Installing Ubuntu 9.04 solved this problem (of course I did end up spending several hours moving files and getting CD, DVD, and MP3 playing working again).  One thread suggested getting the drivers from [http://linuxwireless.org/](http://linuxwireless.org/), but by the time I'd found this in the forum, I'd already switched to 9.04.

---

### Post by manoman67 on 2009-11-28
Hi Clayd,
Thanks for your reply!
I also installed 9.04 on a separate partition, but that did not make the ipw2200 faster. I am now just using the USB wifi, found out I can disable the 2200BG by adding "blacklist ipw2200" to /etc/modprobe.d/blackllist.conf

Might give the linuswireless.org a chance when I have time.

cheers
M

---

