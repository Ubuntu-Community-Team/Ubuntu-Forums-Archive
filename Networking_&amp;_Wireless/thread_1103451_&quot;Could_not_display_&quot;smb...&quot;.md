---
title: "&quot;Could not display &quot;smb://...&quot;"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by vandorjw on 2009-03-22
> 
** Could not display "smb://mikes-desktop/archives/".**
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.


This is a frequent error that I get when using Samba using my wireless connection.(wlan0) When I use the Ethernet cable to connect, it works quite smooth (Auto eth0)

The wireless internet works fine, but the in house LAN does not work using my wireless card. (Intel® PRO/Wireless 3945ABG)

I have no idea why it would work on cable and not wireless.

If anyone has any ideas on how to get samba and nautilus to work properly let me know.

Cheers - CC7

---

### Post by tech.kyle on 2010-10-26
Very similar problem here. Attempting to browse smb shares over wireless causes the DBus message. Connecting to a wired network gets me one step closer to solving my problem. Remote share is on Windows 7 which worked before. 

Dell Inspiron 6400, Ubuntu 10.04 32-bit
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by Dragmah on 2011-03-11
Have you found a solution for this?? I updated my samba on my server PC and it errored during the process and needed to be shut down. The are both plugged into the switch and can ping eachother, even see the files that i am sharing but as soon as you try and access any of them it comes up with the error "could not display "smb://""

any help would be great

---

### Post by vandorjw on 2011-03-12
This post is really old :) The way I 'fixed' the problem was by installing fedora core. I never dug to deep into it to actually solve it on Ubuntu. Some day I might end up reading the samba documentation, and set up a nameserver and do set things up right.

Till then cheers.

CC7

EDIT: I  still run ubuntu on one of my machines, if you want I can install the samba server on it and see if I still have the same problem as 2+ years ago :) and see if i can fix it proper.

---

