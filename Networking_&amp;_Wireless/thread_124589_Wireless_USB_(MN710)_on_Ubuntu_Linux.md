---
title: "Wireless USB (MN710) on Ubuntu Linux"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by StrykerXile on 2006-02-01
So I just receieved my like 45 CD's from Ubuntu's free ShipIt program. I fired a live CD up right away. I like it a lot, but like I feared, my internet was not working.

My receiver is a Microsoft Wireless USB (MN710) receiever. I use a USB receiver because my computer is in a little place built to fit it, right under my desk. If I were to have a Wireless PCI adapter, I would get a crappy signal because it is so cramped down there. My USB adapter sits on the top of my desk in the bottom right corner and gets an amazing signal. My room is upstairs, the router is downstairs.

Anyways, I cannot seem to get the wireless to be detected. It doesn't recognize my receiver in the device manager, but the lights of the receiever are on. I googled for an hour, looking through various linux sites and forums and driver pages.

I cannot find linux drivers for the MN710.

Oh and I checked out ndiswrapper but I don't know how to work it and some of the steps confuse me.  I've never used Linux before that is why I'm trying now.  I checked the list of supported network adapter for ndiswrapper and mine was not one of them but it said it's possible others can work.

Ndiswrapper mentions if it's the first time installing ndiswrapper I have to install the windows drivers.  What windows drivers?  The adapter works fine on windows.  Is that what is is referring to?

Does anyone have a solution?

Thanks.

---

### Post by Lambert on 2006-02-02
The lights are on because there is power to the device but it probably doesn't have a driver so it can communicate with the os.

I'm not sure what chipset your device used but a 710 & 730 both use the broadcom chipset so it's possible that's what you use.

In breezy there is no native driver for a broadcom chipset so an app called ndiswrapper is used to wrap around and make the windows drivers work under linux.

There is a module in ubuntu for ndiswrapp which is v 1.1 but you need to install a package called ndiswrapper-utils to make it work and load the drivers. Dending on your device's support you may need to compile and install a newer version of ndiswrapper but try the version with breezy first.

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

Check out this link for instructions on installing ndiswrapper, anything you don't understand or if you get stuck just come back here and post what you've done and where you're stuck including output of commands where you're stuck at.

---

### Post by StrykerXile on 2006-02-02
[QUOTE=Lambert]The lights are on because there is power to the device but it probably doesn't have a driver so it can communicate with the os.

I'm not sure what chipset your device used but a 710 & 730 both use the broadcom chipset so it's possible that's what you use.

In breezy there is no native driver for a broadcom chipset so an app called ndiswrapper is used to wrap around and make the windows drivers work under linux.

There is a module in ubuntu for ndiswrapp which is v 1.1 but you need to install a package called ndiswrapper-utils to make it work and load the drivers. Dending on your device's support you may need to compile and install a newer version of ndiswrapper but try the version with breezy first.

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

Check out this link for instructions on installing ndiswrapper, anything you don't understand or if you get stuck just come back here and post what you've done and where you're stuck including output of commands where you're stuck at.[/QUOTE]I'll give it a shot but will this work with a Live CD?  I'm going to do a dual-boot in a week or so.  Should I try to get this to work with the live CD so I know how to do it when I install it?  Or is it pointless getting it to work on the live CD?

---

### Post by Lambert on 2006-02-02
I do not believe ndiswrapper works with a livecd.

---

