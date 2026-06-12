---
title: "Wireless Firmware"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by xLegacyy on 2011-05-10
First of all I'd like to say that I'm absolutely loving Ubuntu (even though I'm a complete noob when it comes to computers). Before I go on to my main question I was actually wondering something. I downlaoded the WUBI thing and have Ubuntu installed like that, would it be fine if I just kept it dual booted like that forever, or should I download a full version or something?

Now on to the main question. First of all, I know there have probably been hundreds of these threads created, but like I said, I'm a complete noob when it comes to computers in general that I'll need a noobs guide on how to fix it. Like many other people when I log into Ubuntu I get this firmware issue, I'm on an HP DV4 laptop, any help?

Thanks.

---

### Post by mikewhatever on 2011-05-11
A wubi installation is as full featured as the regular one, with the exception of wubi installing into a file inside the Windows file system, as opposed to a dedicated partition. I don't know if you can keep it forever (surely can for a long time), it would probably be best to do a proper installation at some point.

The missing firmware message means the driver for your wireless card is not installed. Hook up an ethernet cable, and if the driver is available, you should get a prompt to install it. If nothing happens, you'll need to figure out the card's model. The output of **lspci** from a terminal window should show what it is.

---

### Post by xLegacyy on 2011-05-11
Hopefully this is the correct sentence:

Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01).

Also every other time I run Ubuntu I get this error where a bunch of hex values appear on a black screen and I get a bunch of other stuff, I'll copy some of it down th next time it happens.

---

### Post by mikewhatever on 2011-05-11
Yes, that output is perfect. If you don't get a driver installation prompt, open the Software Center and search for the **bcmwl-kernel-source** package. Install it, and the wireless should work after a reboot.

---

### Post by xLegacyy on 2011-05-11
I've been trying to copy and paste that into the search bar of the software thing but it's not coming up with any hits. =(

---

### Post by mikewhatever on 2011-05-11
Hm..., that package is available for all currently supported versions of Ubuntu. Do you know what version you have installed?
```
cat /etc/lsb-release
```

---

### Post by northd_tech on 2011-05-11
@XLegacy-

My HP DV98xx laptop has a Broadcom 4321AG wireless (usually reported by Ubuntu as "4328": 

> 03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03) )

Mine seems to prefer the Broadcom "STA" wireless- and that SOMETIMES allows the 802.11n speed (although my WiFi connection usually reports ~54 Mbps).  The "STA" driver has mostly worked "out of the box"/Ubuntu install since about Ubuntu 9.04 or so, but I've been reading about many wireless troubles with 11.xx recently.

This is a pretty good, recent thread about the Broadcom family wireless:

[http://ubuntuforums.org/showthread.php?t=1748245](http://ubuntuforums.org/showthread.php?t=1748245)

Your Broadcom 4322 should be quite similar to my Broadcom "4321AG/"4328", so we could examine my working wireless setup if you still encounter problems for some reason.  I posted my installed Synaptic Package Manager specs at post #9 for my working "STA" WiFi connection:

[http://ubuntuforums.org/showpost.php?p=10763563&postcount=9](http://ubuntuforums.org/showpost.php?p=10763563&postcount=9)

(When you run into the "b43" stuff- you might want to consider that my "4321AG"/"4328" was also able to use the "b43" Broadcom fixes with the slower speed routers just fine, too).

I believe that you will want to AVOID any of the **specific** fixes/threads for the Broadcom "4318 [Airforce One]"- that one is kind of a 'horse of a different color.'

It might be worth you posting the output from these terminal commands though:

```
lspci -vnn | grep 14e4

lsmod

```

---

### Post by xLegacyy on 2011-05-11
Nvm guys the driver started installing now. Thanks a lot for the help. ^^

---

### Post by mikewhatever on 2011-05-11
My bad, it should have been **cat /etc/lsb-release**. 
Fixed above as well.

---

### Post by northd_tech on 2011-05-11
> **xLegacyy said:**
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

Module                  Size  Used by
**b43**                   318638  0 
mac80211              294370  1 **b43**
[COLOR=DarkOrange]hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi[/COLOR]
ssb                    51945  1 **b43**
r8169                  48022  0 

Well, it looks like you have the "**b43**" modules already inserted into your Ubuntu kernel, and most of the "b43" stuff is there that I remember those needing.  I'm a little concerned about that "[COLOR=DarkOrange]hp_wmi[/COLOR]" modules that I highlighted in [COLOR=DarkOrange]orange[/COLOR] though- some laptops have "issues" with factory wireless "drivers" preventing the wireless from working for whatever reason(s).  All of that orange stuff might be perfectly fine though- I've not seen those on my HP but I've got an old-fashioned ON/OFF switch on the front of my HP for wireless- yours might have a "software" wireless switch that "needs" those modules for some reason.

Can we also see the output of these terminal commands?

```
cat /etc/modprobe.d/blacklist.conf

ls /etc/modprobe.d/

cat /etc/modules

cat /etc/issue

```

EDIT:  Well- glad to hear the wireless fixed itself somehow.  You might want to keep these 2 threads handy in case the newer Ubuntu versions also have "wireless issues"- that's pretty common.   Also, my "full install" Ubuntu seems to repair my Windows partition on a VERY regular basis- you might want to consider a dual boot "GRUB" install as you gain more experience with Ubuntu.  Running **Linux under Windows** will probably circumvent several of the advantages ( data recovery, "crash" survival, virus resistance, etc. ) that Linux offers you.

---

### Post by northd_tech on 2011-05-11
> **xLegacyy said:**
> 
Also every other time I run Ubuntu I get this error where a bunch of hex values appear on a black screen and I get a bunch of other stuff, I'll copy some of it down th next time it happens.
Here, you might be describing a **normal** Linux boot sequence output (when it's not hidden by a "pretty?" :confused: splash screen graphic)-  I'm kind of "old school" Linux and disabling the Bill Gates-esque splash screen and ENABLING the verbose diagnostic messages is one of the first things I do on nearly ANY fresh Linux install...

---

### Post by xLegacyy on 2011-05-11
I'm hoping to get familiarized enough with Linux to a point where I can uninstall Windows completely, but I don't think that will happen anytime soon.

Lol oddly enough, even though I hate Windows, I get this homesick feeling when I'm using Ubuntu and not Vista, wierd eh?

---

### Post by northd_tech on 2011-05-11
> **xLegacyy said:**
> I'm hoping to get familiarized enough with Linux to a point where I can** uninstall Windows completely**, but I don't think that will happen anytime soon.

Lol oddly enough, even though I hate Windows, I get this homesick feeling when I'm using Ubuntu and not Vista, wierd eh?

Although I'm fairly against Micro$oft products myself, I'd say that the above statement is a little "drastic"- I'm still a HUGE fan of having a "plan B/plan C/D/E..."/redundant operating system(s), and apparently AutoCAD (or ANY OTHER "DECENT" CAD program and many professional GIS systems seem to "require" Windoze still).  A family member in the Arts industry tells me that Adobe Creative Suite also requires Windoze (7 only, on the "newer" versions I believe).

Also, there are (sometimes roundabout) ways of making Linux look like Vista, or Win7, or Mac OS/X... :

[http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/](http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/)

[http://www.themelinux.com/](http://www.themelinux.com/)

Finally FWIW, *I would personally recommend* the "LTS" versions of Ubuntu (and "fixing" individual hardware/software issues like **wireless** as needed) rather than running the "newest/best-est?" thing under the Ubuntu sun... :

[http://www.ubuntu.com/business/desktop/long-term-support](http://www.ubuntu.com/business/desktop/long-term-support)

---

### Post by xLegacyy on 2011-05-11
Okay thanks, also I have another question that is kind of off topic, but I don't want to create another thread for it.

When I go into properties of the system looking thing (sorry I don't have my laptop in front of me so I can't check its exact name or location) it says I only have about 12GB of space left, and ~ 15-16 GB that have been used, obviously this isn't close to being 50/50 with Windows, is there any way I can take away some space from Windows and add it to Ubuntu?

---

### Post by mikewhatever on 2011-05-11
Since this is a wubi install, you are limited to the size of the virtual file system.

---

### Post by Pilot22 on 2011-05-25
I too am using an HP DV4 with the same wireless card. I ran dual boot using Wubi, and now that I have done a full install I am having trouble with my wireless card not installing. I have tried many of the fixes I have found here and on the net elsewhere, to no avail. Apparently, using the windows driver and firmware kept it working before. 
I am still attempting to get on line wirelessly. 
So, I would back up your windows drivers before doing a fresh install, and maybe do a dual boot just in case, using a full non wubi install. And if you want to share your windows wireless card drivers I would love a copy, as this was one suggestion I could not follow as I deleted windows on my install. 
I have downloaded a windows driver from Broadcom, which does not seem to help even when I can install it using WINE, so good luck with your HP.

---

### Post by Pilot22 on 2011-05-26
BTW, I was able to get my wireless working on my HP DV4, with the Broadcom 4322 card. But for my Ubuntu 11.04 distro to work, I had to install an earlier distro, and that one was able to get the wireless card working right from the get-go and then I did updates to get me back to 11.04. I know this is not a bug fix, but it seems to work with this particular PC. So if you decide to dump windows,you may want to have a second CD for Ubuntu.

---

