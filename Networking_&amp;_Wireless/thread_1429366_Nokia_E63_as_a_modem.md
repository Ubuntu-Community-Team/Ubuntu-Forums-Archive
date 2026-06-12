---
title: "Nokia E63 as a modem?"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by crlang13 on 2010-03-14
Hey all,

I've got a Nokia E63 phone and I believe you can use it to connect a computer to the internet.

I plugged it into my computer via usb, Ubuntu found it fine, the phone saw I was connected to the computer and asked if I wanted to connect the computer to the internet, I told the phone yes.  But nothing changed on Ubuntu, no options on my network applet to connect or anything.  A new icon for the phone popped up on the desktop, I explored it and there were a couple of .exe files in there... no help on Ubuntu.

Anyone else get this to work?  I'm using Ubuntu 9.10 by the way.

Thanks

---

### Post by Danny Rafferty on 2010-03-20
Sorry I don't have any help for you, but I'd really like to do this myself. Might try to do this via wifi, as nokia don't supply a cable as standard.

---

### Post by Fafler on 2010-03-20
Its a virtual CD-ROM with windows drivers. Sometime in the future udev will be able to change it to the actual modem device, but for now choose PC Suite instead and configure with the network manager applet.

---

### Post by Peacepunk on 2010-03-23
hi.

If the 63 is a 3G phone, then NetworkManager _should_ be able to handle it, no fuss. There are settings to configure thou, if your country/operator isn't listed.

My wife  and I use everyday a 5800 and an E71, with 904UNR, UStudio910 and Debian Squeeze. We used with Fedora9 and 10 before.


The 3G limitation is strange, because when I don't have 3G then my phone keeps me connected with EDGE anyway; nevertheless I have yet to see a GPRS/EDGE phone working out of the box with NetworkManager.


Please also notice there are inconsistencies between distros, releases and hardware. Since we can't do without our cellphones as access points, I've had to throw away Fedora12 from my Laptop, and U910 doesn't connect on this 2core laptop either; only Ubuntu Studio (same NM version) works on my Desktop. UNR904 is doing fine on the AcerOne, so I am just NOT going to touch it, ever :)


Running Debian Testing allows you to stay close to the day-to-day devlopement of software, and NM is being heavily worked on right now, with stuff done on Bluetooth connections. I am mostly happy, it's not flawless, requires a reboot sometimes, and can disconnect on you every few minutes... But then I live in Cambodia, not the best place for bandwidth.


Your mileage WILL vary; there is no way I can understand why the same version of NetworkManager works on the desktop IF with Ubuntu Studio and not on my laptop with the standard U; I am reporting bugs now and then but I am a bit lost on this one.


Fedora12, which must be on par with U910 version-wise, was also showing the Nokia as an external device/drive like yours, and _absolutely_ refused to even try to connect to the phone. So much for allowing us to Automount the phone as a drive while being in "desktop" mode.


You could try with joikuspot, but your battery life will sink.
Then, that's what I am using now to write this :)

Cheers
Jean-Philippe

---

