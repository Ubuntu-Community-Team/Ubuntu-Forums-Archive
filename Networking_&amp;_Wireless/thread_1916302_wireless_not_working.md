---
title: "wireless not working"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by llladwod on 2012-01-27
My wireless is not working with Ubuntu, I have a Dell Notebook and I've tried pretty much everything that I could find online in the forums. I have tried installing new firmware(b-43) and ndiswrapper, and I am out of ideas.

I am not online so I am doing everything through a computer with microsoft and moving anything I find over with my USB stick.

Help anyone please???

---

### Post by ts3 on 2012-01-28
> **llladwod said:**
> My wireless is not working with Ubuntu, I have a Dell Notebook and I've tried pretty much everything that I could find online in the forums. I have tried installing new firmware(b-43) and ndiswrapper, and I am out of ideas.

Hello and sorry about the wireless :(   My experience is fairly limited but you can try to run the following commands, one at a time, in a terminal, to gather some basic information about your wireless setup, and then post the output of the commands:

```
cat /etc/lsb-release; uname -a 
lspci -nnk | grep -iA2 net 
iwconfig 
rfkill list all 
nm-tool
lsmod 
```I've shamelessly copied these commands from wildmanne39 posts, who seems to be a wireless troubleshooting hero on these forums.  Actually I'm hoping that wildmanne39 or someone else will step in to help you further :)

In addition you can try going through this guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

It is a good and safe way to get familiar with your wireless set-up.  

One final thought: if you've tried many different solutions as you mention above you might have ended with conflicting drivers (this happened to me).

Good luck and cheers :)

---

