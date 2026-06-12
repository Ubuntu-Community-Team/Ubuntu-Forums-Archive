---
title: "Samsung R522 realtek RTL8192E wlan"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by Romualdou on 2009-12-20
Hi,
 
I'm getting trouble to have my Samsung R522 Wifi working. 
Tried with Ubuntu 9.10 64bits version. 
 
Samsung R522
Realtek RTL8102E
 
 
 
I tried to set up using ndiswrapper with several windows drivers (XP, Vista, 7, 32 and 64bits) downloaded from Samsung site. After modprobe ndiswrapper, dmesg will bring following result :
 
couldn't prepare driver 'net819xp'
couldn't load driver net819xp
 
wconfig and ifconfig show no wlan interface.
 
Using 32 bits driver would bring an additional message stating that driver is 32bits whereas system is running 64bits. 
 
I read somewhere that the configuration would run with the 32bit version, but before making a full reinstall and downgrading, I'd like to know if there's anything I can do to get wlan running. 
 
 
With ATI graphics and Realtek wlan, it seems I picked up just the right hardware to get into troubles with ubuntu... :(
 
thanks for any help.

---

### Post by Dude-PWB- on 2009-12-20
Have you checked this thread?

[http://ubuntuforums.org/showthread.php?t=1239342](http://ubuntuforums.org/showthread.php?t=1239342)

There are native linux drivers for that adapter, but to get the 64bit driver, you may have to send an e-mail to realtek to get them. That's what i had to do for my 32bit drivers. 

Good Luck!

---

### Post by Romualdou on 2009-12-20
Thanks, but I already tried all this...
 
I eventually came a bit forward, quoting Wikipedia : 
 
"Also, NDISwrapper does not implement NDIS 6 (Windows Vista version) yet, limiting drivers to Windows XP."
 
The 64bits drivers I found so far were for Vista or W7, so I guess I should look for XP64 drivers. Keep you posted if I found some.

---

### Post by Romualdou on 2009-12-20
Downloaded XP drivers from Realtek site. Took the one called X64, only that one I didn't try so far. I guess it stands for XP 64bits. Caused a red <!> to show up in the taskbar. Guess it is a kernel malfunction. Computer hanged up on reboot and hangs up on login. 
I booted safe mode and deinstalled the driver with ndiswrapper. Boots again, but I'm back to where I started. 
 
I will now download 32bit version of Jaunty, reinstall completely and hope to have better success with the 32bits version !

---

### Post by Romualdou on 2009-12-20
Back online, this time with Ubuntu running on my laptop ! I wiped out the 64 bits install and did it all again with the 32 bits. This time it works !

My personal conclusion : realtek 8192E does not work with 64bit Ubuntu 9.10 ! :(

If somebody managed to have it work, I'd be happy to get to know it !

Not sure if this thread can be considered as solved... :confused:

---

### Post by northd_tech on 2010-02-06
> **Romualdou said:**
> Back online, this time with Ubuntu running on my laptop ! I wiped out the 64 bits install and did it all again with the 32 bits. This time it works !

My personal conclusion : realtek 8192E does not work with 64bit Ubuntu 9.10 ! :(

If somebody managed to have it work, I'd be happy to get to know it !

Not sure if this thread can be considered as solved... :confused:

Realtek might have finally bailed us out of this dilemma- see this thread for details:

Realtek rtl8192e wireless not seen
[http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E](http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E)

---

### Post by Romualdou on 2010-02-07
Well, I guess this would do it. 

But at this stage, I will not consider moving back to 64bits as my whole system is now properly tuned after 32bits install. Maybe by some later update. 

I now have to spend some _productive_ time on my laptop :D

Thank you for the hint anyway, I think we can consider this thread as solved. 

Just need to figure out how to mark it solved...

Regards,

---

### Post by Daniel Lewandowski on 2010-03-12
Problem is inside the Realtek driver. I don't exactly remember but on the 64bit platform the timeout for the firmware initialization is too small. On the 32bit platform this timeout (something about 20ms) is enough.

If someone is interested I can send the modified file.

---

