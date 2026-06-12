---
title: "wusb54gc(version 3) wont work!"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by The_LinuX_Noob on 2010-01-28
I had originally posted this on the Beginner Talk forum, but i now realize that i should have posted it here.
Im completely new to everything Linux, ive never used anything other than windows and ive decided to jump to kubuntu.  And the only way i get internet is through a wireless usb Linksys WUSB54GC version 3.  It and the cd it came with wont work at all.  Are there some things kubuntu wont work with? And is this one of those things?

Thanks!

---

### Post by bkratz on 2010-01-28
> **The_LinuX_Noob said:**
> I had originally posted this on the Beginner Talk forum, but i now realize that i should have posted it here.
Im completely new to everything Linux, ive never used anything other than windows and ive decided to jump to kubuntu.  And the only way i get internet is through a wireless usb Linksys WUSB54GC version 3.  It and the cd it came with wont work at all.  Are there some things kubuntu wont work with? And is this one of those things?

Thanks!

Probably worth at least looking at

[http://ubuntuforums.org/showthread.php?t=1353044&highlight=WUSB54GC](http://ubuntuforums.org/showthread.php?t=1353044&highlight=WUSB54GC)

---

### Post by chili555 on 2010-01-28
> the cd it came with wont work at all.Well, Windows is not Linux is not Windows. They use entirely different systems for almost everything. Actually, there is a method to use the Windows drivers in Linux, but let's save that for another day!

I believe this device uses the *rt2870sta* module, which probably loaded by default already! The problem is often that another conflicting module also loads and they end up fighting. Let's see what is loaded. Open a terminal and do:```
lsmod | grep rt
lsusb
```Post the results of these commands and we'll get it sorted out.> Are there some things kubuntu wont work with?Very, very few.>  And is this one of those things?Nope.

---

### Post by The_LinuX_Noob on 2010-01-29
Well, im kind of a general computer noob.  What are modules and where am i supposed to be typing these commands?  Sorry for being such a noob!

Thanks

---

### Post by bkratz on 2010-01-29
> **The_LinuX_Noob said:**
> Well, im kind of a general computer noob.  What are modules and where am i supposed to be typing these commands?  Sorry for being such a noob!

Thanks

What Chili555 was looking for requires the use of the terminal.  In Ubuntu (don't know about Kubuntu, but probably close) it is under Applications>>Accessories>>terminal in the menus

You would have to type in the commands he asked for (one at a time) and copy/paste the outputs back here.  If any of them started with the word "sudo" they would require your password which will not be echoed back to you. Simply hit enter after putting in the command.

By the way--

lsmod | grep rt
lsusb

Those commands are ( LSMOD and LSUSB in lowercase not "1"s.

---

### Post by The_LinuX_Noob on 2010-02-02
ok, sorry i havent replied for so long, i got really busy.  And after researching it a bit more and trying ubuntu more in depth, ive decided to switch to ubuntu but i dont think its gonna matter at all.

So heres the results from typing those commands:

i typed lsusb and got:
     Bus 001 Device 004: ID 0bc2:3000 Seagate RSS LLC 
  Bus 001 Device 003: ID 1737:0077 Linksys 
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
  Bus 002 Device 002: ID 045e:009d Microsoft Corp. 
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 



and heres lsmod | grep rt:
   rt2800usb              37372  0 
  rt2x00usb              11548  1 rt2800usb 
  rt2x00lib              29756  2 rt2800usb,rt2x00usb 
  led_class               4096  1 rt2x00lib 
  input_polldev           3716  1 rt2x00lib 
  mac80211              181236  2 rt2x00usb,rt2x00lib 
  cfg80211               93052  2 rt2x00lib,mac80211 
  crc_ccitt               1852  1 rt2800usb 
  parport_pc             31940  1 
  parport                35340  3 ppdev,lp,parport_pc 
  agpgart                34988  2 drm,intel_agp


so thats it, what is all this btw?  To me its pretty much all gibberish.  And will this help me get the wireless usb's driver?


Thanks

---

### Post by chili555 on 2010-02-02
> what is all this btw? To me its pretty much all gibberish. And will this help me get the wireless usb's driver?*lsusb* asks the system to [COLOR="Red"]l[/COLOR]i[COLOR="Red"]s[/COLOR]t all the [COLOR="Red"]USB[/COLOR] devices that are connected. With that information, especially the Device ID, in your case, *1737:0077*, we can match up the appropriate driver to the device.

*lsmod* means [COLOR="Red"]l[/COLOR]i[COLOR="Red"]s[/COLOR]t all the kernel [COLOR="Red"]mod[/COLOR]ules, also known as drivers, that are now loaded. The pipe symbol | asks that the results be piped through another command, *grep*, which looks for a specific pattern, in this case, modules with rt in their name.

We see that rt2800usb is loaded, along with all its dependencies, rt2x00lib, etc. So your system thinks that is the correct driver and has it all ready to go. No conflicting modules are loaded, that I see.

The next step is to see if a wireless interface was created. Please open the terminal again and do:```
iwconfig
```That means, show me the configuration of all my wireless devices. You should get something like mine:> lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

[COLOR="Red"]eth1      IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 88:24:56:2A:99:29   
          Bit Rate:54 Mb/s[/COLOR] 
--- snip ---The highlighted part means, YES!, we have a working wireless interface! I suspect you do, too. Yours may be named ra0 or wlan0 or something else different from my eth1.

The final step is to click the Network Manager icon at the top right of your desktop and see if you see your network. Please see attached. If so, click on it and connect. Download updates, torrents, mp3s and enjoy!

Of course, if it all doesn't quite go as planned, post back and we'll help.

---

### Post by The_LinuX_Noob on 2010-02-03
owner@ubuntu:~$ iwconfig
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  wmaster0  no wireless extensions.
  
   
   
  wlan0     IEEE 802.11bgn  ESSID:""  
  
            Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
  
            Tx-Power=12 dBm   
  
            Retry  long limit:7   RTS thr:off   Fragment thr:off
  
            Power Management:on
  
            Link Quality:0  Signal level:0  Noise level:0
  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
  [FONT=&quot]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT][FONT=&quot]
What does this mean? Cause it didnt work.

Thanks

All those surprise faces are : 0 or : o
[/FONT]

---

### Post by chili555 on 2010-02-03
This all means your wireless interface is sitting idle because it hasn't associated with your network yet. What happened when you clicked the Network Manager icon? Did you see your network? Did it try to connect?

I like all the smiley faces!

---

### Post by The_LinuX_Noob on 2010-02-03
oh yea, i forgot about that part.  When i clicked Network Manager i saw the network i use but when i clicked it it started connecting, and then said it was disconnected, i tried it several times and got the same result each time

---

