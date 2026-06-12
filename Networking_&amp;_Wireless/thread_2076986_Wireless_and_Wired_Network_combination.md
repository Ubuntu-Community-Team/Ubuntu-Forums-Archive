---
title: "Wireless and Wired Network combination"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by rich86 on 2012-10-27
Hi,

I have a desktop PC and laptop both running Ubuntu i want to be able to use my laptop plugged into the tv to stream video stored on my PC, the wireless network that i have is a bit laggy and results in a lot of buffering. What i would like to do is have a network cable running from my PC to the laptop to this can be used for streaming video. I can't run cables from from my internet wireless router as it is to far away. I have a second router that i can use to make a second network (on a different subnet) which works if i have the wireless disabled on the laptop. The problem is that the PC then looks for the wired network for the internet so the internet fails.

What is the best way of setting this up? Should i use a bridge? I could use a Ethernet to Ethernet cable instead of the second router do i need a different cable type and how would i set this up to the laptop gets its IP from the internet router? Would the laptop then be able to access the internet through the PC?

Any advise/help/ideas?

Thanks in advance.

Richard

---

### Post by ahallubuntu on 2012-10-27
One point of confusion: is the desktop PC wired now or is it wireless, too?  If it's wired but you can't find a cable quite long enough, setup a switch at the desktop PC and wired the laptop to it from there.  That way, everything will be on the same subnet.  (You can probably turn the 2nd router you have into a switch as well, by disabling DHCP on the LAN.)

Another approach is to invest in a portable hard drive and make a copy of the videos on that, then just wire that directly to the laptop.  Or, move the desktop close enough to wire it directly to the TV.  If the desktop has no HDMI port, you can buy a video card most likely to add one.

---

### Post by rich86 on 2012-10-27
The PC has wireless to connect to the internet router. No cables will reach from the internet router to either the laptop or the PC.

The much easier approach would  be to have the TV as a second monitor but that tends to end up with problems setting up the displays and making sure things appear on the correct screens. I do have a usb that i can use to watch stuff from the PC on the laptop, i was just wondering if there was a way of setting this up to have the PC as a file store to save having to copy things across each time.

Thanks for your thoughts.

---

