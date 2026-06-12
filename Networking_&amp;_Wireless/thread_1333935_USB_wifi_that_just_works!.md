---
title: "USB wifi that just *works*?!?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by memilanuk on 2009-11-21
Hello,

I'm curious... given the huge number of threads and posts on wireless problems (both in Ubuntu forms & mailing lists, and those for other distros)... are there any wireless USB adapters that just plain *work*, without having to fiddle around with ndiswrappers, patched kernels, 'borrowing' drivers from Windows, or wade through nearly 20 pages (in one forum thread alone) or more of posts on getting the dang thing working.

I realize that even in Windows many times a special driver is needed for a lot of wifi adapters, and either has to be downloaded via a wired connection, imported via a USB thumb drive, or obtained someway or another.  Even then they aren't always 'plug-n-play'.  And yes, I've checked the various hardware compatibility lists.  For every nearly every entry that says 'works great out of the box' you can find 15 posts in forums or mailing lists that bemoaning that it *does not work*.

Seriously.  I'm looking for a decent wifi usb adapter that supports 802.11g (n would be a nice plus) + WPA2 Personal encryption, that I can stick in my laptop or desktop and have it just *work*?

Any takers?

---

### Post by mach3 on 2009-11-22
Just my words!

---

### Post by coffeecat on 2009-11-22
Yes, most 'just work'. But you wouldn't guess it from the number of support threads here. 

> **memilanuk said:**
> And yes, I've checked the various hardware compatibility lists.  For every nearly every entry that says 'works great out of the box' you can find 15 posts in forums or mailing lists that bemoaning that it *does not work*.

There are two problems. The first is that most (all?) manufacturers (*cough* Belkin *cough*) muddle things by releasing entirely different chipsets, but they keep the same model number. As an example, I have two Belkin (*COUGH*) USB sticks, both model F5D7050. One has a Zydas chipset, the other a Ralink - entirely different manufacturers. Fortunately for me they both work just fine in both Jaunty and Karmic. Granted the release numbers are different but to know that you have to look at the output of lspci.

But there's more. It's not just different chipsets at different times in one country. It's different chipsets at the same time in different countries. :(

The other problem is that some people either get in a muddle when trying to configure their device or they have a different problem on their network, and they wrongly ascribe the difficulty to the wireless nic. Hence the 'does not work' posts.

All of which doesn't get you very far. Except to say: if someone tells you to get - say - a Netgear USB stick, model unspecified, don't listen. If they recommend a Netgear model X, don't listen. If they say, Netgear model X, revision number Y, lspci output Z, purchased in country A, then you **might** be lucky.

All I can suggest is to find a hardware supplier who specialises in Linux. Here in the UK we have [The Linux Emporium]("http://www.linuxemporium.co.uk/"). Click on their Linux WiFi link and you'll see that they're selling wireless NICs that they know work. If they sell you a pup, comsumer law means that they have to refund your money. So - is there anything like that where you live?

By the way - don't buy an Edimax just because Linux Emporium are selling them in the UK. You might be lucky, or Edimax might be stuffing a completely different chipset in the devices they sell where you are.

---

### Post by memilanuk on 2009-11-22
> **coffeecat said:**
> 
All of which doesn't get you very far. Except to say: if someone tells you to get - say - a Netgear USB stick, model unspecified, don't listen. If they recommend a Netgear model X, don't listen. If they say, Netgear model X, revision number Y, lspci output Z, purchased in country A, then you **might** be lucky.


And in my experience... most of the time I have no way of telling what revision number a given adapter is without ripping open the packaging and getting out the magnifying glass.  Not surprisingly, most retailers are funny about that ;)  

The bit about finding a domestic vendor that specializes in Linux might have some merit... just not sure who that might be.  I know of any number that peddle *systems*, from bare-bones kits to full turn-key machines, but not hardware accessories.  A-Googling we shall go...

---

### Post by coffeecat on 2009-11-22
> **memilanuk said:**
> Not surprisingly, most retailers are funny about that ;) 

They are over here as well. Isn't that weird! :P

By the way, I've just noticed that you say you are running Hardy - according to your personal details to the left of the post. This complicates things slightly. Generally speaking, wireless support will be better in Intrepid, and then Jaunty better than Intrepid and Karmic better than Jaunty. Yes, I know about the occasional regression, but for most wireless chipsets this is true. There are chipsets that will just work in Karmic, that simply won't show a flicker in Hardy, because more chipsets are supported in Karmic. This, of course, is because a newer release means a newer kernel and the kernel is where you find the wireless drivers.

If you are running a later version, then you might want to amend your personal details :wink: but if you are running Hardy, you might want to think of a later version.

---

### Post by old fert on 2009-11-22
You are my hero. I have a Belkin F5D7050 adaptor that didn't work with Hardy or Intrepid. (Possibly, I'm not smart enough t figure it out....nah).  Haven't felt like trying with Jaunty.   Forget the wireless.  Ethernet is your friend.

---

### Post by memilanuk on 2009-11-22
coffeecat,

I'm running 8.04 LTS on my home server, *trying* to get wifi working on 9.04 on an older Sony Vaio laptop.  I'm just about to the point of saying the heck with it and tossing the dang thing in the dumpster.  It's old, slower than a seven year itch, I just replaced the battery and now *it* won't fully charge... I can't even boot half the Live CDs out there from various distros, as they require too much graphics horse power to run.  Debian Lenny 5.03 + LXDE works okay, but Debian is even more 'fun' to get stuff working that doesn't isn't auto detected.  My hopes/plans are to get wifi working (someday) and then proceed to strip this Ubuntu install down, install LXDE, and see if things run a little better then.

Anywho, back to the topic... if I had to go off of recommendations off the Net, I'd be looking very hard at a Edimax EW7318USg or Hawking HWUG1 - but as you mentioned... some work, and some don't, and there's no real way to tell until you plug 'em in :(

old fert,

Ethernet kind of defeats the purpose of a laptop - the wifi router is in kind of a less-than-comfy spot to sit tethered for any length of time.

---

### Post by revdode on 2009-11-22
I bought a Hama WLAN adapter ref. 00062734 and it just works. Plugged in detected (Ubuntu 9.10) and apart from entering my SSID into network manager no other manual operation was required.
I bought it as the cheapest in the shop (mediamarkt) expecting nightmares but it was way too easy.

---

### Post by old fert on 2009-11-22
You're right of course.  I would be very happy if wireless worked on my laptop.  I gave up out of frustration and exasperation.  What irritated me the most was that it took about 3 minutes to set up in windows and probably about 5 or 6 hours of trying in Ubuntu before I gave up.  

I'll try again in Jaunty sometime when I have a long boring day to kill.

---

### Post by fluxbuntu on 2009-11-22
I run Jaunty on my PC and Debian Etch on my laptop. Bought a SMC EZ Connect G wireless usb adapter and it works on both. I use WICD as the connection manager and it works with WPA2. Total plug and play here. Hope that helps.

---

