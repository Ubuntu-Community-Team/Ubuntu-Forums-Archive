---
title: "Problem Connecting to DHCP Network"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by PerfectReign on 2009-08-10
I run 9.04 on my laptop with a Intel wireless and broadcom wired network.  I typically use wireless at home and always use wired at work.

At home, I have a DHCP address assigned on my network which is behind a hidden SSID using WPA.

At work, I'm on a NT Lan Manager Active Directory network using the wired network with DHCP as well.  

I use Network manager to connect in both instances and always go through the GUI. I don't use ifup at all.


Now - at home, I have no issues connecting. At work, when I first installed Ubuntu (I had been using openSUSE on this laptop for the first year of having it) I had no issues connecting.

The past week, however, I have been unable to obtain an IP address here at work without having to go into the command line, type in su, enter my password, then type dhclient.

I searched the forum and found this thread - [http://ubuntuforums.org/showthread.php?t=24994&highlight=dhclient](http://ubuntuforums.org/showthread.php?t=24994&highlight=dhclient) - which may or may not be what I need. 

Any ideas what could have changed either on my side or the Active Directory side to cause me not to pick up an IP at work? (Remember, I have no issues picking one up at home.)

---

### Post by Iowan on 2009-08-10
I keep trying to make [this]("http://ubuntuforums.org/showthread.php?t=1156441") fit... usually unsuccessfully, but worth a check.

---

### Post by PerfectReign on 2009-08-27
Hmm. Tried that thread and was still unable to connect without running dhclient.

As a kludge fix, I wonder if there's a way to automatically run dhclient without user interaction on boot. 

In other words, run it without having to type the root password in some startup script.

---

