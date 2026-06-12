---
title: "Working bcm43xx but no scan"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by VersusGod on 2006-06-10
**EDIT:  I FIXED THE PROBLEM! The solution is at the end of this post.**



Hey All.

I've been lurking in these forums for a long while.  I have usually been able to resolve my problems by reading many other posts.  This time, I haven't been able to find anyone quite in the same situation as I am now.

I'll try and be as thorough yet concise as possible.

I installed Kubuntu Dapper 6.06 on this laptop for the first time last week.
I had my bcm4306 card working beautifully after a short amount of time using the bcm43xx driver and the Experimental bcm43xx-firmware package.

Everything was peachy-keen unicorns and marshmallows.

I started with WEP encryption and was happy when I upgraded to WPA-SPK on my first try.

Every iwlist eth1 scan I would do would bring up my access point as well as a few neighbours.

This is no more.
```

sudo iwlist eth1 scan
eth1      No scan results
```

Is now what I am comfronted with.

**Circumstances**
I was trying out some aircrack tools before this happened.  Not to be malicious, but just to see how they work.

Having tried aircrack, and not having much success, I found aircrack-ng.  
I tried it some, including some ARP injection stuff.

About this time, a new version of bcm43xx-firmware showed up in my package manager.  Naturally, I selected to upgrade it.  Uh ohes!  It appears that the maintainer made a mistake with his webhosting.  I'm getting 403 errors!  Even with all gpg stuff configured properly.

The poop hits the fan.  Suddenly no ESSIDS are showing up, and signals show zero.  Time to start troubleshooting.

**What I have tried (not necessarily in this order)** 
Reloading bcm43xx module.
Rebooting
Re-installing old bcm43xx-firmware package
Installing new bcm43xx-firmware package
Installing firmware from wl_apsta.o using firmcutter
Trying different rates
Trying iwconfig eth1 essid on
Trying iwconfig eth1 ap any

**Current Situation**
```

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

This seems pretty standard with other posts which are asking for help.

I was concerned perhaps that the aireplay-ng or airodump-ng I was using may have put my card into promiscuous (or whatever equivalent) mode and that the card hasn't been able to return from it properly.  I looked at iwpriv.

```

          set_interfmode   (8BE0) : set   1 int   & get   0
          get_interfmode   (8BE1) : set   0       & get  80 char
          set_shortpreamb  (8BE2) : set   1 int   & get   0
          get_shortpreamb  (8BE3) : set   0       & get  80 char
          set_swencrypt    (8BE4) : set   1 int   & get   0
          get_swencrypt    (8BE5) : set   0       & get  80 char
          write_sprom      (8BE6) : set 512 char  & get   0
          read_sprom       (8BE7) : set   0       & get 512 char
```
```

iwpriv eth1 get_interfmode
eth1 get_interfmode:0 (No Interference Mitigation)
```

I've tried putting the mode into other Mitigation modes (1 and 2) but it didn't seem to make much difference. (Granted I may not have rebooted between each attempt.  Not sure if that matters).

```

>iwpriv eth1 get_shortpreamb
eth1      get_shortpreamb:0 (Short Preamble disabled)
```

I've tried enabling it, however I don't really know what it is.  Still no success.

I've tried using iwevent while trying a scan, but it doesn't seem to show anything helpful:
```

Waiting for Wireless Events from interfaces...
15:18:49.168375   eth1     Scan request completed
```

dmesg doesn't show anything out of the ordinary.  I no longer get any firmware loading errors like I did before I installed them.

I'm running kernel 2.6.15-23-386 /w kde 3.5.2

```
/lib/firmware$ ls
2.6.15-23-386         bcm43xx_initval06.fw    bcm43xx_microcode4.fw
backup                bcm43xx_initval07.fw    bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw    bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw    bcm43xx_pcm5.fw
bcm43xx_initval03.fw  bcm43xx_initval10.fw    frompackage
bcm43xx_initval04.fw  bcm43xx_microcode11.fw
bcm43xx_initval05.fw  bcm43xx_microcode2.fw
```


I have read the wiki page regarding bcm43xx and I have not had ndiswrapper installed.

**Have I fried my card?  How can I check?**

Any help would be greatly appreciated.

-VG

**Addendum with solution!**

I had a feeling the problem was something quite asinine.

After installing ndiswrapper and having no more luck, I finally came accross the problem:

```

sudo lshw -C network
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@00:0c.0
       logical name: eth1
       version: 03
       serial: 00:90:96:6f:f9:3e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0004000-d0005fff irq:10

```

Thats right. DISABLED!

Now how could this be?

Well, it turns out, that my switch-desktops key-combo is ctrl+F<desktop#>.

To the left of my ctrl key is the Fn key.  My F2 has a (((e))) symbol on it (with the stylized e from emachines), and I had no idea what it was until about 5 minutes ago.  It turns out, its the WIRELESS button.  So, I must have inadvertantly hit Fn+F2 instead of ctrl+F2 during one of my many desktop switches.  This killed my wifi card without any visual clues at all.  WONDERFULL

ARRRRRRRRRRRRRGH!

So, once I get back to the bcm43xx driver things should be peachy-keen unicorns and marshmallows once again.

Thanks for your time! 

-VG

---

