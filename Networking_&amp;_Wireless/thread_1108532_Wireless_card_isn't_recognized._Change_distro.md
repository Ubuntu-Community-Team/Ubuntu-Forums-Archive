---
title: "Wireless card isn't recognized. Change distro?"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by goettlek on 2009-03-27
Hi all,

I just installed Ubuntu Studio two days ago and I really like it. My first experience with Ubuntu was with Kubuntu, which I like a little bit better, but the audio software is hard to beat in Studio. Either way, Linux beats Vista by a long shot!

Anyway I've been trying for days to get my Intel PRO/Wireless 3945ABG wireless card to work. I've tried using Intel's recommended Linux drivers (the iws3945 i think). It didn't work. So I tried the ndiswrapper method. It said the driver was installed, *device* installed (or something to that effect) and I still couldn't get it to work in Network Tools.

Now I'm pretty much at end with this. It seems like too much trouble, and I could just download the audio software into Kubuntu. Could switching help solve the problem? I don't mind switching at all, since I kind of like KDE better than GNOME:P

I just booted into Kubuntu 7.10 via Live CD and the wireless works. Will the wireless still work even if I install?

---

### Post by chili555 on 2009-03-28
Switching to kubuntu is unlikely to really change anything. Kubuntu uses KDE, as you know, instead of Gnome. However, the underlying module, *iwl3945* is the same in both. > I just booted into Kubuntu 7.10 via Live CD and the wireless works. Will the wireless still work even if I install?Probably, but not absolutely. Incidently, I believe 7.10 uses a different module, [COLOR="Red"]ipw[/COLOR]3945.

So, where are you now? Is ndiswrapper installed? Let's check by running two terminal commands:```
lsmod | grep ndis
lsmod | grep iwl
```*lsmod* will tell us which modules are loaded. 

If we need to, can you waltz the laptop over to an ethernet connection in order to be able to download and install fixes?

---

