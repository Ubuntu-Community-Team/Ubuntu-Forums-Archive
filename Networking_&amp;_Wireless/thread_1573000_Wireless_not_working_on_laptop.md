---
title: "Wireless not working on laptop"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by ironic.demise on 2010-09-12
So, This is my family's laptop and my brother installed Ubuntu 10.04 after he used it on my desktop.
It won't connect to the internet.

The ouput of lspci is that it's Marvell 88w8335
ndiswrapper claims it has the id 11AB:1FAA

the card is a mini pci
it came in a HiGrade VA250D (or P) laptop
The driver that came with the laptop is apparantly liteon but does not work (Even ndiswrapper claims the device is not present)

I've found next to no documentation on the wireless card or the laptop and there are several wireless cards with Marvell 88w8335 11AB:1FAA descriptions and I've tried several, none seem to work so far.
NDISwrapper usually claims the device is present, but shows no connections.

Can somebody tell me which driver I'm supposed to use?

I've used ndiswrapper before
and usually sudo modprobe ndiswrapper starts the wireless, but not as easy on this laptop?

---

### Post by ironic.demise on 2010-09-12
Any help would be appreciated

---

### Post by ironic.demise on 2010-09-12
Okay, I've found out the disc that came with the laptop conatining drivers.
There are several that include XP or Vista 64 or 32 bit and I've tried all of them yet none seem to work... modprobe ndiswrapper seems to do nothing at all... ever?

---

### Post by MaindotC on 2010-09-12
Find out what driver is supposed to be used with that wireless card, then please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know if you have any difficulty and precisely where so we can better help you.  There is a subsection on ndiswrapper.

---

### Post by ironic.demise on 2010-09-12
Thankyou for the reply, I looked at the troubleshooting

The device is detected by lshw, It shows as Marvell wireless
there is no native driver
the modem driver was installed from system-hardware drivers but does not enable wireless
iwconfig only shows eth0

So I can see the hardware, but as there are no drivers it shows no wlan0 or ath0

So, the last resort is ndiswrapper
I've insterted the driver disc (which has several drivers for Vista and XP, 32 or 64 bit)
and I've tried the drivers available, it states that the driver is correct, that it matches the hardware and SHOULD work but upon sudo modprobe ndiswrapper absolutely nothing happens, no driver is loaded and no error is posted

I click the network icon and it shows only a wired connection

Is it possible ndiswrapper is not installed correctly?

---

