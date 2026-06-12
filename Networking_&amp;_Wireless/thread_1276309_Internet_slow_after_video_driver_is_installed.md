---
title: "Internet slow after video driver is installed"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by sakundiak on 2009-09-26
I'm fairly new to ubuntu but i got my hp laptop running jaunty and i love it. Wireless works great! My question is when i run a speed test i average close to 30mb down and 1mb up then after in install nvidia graphics driver version 173 my connection slows right down to 1mb down and .5mb up. I uninstalled the driver and my connection goes right back up to 30mb down. Why would my video driver interfere with my network connection. My wireless card is a broadcom if that helps. Thanks

---

### Post by sakundiak on 2009-09-27
Ok this might seem like a stupid question but i tried it five more times this morning with the same results. As soon as i install my nvidia driver for my graphics card my connection seems to get throttled right back and is very glitchy. It will disconnect for no reason, seems like it will get bursts of data then nothing, web browsing is very slow. Any one have any ideas since i would sure like the benefits of having the nvidia driver installed but if it means a slow network than i guess i will do without.

---

### Post by sakundiak on 2009-09-28
bump

---

### Post by frito on 2009-10-04
I am having the exact same problem. Kubuntu with nvidia-current (same thing happens with nvidia-173)
Using an ath5k wireless adapter on a WEP network.

---

### Post by houstonbofh on 2009-10-04
What graphics card?  Shared memory?

What nic?

How is your other hardware?  Could the nvidia driver allowing compiz be killing your performance, for example?

---

### Post by frito on 2009-10-04
No the rest of the system is fine. Neither compiz nor KDE effects are enabled.
Its a PCI wifi card and a 7600GT AGP card. No shared memory
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home"
          Mode:Managed  Frequency:2.447 GHz  Access Point: ME:GA:SE:CR:ET
          Bit Rate=54 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Iwconfig output does not change when nvidia graphics are installed

```
lspci
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a2)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:09.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
05:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

With the boring stuff removed

```

---

### Post by houstonbofh on 2009-10-04
Both Atheros and nvidia use drivers that do odd stuff in the kernel.  They are reacting together, and not in a good way.  You can try the madwifi drivers and see if that helps.

---

### Post by frito on 2009-10-05
> Both Atheros and nvidia use drivers that do odd stuff in the kernel. They are reacting together, and not in a good way. You can try the madwifi drivers and see if that helps.

Does that actually make sense? They dont even have the same NIC.

I would rather not go to the hassle of blacklisting ath5k etc. I guess I can just stick with the open source drivers for now... sigh... 3D

Tangent: If Nvidia drivers do wierd things, are the ATI drivers any better? or is graphics just a c**pshoot? both open and closed. 
I know its always been the reliability sticking point in my mind for linux but I've never run into a problem like this.

---

### Post by houstonbofh on 2009-10-08
I have been an nvidia bigot a long time.  But it looks like the open source ATI drivers are really coming up.  Phoronix did a benchmark, and the FOSS drivers beat out the ATI binary drivers!

So, I just don't know any more.

---

