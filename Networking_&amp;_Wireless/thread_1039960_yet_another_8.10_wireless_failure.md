---
title: "yet another 8.10 wireless failure"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by digitalramble on 2009-01-15
Yeah I know it's been a while.  I've been using a wired connection in the meantime, but I'd really like to get the wireless back up.

Background:  Same computer, same hardware since warty warthog.  Clear up to 8.10 install, the wireless worked a charm, right out of the box.  After 8.10, it acts like I have no wireless whatsoever.

I spotted this in the dmesg, does this provide any ideas about what is going on? 

[   28.030289] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   28.486895] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   28.486902] ipw2200: Unable to load firmware: -2
[   28.486906] ipw2200: failed to register network device
[

Thanks for any help.

---

### Post by cdtech on 2009-01-15
> To work around this, you can increase the default timeout value:

	echo 100 > /sys/class/firmware/timeout

and then reload the ipw2200 module. If this corrects your problem, you may wish to add the above line to your system startup scripts prior to the point at which the driver module would be loaded.

The other most common reason for getting the above error is that the firmware files are not installed in the correct location. Please see the INSTALL document for information on installing the firmware files.
Taken from this site:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by digitalramble on 2009-01-15
> **cdtech said:**
> Taken from this site:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
Thanks for the pointer, very interesting information. I seem to be unable to change the /sys/class/firmware/timeout file, though.  Sudo doesn't work.  vi (in sudo mode) refuses to change it, even when I try to override.  (Was going to just change the file and reboot to see if this was the problem, but I'm kinda stopped here.)

While I'm here, would modprob or insmod for reloading be better?  And when I did a locate on the ipw2200 module to see where it was, I got quite a few listed. How would I determine which one was actually used?

Not new to linux, but this is an area I'm not so familiar with, so thanks in advance...

---

