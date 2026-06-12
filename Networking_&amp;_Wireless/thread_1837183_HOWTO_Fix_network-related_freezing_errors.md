---
title: "HOWTO: Fix network-related freezing errors"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by rectec794613 on 2011-09-01
_Introduction_
I've noticed quite a few users who are having Ubuntu, or any other Linux distribution lock up whenever they shutdown, stand-by, disconnect from their wireless internet, or even on the login screen. This could be due to conflicting wireless adapter/card drivers. In other words, there's 2 drivers/modules trying to access the same hardware. So whenever something causes the networking system to be turned off (be it shutdown, stand-by or manually disabling it), the system freezes. This guide will aim to fix this issue by removing the extra module and blacklisting it.

**[COLOR="Red"]Disclaimer: As far as I know, the only conflicting wireless modules are the RT2860s for use on some Realtek/Ralink wireless cards. This might work for other models, but I cannot guarantee it. If you run into a problem along the way, I will try my best to solve it, but this is ultimately your responsibility. If something goes wrong, see the "Part Two: Recovery" section at the end of this guide to reverse the process.[/COLOR]**

**_Part One - Removal_**
_Step 1 - Identify your wifi adapter module_
Open up a terminal window. By default the key combination is CTRL+ALT+T. Enter this command to list the modules/drivers in use for your hardware and highlight the ones with "rt" in the name:
```
lsmod | grep rt
```
If it shows something along the lines of "rt2860", your good. We've found the culprit. If not, **please either turn back and seek help elsewhere or continue carefully and at your own risk.** 

_Step 2 - Modprobe_
Modprobe, basically, is a simple tool included in the Linux kernel that is used to add or remove a module. We need to remove the extra wifi adapter module so our troubles will go away, so we'll go ahead and enter these commands to remove both wifi drivers, then add only one back in.
To remove the first module:
```
sudo modprobe -rf rt2800pci
```
And to remove the second one:
```
sudo modprobe -rf rt2800sta
```
Then finally add just one back in:
```
sudo modprobe rt2860sta
```

_Step 3 - Backup Blacklist_
Before we blacklist the offending module, I recommend backing up the blacklist file at /etc/modprobe.d/blacklist.conf. To do this, we'll make a copy of the file and put it in the home folder.
```
sudo cp /etc/modprobe.d/blacklist.conf ~
```
**Make sure you include that last tilde (~).**

_Step 4 - Blacklist_
Now it's time to get rid of this module once and for all. Enter the following command into the terminal:
```
blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
``` 

_Step 5 - Restart_
You can do this right? If not do this :)
```
sudo reboot
```

And that's it! Hopefully the problem is gone. Thanks for reading this guide. If you have any problems after restarting, or you need to reverse the process, see below.

**_Part Two - Recovery_**
Did I screw your computer up? Damn. Here, just follow these instructions.

_Step 1 - Un-blacklist_
Just take that backup of the blacklist file in you home directory and replace it with the new one with this command:
```
sudo mv ~/blacklist.conf /etc/modprobe.d/
```

_Step 2 - Un-modprobe_
Use this command to add the module back in: 
```
sudo modprobe rt2800pci
```

I hope this helped. Any improvements, suggestions, or questions are welcome. Either reply to this thread or PM me.

Credit for commands goes to Linuxexperte and her life saving post: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103)

---

