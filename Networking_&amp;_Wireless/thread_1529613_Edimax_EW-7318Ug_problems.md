---
title: "Edimax EW-7318Ug problems"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by dcforeman on 2010-07-12
Hi, I've ready posted once about Ubuntu, and was told basically that this device should run out of the box, however I'm getting some weird results.

I decided to give kubuntu a go, as it's plasma interface was prettier and showed off my nVidia 8800 card to better effect. I was pleasantly surprised to find that when installing kubuntu with a network cable plugged in, when it installed. They wireless Edimax adapter did indeed work! I played around happily all day, downloading compiz, nvidia drivers and a few themes. Then, after installing Skype 2.1 from their site, I was suddenly not able to view anything in Konqueror.

I pulled out the adapter, put it into another USB port, and it found my router under scan, I gave it the WPA key, it said authenticating, then active. But Konqueror still refused to connect. I tried the software install feature to get firefox, that wouldn't connect either. I rebooted, and reloaded. And It still failed to work. I then booted into Windows 7 for a while, rebooted into Kubuntu again, and it started working. Then stopped again.

At first I thought it was a problem with the device, perhaps the adapter is failing? But it's perfectly fine under Windows 7 for long durations. I sent files back and forth between machines for a good 12 hours just to make sure the link was fine.

So I figured Skype must have done something. This time I reinstall Kubuntu without the Ethernet cable plugged in. And my Edimax adapter won't work. I've made no changes to the system. It's finding the router in the scan, it's telling me it's authenticating then Active, but konqueror refuses to connect.

It's telling me the RT73usb drivers are install and it's telling me I have a connection but nothing is getting through.

Any idea's would be welcome!

---

### Post by lescrooge on 2010-07-18
U should be so lucky.
I've got 2 and neither show up anywhere, either on KK or LL.
Either that means that they are both less than useless or there is another reason.
Anyway, I read that one problem might be the DNS settings.
It was all a little vague, but it appears that changing it to OPENDNS does the trick.
If you find out where this happens let me know.
GL

---

