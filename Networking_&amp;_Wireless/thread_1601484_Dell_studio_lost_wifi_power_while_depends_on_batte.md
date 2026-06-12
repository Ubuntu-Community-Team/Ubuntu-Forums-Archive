---
title: "Dell studio lost wifi power while depends on battery"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by morefeo on 2010-10-20
Hi all, I'm expecting a issue with my latptop (dell studio 1558) and its wireless card (broadcom bcm 4312, I use broadcom sta drivers). When I use the energy adapter it goes fast, good signal and all, but when I disconnect it and use the battery it goes slow as hell (less than 2mb) and makes bad ping for everything(more than 200ms).

I've not seen any option in the battery panel to increase its perfomance, what could be the problem?

Sorry for my english and thanks for the help.

---

### Post by morefeo on 2010-10-21
Some help? Is anybody expecting the same problem? I can't even use the laptop for what was designed for -portability- without proper wifi power.

Is there a hidden power option for that?

@Edit (Some information):

With AC adapter:

> [IMG]http://img808.imageshack.us/img808/7505/999715439.png[/IMG]

eth1      IEEE 802.11bg  ESSID:"WLAN_C0"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <I'll hide it>  
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr:  off
          Encryption key: off
          [COLOR="Red"]Power Management: off[/COLOR]
          Link Quality=5/5  Signal level=-57 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:503  Invalid misc:0   Missed beacon:0

Battery:

> [IMG]http://img694.imageshack.us/img694/8600/999716460.png[/IMG]

eth1      IEEE 802.11bg  ESSID:"WLAN_C0"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <I'll hide it>   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr :off
          Encryption key: off
          [COLOR="Red"]Power Managementmode:All packets received[/COLOR]
          Link Quality=4/5  Signal level=-58 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:503  Invalid misc:0   Missed beacon:0

The only difference I can appreciate is the power management mode, as highlighted. I'll try this [http://ubuntuforums.org/showthread.php?t=1360901](http://ubuntuforums.org/showthread.php?t=1360901) and see if it actually works.

Sorry for my english.

---

### Post by bontana on 2010-10-23
Hi,

are you still experiencing this problem? I have a simmilar one but far more drastic.
withour the power cable im barely able to open a site. 

the solution from your link helped?

---

### Post by morefeo on 2010-10-24
Nope, it didn't help, but now I'm expecting the problem with AC adapter too.

For now this command works: sudo iwconfig wlan0 power off

While wlan0 is the name of your wifi connection in iwconfig.

---

### Post by bontana on 2010-10-26
yeah, 
"sudo iwconfig wlan0 power off(eth1 in my case)" is working. It can be easy added into some kind off autostart to the init.d but..............

I dont this this is proper way to do it. looks like a bug to me.....

did you noticed any weird behaviour after applying this command?

---

### Post by morefeo on 2010-10-27
> **bontana said:**
> yeah, 
"sudo iwconfig wlan0 power off(eth1 in my case)" is working. It can be easy added into some kind off autostart to the init.d but..............

I dont this this is proper way to do it. looks like a bug to me.....

did you noticed any weird behaviour after applying this command?

No at this time.

---

### Post by jordanthompson on 2010-11-03
This has been driving me CRAZY!!! Thanks for the post - it is working for me too - now.  Until I read your post, I didn't make the connection between bad wifi connection and no power:oops:

---

