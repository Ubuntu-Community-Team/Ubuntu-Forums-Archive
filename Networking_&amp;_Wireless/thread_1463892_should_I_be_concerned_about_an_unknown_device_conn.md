---
title: "should I be concerned about an unknown device connected to my router?"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by trubliphone on 2010-04-27
The title says it all.

I had previously been having loads of problems getting my wireless printer to work with Linux [[http://ubuntuforums.org/showthread.php?t=1453697]](http://ubuntuforums.org/showthread.php?t=1453697]).  Everything is working fine now.

However, something that confused me is that whenever I tried to ping the printer _before_ I got it working, it would fail with a _different_ IP address.  That is, the command 'ping x.y.z.3' would fail with a message saying it was unable to contact 'x.y.z.2'

Now I am looking at my router - for something unrelated - and I've noticed that rogue IP address shows up in the list of connected devices.  It has a MAC address but for the device name it lists "<unknown>".  

Should I be concerned about this?  Any idea on how to figure out what this device is?

Many thanks for your help.

---

### Post by trubliphone on 2010-04-27
For what it's worth, the full story of my fiddling with the wireless printer can be found here: [http://www.ebusiness-technology.net/2010/technology/how-to-get-a-wireless-hp-officejet-printer-working-with-a-linux-laptop/](http://www.ebusiness-technology.net/2010/technology/how-to-get-a-wireless-hp-officejet-printer-working-with-a-linux-laptop/)

---

### Post by scottuss on 2010-04-27
Is your router protected by a WPA key?

---

### Post by trubliphone on 2010-04-27
Yes, it is.  The router settings show the following security option enabled:

WPA-PSK [TKIP]

---

### Post by scottuss on 2010-04-27
In that case, it is unlikely that anyone is on your router as WPA keys are hard to crack. Think about any devices that may connect that you've not counted in your head (I keep a list of all the things I connect to my wireless router because otherwise, I'd easily forget!)

Don't forget things like game consoles (Wii, PS3, Xbox, PSP) Mobile phones, any laptops, desktops and anything else that may connect.

Double check and if you're still worried, reset your router, creating a new (very long, strong) WPA key.

Maybe also turn MAC address filtering on, for a little added protection (this should never be used exclusively as MAC spoofing is fairly trivial)

Hope that helps a little!

---

### Post by lisati on 2010-04-27
I've had MAC addresses turn up on my router that I haven't recognized from time to time, thankfully not often. One possibility that occurred to me at the time is that a neighbour or a visitor to a neighbour's place have tried unsuccessfully to connect to my network. 

As others have suggested, using WPA/PSK and possibly MAC filtering as well will go some way to preventing unauthorized access.

---

### Post by scottuss on 2010-04-27
> **lisati said:**
> I've had MAC addresses turn up on my router that I haven't recognized from time to time, thankfully not often. One possibility that occurred to me at the time is that a neighbour or a visitor to a neighbour's place have tried unsuccessfully to connect to my network. 

As others have suggested, using WPA/PSK and possibly MAC filtering as well will go some way to preventing unauthorized access.

Yes, but these shouldn't show up as "connected" devices, they would only show up if they successfully connected to your network (in theory)

It's probably nothing to worry about if the entries are in the log, as failed attempts may possibly be logged here.

---

