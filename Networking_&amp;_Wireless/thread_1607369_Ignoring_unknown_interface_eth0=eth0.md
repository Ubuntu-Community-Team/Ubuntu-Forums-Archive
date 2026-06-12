---
title: "Ignoring unknown interface eth0=eth0"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by Xama on 2010-10-27
I am using Ubuntu 10.10 and I am getting this message when try to configure my network connections:

   Ignoring unknown interface eth0=eth0

Does anyone have an ANSWER (not a guess) as to how to fix this. I have seen this question posted but no definite answer ... 

**Gripe mode on!***
I can't configure the thing! I must say I am very annoyed that this useless Network Manager application is totally useless ... I mean why is this nonsensical non-working thing even included if it does not work ... quality control = 0!
**Gripe mode off.**

---

### Post by Xama on 2010-10-27
I am just going to declare 10.10 doa and go back to 9.whatever ... I will wait a year for 11 because this should not be. Mucked with /etc/network/interfaces for too long ...

[http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso) to you I return ... (turns on Player's 'Baby come back').

x

---

### Post by chili555 on 2010-10-27
If it worked under 9.10, I can make it work under 10.10, but first, I need to know what "this thing" is. Please post:```
sudo lshw -C network
```

---

### Post by Xama on 2010-10-27
> **chili555 said:**
> If it worked under 9.10, I can make it work under 10.10, but first, I need to know what "this thing" is. Please post:```
sudo lshw -C network
```

I used wicd. I downloaded the .deb package on another computer. I uninstalled network-manager and then I double clicked the .deb package ... and installed it.

I used Wicd to configure the network interface ... then everything worked. The problem is that Canonical/GNOME did not do any testing on network-manager ... it does not work at all. Very poor quality control ... 

I shall sleep with one eye open as I use this 10.10 version ... 9.x never behaved like this.

x

---

### Post by chili555 on 2010-10-27
Glad it's working.

---

### Post by Xama on 2010-10-28
I am glad it is working too, but it is a shame that I must UNinstall an important part of the bundled application and install something else to get it to work. 

Is this considered acceptable by Canonical? Everyone seems to know that Network Manager is broken and useless, yet we must accept this?

I had a similar problem my Mac a few years ago. Changing locations would cause the whole system to hang, a tech came in and flushed all the Network locations and did some magic to get around this 'known' Mac bug ... but this would have been something an OSX software update should have fixed.

So this Ubuntu situation dredges up bad memories of  that experience ... oooh that bundled software would work.

x

---

### Post by chili555 on 2010-10-28
> Everyone seems to know that Network Manager is broken and uselessI don't. It works perfectly well for me. It connects instantly and even recognizes the 802.11a network at my doctor's office; and connects!

Obviously, only people who have problems post here; those that have no problems whatever never show up here.

What percentage of the questions posted here turn out to be NM issues? In my experience, very few. Most are a missing driver, missing firmware or the person who wonders why his 20-year-old PCMCIA card won't do 802.11N and WPA2. Many are file- and internet-connection sharing issues; many are network printing issues.

I'm sorry, I don't accept your generalization.

---

### Post by daklein on 2011-01-22
Try this:  

```
  ifconfig eth0 up

```

---

### Post by Argentino on 2012-05-24
> **daklein said:**
> Try this:  

```
  ifconfig eth0 up

```

LOLerskates!!! Hours of trying to get the eth* connections up... 

I feel dumb now. :P

---

