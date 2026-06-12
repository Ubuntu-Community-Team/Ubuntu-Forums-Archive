---
title: "Network problems..."
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by sickofthesea on 2009-08-04
Hi, this is a really strange problem, one I just can't seem to fix. 

It's an Ubuntu 9.04 issue as I've never experienced this before with previous releases. I've searched through the forums but cannot find anything similar. 

Network manager appeared to stop working properly but previously had (from fresh install). I thought it was a network manager problem as I switched to wicd and cured it. Now wicd has started doing the same, so I'm lost!

On my hp laptop wicd/network-manager says it's connected to my wireless WPA2 network but I can not get any web pages or ping any sites. The same is true with my 3 mobile usb dongle. Network-manager (not wicd) says it's connected to 3 mobile, the blue light is steady on the dongle, but again no web pages or pinging.

I can connect to 3 mobile using the correct settings in wvdial.conf and "sudo wvdial". Then I get web pages and can ping. If I use "sudo wvdial" whilst leaving network-manager supposedly connected to my wireless network, and then kill wvdial, suddenly web pages are available through my wireless network. Upon re-boot however the problem is back - no web pages.

I thought this might point to a /etc/resolv.conf problem but it remains unchanged with a "nameserver 10.0.0.2" entry (my wireless router ip). My router is set-up with the opendns nameserver entries.

Has anyone any ideas where I can start looking for a fix? I don't think this is a hardware or router issue. I'm leaning towards a software configuration problem with ubuntu.

I can post various outputs if anyone thinks this would help (ie hwinfo, etc). As a quick background I am using a pcmcia wireless card that uses the rt2500 driver. However, because of the problems with this driver (slow download speeds) I'm running the card with ndiswrapper, blacklisting the existing driver.

It's really quite odd how wicd/network-manager were working then just stopped. The fact that I can "sudo wvdial" with my 3 dongle, indicates to me that it's not a hardware problem.

This is the second install of 9.04 I couldn't fix it in the first install so re-installed. Now it's happened in the second install, meaning I can re-create the problem. It wasn't a one off glitch.

Any help or guidance would be appreciated.

Many thanks,

Martin

---

### Post by sickofthesea on 2009-08-10
A big black blob appeared at the bottom right corner of my lcd. Also it was getting extremely hot at that place, to the point where there was a smell of burning plastic.

I've turned it off for good. I reckon the whole laptop was starting to die.

Probably the cause of this headache!

---

