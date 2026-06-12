---
title: "Ipwraw with ipw3945 cant turn on!?!?"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Nosss on 2008-12-28
Hi,
I am having a bit of a problem, I have looked about but cannt seem to find a threat or help online..
I am running Ubuntu 8.10 and have IPW3945!. I am attempting to use aircrack-ng and everything works fine, up till the point where i attempt to scan. So I choose to test ipwraw and ipw3945 by typing

[PHP]iwlist scanning[/PHP]

When I have not patched the Ipwraw-ng-2.3.4 it comes up with wlan0 worked completly fine. After i patch it on it comes up with not able to scan with devices found. I was wondering if I have to turn it on or something i have done 

[PHP]ifconfig wlan0 up[/PHP]

It does not seem to do anything tho, does anyone know a code to help me with this problem. something like...enable wlan0 lol! Any help would be greatly appreciated. Thanks

Nos

P.s Sorry for double posting on other forum, I dont kno which one this would most fall under

---

### Post by Marques de Sade on 2009-01-27
I found information about that on the web, try this:

type:

iwconfig

ubuntu says:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"my essid"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1C:F0:3D:xx:xx 
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality=43/100  Signal level=-83 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

you type:  

modprobe -r iwl3945

//to deativate the actual driver

modprobe ipwraw 

//to activate the ipwraw driver that lets  the wifi bridge in mode monitor

if you type again "iwconfig" you can see that the interface "wlan0" has changed to wifi0 and other called rtap0 that I haven t found it's function at all.

I hope It help you to put in on.

Sade

---

### Post by SmarterThanMyPhone on 2009-04-06
wifi0 should be your injection source, and rtap0 is the monitor side. That could be backwards but I'm pretty sure thats the idea.

---

