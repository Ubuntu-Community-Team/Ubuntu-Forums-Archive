---
title: "How to get ndiswrapper to work for a nic that's detected by default?"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by gizzmoe on 2006-06-04
Dapper tells me it detects my USB wireless adapter when it starts up...it shows up in the list and everything. But, it's all screwed up because I can't get on the internet with it.

When i had breezy installed, i was using ndiswrapper with this adapter perfectly.

What I would like to do is get rid of whatever it is dapper is currently using to see my card and force it to use ndiswrapper since i know that works.

How do i go about finding out what i need to remove or how to force dapper to use ndiswrapper instead of what it is currently using?

---

### Post by DarthMandeep on 2006-06-04
If it's USB, typing "lsusb" in a terminal should give you some info about it. Once you've got that, try a Google search for it so you can find out what chipset and driver it's using. You could also type "dmesg" in a terminal and look through the bootup messages. Once you know what driver it's using, you can type "sudo rmmod drivername" in a terminal to unload it.

Then you can load ndiswrapper and see if it works. To stop the original driver from being loaded every time you reboot, add "blacklist drivername" to the /etc/modprobe.d/blacklist file.

---

### Post by gizzmoe on 2006-06-04
Thanks!!

After a bit of messing around with it, I was able to track down the ones that i needed to blacklist. Going to post my solution in the network adapter solutions thread now :)

---

### Post by barrmulio on 2006-06-04
Can you please detail the solution? I have a nic that's being recognized, I see all my networks, but I can't connect to any...thx

---

### Post by gizzmoe on 2006-06-04
Check out my post here:

[http://www.ubuntuforums.org/showthread.php?t=184795&page=4](http://www.ubuntuforums.org/showthread.php?t=184795&page=4)

---

