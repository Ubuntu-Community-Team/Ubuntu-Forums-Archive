---
title: "Sakis3g needs cold boot to detect modem + Ubuntu network manager issue."
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by Abhishek_K._Pandey on 2013-09-01
Hello all.
Iam very new to Linux and Ubuntu is the first Linux OS I am using.
I want to ask about connecting to internet via USB modem.
This is an epic issue and I can see a lot of users having the same issue.
I have been successful with Sakis3g. But, I have a few very annoying issues with it.

1. Issue is that Sakis3g does not work at all neither Ubuntu detecst modem, if I plug it in when, laptop is already running. Actually, network-manager doesn't detect it all, until I connect internet via Sakis3g. I would like to know that what sakis3g do, which network manager can't. Usb-modeswitch is there for this only na!!
So, if I am running my system and wants to connect, then, I have to close all my programs and cold boot my PC. Even a simple restart is not enough.

2. Also, if network disconnects automatically, then Ubuntu's network-manager does not detect it afterwards, until a cold boot, but Sakis3g still connects. But, this problem does not happen, if I manually disconnect.

Procedure to connect is:
1. Plug in USB Modem.
2. Boot system.
3. Run Sakis3g. Select 'Connect 3g'. It will show some errors like 'PID XXX is using Modem'. Just bear with them. Finally, it'll connect.
4. PROBLEM: Network-manager won't show up as connected. Hence, you can't use Software Centre or update manager.
5. SOLUTION: Disconnect Sakis3g and now connect via network-manager.

I am using Ubuntu 12.04.2 LTS fully updated and my USB modem is Micromax 350G with SD card support. In lsusb, my modem shows up as Omega technology. One more thing, I have noticed is that, product ID of modem changes from f000 to 9605, when it gets connected. I think that's because USB switches mode.

---

### Post by Abhishek_K._Pandey on 2013-09-02
No answer :-(

---

