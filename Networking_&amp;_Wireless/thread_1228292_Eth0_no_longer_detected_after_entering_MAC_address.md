---
title: "Eth0 no longer detected after entering MAC address in nm-applet"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by siamesekatz on 2009-07-31
Hi 

I've just upgraded from Xubuntu 8.04 to 8.1 via the network upgrade on a IBM t21 notbook. All seemed to go quite well, except nm-applet always said "disconnected" despite being connected to the internet via a XP pc sharing an internet connection. 

In my attempts to get the nm-applet working correctly ie entering all the info I had for eth0 (including the MAC address), it seems that nm-applet some how broke the config. This happened just after entering the MAC address and then rebooting.

Now when I run **sudo ifconf -a**

I only get the lo0 interface.

and when I input

sudo **ifup eth0**

[B]eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
[/B]

/etc/network/interfaces file
---------------------------------
auto lo
iface lo inet looback

auto eth0
#iface eth0 inet dhcp

auto eth0
#iface eth0 inet dhcp
--------------------------------

I dont really know what to do. I tried uninstalling and reinstalling the network-manager but no luck. After that I install wicd which at lest gave me some options and when it tries to connect there is "activity" on the network card (lights flashing)but only when trying to connect.

The device manager detects the nic correctly (intel pro 10/100) and it works find in XP (so sad I have to use XP to solve this problem :-(

What to do? Any ideas?

I also tried the jaunty live cd but had the same problem.:confused:

Thanks in advance
peace

---

### Post by Iowan on 2009-07-31
No guarantees... Try commenting out the "auto eth0"'s in /etc/network/interfaces. That *might* let NM play by it's own rules.

---

### Post by siamesekatz on 2009-08-01
Hi,

So far still no luck, also I ran

beertjie@beertjie-laptop:$ **sudo lshw -C network**
  
*-network UNCLAIMED     
       description: Ethernet controller
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 09
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=66 maxlatency=56 mingnt=8

and got that.....
seems that UNCLAIMED network has something to do with it, any ideas?

---

### Post by siamesekatz on 2009-08-02
Got it working!

I had to change the intel pro 100 mini pci driver e100 to eepro100 using modprobe eepro100 and then adding it to the /etc/modprobe .

For some reason the e100 driver was freaking out or not allowed.

It seems now that the nic is eth1 (befor was eth0) but no probs as it works great :D

---

### Post by Iowan on 2009-08-02
You might be able to edit the definition in/etc/udev/rules.d/70-persistent-net.rules... or you might want to leave "working" alone... ;)

---

