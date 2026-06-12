---
title: "Samba stops working after a while"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2010-10-22
This problem has only started happening since I added a 1TB USB HDD to my system, if that helps.

I have created a Samba share, using the fantastic Webmin tool. I have a network media player which can connect to my router, and then access windows (samba) shares. Most of the time, it works fine - it's able to stream HDTV wirelessly across the network. However, every so often, it just stops working ... the media player sees :

Network, then
WORKGROUP, then
FILESERVER-1 (machine name), then
Media (share name), then
Video (subdir, then
TV_Shows (subdir), then
MyShow.AVI ... just hangs

if I use the Webmin tool, I see multiple samba connections all from the media player. 
Restarting samba seems to have no effect. The only way to fix it, is to reboot.

Can anyone suggest a logfile I can check, or a setting I can tweak to fix this issue ?

When it get like this, trying to access the share from a windows machine, just gives me an error saying it can't find the machine. But when it's rebooted, it works fine.

I have mapped the "nobody" linux user to "guest" which is what the media player is defaulted to login with (it's primarily sold as a "Windows" media player), and using Webmin I have assigned the "nobody" user read-only rights to the samba share. It worked fine for 6 months, until I added this new drive.

---

### Post by Jethro_uk on 2010-11-16
Well ! I logged into the machine just now, and noticed the system load was high (15) and had been for a while. I used system monitor, and discovered a few devkit-disks-helper-ata-smart-collect processes had built up.

A quick google finds this:

[https://bugs.launchpad.net/ubuntu/karmic/+source/libatasmart/+bug/419662](https://bugs.launchpad.net/ubuntu/karmic/+source/libatasmart/+bug/419662)

If I read it right, there appears to be an issue with USB drives, powersaving and Karmic ? Could it be that the drive is somehow timing out after a while, and therefore unavailable in samba ?

Anyway, I am building a new server, and will put Lucid on it, to see if it fixes it.

---

### Post by Jethro_uk on 2011-03-07
Well, moving from Karmic to Lucid seems to have cured the bug ....

---

