---
title: "home network"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by loosescrew on 2009-09-05
My desktop (dual boot xp/ubuntu) is connected to a linksys wireless router (WRT160N). Daughters laptops (2) connect thru the router. I was told when I purchased the router that I would be able to see and communicate with the two laptops (Inside the network). My daughters are young and I want to be able to monitor there surfing activities. Was I misled when I purchased the router or is this possible ? A friend suggested I, would need to go to a wired network ? Thanks ,joe

---

### Post by lildigiman on 2009-09-05
You might have a Log Book in the router which will tell you all the data that has passed through it. To access the router go to Firefox and type in the IP address of the router and sign into the router and find a tab that says something about logs.

I'll continue to look for more info if you need it.

---

### Post by loosescrew on 2009-09-05
lildigiman, I appreciate the reply. I can go to my router and look at a log. But that isn't what I'm trying to accomplish. I want to be able to talk between the three computors. For the desktop to be able to see what the two laptops are doing at any given time. For example at work you can go to task manager, users and send a message to another computer on the network. The boss can see what any computer on his network is doing. I was under the impression that you had to be on a wired network to accomplish this. When i went to purchase the hardware to setup a wired network the hand at best buy suggested that I go wireless. He said I could accomplish everything that I wanted without all the wire. Thanks,joe

---

### Post by ugm6hr on 2009-09-06
I suspect you were mislead.  Most home routers cannot do anything like the functions you want.  If those features are not mentioned in the manual for the router, they can't be done.

This is true for both wired and wifi.

What you want is something like a WebMarshall product, which requires a proper server to run on.

---

### Post by 3rdalbum on 2009-09-06
You may be able to do this if you set up a proxy on your computer, and set up your daughters' laptops to connect to the web through the proxy. Squid is one such proxy that can be installed on your computer, and the latest issue of Linux Format has a HOWTO on setting this up. I imagine you'd need to look at your Squid logs to see what websites and web addresses were visited by what computers.

If you want to physically see what's on your daughter's screen, you can use Remote Desktop on Ubuntu, or VNC. This requires setting up the VNC server (or turning on Remote Desktop on Ubuntu) on the laptop, and then using Remote Desktop Viewer on your computer.

If the salesperson told you that you could monitor your daughters' activities online with ONLY a wireless router, then they were ill-informed or lying, unless your router does actually have a comprehensive logging capability like the proxy that I mentioned.

---

### Post by loosescrew on 2009-09-06
ugm6hr,3rdalbum, Thanks,I searched the web for the last few days and agree with you.This is not going to happen with just a router. Thanks for the replies. Joe

---

