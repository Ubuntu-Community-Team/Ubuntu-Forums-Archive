---
title: "New Dell Inspiron 15, New Ubuntu user.  Wireless worked for two weeks, now it don't!"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by ebodnaruk on 2009-05-22
Dell Inspiron 15, running Ubuntu 9.04.  Wireless does not work, but it did previously - that is the weird thing!  Dell Wireless 1397 802.11g card.  

The first couple weeks I had it, I could see wireless networks and connect to them.  I was away from home, trying to connect to any wireless network in the area.  Was successful one day, then the next day had trouble getting a good connection and was trying a lot.  Then I couldn't connect from then on, even at home!  I tried re-checking the "Enable Networking" and "Enable Wireless" check boxes.  I also ran that diagnostic program, and it says my card is disabled.  Weird.  Here's the output, after these couple of sentences.  I don't know if the card crapped out or if there is some tricky Ubuntu thing I don't know of (since I'm a beginner).  I will try using a friend's wireless card to check on that possibility. 

     *-network               
         description: Wireless interface 
         product: BCM4312 802.11b/g 
         vendor: Broadcom Corporation 
         physical id: 0 
         bus info: pci@0000:0c:00.0 
         logical name: eth1 
         version: 01 
         serial: 00:24:2c:58:b0:f0 
         width: 64 bits 
         clock: 33MHz 
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
         configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg 
    *-network 
         description: Ethernet interface 
         product: 88E8040 PCI-E Fast Ethernet Controller 
         vendor: Marvell Technology Group Ltd. 
         physical id: 0 
         bus info: pci@0000:09:00.0 
         logical name: eth0 
         version: 13 
         serial: 00:23:ae:2f:6c:0e 
         capacity: 100MB/s 
         width: 64 bits 
         clock: 33MHz 
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
         configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair 
    *-network DISABLED 
         description: Ethernet interface 
         physical id: 2 
         logical name: pan0 
         serial: 26:df:fe:e7:20:97 
         capabilities: ethernet physical 
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
  
Any ideas?  Thanks,
Ethan

---

### Post by kiridude on 2009-05-22
Try this:

```
gksudo gedit/etc/rc.local
```

enter your password and then add the following at the bottom of the page that will come up:

```
modprobe -r b43 b44 ssb wl
modprobe ieee80211_crypt_tkip
modprobe wl
modprobe b44
/etc/init.d/networking restart
```

close the page and click "save" at the prompt. Restart to check.

---

### Post by kiridude on 2009-05-22
First, if you're running a dual boot, check if you disabled wireless in Windows. On many laptops, if you disable wireless in Windows, it won't work in Linux. Go back into Windows and enable it.

---

### Post by MadJester on 2009-05-22
I'm having a similar problem with a HP dv7t.  Same wireless card.  It worked with a fresh 9.04 install, but now it doesn't.  The proprietary broadcom driver is still loaded, but now it won't scan for networks.  Did a security update cause this?

lspci:
 Network controller: Broadcom Corporation BCM4312 802.11b/g

$ sudo iwlist eth1 scan
eth1      Failed to read scan data : Invalid argument

---

Fixed:  Somehow I had disabled the card without knowing it.  My bad...  Seems to work fine now.

---

### Post by ebodnaruk on 2009-05-22
I entered the gksudo code, and it prompted me for my password.  I entered it, and nothing happened.  I reentered the code gksudo gedit/etc/rc.local and nothing happened! I'm not running dual boot...I wanted to drive a stake into the heart of Microsoft! (albeit a small one)

I also found the file rc.local in the etc folder and tried to add the code you mentioned.  However, it says "Could not save the file /etc/rc.local.  You do not have the permissions necessary to save the file.  Please check that you typed the location correctly and try again."  Any ideas?


> **kiridude said:**
> Try this:

```
gksudo gedit/etc/rc.local
```enter your password and then add the following at the bottom of the page that will come up:

```
modprobe -r b43 b44 ssb wl
modprobe ieee80211_crypt_tkip
modprobe wl
modprobe b44
/etc/init.d/networking restart
```close the page and click "save" at the prompt. Restart to check.

---

### Post by kiridude on 2009-05-23
ok, let's try something else first. Open a terminal and enter:

sudo apt-get update
sudo apt-get upgrade

Then, goto system > administration > synaptic manager and write b43 in the "quick search" field, and see what color the little box to the left of "b43-fwcutter" is. If it is not green, click the box and install it.

Restart your computer and let me know if it works.

EDIT: Woops, forgot to mention that you will need an internet connection when running the above. Since you're wireless isn't working, make sure you plug in.

---

### Post by ebodnaruk on 2009-05-24
Kiridude,

Thanks for your help.  Still no luck though!  What do you think is the matter?  I installed the b43-fwcutter, and restarted.  I still can't see any wireless networks.  It remembers my home network as a hidden network and when I try to connect that way, it fails.  

Do you think my card went kaput?  I don't know why it would work and then stop working!!!

Thanks,
Ethan

---

### Post by Kareeser on 2009-05-24
Hm.

Did you accidentally turn off the hardware radio with the switch on the side?

---

### Post by ebodnaruk on 2009-05-24
oh boy, i'm stupid.  I had tried the wireless button (F2) but always used the Fn button.  When just hit F2 without anything else, it works.  Is there any way I can delete this thread?  lol

I will go hide in shame now.  Thanks everyone!

> **Kareeser said:**
> Hm.

Did you accidentally turn off the hardware radio with the switch on the side?

---

### Post by Iowan on 2009-05-24
> **ebodnaruk said:**
> Is there any way I can delete this thread?  lol

I will go hide in shame now.  Thanks everyone!You could use the "Report Post" icon to request a moderator to delete the thread... but don't hold your breath - they will probably leave it (as they should) so someone else might learn from your "experience".

---

