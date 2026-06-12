---
title: "rt2500: slows network (for EVERYONE connected)"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by Blue-Tiger on 2009-10-23
Hi there!

My Wireless card doesn't work properly, and hasn't for quite some time. Unfortunately, it doesn't just not work for me, but everyone else connected to the same access point will have a crappy reception once my card is active.

I'm currently running Karmic Koala, but the problem already existed in Jaunty, maybe even before that, but back then I didn't care since I had a wired connection available anyways most of the time.

However now I moved into a new house, and here we're 4 people sharing a connection over a wireless router. But once I'm connected to the router, everyones connection speed slows down to max~100 kb/s, usually much slower (sometimes it takes minutes to simply load a page). Also I have frequent disconnects.  Also on the router itself, the "wireless LED" is blinking when I'm connected (according to the manual that means there is some kind of problem with the wireless network, but it doesn't give much information apart from that). 

At first I thought my wireless card might be broken, but when I booted up Windows the problems went away, and the network was smooth again for everyone. So it has to be something to do with me. Here's some hardware infos:

```

tom@blulap:~$ lspci | grep RaLink
02:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

tom@blulap:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"BeBox"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:17:96:47:B1   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

EDIT: the iwconfig-output was made when I was sitting directly next to the router, so (according to the NetworkManager) I had 100% connection strength, but the strength drops quickly once I move away (if I get 60% when I'm only one room away I'm lucky).


Anyone having a similar experience or even a solution is welcome! :)

---

### Post by Firkløver on 2009-10-23
I can confirm the slow network with rt2500 (running karmic atm), though i have not tested the slowness with other systems running at the same time. 

I believe this is linked to the following kernel bug:

[http://bugzilla.kernel.org/show_bug.cgi?id=13362](http://bugzilla.kernel.org/show_bug.cgi?id=13362)

The bug has not been resolved in the mainline kernels (up to 2.6.32-rc5) that i have tested either. There is a thread about this in the karmic forums as well, but i reckon this is the right spot in a few days time.

---

### Post by Blue-Tiger on 2009-10-23
thanks for that information.

---

### Post by coffeecat on 2009-10-23
> **Blue-Tiger said:**
> even a solution is welcome! :)

I came across [this thread]("http://ubuntuforums.org/showthread.php?t=1211513&highlight=rt2500") earlier today. I don't know whether it will solve the problem other users of your network are experiencing, but you might want to look at it.

I've not tried the howto myself. I was stung by this rt2500 "regression" about a year ago and decided to use a different wireless chipset instead. It's a great shame this hasn't been fixed after all this time because it used to be that the rt2500 chipset was the one some people recommended as the most Linux-friendly. Not any longer. :(

**Edit:** by the way, if you look at the latest post (#29) by the op, this hasn't been tested in Karmic yet. No reason why you shouldn't, though. :p

---

### Post by Blue-Tiger on 2009-10-23
> **coffeecat said:**
> I came across [this thread]("http://ubuntuforums.org/showthread.php?t=1211513&highlight=rt2500") earlier today. I don't know whether it will solve the problem other users of your network are experiencing, but you might want to look at it.

I've not tried the howto myself. I was stung by this rt2500 "regression" about a year ago and decided to use a different wireless chipset instead. It's a great shame this hasn't been fixed after all this time because it used to be that the rt2500 chipset was the one some people recommended as the most Linux-friendly. Not any longer. :(

**Edit:** by the way, if you look at the latest post (#29) by the op, this hasn't been tested in Karmic yet. No reason why you shouldn't, though. :p

I have tested it (in fact, if you look at the output of my iwconfig, my transfer rate is set at 11M), but it just doesn't do the trick for me :(

---

### Post by Firkløver on 2009-10-23
The workaround described in the other thread mentioned here fixed the problem in Jaunty. This was because we then used the old rt2500 driver which had a variant of this bug. The new driver rt2x000 has the same bug it seems but does not allow us to manually set the the bitrate (even if it appears like it does). 

Unfortunately that means we have to wait for a kernel fix or find some way of reverting to the old driver.

---

### Post by Blue-Tiger on 2009-10-24
I installed an old Kernel (2.6.28) from here: [http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-15-generic](http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-15-generic)

This of course required me to manually set my transfer rate to 11M (as mentioned in all the other threads). Any other transfer rate seemed to influence download-speed an connection strength in a negative way.

When I'm close to the router this gives me awesome download speeds (~ 700 K/s), however moving further away (e.g. my desk) reduces the speed very noticably (~80 K/s). At first this also did wonders for my connection strengths (giving me 66-85% at my desk, where I usually got only 30-40%). However the connection strength seems to drop down to 20% or so (taking with it the download speed, wget sometimes even temporarily looses the connection to the download-server). 

I haven't yet been able to check with my flatmates if their connection speed also improved or not, I'll let you know once I get to it.

---

