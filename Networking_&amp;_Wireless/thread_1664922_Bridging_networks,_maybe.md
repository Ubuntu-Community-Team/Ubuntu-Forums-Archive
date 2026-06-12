---
title: "Bridging networks, maybe"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by bguezzie on 2011-01-11
I've got a somewhat unusual network configuration in my home office, and I'm hoping Ubuntu can save me on this one.  However, I'm having a hard time getting things talking.  Here's some background on my network setup (all connections are Ethernet except for the one wireless connection which I've marked):

Home office network -> router -> laptop -> [wireless] -> wireless router -> cable modem

Now some constraints:
 1) The laptop needs to be running Window 7 as its main OS (hands are somewhat tied on this one...it's a work machine)
 2) The home office network needs to be able to access the Internet
 3) The laptop needs to be able to access machines inside the home office network

I originally had a bridged connection in Windows, but that only satisfied constraints 1 and 2.  So, I've been trying to use Ubuntu (running in VirtualBox) to act as a bridge in hopes that I can still use my Ethernet interface in Windows to be able to talk inside the network.

However, I have not had any success with getting machines in the home office network to talk to the outside world.  I have tried using Firestarter with ICS as well as setting up a bridge.  Neither works (router is not able to ping the Ethernet interface of Ubuntu).  In VirtualBox both interfaces are set up as bridged, so they should essentially have direct access to the network.  Is this even the right approach to take?

Does anyone have any ideas of how to solve this, please?  Thanks in advance for your time and help.

---

### Post by PatchesTheCaveman on 2011-01-12
I don't think you'll be able to achieve 3 with any setup, unless there's some sort of complicated NAT setup that I'm not aware of.  Even if you could, performance would be horrible.

Your best option is to buy a wireless bridge.  They're devices designed to connect a wired network to a wireless one, exactly what you're trying to do.  You can find them in many electronics stores and, of course, online.

If you happen to have an extra wireless USB dongle hanging around, you could use that for the bridge and the internal one for the laptop's connection.  But I wouldn't recommend buying one for that purpose because a bridge will only cost $10-20 extra and will work much better.

---

