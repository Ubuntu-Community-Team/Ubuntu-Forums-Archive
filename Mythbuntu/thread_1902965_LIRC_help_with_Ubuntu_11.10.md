---
title: "LIRC help with Ubuntu 11.10"
date: 2012-01-01
forum: Mythbuntu
---

### Post by JimLS on 2012-01-01
I have a fresh install of 11.10.  Installed Mythtv and got my tuner and output working.  But LIRC doesn't work except arrow keys.  I have done a bunch of reading - lots of people with similar issues.  But documented fixes are all a bit different.  ubuntu.com doesn't seem to have anything on lirc that applies to 11.10.  I have read that lirc for usbmce is part of the kernel but I am not sure what that means - I have some idea but not how that affects using it.  I haven't been able to find the lirc config files and would like to just turn off the kernel stuff and go back to a classic lirc install.  I currently have a usbmce transceiver but may go with a serial UIRT2 or some such.  I also would like lirc to work with some older programs so think using the non-kernel version may be easier.  

I have found the post on bugs here:

but not sure exactly what to do.  They did a lot of stuff before getting it to work and not sure all of it is needed.  What does the line 

[http://ubuntuforums.org/showthread.php?t=1859528&highlight=lirc+11.10&page=11](http://ubuntuforums.org/showthread.php?t=1859528&highlight=lirc+11.10&page=11)

Can someone tell me what this line does?
sudo sed -i '$i echo lirc > /sys/class/rc/rc0/protocols' /etc/rc.local

If I try to use the kernel version where is some clear documentation on how to configure and use it and how to deal with the changes?  Apparently this was done to make things easier - well, that doesn't seem to be the case.  

This apparently isn't just an ubuntu issue but I didn't find anything that looked to cover this on the lirc site either.

---

### Post by nickrout on 2012-01-01
[http://www.gossamer-threads.com/lists/mythtv/users/499513#499513](http://www.gossamer-threads.com/lists/mythtv/users/499513#499513)

---

