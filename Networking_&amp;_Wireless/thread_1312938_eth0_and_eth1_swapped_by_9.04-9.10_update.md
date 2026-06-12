---
title: "eth0 and eth1 swapped by 9.04-9.10 update"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by deparvius on 2009-11-03
This issue has been causing me no end of frustration since the 9.10 update (by internet) has effectively shutdown my local network and internet connections.

/etc/udev/rules.d/70-persistent-net.rules is set properly by MAC address to each card, but then Network Manager for some reason during boot swaps eth0 and eth1, causing eth0->eth1_rename and eth1->eth0.  Swapping the definitions in 70-persistent rules results in no such swap, but the wrong cards of course being used.

Settings from /etc/network/interfaces don't get swapped, however, so affect the opposite NIC.

Swapping the ethernet cables results in at least being able to ping the router on eth1 (eth1_rename does not occur) but no internet, and the LAN avahi server no longer works either.  It is all rather confusing.

What I want is for Network Manager to not swap these out, and simply use eth0 for LAN server and eth1 for internet as before.  Then hopefully this is the only problem and I can get internet and my gigabit LAN back online.  The only hint I have is a /var/log/syslog message saying Network Manager is redefining the interfaces.

Thank you very much in advance for any help!

---

### Post by dr_voodoo on 2009-11-03
I have a very similar problem to this and I'm not getting much joy from the upgrade forum. 

I autoupdated 2x Dell Dimension 4600s from Jaunty to Karmic. Both are identical save for differing RAM, Video and Sound cards. 
According to Karmic's system profile the Ethernet controller model is Intel 82562EZ 10/100 rev. 02 (motherboard based)

Although the networking icon in the taskbar shows Eth0 is connected, I have no internet access within Firefox (time outs), but I CAN ping web pages from within the terminal. 
Synaptic/Ubuntu Software Manager will give me the list of programs available for install but freeze and crash when I try and downloading anything. 

I thought I would try and solve the problem by reinstalling Karmic from the LiveCD - however when I booted into Karmic from the 'try without making changes' prompt, exactly the same problem occured, so I am guessing it's an incompatibility with Karmic and the Intel network controller. 

I need to get these issues resolved ASAP as I have people that need to be doing web-based work on these machines, and I don't really want to roll back to a clean install of Jaunty and reconfigure, only to upgrade to KK again after a couple of days. 

Also there are no problems with the network itself - I am typing this from a *ista machine on the same network.

---

### Post by deparvius on 2009-11-04
I've isolated and fixed my problem.  The update didn't break anything per se, just modified how Network Manager behaves when it sees non standard input.   I had something in my avahi ruleset in /etc/udev/rules.d (to set multicast parameters) that was ignored before but the update rightly looked at it, but the behavior of network manager is still a bit off.

Specifically, I redefined the IP of the eth0 device to an IP I was no longer using using PROGRAM="ifconfig %k <oldIP>" as a rule.   Network manager must have panicked.  Instead of redefining the IP, it swapped the devices and caused eth0 to be called eth1_rename.  Before, it simply ignored this IP change, or changed it back after /etc/network/interfaces was read.

In conclusion, this is my error, since IP should be defined in /etc/network/interfaces but very odd behavior by Network Manager nonetheless.

I suggest this issue is resolved in NM, or at least some relevant error messages by NM to syslog about why it decides to swap interfaces.

dr_voodoo is having different problems, since I was not able to ping websites from my terminal.  It sounds like maybe a strange Firefox/DNS issue.  Maybe try wget or lynx to see if terminal web browsing can work.

---

### Post by deparvius on 2009-11-05
Or not.  The problem has risen from the dead the very next day and I'm even more confused.  There are some definite issues with Network Manager.  I'm posting a new thread.

---

### Post by humble_coffee on 2009-11-10
I've got the exact same problem. I can still use the network, however because the names have changed, programs for I need to manually set the name of my network interface then break. So my virtual machines no longer appear on the network as VirtualBox is trying to connect to the wrong interface. 

It appears as though the rules in etc/udev/rules.d/70-persistent-net.rules are just being ignored.

---

### Post by mstombs on 2009-11-14
I also have this problem  IT IS NOT FIXED!, in trying to fix it Network Manager or udev is now renaming eth0 to eth1_rename and eth1 to eth0.

Its great that I can always find someone else with the same bugs on 9.10, and usually workarounds.  Its a real shame that there are so many similar undesirable features in 9.10

[edit]

Not a fix likely to be recommended - but I have got my network card interfaces back to their correct names following a power cut which turned off the PC without shutting down cleanly.  Presumably some hardware table got corrupted and was rebuilt on successful reboot?

[edit]

A hang on reboot left the message on screen "udev - unable to swap eth0/eth1 device in use or busy",  Now eth0 and eth1 wrong way round again.  I tried changing /etc/udev/rules.d/70-persistent-net.rules to use eth5 and eth7 to see if the issue was re-using the old names, but it didn't help.  Just ending up with eth0 and eth5, the problems seems to be that the first named interface won't give up its name.

---

