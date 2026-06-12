---
title: "No wireless (pcmcia) after upgrade"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by misterfish on 2010-08-06
I installed version 9 some time ago and got my pcmcia Netgear WG511 card to work fine (I had to use iwconfig to do the configuring).

So I thought I'd upgrade to v10 using the upgrade manager and doing it all online - working on the assumption that working configuration options would be carried over.

So after the upgrade completed and rebooted - no network. Tried iwconfig - nothing - just a single entry - no wlan or anything like that. 

Any suggestions as to how to get the pcmcia network card to work - in simple terms as I'm not practiced in linux/ubuntu

Misterfish

---

### Post by misterfish on 2010-08-07
Hmm. Deathly silence!!

So, as a first attempt to solve this I downloaded 10.04 and burned onto a CD. Then did a complete clean install.

And... no difference. Iwconfig just showing 'lo' no device (or words to that effect, but nothing else listed.

Dug out my 9.10 disk and did a complete clean install. In this case iwconfig shows the pcmcia network card. Used the network utility to add and configure the wireless connection and networking sprang to life. It automatically ran update manager and is now doing the 308 updates. I did not choose to update to 10.04 LTS.

It is annoying that there is no (apparent) straightforward way to get the networking functioning with the latest version as I'd like to be up to date.

Any advice about accessing/configuring pcmcia would be appreciated.

Misterfish

---

