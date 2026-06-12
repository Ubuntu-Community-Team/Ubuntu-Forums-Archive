---
title: "Cannot connect to internet at all. Wired."
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by DuckyVader on 2010-07-24
Please excuse me beforehand for I am really new to Unbuntu. I recently got a laptop from a friend who knew nothing about it. I have a Motorola cable modem connect to a Netgear router. The router is connected to my windows xp pc, and to my ubuntu laptop with ethernet cables. Internet works perfectly on my win xp, but im not getting anything at all on my laptop. I'll try my best to explain everything out. It says im using Ubuntu 10.04 LTS the Lucid Lynx with I guess GNOME desktop. When I go to network connections, nothing shows up. Thank you in advance.

---

### Post by DuckyVader on 2010-07-24
Also, when i hover over the network icon it says network is disabled, but when i right click it shows Enable Networking is ticked. I can't un-tick it either. When I left click the icon it says networkmanager is not running...

---

### Post by Iowan on 2010-07-24
Network Manager may not be running if the machine thinks there is nothing to manage. From a terminal(Applications->Accessories->Terminal) enter **sudo lshw -C network** Post results (if possible). You might need to:```
sudo lshw -C network > lshw.txt
``` then copy that file to a floppy, USB stick, etc to transfer to another machine to post here.

---

### Post by DuckyVader on 2010-07-24
Ok I typed in sudo lshw -C network in terminal and I got this:


[B]  *-network DISABLED      
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:e6:13:d9
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:3000(size=256) memory:f2010000-f2010fff(prefetchable) memory:f2000000-f200ffff(prefetchable) memory:f2020000-f203ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:1a:04:6c:23:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/B]


Also, today when I started my laptop, the networking icon on the top right wasn't there anymore. I realized the laptop has built in wifi adapter, so I want to figure out how to enable it too. The wireless light on the front is orange.

---

### Post by Iowan on 2010-07-24
> **DuckyVader said:**
> 
Also, today when I started my laptop, the networking icon on the top right wasn't there anymore.Hmmm... doesn't seem like progress :(
*Sometimes* you can get the icon back by adding a "Notification Area" to the top panel. [Here]("http://ubuntuforums.org/showthread.php?t=1505217") is something else to try.

---

### Post by dineshs on 2010-07-24
From lshw output
> product: RTL8101E/RTL8102E PCI Express Fast Ethernet controllerand the driver loaded is > driver=r8169
Pl see this link
[http://ubuntuforums.org/showthread.php?t=1328011](http://ubuntuforums.org/showthread.php?t=1328011)

---

### Post by DuckyVader on 2010-07-24
I think I got it. I typed in rm -r ~/.gconf/apps/panel in terminal. Not really sure what that did but it was supposed to reset gnome panel to default, then I logged out and on the bottom I saw it said gnome failsafe or something of that sort and I switched it to just gnome, logged in. My network manager icon is back along with my battery icon. Ok, I'm trying to connect to my router wireless now...... YES!!! It worked. I have an internet connection:)

---

### Post by Iowan on 2010-07-24
:shock: Wow... I hadn't seen that method before. Glad it worked! =D>
If it STAYS fixed, mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") I'll add this one to my subscriptions.

---

### Post by DuckyVader on 2010-07-25
Yeah it's been working all day. Turned off laptop then turned it back on, searched and found my router instantly. Thank you, you guys for helping.:)

---

