---
title: "Mobile Broadband in Ubuntu"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by svaens on 2009-09-23
Hi all, 

I thought it would be a good thing to document my experience with Mobile Broadband on Ubuntu. With documentation for mobile devices usually catering to windows, and maybe MacOS, when it comes to configuring your device, it is not always obvious what you need to do (even if it ends up you don't need to do much at all). 

Maybe we can turn this into a list of configurations, so that those looking for help can find our examples, and benefit. 

------------------------------------------------

Note: The text <blank> means that the field is blank (contains no text)

OS: Ubuntu 9.04
Device: HUAWEI E1762 HSPA USB Stick
Provider: Exetel (Australia) through Optus network
Account type: Pre-paid

Connection settings:
Connect automatically: 1
Mobile Broadband tab
--------------------
Basic:
Number: *99#
Username: <blank>
Password: <blank>

Advanced:
APN: exetel1
Network: <blank>
PIN: <blank>
PUK: <blank>

PPP Settings Tab
----------------
<default>

IPv4 Settings Tab
-----------------
<default>

===========================

Setup steps:
1. Do NOT yet insert your USB Device
2. right click network manager sys-tray icon, click menu item "Edit connections"
3. Navigate to the "Mobile Broadband" tab
4. click the + Add button
5. In the popped up dialog, click 'Next' and choose the appropriate provider setting type. 
6. For exetel, it should result in settings as found above. Nothing in username or password. The important thing is the setting - APN: exetel1
7. Insert the USB device. Now with the correct network settings, and a recognized USB device, the connection should be made. 

On the HUAWEI E1762, there is a LED that blinks first green, then blinks blue, then finally rests on blue once the connection is up.

---

### Post by 3rdalbum on 2009-09-23
I think every device has that same configuration, except different provider names.

In any case, this isn't the appropriate place to submit configurations. The Network Manager project is the correct place, and this way they end off upstream.

---

### Post by icecoffee69 on 2010-09-14
How do my e1762 on Optus plan to work:10.4 Ubuntu i have a optus prepaid and it work fine 
thank-you
:)

---

