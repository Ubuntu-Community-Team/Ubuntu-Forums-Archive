---
title: "WiFi problem"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by jimmys_ on 2009-02-04
Hi.
I have installed Ubuntu 8.10 using Wubi on an HP Laptop. The problem is that by default my WiFi connection doesn't work and when i switch it on/off using the button on the laptop nothing happens. I found out that using the command *sudo ifconfig wlan0 up* my WiFi turns on and is working but when i restart it the same problem exists. My question is if what i did was the right way for turning the WiFi on or if there is an easier way and how will i make the WiFi button to work so even when i restart the PC using the button i could turn on/off the connection. Also, when the WiFi is on the WiFi led light is flashing when it is transmitting and is very annoying. Instead it should be just red when it's off and blue when on.

Thanks.

---

### Post by jimmys_ on 2009-03-04
doesn't anyone encountered the same problem? how do you turn your wireless on?

---

### Post by Cotopaxi on 2009-03-09
Yes, I DO encoounter the same problem on my laptop!

I can choose a lan from the list offered, but it DOES NOT manage to connect!

---

### Post by issih on 2009-03-09
@jimmys_, you should be able to enable your wireless card by simply right clicking on the network manager icon in the system tray (top right by default) and selecting to enable wireless. Once enabled though it really should stay on between reboots, if that behaviour persists let us know.

As for the wireless switch and light, unfortunately laptops are very proprietary and these kind of hardware details are not things that a generic OS cannot always get right without help from the manufacturer. 

Your best bet is to search for the exact model of your laptop and see if someone knows a workaround. Be grateful that the actual wireless functionality works, it doesn't for a lot of people to begin with :(

@cotopaxi, your problem is distinctly different, as you are actually failing to get a network connection. I'd recommend starting a separate thread, and detail the make and model of your wireless card (run "sudo lshw -C network" if you don't know) and give as many details of the situation as possible, its also a good starting point to disable encryption on the wireless router whilst trouble shooting these things, although you should obviously put it back on once you have it sorted.

Hope that helps

---

### Post by Cotopaxi on 2009-03-11
issih,

Thanks for your reply, I will do that.

---

