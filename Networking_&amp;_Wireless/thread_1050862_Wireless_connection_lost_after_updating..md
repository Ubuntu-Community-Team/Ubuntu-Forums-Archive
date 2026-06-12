---
title: "Wireless connection lost after updating."
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Nidding on 2009-01-26
Can't find quite this problem on the forum, so here goes...
After updating for the first time in a while this morning, my Acer aspire lost it's wireless network connection. It doesn't connect or even detect wireless networks, plus the 'wireless networks' doesn't appear on the networks list.

Any suggestions on what could be wrong?

---

### Post by Kobalt on 2009-01-26
How did you get your wireless working? Did you have to install some drivers, etc.? If today's updates "broke" something it should be in this area...

---

### Post by desultory on 2009-01-26
I'm having similar issue.  Installed new Ubuntu 8.10 on old HP laptop and got wireless working without installing anything just using 8.10 out of the box network configuration tool.  Updated 200+ something updates over the wireless connection then restarted.  After restarting the connection fails authentication on hidden ssid wep enable linksys wireless router.  There is an error message in the log stating an issue with expected "magic" values.  This is my first "Linux" install and enjoying the change and challenge of learning something new.

---

### Post by timcredible on 2009-01-26
if the updates had a new kernel, you have to install the wireless driver in the new kernel.  to test, pick the old kernel (if available) in the grub menu - if wireless works, then that's the issue.

---

### Post by desultory on 2009-01-26
Since I'm new to this world it sounds like you are saying the wireless drivers which are part of the live cd install were already installed in the kernel.  I was reading a saw there are 3 "packages" that 8.10 comes with, ndsiwrapper, b43 or something like that and another broadcom can't remember the actual name.  When you say install driver just installing one of those 3 back into the kernel since that is what was working before?  Also if the new kernel is missing the needed installation how would that allow for connection but reject authentication terminating the attempt to connect?  Also since I didn't install any drivers in the first place why would an updated kernel require me install them now?  Confused newbie!

---

### Post by Nidding on 2009-01-27
> **Kobalt said:**
> How did you get your wireless working? Did you have to install some drivers, etc.? If today's updates "broke" something it should be in this area...

It worked out of the box when I installed Hardy. The wireless card is an Atheros AR5BXB63. It didn't work by default in gutsy, but I got it to work there. Can't remember how, though...

Also, I have realized that my sound card is no longer working either. Pardon my French, but wtf is up with this upgrade???:confused:

---

### Post by desultory on 2009-01-27
I think I figured out many of the "work before but not after updating" issues.  The problem I found with my wireless was two drivers orinoco drivers and hostap drivers for one piece of hardware.  The updated kernel has different drivers set as default than the previous kernel or something like that.  Might be mistaken since reading forum posts for two days.  Here is the final post that helped me.  [http://ubuntuforums.org/showthread.php?t=968797]("http://ubuntuforums.org/showthread.php?t=968797")  I'm guessing if this happened with one type of hardware it may have happened with others.

---

