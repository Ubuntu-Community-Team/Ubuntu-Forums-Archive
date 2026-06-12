---
title: "Wireless once worked, now broken in HP Mini 110 Ubuntu"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by Greg Kuperberg on 2009-10-24
I am the proud owner of two HP Mini 110 Mi edition netbooks.  Actually they are for my children.  As I understand it, these netbooks come with modified Ubuntu 8.04 distributions.  Wireless used to work on both of these netbooks, but now it only works on one of them.  We are out of ideas for how to fix the problem, other than an emergency reinstall of the factory state of the SSD.

When the computer first boots, or when it is in sleep mode for long enough, the wireless LED is blue (which means wireless is on, killswitch is off).  However, when I log in or wake up the computer after first log in, it turns orange.  It stays orange when I slide the switch; we have slid the switch dozens of times and it stays orange.

I looked at dmesg and syslog as root to get clues.  dmesg gives every indication that the wireless card (which is a Broadcom 802.11g card) and its driver work.  (Note that wireless is handled by NetworkManager.)  syslog is a different story.  Even when it was working, syslog would have the line "Deactivating device wlan0."  However, it would be followed by the line "SWITCH: no current connection, found better connection 'wlan0'" and then by various lines that show NetworkManager bringing up a connection.

Now when we log in, syslog still says "Deactivating device wlan0" once or twice, but there is no line in syslog that says "SWITCH" and nothing much happens in syslog after that.  That seems to be about the time that the radio killswitch turns orange.  What is frustrating is that it is blue when it wants to be blue and orange when it wants to be orange, and sliding the switch does no good.  Moreover, once it is orange, nm-applet disables the wireless checkbox, and manual configuration doesn't seem to help either.

We installed a few things on this computer (using synaptic or apt-get or something) as root:  wine, planet penguin, eog, fspot, and some automatic updates.  Other than that, I don't see what we did to ask for this.

---

### Post by Greg Kuperberg on 2009-10-24
Update:  I got frustrated with this wireless problem, so I did a "system restore", which on this computer is a reinstallation of a factory OS image from ROM.  It didn't work!  The problem is the same as before.  I conclude that somehow the EEPROM on the wireless card became corrupted, that the wireless card needs to be reset, and that NetworkManager gives up and concludes that wireless does not exist.

We have a help ticket number to send the netbook to HP and have them fix the problem.  This is not ideal, so I am wondering whether there is some Ubuntu/NetworkManager utility to fully reset the wireless card.  Again, the computer is a Mini 110-1000CTO and the card is a Broadcom 802.11g.

---

### Post by backpaddle on 2009-12-21
FYI, I have encountered the identical problem.  I have done no system updates since the wireless was working fine.  I am running the OS that was delivered on the HP mini 110 mi, plus a few extra applications.  It it like the kill-switch is activated whenever nm-applet (the network manager) tries to activate.  "iwconfig" responds as if the device is turned off.

---

