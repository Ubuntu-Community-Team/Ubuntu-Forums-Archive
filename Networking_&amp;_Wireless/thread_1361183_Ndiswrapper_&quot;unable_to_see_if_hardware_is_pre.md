---
title: "Ndiswrapper &quot;unable to see if hardware is present&quot;"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by matbence on 2009-12-21
**EDIT: I thought I should put this in at the top. It turned out that my wireless device was disabled, which was easily fixed by turning it on with an Fn+F2 keyboard shortcut. My device was already supported by ubuntu 9.10 and the problem was nothing to do with ndiswrapper.**


Ndiswrapper gives me the error message "unable to see if hardware is present", after I install the w70n51 driver for the Intel PRO wireless 2100 3A adapter that is supposedly somewhere inside my inspiron. The adapter was working fine earlier today while XP was still installed.

I have noticed that a few other people have been having similar problems. I have tried following advice given to them, but none of it has worked for me. I'm not sure if it makes any difference that I am using 9.10 or not or that I got ndiswrapper from the ubuntu CD.

when I type 'sudo lshw -C network' I get the following:

  *-network:0
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: wlan0
       version: 04
       serial: 00:0c:f1:50:4e:08
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w70n51 driverversion=1.55+Intel,10/11/2003,1.2.1.3 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: irq:5 memory:fcffe000-fcffefff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 81
       serial: 00:0f:1f:9f:d8:76
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:fcffd000-fcffdfff ioport:ecc0(size=64)


Before installing the driver using ndiswrapper it said UNCLAIMED next to my wireless adapter.


I have tried blacklisting drivers and now my '/etc/modprobe.d/black list' file contains the following:

blacklist ssb
blacklist bcm43xx
blacklist b43
blacklist b43legacy


I would really appreciate any help or suggestions as I am very new to linux and trying to get a taste for it.

---

### Post by shredder12 on 2009-12-22
I am a little confused here.. did you install the drivers in xp or ubuntu?
As far as i know ,, all ndiswrapper does is takes a .inf file from your windows wireless driver and use it ... 
so, are you getting an error after doing this?

---

### Post by matbence on 2009-12-22
Well I'm not exactly sure how ndiswrapper works, but in ndisgtk it had an 'Install New Driver' button. When I press that, I browsed to the folder contain the w70n51.sys and w70n51.inf files and selected the .inf file.
I downloaded the driver files from the sourceforge ndiswrapper page on my wifi adapter.

After selecting w70n51.sys, I recieve an error message saying 'Unable to see if hardware is present'. When I press OK, the window disappears and the windows wireless driver window, shows my driver installed (or loaded, whatever ndiswrapper does) and that the hardware is present.

I kind of assumed that what I have done with ndiswrapper is fine, because when I type 'sudo lshw -C network' it seems to show that the driver for my Wifi adapter is provided by ndiswrapper (under configuration).
Unless ndiswrapper isn't working properly...
Or the driver I downloaded doesn't work...

Could the problem be other drivers that I have already stopped? Or drivers that I still need to stop?

---

### Post by matbence on 2009-12-22
Another thing to mention, before using ndiswrapper i tried downloading a linux driver for my wifi adapter, but had no idea how to install it. If I could do this then I could stop worrying about ndiswrapper.

---

### Post by coffeecat on 2009-12-22
@matbence, did you try connecting to your wireless network using network manager **before** you installed ndiswrapper? The Intel 2100 wireless chipset *should* work out of the box. The driver and firmware are included in a default install.

---

### Post by matbence on 2009-12-22
Yes I did try. I did find something telling me that intel 2100 3B (mini PCI) is supported. When I still had xp on the machine it told me I had a 2100 3A (PCI) adapter.

I just did another search and found [this]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron510m"), suggesting that wifi should work with network manager.

Does this mean i need to unblacklist whatever drivers it was I blacklisted and look for the problem elsewhere?

How do I unblacklist the drivers? Also, any tips for where else I can look for a problem?

---

### Post by coffeecat on 2009-12-22
According to your earlier post, the modules you have blacklisted probably won't make any difference (three are for broadcom cards, but I don't know what ssb does), but you could simply undo the edits you did to /etc/modprobe.d/blacklist.conf. (I presume that's the file you edited.)

If you then uninstall ndiswrapper, that should prevent the Windows driver being loaded. Do a reboot, but do a cold reboot - i.e. power down completely and then boot up after a few seconds. I don't know whether this affects the Intel 2100 chipset, but with some wireless chipsets, the firmware doesn't get reloaded properly if you do a warm reboot, especially from Windows to Linux. Or so I read somewhere.

Once you're back into the desktop, simply left-click on the network manager icon (near the top-right). Do you see your wireless network? If so, click on it and you should be prompted for your passkey. And that should be it.

---

### Post by matbence on 2009-12-22
The File only contains those four lines. Can I just delete the file?

---

### Post by coffeecat on 2009-12-22
> **matbence said:**
> Can I just delete the file?

No, don't do that! :shock:

:wink:

Open it with:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```... remove the four lines you added, save it and close the text editor.

**Edit:** sorry! Not being clear. If it's a file you made yourself, yes, delete it. If it's blacklist.conf, don't. :)

---

### Post by matbence on 2009-12-22
Looking at it, I think I may have accidentally created a file called blacklist instead of editing blacklist.conf

Is the file 'blacklist', that contains only the four lines I posted above not doing anything anyway? How would I delete it in the terminal (total beginner)

---

### Post by coffeecat on 2009-12-22
> **matbence said:**
> Is the file 'blacklist', that contains only the four lines I posted above not doing anything anyway? How would I delete it in the terminal (total beginner)

```
sudo rm /etc/modprobe.d/blacklist
```

But make sure /etc/modprobe.d/blacklist is the one you want to take out. There's no going back from that command. :-s

Once you've done that, let us know how you get on. If things don't connect the way I suggest, post back. There are some terminal commands that will give useful information.

Good luck!

---

### Post by matbence on 2009-12-22
Doesn't work, its just like when I had first installed ubuntu on the computer. When I type lshw -C network into a terminal is says that my wifi adapter is UNCLAIMED.

---

### Post by matbence on 2009-12-22
I was wondering if there was a problem with my install. When I boot up ubuntu tells me that my disk has many bad sectors and my CD drive isn't exactly great.
To see if there was a problem with my install I have just booted from a usb stick and I still have exactly the same problem of not being able to use my wireless adapter.

When I type 'lshw -C network' in a console this time it tells me that it is using the ipw2100 driver for my adapter.

If it is not the hardware that is the problem (was working in windows yesterday), or the driver (seems to be trying to use the right driver) - what else can be the problem???

help

---

### Post by coffeecat on 2009-12-22
The 'Palimpsest' Disk Utility is giving out false positives with some makes of hard drive, so the 'bad sectors' may or may not be true. There have been a few threads about this.

Let's take one thing at a time. You've told us that 'sudo lshw -C network' (use sudo with lshw - you get incomplete output if you don't) with the live USB environment shows that the device is using the ipw2100 driver. That's good. That's as it should be. What you haven't said is whether you could see any wireless networks in the live environment. Did you? Try booting up from the usb stick and click on the network manager icon. Are there any wireless networks showing? Can you connect to yours?

What we need to establish is whether a default install will connect OK on your hardware. The live session should be able to tell us this. So - if you can connect with the live session but not from your HD install, we need to look deeper into what's gone wrong in the HD install.

---

### Post by matbence on 2009-12-22
I couldn't connect wirelessly in the live environment.

When I clicked on the network manager icon it shows two bold headings, wired network and wireless networks. My wifi network does not show up underneath the wireless networks heading.

I have just finished a fresh install of ubuntu to revert any changes I may have inadvertantly made while trying to enable my wifi adapter. So hopefully anything I try now will be on a fresh slate.

---

### Post by matbence on 2009-12-22
When I enter 'sudo lshw -C network'  into a terminal the fresh install is telling me the same as the live environment was - that it is still using the ipw2100 driver.

Right, now I am back to square one, what should I have done?

---

### Post by coffeecat on 2009-12-22
> **matbence said:**
> When I clicked on the network manager icon it shows two bold headings, wired network and wireless networks. My wifi network does not show up underneath the wireless networks heading.

Hmmm. That doesn't sound good. No wireless networks at all? Have you, by chance, hidden your SSID on your router?

---

### Post by coffeecat on 2009-12-22
> **matbence said:**
> When I enter 'sudo lshw -C network'  into a terminal the fresh install is telling me the same as the live environment was - that it is still using the ipw2100 driver.

Please tell us what you see when you click on the Network Manager icon. At the moment that's much more important.

---

### Post by matbence on 2009-12-22
> **coffeecat said:**
> Hmmm. That doesn't sound good. No wireless networks at all? Have you, by chance, hidden your SSID on your router?

No, I don't it is even possible to on a BT home hub.

Here is a screenshot of the menu:
[IMG]http://tinypic.com/r/k04j1d/6[/IMG]

---

### Post by matbence on 2009-12-22
Hang on I'll try that again:

[http://tinypic.com/r/k04j1d/6](http://tinypic.com/r/k04j1d/6)

---

### Post by coffeecat on 2009-12-22
> **matbence said:**
> Hang on I'll try that again:

[http://tinypic.com/r/k04j1d/6](http://tinypic.com/r/k04j1d/6)

Sorry - I'm out of ideas. Your NM is showing no networks.

To recap: sudo lshw -C network is showing that your device is using the ipw2100 driver. That's correct - and good. The firmware comes in the box, so that shouldn't be a problem. And the link you provided states that wireless works on your machine with every version of Ubuntu going back some time. I'm baffled. If there was a problem with either the driver or the firmware, then you would see in that screenshot, 'Wireless networks - something else'. With the something else being 'disabled' probably.

This is unlikely to provide any more information because, basically, this is what NM does but open a terminal and post the output of:

```
iwlist scan
```

---

### Post by matbence on 2009-12-22
I'm feeling pretty stupid now. I just found a keyboard shortcut using the Fn+F2 keys on my keyboard for enabling the wireless adapter. The hardware was just not enabled. Shouldn't ubuntu have told me this?
Nevermind, thanks for all of your help Coffeecat, sorry to have wasted your time.

---

### Post by coffeecat on 2009-12-22
> **matbence said:**
> I'm feeling pretty stupid now. I just found a keyboard shortcut using the Fn+F2 keys on my keyboard for enabling the wireless adapter. The hardware was just not enabled. Shouldn't ubuntu have told me this?
Nevermind, thanks for all of your help Coffeecat, sorry to have wasted your time.

Not at all! :lol: I'm just glad it's working. Don't be hard on yourself. Console yourself with the thought that the Fn keys work in Ubuntu on your laptop! :wink: Not everyone can say that.

> **matbence said:**
> Shouldn't ubuntu have told me this?

I don't know. The hardware in laptops varies so much that's it's amazing that most things work in Ubuntu on most machines. On the Sony laptop I'm posting from, there's no Fn key combination to switch the wireless off, but there is a little hardware switch for this. And, yes, I have spent half an hour cussing at the machine when I accidentally switched the little switch without noticing. :rolleyes: On this machine there's also a little light by the switch that goes out if I slide the switch to the off position. It also goes out if I right-click on NM and untick 'enable wireless'. Does yours have a light for wireless?

Happy Ubuntu-ing!

---

### Post by matbence on 2009-12-22
Mine doesn't have a light for wireless. Having had a similar problem with a laptop touchpad before, I think I have learned my lesson.
Right, now to lock myself away for a while and learn about ubuntu...

---

