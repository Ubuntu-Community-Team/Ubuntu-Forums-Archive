---
title: "Update kills all network connections"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Mr_Wonderful on 2009-12-07
good afternoon all, following a pretty serious issue with graphics issue with my ATI graphics card I deleted my Linux partition on my hard drive and started again (in the process installing 9.10, previously running Jaunty)

on start-up I had no option to use my wireless card (which I kind of expected, network manager didnt work in Jaunty either), but WICD did, so I installed that and still no option for wireless, I could kind of cope with this and just ran an ethernet cable across my room and was gonna "fix it later", any who.... last night the update manager popped up telling to download and install some crap (which I did) after a restart I was presented with a password box saying WICD needed to access my network connections so I popped my root password in (Im the only user on the computer so there should be no issues with permissions ect....)

now I cant even connect to a wired connections, I have tried to open WICD but the screen just kind of flickers and nothing happens.... typing wicd into TERMINAL give the response "Root privileges are required for the daemon to run properly.  Exiting."

the update is called 2.6.31-16-generic in GRUB.....

my question is, is there something I should be installing which works better with 9.10 than Wicd and if so how do I install it without a internet connection, from a flash drive or something ???>

cheers for you time and apologise on the long post

Nick

---

### Post by bayvista on 2009-12-08
I think there is a major problem with networking on 9.10 and I suggest you go back to 9.04 until they fix it. That's what I have done.

---

### Post by seenthelite on 2009-12-08
> **bayvista said:**
> I think there is a major problem with networking on 9.10 and I suggest you go back to 9.04 until they fix it. That's what I have done.

I agree.

---

### Post by alexyz on 2009-12-09
[deleted:  I posted to the wrong thread by mistake.]

Mr_Wonderful, you can run network-manager instead of wicd.  (That said, many people run wicd because they have fewer problems than with network-manager.)  If you don't have a connection you can download the .deb files to a usb and install from there.

---

### Post by GSGITU on 2009-12-10
> **alexyz said:**
> [deleted:  I posted to the wrong thread by mistake.]

Mr_Wonderful, you can run network-manager instead of wicd.  (That said, many people run wicd because they have fewer problems than with network-manager.)  If you don't have a connection you can download the .deb files to a usb and install from there.

can someone point me to the .deb file for the network manager.
thanks

---

