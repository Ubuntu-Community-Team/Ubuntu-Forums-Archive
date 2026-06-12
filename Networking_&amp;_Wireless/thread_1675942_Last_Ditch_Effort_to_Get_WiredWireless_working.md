---
title: "Last Ditch Effort to Get Wired/Wireless working"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by carosaurusrex on 2011-01-26
Hello. I posted here a couple weeks ago about my wireless issues and someone suggested I download an update of firmware for my Broadcom wireless card. The problem is I can't even connect to the Internet with a wired/Auto Ethernet connection in order to download said firmware. I tried downloading it on a different computer then using a flash drive to transfer it, but when I opened it on my computer, a message popped up saying the files were corrupted (this happens every time I try to install any program/update from a flash drive). So I tried today to use the wired connection to download the firmware but a) it wouldn't recognize the connection, so I deleted the AutoEthernet connection, rebooted, and activated the new one, as per the solution I'd read in a different thread on the forums. The wired connection worked, but only intermittently--it disconnects about every minute or so--and even when I'm connected, Firefox won't load any pages so I still can't get the update I need for my card. I feel like I'm out of options here--I've been having this problem for about 7 months and I, or my much more Linux-savvy acquaintance, have not been able to figure out the problem. I'm thinking the only solution at this point is to go back to running Windows, which I really don't want to have to do. Any thoughts/advice would be appreciated. Thanks.

---

### Post by Kirboosy on 2011-01-26
Ok so can you post what wireless card we are working with and what version of Ubuntu you are running?

---

### Post by carosaurusrex on 2011-01-26
Yeah, my bad for not posting those things before. I'm running the newest distro 10.10 and my wireless card is a Broadcom 802.11a/b/g draft-n. I got the wireless card tested and everything so I know all the hardware is working (unless the people at the shop I took it to missed something major...they didn't look into any software/OS issues because they aren't familiar with Linux...I know a bit, but I'm still uncomfortable at the idea of going in and messing with terminal commands unless I know that what I'm doing will work, or at least be reversible if it doesn't, you know?). Thanks!

---

### Post by Kirboosy on 2011-01-26
I know you said your internet works intermittently but did you get a chance to update your computer all the way?

Also does it prompt you to install Additional Drivers? (System--Admin--Additional Drivers)

---

### Post by carosaurusrex on 2011-01-26
I think so. When I installed 10.10 I did so hoping that an upgrade would fix the software issue (I wasn't connected to the Internet when I upgraded), and when I checked for updates today, nothing came up.  I just checked about the additional drivers and nothing came up (but again, I wasn't able to connect to the Internet when I checked).

---

### Post by Kirboosy on 2011-01-26
Have you tried to use it through "ndiswrapper"? That is like the only other option I can think of.

---

### Post by carosaurusrex on 2011-01-26
At the risk of sounding ignorant, how would I go about doing that? (step by step directions please? :D)

---

### Post by Kirboosy on 2011-01-26
Open Synaptic (System-->Administration-->Synaptic Package Manager)

In the Quick Search box type **ndiswrapper**

Check all the packages that appear and install it by using the Apply button.

See [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for the rest of the setup process. (no sense in repeating a already published How To)

---

### Post by Charlie: on 2011-01-27
caro: Let me know if this helps you in any way, I've been having the same problems but this is my first Linux install of any sort. PM if it goes well on your end, please!

Caboose: Thanks for the read, I'll try it out tonight also!

---

### Post by Kirboosy on 2011-01-27
Let me know if I can be of anymore help to you.

---

### Post by Charlie: on 2011-01-27
Looks like the latest version of Ndiswrapper is only supported up to Lucid? Say it ain't so 'Boose!

---

### Post by bkratz on 2011-01-28
> **Charlie: said:**
> Looks like the latest version of Ndiswrapper is only supported up to Lucid? Say it ain't so 'Boose!



I use ndiswrapper in my 10.10 system,  if you do a search with synaptic does it show up? I always load in ndisgtk (which loads the others) for ease of use. The GUI shows up under system//administration//windows wireless drivers.

---

