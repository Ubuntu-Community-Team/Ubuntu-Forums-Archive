---
title: "C an't Get Wireless Going on HP G60 Notebook"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by oldefoxx on 2010-11-30
My grandson is now running on Ubuntu, but I tried an upteem dozen times to get it to install and have Wireless working, and two times the light went from orange to blue, but some later problem caused me to do the install over, and when I did that, I would lose the wireless mode.  And every attempt I made with the Network settings under System/Preferences or System/Administration did not help.

Now I wrote here about my long effort getting wireless going in my own L355-S7915 Toshiba notebook, and how I finally beat it without actually knowing what I did that finally got through, but that won't work on this HP G60-630US model.  Fact is, HP doesn't neven name the motherboard or the chipset, or the Wireless Adapter involved.  I keep searching for more specific language, but nothing turns up.

If anybody has found a way to beat this thing, I sure would like to know about it.  One thing I remember doing was using wicd in place of Network Manager at one point, and it really did work better on my machine, but I can't find wicd as something I can install now with the newer versions of Ubuntu.  So far I have tried 9.04, 9.10, 10.04 LTS, and 10.10, and my sone is presently making his first shot at Ubuntu using 9.04 64-bit version.  Still no wireless.  If it shows up in a screen menu, and it doesn't always, it will be grayed out and might show that it is disconnected, and I don't know how to connect it.

Any help would be much appreciated.  Again, this is an HP G60-630US laptop I am dealing with here, and stuff I went thru way back then has gotten lost in the midst of my 69 year old collection of memories. I went back through what I wrote then, but it is not a match to what I am dealing with now.

---

### Post by Davste on 2010-11-30
Hi

what do you mean when you say 
      > HP doesn't neven name the motherboard or the chipset, or the Wireless Adapter involved. 

can you go on linux and type this in so we can try to get the chipset name?

```
lspci -v | less
```

---

### Post by oldefoxx on 2010-11-30
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information <?>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, fast devsel, latency 0, IRQ 2299
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5110 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, fast devsel, latency 0
        Memory at d2500000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 50e0 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 50c0 [size=32]
        Capabilities: [50] PCIe advanced features <?>
        Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
        Subsystem: Hewlett-Packard Company Device 360b
:

---

### Post by Davste on 2010-11-30
Sorry.... can you do that again and hold enter so I can see all the way down to the bottom? Thanks

A lesson from experience: when installing ubuntu, connect it to the ethernet first - using a cable - and then let it download all the updates. Doesn't always work.. but hey. Usually internet will work instantly when you plug in the cable, so you can conveniently paste the results from the laptop itself.

---

### Post by oldefoxx on 2010-11-30
Oh, I've plenty of experience in setting up Ubuntu, and nearly always use the cable connect approach first.  In fact you have to in order to do the install if the wireless doesn't connect,  Why it works once in a great while but fails other times is a mystery, and Network Manager seems really limited when it comes to helping out or solving the problem.

I can try do do another dump like you ask, but my ex-son in law has the machine in his hands at the moment and is disinclined to give it up,  So I will repeat your requested process a bit later on when he shoves off.

It seems strange you can pick up any hand held and have instant network connectivity with no struggle, but can't do the same thing with a PC going wireless without this horrific battle over drivers and getting extra code run to surrmount some roadblock that always crops up in some cases, even on the laptops and notebooks of my experience.  It seems they only work if still running on from the factory code.

Hold on, my ex-SIL just handed the machine back over.  I will do that now.

---

### Post by oldefoxx on 2010-11-30
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: fast devsel, IRQ 11
        Memory at d4704000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 3

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, fast devsel, latency 0, IRQ 27
        I/O ports at 3000 [size=256]
        Memory at d0410000 (64-bit, prefetchable) [size=4K]
        Memory at d0400000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at d0420000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
        Capabilities: [cc] Vital Product Data <?>
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-00-01
        Kernel driver in use: r8169
        Kernel modules: r8169

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Hewlett-Packard Company Device 303f
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
        Capabilities: [170] Power Budgeting <?>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

(END)

---

### Post by oldefoxx on 2010-12-01
Okay, I had to hold down the Enter key to get all the missing lines included.  Then I saw the critical pieced of interesting info:

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

So I took the AR9285 Wireless and searched with it, and found a related thread that suggested that the AR9385 module was missing from 9.04 and how to get it added.  I'm using 9.10, but maybe it is missing threre as well.  So I dropped the version name reference at the end of the command and added *.  The recompile ran for about an hour, but it looks like it solved the problem.

---

### Post by Davste on 2010-12-01
Thought so. You have exactly the same problem I do, with exactly the same driver. The moment I manage to fix mine, I will  tell you how, and believe me, I'm determined to fix it. 

I'm trying to get it working on the 10.10, instead of 9.10 though. It seemed to work out of the box, but it was inconsistent, it kept disconnecting.

If you decide to install 10.1, tell me this - When it does work, quickly type in iwconfig and tell me the bitrate. When it doesn't, do the same, and post both results here.

One more thing, does Ethernet work?

---

### Post by Davste on 2010-12-01
Many people from previous threads said they managed to get it working on 9.4, but I'm just not happy with 9.4..... I want the latest and greatest :P

looks like I'm one of the first to deal with this on 10.1, I have not been able to find a thread yet with the AR9285 on ubuntu 10.1!

Ubuntu is a wireless nightmare. That's what I found out, exactly after I tried it out. I really wish that in this sense, it could work like windows does. Put in cd > install driver > WiFi works. But no... we have to get things all complicated and dirty.

---

### Post by desnaike on 2010-12-01
Hi everybody I have the HP G61 with the same wifi card and it works out of the box on 10.04/10.10 on 3 distros k/x/ubuntu no problems so just maybe it's not the card causing the problem.

---

### Post by Davste on 2010-12-01
I don't have an hp but an EEE PC, but it has an AR9285 chipset with ath9k drivers. I tried connecting to many different WiFi networks, and it works fine.... for 2 minutes. Then I have to reconnect for it to work again. I am really frustrated that I can't get it to work, I'm going to try ndiswrapper next. After all, it works flawlessly on windows. Could it be a network configuration problem? I don't know. I tried disabling ipv6, and many different settings. I have spent days now, searching this forum with no success. It's a pity really, I can't wait till I get WiFi to work, then remove windows once and for all.

---

### Post by oldefoxx on 2010-12-03
[http://ubuntuforums.org/showthread.php?t=1514492](http://ubuntuforums.org/showthread.php?t=1514492) **AR9285 Will Detect Wireless-N Network But Will Not Connect**

Commands used in that thread or related from other threads:
  sudo -s
  iwconfig
  lshw -C network
  ifconfig
  lspci -v | less
  rfkill
  modprobe
  wicd

That thread indicated that support for the AR0395 was removed from the Linux 9.04 kernal, but gave this basic instruction for adding it back, which involved a recompile effort, something that took well over an hour on my PC.  It was not for the same Ubuntu version (9.10 in place of 9.04), but did the trick:

  > Under Lucid, installed 'linux-backports-modules-wireless-lucid-generic', shows 150 Mb/s throughput, much more consistent signal strength.

Cheers

Nick

> Some routers can be funny about mixed n/g networks.

Have you tried using wicd instead of network manager - some threads imply that network manager may be [part of] the problem.

Cheers

Nick
> Atheros driver built in the kernel so it should work with Ubuntu 9.10 (it has linux kernel 2.6.31).
However I found a thread about this: [http://ubuntuforums.org/showthread.php?t=1244686](http://ubuntuforums.org/showthread.php?t=1244686)
They have the same problem with this Atheros card, however they use older Ubuntu with older kernel. I think it should work well with Karmic. They installed the backports (on Ubuntu 9.04) in order to get the driver you currently use, but you can also try to install the backports modules, maybe there is a newer backported Atheros module wihich works.
You should attach more information about your problem:
- dmesg
- lsmod
  iwlist scan
- Network Manager log (I don't know here you can find it)
I use wicd not Network Manager to connect, you can try it if you want, but it probably won't fix the problem, maybe help to debug it. Wicd has quite detailed log: /var/log/wicd.log
Wicd guide for Karmic: [http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu)
Maybe someone who know Network Manager better can help you.
All in all if it is a driver problem installing a newer kernel probably solve your problem. It can also be a bug in Network Manager, maybe it works with wicd. It should work, happy bug hunting.

apt-get install linux-backports-modules-$(uname -r)

do-release-upgrade -d
(or in a graphic environment, press CTRL-ALT-F2, and type "gksudo update-manager -c -d" in the run box)

Both of these solutions will add the appropriate drivers. Restart network or reboot. The device will be added to your system... look in /etc/udev/rules.d/70-persistent-net.rules to see what interface name the system created for your device. It will be the one using the ath9k driver.
The backports solutions works great, thanks!
> Hello ALL

I have managed to fix an issue with no WIFI on my Atheros AR9285 card by doing

Quote:
apt-get install linux-backports-modules-$(uname -r)
Unfortunately yesterday I have noticed that it does not support WPA2 PSK encription

Any one who can help ?? if yes I can provide more details

Cheers



This is where I encountered a link to using madwifi drivers at [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072).  It seems to work for a number of people, but is lengthy, so this is just for reference.

I haven't chanced on the link that took me through the recompile stage of getting the missing modules recompiled and reapplied to the kernal,
and that did work for 9.10, but maybe someone can add that info to this thread.  What I did note with the hundred or so missing modules is that they were being returned from a deselected state, meaning they had been there before.


That made me think that the kernel supports wireless, but the distro may have pulled a lot of that in an effort to squeeze more applications onto a CD, which is also the reason that you have only the choice of a desktop or server edition when it comes to download and install.  You can add the wireless support back after the install, but you have to know that it is missing and what needs being done to get it back.  Maybe all the distro LiveCDs are somewhat different, where some still have the wireless modules in them and others don't, which is why some have more success than others.  Or maybe they left just a bit of the needed code which sometimes catches and other times does not.

Anyway, my ex-son in law took it upon himself to decide to go from a working 9.10 to 10.04, and the wireless died in the process.  So now I have to see if I can do it all again.  I hope someone turns up the recompile code that I was working from before, because that did it.

---

### Post by oldefoxx on 2010-12-03
> **desnaike said:**
> Hi everybody I have the HP G61 with the same wifi card and it works out of the box on 10.04/10.10 on 3 distros k/x/ubuntu no problems so just maybe it's not the card causing the problem.

Nobody said it was the card,  The G61 is a different and later model, and obviously more expensive since you sport a 23" screen and my grandson's is a G60 with a 15.6" screen. That means maybe a different chipset is likely, maybe even a different interface.  Trying to determine
the exact differences in hardware is hardly conducive to determining why one works and the other doesn't if you lack sufficient knowledge of the software and drivers involved.  We don't have those details, and yet we are led to believe that it should all just come together and work.  Only in some cases it doesn't, and we have very few clues why.

Seems to me what is really lacking is a package with the needed tools and drivers to take over and solve this problem for us.  All we as humans do is try different combinations of things until we get a result, and if it is a good result we keep it.  If it isn't, we try something else.  What you need is a way to project what the result you want onto the package and let it work out the ways to get it.  That is a feature that the Network Manager does not have.

I'm presently stuck with my ex-son in law's upgrade to 10.04, and I get the same message that Wireless is disabled.  Nothing tells me exactly what this means or how to change that status.  It is a status indicator,
and that is not the status I want to see, but what tool, method, or approach is available to change it?  Maybe there ought to be a detailed help section on getting Wireless going.  Well, that might help, but why should users have to struggle so hard on matters like this.  If the geeks can't get it in their thick knoggins that general users just want a box that will power up and work without of study and experimentation, then a general move to something like Ubuntu just isn't going to happen.

Now here is a particular situation that probably happens often, yet there is no evident address of the consequences.  Suppose you have a good wire and wireless conncection going at the same time.  Which gets
used?  I suspect the wired, since it is simpler and faster.  But then what purpose, if any, might the wireless side be applied to at the same time?  might there not be a way to divide up the activity of both for some specific purpose?

Anyway, getting back to the original issue, I'm again stuck with this 
g60-630US being unable to get 
wireless going under 10.04, though I did manage at last to get it working under 9.10 by getting a whole bunch of modules reapplied, but I can't track back to where I got the one line instruction for making that happen.  So a bit of help could fit in here if anybody has some ideas of what to try.

Seems I've noted some desktops which have made the move to wireless as a means of cutting cable clutter.  Wouldn't it be something if Ubuntu had to admit that their desktop and server downloads presume that a wired network was in place because they could not be counted on to work on anything but?  And that to circumvent this problem, you had to either add a wired adapter or take your PC to a specialty shop to work out the software issues involved?  A task that with my experience can take not just hours, but weeks?  What an image for a product some deem superior to Windows7.

---

### Post by Davste on 2010-12-03
I'm searching hard for drivers, but I simply can't find the right ones. It would be great to get some help here, I know there are alot of people who will read this that are more than capable of helping.

---

### Post by corasian on 2011-01-07
Ok gents,

I see there was a little side-track on the second page of this thread, however for the HP G60 I found a quick and dirty fix that has worked for my wife with no issues. (I upgraded my wife's G60 to ubuntu 10.10 +500GB after a Hard Disk fail, and was promptly informed that the wireless didn't work, so I fixed it.) 

BLUF: here's my fix

1.using your favorite text editor, create a small script such as the one below: (quck & easy - cut and paste this into a new text file and save it as 'wireless.sh')

```
#! /bin/bash
#a simple script to fix the wireless for the G60

rfkill unblock all
exit 0

``` 

save it somewhere easy to get to (e.g. ~/wireless.sh)

2. in terminal, run: chmod 755 ~/wireless.sh  (makes it executable)

3. system>preferences>startup applications - add the new script to the list of startup items and it will be run upon login, the only telltale signs being that the wireless networking works. 

*notes: 1) if the network manager is not showing any enabled wireless devices after reboot w/ the script set in startup, try pressing the wifi button on the machine. see below for more detail.




A little deeper:
After Browsing countless forum topics for this machine & chipset, I noticed the major trend was not really driver-related at all, but just a rfkill blocking issue. For some reason, I know not why, the default setting is for this interface to be blocked.

So, first, I un-did all the previous changes I had made to the drivers and blacklists and blah blah. Then I examined the rfkill utility.

the output for '~$ rfkill list' showed this:

```
0: hp-wifi: Wireless LAN
        Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
```

so, the hardblock on the 'hp-wifi' is controlled by the wifi button on the machine, and the softblocks are controlled by rfkill.  I've noticed that after inserting 'rfkill unblock all' at startup, the hardblock has not shown back up after login (unless i hit the button ;) ), and a secondary side effect is that it seems to catch the network quicker (it's done connecting and ready to go before the desktop has finished loading after login)  

Hope that helps.

---

### Post by oldefoxx on 2011-01-14
You people have really helped in this matter.  But would you believe that I can't try and cash in on any of this right now?

See, another problem plaguing that laptop were constant warnings that the battery was at less than 40%, meaning either broken or left uncharged.  We only use it with the adapter plugged in.  My
grandson contacted HP, and we are now awaiting a shipping box and RMA to send it back under the warantee.  I'm afraid this will be my grandson's last venture with Ubuntu.  Can't say I blame him.

---

### Post by dli8ilb on 2011-01-15
> **corasian said:**
> 
```
#! /bin/bash
#a simple script to fix the wireless for the G60

rfkill unblock all
exit 0

``` 

thanks, this worked for me with only minor changes:
```
#! /bin/bash
#a simple script to fix the wireless for the Compaq CQ60

rfkill unblock all
rfkill unblock 0
exit 0

``` 

for some reason mine needed that extra command. after boot, the hp-wifi was the only thing soft blocked, so one more unblock did the trick.

[quote=rfkill list]0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no[/quote]

---

### Post by dli8ilb on 2011-01-15
> **oldefoxx said:**
> See, another problem plaguing that laptop were constant warnings that the battery was at less than 40%, meaning either broken or left uncharged.  We only use it with the adapter plugged in.  My
grandson contacted HP, and we are now awaiting a shipping box and RMA to send it back under the warantee.  I'm afraid this will be my grandson's last venture with Ubuntu.  Can't say I blame him.
i'm getting the same warnings with my compaq cq60 (it's only a couple years old) for which i've used the battery quite often.

you can disable this warning using gconf-editor, navigate to /apps/gnome-power-manager/notify/low_capacity and uncheck it.

---

