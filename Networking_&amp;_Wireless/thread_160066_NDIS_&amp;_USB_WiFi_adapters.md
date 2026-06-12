---
title: "NDIS &amp; USB WiFi adapters"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by Geffers on 2006-04-14
I have a Linksys WUSB11 V2.6 WiFi card which I have used on Windows98 and would like to experiment with on my ubuntu system :) 

I do also have an ethernet connection.

I have ndis gtk and this is where my confusion starts; the ndis WiKi mentions inf and sys files but ndisgtk appears to only deal with inf files.

I've unpacked the linksys drivers (downloaded from the ndis recommended source) and the only inf I can find is setup.inf

As the adapter is a USB have I got to instal extra driver files.

Geffers

---

### Post by az on 2006-04-14
I am pretty sure than most of the revisions of your card already have linux drivers.

Google says that your card is a AT76C503A.  That card works fine in Ubuntu.  Scanning, however, does not work.  If this is not a problem, just plug it in and configuire your wireless connection, putting in your ssid by hand.

I have two such devices and they work flawlessly and reliably.

If this does not work, plug in your device and post what the device manager says your wireless device is.

---

### Post by Geffers on 2006-04-14
[QUOTE=azz]I am pretty sure than most of the revisions of your card already have linux drivers.
[/QUOTE]

A reply from Linksys when I enquired about the inf file stated they did not support Linux

[QUOTE=azz]
Google says that your card is a AT76C503A.  That card works fine in Ubuntu.  Scanning, however, does not work.  If this is not a problem, just plug it in and configuire your wireless connection, putting in your ssid by hand.
[/QUOTE]

Are you suggesting that I may not have to load any drivers at all, initially when I did not have an ethernet connection the Linksys device did not work, can't recall the system message but from memory it suggested something was missing.

[QUOTE=azz]
I have two such devices and they work flawlessly and reliably.

If this does not work, plug in your device and post what the device manager says your wireless device is.[/QUOTE]

I'm in Windows at the moment but will change soon and give that a try, thanks.

Geffers

---

### Post by az on 2006-04-14
[QUOTE=Geffers]A reply from Linksys when I enquired about the inf file stated they did not support Linux[/QUOTE]

Much of the hardware support in linux is from reverse-engineered code.  I am sure Linksys did not contribute a thing to any linux drivers, but most of their devices can work in linux - some without ndiswrapper.


[QUOTE=Geffers]
Are you suggesting that I may not have to load any drivers at all, initially when I did not have an ethernet connection the Linksys device did not work, can't recall the system message but from memory it suggested something was missing.[/QUOTE]

The driver was not in the hoary kernel.  It was introduced in the breezy kernel.  Post the message if you can.

[QUOTE=Geffers]
I'm in Windows at the moment but will change soon and give that a try, thanks.

Geffers[/QUOTE]

If you can tell me the chipset, your device can start working.

---

### Post by Geffers on 2006-04-15
[QUOTE=azz]Much of the hardware support in linux is from reverse-engineered code. 

If you can tell me the chipset, your device can start working.[/QUOTE]

Using ndisgtk I installed netusb.inf from the original Linksys driver file, after reading your message I plugged in my adapter and 'hey presto', it was working.

Strangely, the following day (Saturday) I booted to ubuntu and the Wifi didn't show, tried a few things with no luck, shut down and rebooted and it was there again.

So, at the moment it is working but I need to work at the reliability.

Once that is working I'll look in to the card more as I want to experiment with some of Linux's network security utilities such as kismet and airsnort.

Not sure how I find out the chipset of my card.

Geffers

---

### Post by az on 2006-04-15
I am not sure if you have the ndiswrapper module loaded or not.  You cannot have two drivers trying to use the same hardware, or it will not work reliably.

---

### Post by whereareyoutakingme on 2006-04-18
i checked another thread to get the commands to get my WUSB11v4 Linksys Wireless 2.4Ghz 802.11b card working and this is what i typed in

"$ sudo apt-get install ndiswrapper-utils" --> into a terminal

copied the .sys and .inf Windows drivers to <username>/Drivers/LinkSys Wusb11

"$ cd <username>/Drivers/LinkSys Wusb11"

"$ sudo ndiswrapper -i <name>.inf"   <----problem line

and then i was going to type...

"$ sudo modprobe ndiswrapper"  into a terminal, but when I hit enter on the before indicated problem line, i got an error message that said

"ndiswrapper: command not found"

What do I do to get my internet working?

---

### Post by az on 2006-04-18
Open up synaptic and see if ndiswrapper-utils is properly installed.


If so, maybe youmispelled ndiswrapper?

---

### Post by kenstrus on 2006-11-19
Hello there. I'm new to Ubuntu. Would like to get some suggestions on what manufacturer to purchase a wireless card from. That has been proven fairly easily installed and to get up and running. Hope to hear soon. Thanks

---

