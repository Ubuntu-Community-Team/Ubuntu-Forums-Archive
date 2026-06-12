---
title: "Dlink DWA-556 card gone from net manager"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by Baneblade on 2009-08-12
Hi all, my wireless card has just stopped working for no apparent reason.
I have the DLink DWA-556 ([http://www.dlink.com/products/?pid=549](http://www.dlink.com/products/?pid=549)) installed on Ubuntu 9.04 64bit.

It was working to an acceptable level. Signal was poor, and I could see less networks than my laptop (HP DV2000 also with an N card) but speeds maintained in 48-54Mbit range on a G router, which i was satisfied with.
I woke up the other day and now it has vanished from my network manager totally.

Output from "lspci"
```
05:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```

Output from "iwconfig"

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

Iv checked the back of my box and the card is flashing its status led in 1 sec intervals (showing its powered up, but not connected I assume?)

I'm not sure what i should try next to get this card working again.. any thoughts?

---

### Post by Baneblade on 2009-08-13
Bump

---

### Post by Baneblade on 2009-08-18
Bump Bump :(

---

### Post by smakand on 2009-08-18
Hey Baneblade, what driver are you using? Just the default one, or one you installed yourself?

Also, post the appropriate part of [COLOR=Sienna]lshw[/COLOR] for your wireless card. If you can't find it, just post the whole thing to [http://pastebin.com/](http://pastebin.com/) and we'll figure it out.

---

### Post by Baneblade on 2009-08-18
> **smakand said:**
> Hey Baneblade, what driver are you using? Just the default one, or one you installed yourself?

Also, post the appropriate part of [COLOR=Sienna]lshw[/COLOR] for your wireless card. If you can't find it, just post the whole thing to [http://pastebin.com/](http://pastebin.com/) and we'll figure it out.

Hey thanks for getting back to me! :)

Im just using the standard driver that Ubuntu installed for it.
When i installed the card it just worked out the box.

Output of "lshw" is
```
        *-pci:4
             description: PCI bridge
             product: MCP55 PCI Express bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: a3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: AR5008 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0

```

I cant think why its being recognised, but not showing up in the network manager any longer?

---

### Post by smakand on 2009-08-18
I noticed the 'UNCLAIMED' tag next to your output, and so I looked up what it means:

> lshw displays nodes with attributes in a tree-like structure (that can be in indented plain text form, HTML, XML or graphically displayed in the GUI). Each node has its individual status: it be *CLAIMED* (potentially usable) or *UNCLAIMED* (no driver has been detected for this node), *ENABLED* (this device is supported and can be used) or *DISABLED* (this device is supported but has been disabled):Can you find anything on your wireless card with [COLOR=Sienna]lsmod[/COLOR] (or [COLOR=Sienna]lsmod | grep wlan[/COLOR])? I'll be honest with you, I don't know what I'm doing either, just trying to help.

---

### Post by Baneblade on 2009-08-18
lsmod outputs a LONG list of stuff, but the only networking related entry is
> ndiswrapper   250624   0
presumably from when i tried to install the windows drivers after my card stopped working? While they installed fine using the .inf file and the latest download from Dlink, there was some error about the hardware not being detectable (i cant recall the exact msg, but the drivers didnt fix the problem)

> lsmod | grep wlan
this doesnt output anything. I appended the "-v" tag to it and got the same output and "lsmod" (from what i can see)

---

### Post by smakand on 2009-08-18
Alright so we can't attribute your card not working to the ndiswrapper, but the madwifi drivers work much better for our type of card (I have a DWA-552). Have you tried installing those?

---

### Post by Baneblade on 2009-08-18
> **smakand said:**
> Alright so we can't attribute your card not working to the ndiswrapper, but the madwifi drivers work much better for our type of card (I have a DWA-552). Have you tried installing those?

Ok, how do i do that? Iv looked through Synaptic and only found "madwifi-tools" installed them anyway though, as im guessing they are used?
I cant seem  to find the launch command though (or the gui entry for that matter?)
Can you point me in the right direction? Im assuming that im looking for an interface like ndiswrappers "Windows Drivers"?

---

### Post by smakand on 2009-08-18
No problem. First make sure you have the required packages:

```
sudo apt-get -y install build-essential bin86
sudo apt-get -y install sharutils
sudo apt-get -y install subversion
```Next, lets head over to /usr/src.
```
cd /usr/src
```Lets check out the latest copy of the madwifi drivers (sudo because /usr/src is usually restricted):
```
sudo svn checkout http://*madwifi*-project.org/*svn*/*madwifi*/trunk madwifi
cd madwifi
```And we can try to install
```
sudo make clean
sudo make
sudo make install
```If you are prompted to remove old drivers.

To test it out, type
```
sudo modprobe ath_pci
```And if everything goes without errors,

```
sudo gedit /etc/modules
```Add a line at the very end of the file:
```
ath_pci
```
Also remove any ndiswrapper lines you see in that file. If there are any errors compiling hopefully I can help.

---

### Post by Baneblade on 2009-08-18
You sir, are a genius!
Wireless is back up!
Signal is still poor, and can still see less AP's than my latop (same situation as before it broke)...
But its working again! 
Thank you so much for your time and effort! That guide was excellent!
:D

---

### Post by smakand on 2009-08-18
Haha excellent. I had just installed the driver today, so everything was fresh in my memory.

---

### Post by ctmstudios on 2011-06-17
This solution worked great as well for DWA-547

Thanx!

---

