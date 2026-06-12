---
title: "wireless no longer detects"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by kimbroBranch on 2009-08-29
Dell Inspiron 1545, 
Dell Wireless 1397 802.11g Half Mini Card
with ubuntu 8.1 installed.
Day 1::  (Aug 21) detected the wireless network at the coffee shop, downloaded and installed ubuntu 9.04
Day 2:: detected a friend's wireless nerwork and downloaded emacs
Since then have not been able to detect either of the above networks nor my new router (which was tested with another laptop). Wired connection works..
After reading this forum, I think the followimg might be meanngful to someone who knows what they are doing.

system->administration->hardware drivers
Broadcom STA wireless driver
tested by ubuntu developers
license:Proprietary
This driver is activated and currently in use.

the last item listed from lspci -v

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Dell Device 000c
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    
TIA for any suggestions.

---

### Post by Metaljaz on 2009-08-29
Try this driver:
This has been the easiest way for me:

If your results of typing lspci in a terminal window reveals something to the effect of Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

---

### Post by kimbroBranch on 2009-08-30
Metaljaz, your instructions were very clear.  Thank you so much for the effort.

Synaptic Package manager listed b43-fwcutter so I installed and applied. rebooted.  Disconnected the wired internet connection.
There is no mention of it in hardware drivers, so I disabled the broadcom wireless and rebooted.  Still no mention of fwcutter in hardware drivers.  Package Manager says b43-fwcutter  is installed.  Now I have enabled broadcom. And no wireless detected.

---

### Post by Metaljaz on 2009-08-30
After going back and rereading your post to see if I missed something i see this and I am confused:

Dell Wireless 1397 802.11g Half Mini Card and I also see 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01). Now I guess I am trying to figure out which one you are using.

Double check to make sure you did not accidentally turn off your wireless. I have a keyboard function on my dell that allows me to turn on/off wireless. Mine is F2 some use FN F2. 

Also, when you left click on the wireless icon on the top right screen are the wireless network options grayed out? If they are try creating a new wireless network using the information for your setup. Or if you are using a secured network try connecting to hidden network.

---

### Post by kimbroBranch on 2009-08-30
Thank you again, Metaljaz!

I reported the Dell wireless mini card strictly from the invoice.  I suspect it is a Broadcom product made for Dell, if that makes sense.

I am confident that wireless is enabled.  I fell into that problem early on :)

Left clicking the network icon shows wireless grayed out.  I am not using a secured network.  Now, where do I get the setup information?

As i continue with ubuntu, I hope someday to be able to help someone as much as you have helped me.

---

### Post by Metaljaz on 2009-08-30
Left click on the network manager and try selecting create new wireless network. Enter the name of your network and select the type of wireless security that you use, if none leave none selected. Your network name should have been selected when you set up your router.

Also, under System>Preferences>Network Connections you can add a wireless network. Under the wireless tab click add and try selecting connect automatically and see if it works.

I would again double check and make sure that your wireless is enabled on your laptop.

Try typing iwconfig from the terminal window. If all devices listed say "no wireless extensions." then your wireless card is not configured. The device may be disabled - you could try typing this in the terminal window: sudo ifconfig wlan0 up

Lastly, if its not to much trouble try a fresh install of Ubuntu 9.04. Everything should work out of the box.
Please post back and let us know what happens.

---

### Post by kimbroBranch on 2009-08-31
you are so right - I do need to reinstall 9.04.  I'm starting to get error messages at boot and shut down.

It will be awhile, but I will report back here.

a piece of NON information : pressing F2 twice caused it to detect wireless networks.

thanks again.

---

### Post by kimbroBranch on 2009-09-01
after a clean install of 9.04, everything works.  Thank you so much for the valuable advice.

---

