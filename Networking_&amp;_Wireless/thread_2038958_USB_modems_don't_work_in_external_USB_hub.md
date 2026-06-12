---
title: "USB modems don't work in external USB hub"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by donalbane on 2012-08-07
I am running Jaunty on an IBM Thinkpad T41. I can plug Novatel USB760 and Sierra Wireless 598U usb modems into the laptop's USB ports and the computer will recognize them, and I'm able to successfully launch pppd on each using pon. However, if I plug them into a Satechi 4-port USB3.0 hub, the symlinks to the devices in /dev (created in /etc/udev/rules.d/50-myrules) may or may not show up, depending upon which port the devices are plugged into. Even if they do show up, pon fails for each. The pppd log shows that /dev/USBModemVerizon4 could not be found, for instance, even when ls -l /dev shows the symlink.
 
Can someone offer some advice to on how to get USB modems to work with a USB hub? I'm forced to use a hub because I will need to use 3 modems, 1 GPS receive, and a mouse for my application, and the computer only has 3 USB ports.
 
Don

---

### Post by donalbane on 2012-08-08
I have some new information to add.  I tried an older Belkin 6-port USB hub instead of the Satechi, and both devices show up in /dev with the expected names.  The Sierra Wireless device even works with pon, but the Novatel USB760 does not.  However, if I go in through System-Preferences->Network Connections and set that device to automatically connect, IT DOES.  Any ideas on what magic the Jaunty auto-connection is working to allow the device to connect that pon is not working?  I need to be able to turn the device on and off programatically, and it would be useful to know what is going on behind the scenes.
 
Don

---

### Post by donalbane on 2012-08-08
I was able to get things to work.  I had previously followed the advice in this thread:
 
[http://ubuntuforums.org/showthread.php?t=1002262](http://ubuntuforums.org/showthread.php?t=1002262)
 
It mentions editing the line in /etc/udev/rules.d/70-persistent-cd.rules that contains the "Novatel_Mass_Storage" label.  I did this.  However, I only did it for the FIRST occurance of this label.  It actually occurred multiple times in the file.  When I made the suggested edits for every occurrence of the label, the modem worked from the external USB hub.
 
Don

---

