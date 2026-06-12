---
title: "Having trouble connecting to both wireless and wired networks"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by skeays on 2009-07-17
Hi, I am an ubuntu noobe and I have somehow disabled my computer's ability to connect to the internet. I am currently running Hardy Heron on an old Toshiba Satellite. My taskbar shows that it is receiving a signal, but, when I launch firefox, it keeps telling me that the address is not found. Also, when I try to connect to a wired connection, nothing seems to be happening there either. Where you plug in isn't even indicating that it detects the network. Any help that you folks could give me would certainly be appreciated. 
 
Cheers and beers.

---

### Post by coffeecat on 2009-07-17
I think (indeed I hope) that all you've done is to accidently disable networking in Network manager.

Try this. Make sure that your ethernet cable is plugged in and that your modem-router is switched on and connected. Now look for the Network Manager applet icon. It's on the upper panel towards the right, probably just to the left of the volume control icon and the system clock applet. The icon design varies depending whether you have a wired or wireless connection and whether it is enabled or not.

Right-click on the applet icon and make sure the 'enable networking' box is ticked. If you do this and you have a live wired connection, it should just connect by itself. However....

> **skeays said:**
> My taskbar shows that it is receiving a signal

I'm not quite sure what you mean by this. Do you mean that Network Manager is showing wireless networks in range? If so, and whether or not you try to connect with a wired connection or wirelessly, right-click on the NM applet icon and select 'Connection Information'. That should show you whether your router has assigned you an IP address, and whether your system has picked up your ISP's DNS addresses.

I'm assuming you are using a modem-router. Perhaps you could give us more details about your internet connection.

---

### Post by skeays on 2009-07-17
Thank you for the advise.  
 
The network manager is showing wireless connections in range.  It says that I am connected to a random network in my office building with 58% signal strength.  When I rightclick on "Connection Info", there is no IP address and the Configuration setting is on "Automatic Configuration (DHCP)."  It still will not go to my homepage, though.  
 
The back of the computer where you plug in the internet is indicating that the computer does detect it being plugged in (the little lights are flashing). 
 
Thanks again!
Scott

---

### Post by coffeecat on 2009-07-17
> **skeays said:**
> The network manager is showing wireless connections in range.  It says that I am connected to a random network in my office building with 58% signal strength.  When I rightclick on "Connection Info", there is no IP address and the Configuration setting is on "Automatic Configuration (DHCP)."  It still will not go to my homepage, though. 

If there's no IP address, then you are not connected. The IP address is allocated by the DHCP server, in this case I guess this would be the wireless router that you've detected.

When you say a "random network" is this one of your employer's networks, or a network from another company? If the latter, it's illegal in most countries (certainly here in the UK) to piggyback on a network without the consent of the network owner. Besides, a wireless network run by a company is almost certainly password protected, which is probably why you cannot connect.

Before we go any further, what networks do you have in your own organisation that you can legally connect to? Are they wired or wireless? Do you have an ethernet port near your workstation you can plug into? If wireless, do you have a WPA code (or whatever encryption protocol is being used) for this?

---

### Post by skeays on 2009-07-17
I have a wired port both here and at my office.  The signals that I'm picking up are most likely from surrounding companies.

---

