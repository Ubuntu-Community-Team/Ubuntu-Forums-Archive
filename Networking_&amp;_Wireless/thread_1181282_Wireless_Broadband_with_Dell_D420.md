---
title: "Wireless Broadband with Dell D420"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by Sleestack on 2009-06-07
I'm using Ubuntu 9.04 on a Dell D420 that has a built-in wireless broadband device. Upon boot, Ubuntu recognized the device and I followed the wizard to enable the mobile broadband but the results have been disappointing. It only occasionally connects, even then only at very slow speeds and then it spontaneously disconnects and I can't re-connect. I'm not even sure where to go from here...I'm a bit of a newbie with mobile broadband. Any suggestions?

---

### Post by superprash2003 on 2009-06-08
could be related to [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by Sleestack on 2009-06-08
Thanks for the link. That discussion thread is related to WiFi and not broadband, but the gist of it all to me seems to be the Linux kernel and wireless just isn't there yet. I'm gonna have to punt on this one, I guess, and switch hardware devices...maybe a USB device may work. Ubuntu is still a great OS choice for me, but this is disappointing. 

I live in the US (New York) and am open to using any wireless carrier. Is there a USB device and carrier anyone can recommend?

---

### Post by GeorgeVita on 2009-06-08
Hi **Sleestack**,

> **Sleestack said:**
> ... Ubuntu recognized the device and I followed the wizard to enable the mobile broadband ...It only occasionally connects, even then only at very slow speeds and then it spontaneously disconnects and I can't re-connect...

As you have connected at least once the h/w works fine. Low speeds possibly means GPRS instead of 3G (HSPA) signal. Disconnection and/or no connection could be low signal or searching for a good signal. Recent version of Network Manager does not show you the 3G network status or the signal strength. Some users have tried umtsmon instead. Another issue could be the wrong initialisation done by the system (9.04).

My opinion is first to determine if it is caused due to low signal (test signal strength by inserting the SIM to a GSM phone?). Then try another O.S. (if any) or a previous 8.10 LiveCD. Last idea is to open a thread at "Dell Ubuntu Support" category ([http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)) as more Dell users/developers can test to solve your problem.

Regards,
George

(P.S. WiFi=Broadband, HSPA/UMTS is more Mobile than Broadband!)

---

