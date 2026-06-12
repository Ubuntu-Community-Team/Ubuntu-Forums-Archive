---
title: "help! im wanting to audit my home network but i cant find which dirvers i need..."
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by fozbolt on 2009-08-07
i have a new macbook and i can find my card in terminal but i cant tell which chipset it has and therefore am unable to find the needed drivers among the massive lists for the audit. also its coming up under the eth1 port. 
      thanks!

---

### Post by Metaljaz on 2009-08-07
type lspci in the terminal window. Look for the line that says network controller. It will list controller and chipset. Should look something like this: 

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


I assume this works for the macbook as well.

---

### Post by fozbolt on 2009-08-09
thanks!!! that helped alot!!

---

### Post by fozbolt on 2009-08-09
ok so now heres another question. i have this chipset for my wifi card- 

03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

and i found a patch for it (the b43) patch but it said that most people used it and had little success with it, but apparently its needed in order for packet injection. and when i ran the packet injection test earlier it said packet injection wasnt found. advice??

---

### Post by Metaljaz on 2009-08-09
All you should need is the broadcom b43 wireless driver.
Try this: (now these instructions worked for me - not a mac, but should work for you as well)

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window (make sure you are using your wired connection):

sudo apt-get update

sudo apt-get install b43-fwcutter

Post back with results

---

### Post by fozbolt on 2009-08-09
patch is installed.  but im still getting error messages. here it is-

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

does this make any sense?

---

