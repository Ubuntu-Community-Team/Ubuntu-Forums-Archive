---
title: "auto enter WPA pass for external USB adapter"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by Exonimus on 2009-12-17
Hi guys,

I recently installed ubuntu on a laptop for my parents to try out. So far, the experience has been good. However, I've now used a blank keyring password because they don't like entering it on start-up every single time. This works decently, but recently our network has been having some slight problems, and sometimes the internal network card just doesn't cut it. Until I have fixed that problem(if I can. It happened in windows too..) I've given them an external usb adapter to plug in. However, on boot up ubuntu shows me two wlan cards(obviously) and I can see my network twice. However, whatever I do, it always asks me for a network password(probably for the external usb one).
So my question is: is there any way for me to 

A: set both cards to be 'default' or set in such a way that one doesn't have to enter the network pass? 

or B: to completely disable the internal NIC so it uses the external one as default? I did try to find it in the bios settings, but because it is a certain brand of laptop, most advanced settings are just not there.

Thanks in advance.

edit: I just talked to a friend, and he told me to look in the preferences->network connections->wireless tab and it seems one of the two didn't have an 'auto' password there. Since I entered that, it seems to work. Would removing my NIC there also leave it disabled as default? Because right now, while one nic works the other one keeps searching and asking for a pass even though it's entered in the NM settings

---

