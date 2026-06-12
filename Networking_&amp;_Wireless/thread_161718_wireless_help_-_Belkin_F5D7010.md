---
title: "wireless help - Belkin F5D7010"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by sunspots on 2006-04-17
I checked the other requests for help in this forum, but I believe my problem is different as the connection seems to be there. Tell me if I'm wrong.

My set up is:
Dell C400
Ubuntu 5.10
Belkin wireless 802.11b F5D7010
Belkin wireless router F5D7230

Router:
ssid: XXX (for arguments sake)
encryption: disabled (was originally on with 128bit)

Unbuntu setup
lsmod
-------
Module size used by
ipv6 217408 6
rfcomm 34972 0
orinoco_cs 8456 1
orinoco 33932 1 orinoco_cs
hermes 6912 2 orinoco_cs, orinco
pcmcia 24584 3 orinoco_cs

{I only listed what I though was relevant, as I do not have access to internet via Ubuntu}

ifcong -f
---------
eth0 Link encap:Ethernet HWaddr 00:06:5B:02:2E:43
inet addr: 172.a.b.c Bcast: 172.a.255.255 Mask: 255.155.0.0
inet6 addr: fe80::206:5bff:fe02:2e43/64 Scope:Link
UP BROADCAST MULTICAST MTU: 1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueueln:1000
RX bytes:0 (0.0 b) TX bytes: 0.0 b)
interrupt:11 Base address:0xec80

eth1 Link encap:Ethernet HWaddr 00:30:BD:64:4C:84
inet addr: 172.a.b.c Bcast: 172.a.255.255 Mask: 255.155.0.0
inet6 addr: fe80::230:bdff:fe64:4c84/64 Scope:Link
UP BROADCAST MULTICAST MTU: 1500 Metric:1
RX packets:169 errors:0 dropped:0 overruns:0 frame:0
TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueueln:1000
RX bytes:21566 (21.0 kib) TX bytes:11304 (11.0 kib)
interrupt:3 Base address:0x100

iwconfig
---------
lo no wireless extensions

etho no wireless extensions

eth1 IEEE 802.11-DS ESSID:"XXX" Nickname:"Prism I"
mode:Managed Frequency:2.472 GHz Access Point: 00:30:BD:98:C6:34
Bit Rate:11 Mb/s Tx-Power=15 dBm Sensitivity:1/3
Retry min limit:8 RTS thr:off Fragment thr:off
Encryption key: off
Power Management:off
Link Qualtiy=0/92 Signal level=128/163 Noise Level=107/153
Rx invalid mwid:0 Rx invalid crypt:0 Rx invalid fraq:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions

Wow I think I got it all.

I have tried a few variants of Linux and some I got very close to having my wireless card work. I keep coming back to Linux as I really want to get away from the other OS. I'm able to connect via cable to the network but as soon as I try using the wireless card, I lose out and walk awy dismayed.

Well I back trying Linux with Ubuntu. On all accounts I've been told it is easy. But not the case with my wireless card.

I originally had encryption on, and the card had a consistent light and the network tool showed 80 or more percent signal strength. But the browser would time out trying to contect to the world.

When I tried to send I would get packets sent but nothing received and the strength was very good. I would also stand right next to my wireless router.

I took the encryption off and was then seeing send and receive packets. But eventually the browser would timeout.

Trying the wired connection does work and I'm able to surf the web.

My wireless card does work as I use it with another OS.

Any help would be great as I really want to become a convert to Linux.

Thanks

---

### Post by rabidphage on 2006-04-17
All that i can say ATM is that you are not alone.](*,)

---

### Post by Fitzcarraldo on 2006-10-07
*sunspots*,

Different version of the OS (6.06 Dapper Drake) to yours, but same Belkin card model number (F5D7010) as yours, so perhaps the following thread might be of some use:

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

---

### Post by sunspots on 2006-10-07
hi Fitzcarraldo,
Thanks for the link to the thread. I'll print it out and give it a go during the week (once my download limit has been reset for the month).

Regards
Peter

PS I have now upgraded, well freshly installed Unbuntu Dapper 6.06 over the previous.

---

### Post by sunspots on 2006-10-16
Hi Fitzcarraldo,
Well I finally got around to go through the notes from your brother. Tell him it worked (with a few hiccups).

Firstly, I must have been asleep when I wrote the original note. My Belkin is F5D6020 wireless card.

Anyway, I followed the notes and had a few hitches.

1. Where to find the drivers. Eventually found them on [http://www.drivermagic.com/](http://www.drivermagic.com/) (see step 6 in document)

2. What drivers to look for, for my Belkin F5D6020. Eventually found out that I needed (well thought at this stage) RTL8180.SYS, NET8180.INF (see step 6 in the link document)

3. Unable to copy to the directory /windows-drivers via the browser. Told I did not have sufficient permissions. So, copied to the desktop and then from the terminal server, used "sudo cp" to copy files to the folder. (see step 6 of the link document)

4. Replaced all mentions of rt2500 with NETR8180 or NETR8180.INF

5. After plugging in the wireless card, the "sudo ndiswrapper -l" just showed "netr8180 driver present". No mention of hardware present. (see step  15 in the link document)

6. "ifconfig" did not show "wlan0" but "eth1" (see step 16 in the link document)

7. Configured the card via "System > Administration > Networking", but it gave me an error that "eth1" did not exist and it then deactivated the card. (see step 18/19 in link document)

8. Rebooted the system but the card light just flashed and no results from pinging.

9. Clicked on reactivate for eth1.

9. Then followed step 22 in the link document, ie, "sudo gedit /etc/modules" and added the line, "ndiswrapper" with carriage-return at the end of the file. Then rebooted.

10. After reboot, the light was steady. But "sudo ndiswrapper -l" (minus el) still did not show the hardware being present.

11. ping of my favourite site worked. Then tried my browser and found websites.

Once again it worked in the long run.

Thanks

---

