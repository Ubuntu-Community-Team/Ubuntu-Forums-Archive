---
title: "No proprietary drivers are in use on this system"
date: 2011-01-25
forum: Multimedia Software
---

### Post by balaji31d on 2011-01-25
Hi, have an issue with the audio staggering while playing music/ video rainbow and stuttered during loading / video shaking while playing movie. (cpu usage hitting 100%)

System: (this is a clean install)
Laptop model: Fujitsu Lifebook S2210
OS - ubuntu 10.10 (software updated) 
AMD Turion 64x2 (installed 32bit OS)
Video- ATI (RS482 Radeon express 200M)
Audio - ATI (IXP SB4x0 HD Audio controller)

Steps Tried:
1. edited /etc/pulse/default.pa to include tsched=0 (issue no change, reverted)
2. updated kernel to 2.6.36 and 37 (issue not changed, had new issues, revered)
3. installed fglrx (additional drivers reported 'No proprietary drivers are in use on this system') - no change, so purged fglrx . (Still have jockey and fglrx-modaliases installed/ visual effects is set to none)

Any help is appreciated.

---

### Post by balaji31d on 2011-01-25
Appreciate someone throwing some light

---

### Post by cascade9 on 2011-01-25
ATI x200 hasnt had support from ATI for a long time now. IIRC the last ubuntu version to have ATI drivers for that card was 8.10 or maybe 9.04. 

Were you trying to play HD videos? That CPU probably doesnt have quite enough power for HD, that is why you were having problems.

---

### Post by balaji31d on 2011-01-25
Below is an example:

video- dimension (1280x 688) | codec (h.264/avc) | 24 frame/s | bitrate 2028 kbps
audio- mpeg-4 aac audio | surrund 5.1 | 4800 hz | 319kbps

I agree that i am overloading the pc but even if i play a normal mp3 file in movie player and drag the progress bar randomly, my cpu fan will go wild and the usage increases to say 80-90%

I also experience wireless loss very frequently and i guess it is because of the drivers too. is there any suggestion for my next action?

btw, pulse audio is not the cause (issue happens even after uninstall)

---

### Post by Yellow Pasque on 2011-01-25
Smooth video playback might be out of the question. :\
What wireless chipset do you have?:
```
sudo lshw -C network
```

---

### Post by balaji31d on 2011-01-26
> **Temüjin said:**
> Smooth video playback might be out of the question. :\
What wireless chipset do you have?:
```
sudo lshw -C network
```


Hi, Please find the wireless chip details.

description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:3e:6d:a7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:c0300000-c030ffff

---

### Post by Mark Phelps on 2011-01-26
> **cascade9 said:**
> ATI x200 hasnt had support from ATI for a long time now. IIRC the last ubuntu version to have ATI drivers for that card was 8.10 or maybe 9.04.

+1 -- it was 8.04.

The only reason you're getting ANY display is because you purged the fglrx drivers.

That's a really low-end integrated video chipset.  I would be very surprised if you get decent 3D video performance using it.

---

### Post by balaji31d on 2011-01-26
True - When i installed fglrx, my monitor displayed little-nothing and then i had to purge it to get into working gui.

Surprisingly, when i play a movie (big file) in the morning after having my machine off for a long period, it does play well and then slowly after 2 - 3 minutes, my cpu usage will start to grow (witnessed by top). In the evening , after having it ON for a while, if i play a file, immediately it will say no.. :)  i guess its no fault with the OS - its my machine.

btw, i had to mention that, when i installed kernel 2.6.36 (my monitor will OFF and ON - this will be in cycle with 2 sec interval)
but, when i installed kernel 2.6.37 - my gui performance was comparatively v.good but had errors pertaining to some controller during startup.

---

### Post by balaji31d on 2011-02-08
Since this issue is pertaining to the shortcomings of the video device i have and the overload i am trying to put in, this has nothing to do with ubuntu drivers. i mark this thread as solved.

---

