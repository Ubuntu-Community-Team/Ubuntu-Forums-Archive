---
title: "Ethernetcard not recognised"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by bol on 2012-06-06
Hoping in your assitance in the matter of a built-in [COLOR=#000000][FONT=Arial]Intel 82579LM Gigabit card not being recognised [/FONT][/COLOR]as the ethernet card (eth0).

~$ ifconfig eth0
eth0: error fetching interface information: Device not found

and here it is, but 'unclaimed' How do I claim it?


~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:d4700000-d471ffff memory:d472a000-d472afff ioport:4060(size=32)
  *-network
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: wlan1
       version: 3e
       serial: 24:77:03:70:f5:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.187 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:d4400000-d4401fff


OS is Ubuntu 10.04LTS (because that is what I am running without  any problem on four other computers) and the machine is a new HP Elite Book  2560p.

Most other things run as expected (except that the screen is out of proportions and not properly recognised; but that will be the next issue)

Hoping for assistance!

Bo L

---

### Post by chili555 on 2012-06-06
A new computer with an old Ubuntu version. Hmmmmm.> and here it is, but 'unclaimed' How do I claim it?
You supply it with a driver. I suspect the driver e1000e. I also suspect the driver version in 10.04 was written before your Intel 82579LM Gigabit card was released and so doesn't recognize it.

...but I could be wrong...

Please run and post:```
lspci -nn | grep 0200
```We'll investigate further.

---

### Post by bol on 2012-06-06
Output as requested:

bo# lspci -nn | grep 0200
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)

ANd the old Ubunte because I am running four other computers with 10.04LTS. I am aware of time running out but I prefer to have also this new baby under control before I upgrade the lot.

Looking forward to any further advise.

Bo L

---

### Post by praseodym on 2012-06-06
System is up-to-date? Try to load the driver by hand:

> sudo modprobe -v e1000e

---

### Post by bol on 2012-06-06
As for the modprobe suggestion:
# modprobe -v e1000e

resulted in:

insmod /lib/modules/2.6.32.-41generic/kernel/drivers/net/e1000e.ko

but, sad to say, in no eth0

Thanks, anyway. It was worth a try.

Bo

---

### Post by praseodym on 2012-06-06
Sorry, wrong post.

Try a newer kernel, package "linux-image-generic-backports-lts-oneiric" plus the corresponding "headers". Reboot after that

---

### Post by chili555 on 2012-06-06
> Ethernet controller [0200]: Intel Corporation Device [[COLOR="Red"]8086:1502[/COLOR]] (rev 04)This device is not covered by e1000e in Ubuntu 10.04. We could try to compile something with no guarantee of success. Getting the kernel headers and compile tools installed on a system without ethernet is a huge task. Or, as I suggested before, you could upgrade to 12.04 in 20 minutes and it will work.

---

### Post by bol on 2012-06-06
Don't think I'm not tempted. 
But, how about this:

"It is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in July, before upgrading. 
To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure. 

[LIST=1]
[*]Start System/Administration/Software Sources
[*]On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
[*]Press Alt-F2 and type update-manager -d
[LIST=1]
[*]Click  the Check button to check for new updates.    If there are any updates  to install, use the Install Updates button to install them, and press  Check again after that is complete.
[*]A message will appear informing you of the availability of the new release. Click Upgrade.
[/LIST]
Follow the on-screen instructions.  "
[/LIST]


(Quoted from [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop))


Would it be safe to following the above instructions? In spite of the introductory warning?


Tempted, yes ...

---

### Post by chili555 on 2012-06-06
> Would it be safe to following the above instructions? In spite of the introductory warning?I only have five computers in my house running Ubuntu. Not bad for a house of two people, eh? I have upgraded over the network many times. I have had it fail once. I don't know for sure that the fault wasn't the hardware, because the whole laptop died a few weeks later. In my experience, it usually works perfectly well; 'usually' meaning it's not 100%. Assuming you don't have a separate /home partition, I wouldn't be afraid to do so now.

If you do have a separate /home partition, and I recommend everyone to have such, I'd download and burn the alternate install CD and upgrade that way.

As in all such things, back up your essential data. Blank DVDs are relatively cheap.

Of course, you can also download and burn the live CD to make sure everything works well before you proceed.

---

### Post by bol on 2012-06-08
So I took a chance and plunged into deep water; And the upgrade to 12.04 LTS was succesful. Not only do I have cabled network, but the screen resolution and screen ratio is now perfect.

But I miss the layout of my old dwsktop and my custom panels with my chosen applets.

Nevertheless:
Thanks for all the assistance!

Bo L

---

### Post by praseodym on 2012-06-08
Install the package "gnome-shell" and choose "GNOME Classic" at Login.

---

### Post by chili555 on 2012-06-09
> So I took a chance and plunged into deep water; And the upgrade to 12.04 LTS was succesful. Not only do I have cabled network, but the screen resolution and screen ratio is now perfect.Awesome! I'm very glad it's working as expected. Have fun!

---

