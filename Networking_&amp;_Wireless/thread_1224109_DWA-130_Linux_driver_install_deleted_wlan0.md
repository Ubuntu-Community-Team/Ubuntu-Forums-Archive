---
title: "DWA-130 Linux driver install deleted wlan0??"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by MrCode on 2009-07-27
Hi, all.  I have been trying to get wireless working in Ubuntu for a while (a couple weeks, in fact), with hardly any luck.  I have two OSes:  Windows XP (came with computer), and Ubuntu Jaunty (installed on separate hard drive).  I also have two USB wireless adapters, both of which work in XP: a Netgear WN111v1, and a D-Link DWA-130.  I've had about an ounce of success with the Netgear under ndiswrapper, as it would *sometimes* connect, but after a while it didn't seem to want to connect at all.  D-Link provides a [Linux driver]("http://www.dlink.com/products/?tab=support&pid=DWA-130&rev=DWA-130_revC") for the DWA-130 on their website, so I figured I'd try it to see if it'd work.

I tried using method 1 in the readme file, only to have it error out when doing a [sudo make install], so then I tried method 2, and it seemed to work ok, but after I ran the wlan0up script, I looked in the NetworkManager applet to see if it was detecting wireless networks, and it just said "Wired Network: [something, I don't remember exactly]".

Then I pulled up terminal, did an [iwconfig wlan0], and it gives me the message: [wlan0:  No such device] or something along those lines.  Is there any way I can get that interface back without re-installing Ubuntu and starting all over again??

PS:  yes, I did look at the other interfaces and it doesn't detect the card as ath0 or ra0 or anything like that.

---

### Post by MrCode on 2009-07-27
Ok never mind, it's back after I rebooted this morning.  Still refuses to connect with the Netgear adapter + ndiswrapper drivers, though.

EDIT:  I'm thinking it may have to do with DHCP and/or DNS...I can sometimes get it to connect with "DCHP (addresses only)" but not regular DHCP.  I can also guarantee a connection if I use Manual. However, I get no internet when I use either of these.  Can anyone help?

---

### Post by MrCode on 2009-07-28
Maybe I haven't provided enough information:

Network encryption: WPA-PSK
Adapter (currently in use): Netgear WN111v1 USB
Driver: netmw245.inf + Mrvw245.sys under ndiswrapper
System:

OSes: Windows XP + Ubuntu 9.04
   CPU: Pentium 4 @ 2.66GHz
   RAM: 1.5GB
   GPU: NVIDIA GeForce 7300GT 512MB (I have Compiz enabled, if that would make any difference.  Not that I really think it would, but at this point I'm about ready to try anything.)

As far as I know Netgear dosn't provide a Linux driver for their adapters.  Only routers (which is stupid, if you ask me).  The adapter works perfectly in XP

---

### Post by bkratz on 2009-07-28
[QUOTE=MrCode;7690433]Maybe I haven't provided enough information:

Network encryption: WPA-PSK
Adapter (currently in use): Netgear WN111v1 USB
Driver: netmw245.inf + Mrvw245.sys under ndiswrapper
System:




I have the same DWA130; mine is a version A: " the linux drivers are only for version C ". You seem to have changed to a different usb adapter, the Netgear.  Although you mention the Netgear later on the drivers you have loaded under wrapper are exactly the same as the ones I use "netmw245.inf + Mrvw245.sys". I know nothing about the Netgear version, but unless it has the same chipset  it appears you are using the drivers for the Dlink with the Netgear.
By the way mine works fine with wpa2 or unencoded, I just have to make sure I plug it in and remove it after bootup and before power down.  Try plugging in the dlink again! Feel free to PM me.

---

### Post by MrCode on 2009-07-29
Thanks for the reply, but I know that these are the Netgear drivers because I got them from the windows folder after I installed them from the CD.  I also tried the drivers that came on the D-Link's installation CD, but ndiswrapper appears not to like them, as they won't work at all.  I've also determined that I do in fact get an internet connection using Manual configuration, but it can't resolve DNS names.  I can ping to outside websites using their IPs, but not their domain names.  Firefox won't let me use an IP address as part of the URL (i.e. [http://64.233.161.147/](http://64.233.161.147/), which is Google), complaining "Invalid address '/'".  I'm thinking it's trying to incorporate the "/" into the IP, which of course is going to return an error.

Is there any way I can get it to resolve the domain names without using DHCP?  I've tried putting the IP address of my ISP's home website in as a DNS server, but that gets me nowhere.  What address would I need to know to put in as the primary DNS server?

---

### Post by bkratz on 2009-07-29
Most around here seem to recommend using the free OpenDNS server. 

[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by MrCode on 2009-07-29
Thanks!  So far it seems to be working...though it took forever until I got an actual net connection (tried pinging their address, didn't return anything but "Destination Host Unreachable" for a few minutes).

I don't know how permanent this is, but I'll take advantage of it while I can!

---

