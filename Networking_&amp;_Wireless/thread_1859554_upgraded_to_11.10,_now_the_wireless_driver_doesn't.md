---
title: "upgraded to 11.10, now the wireless driver doesn't work"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by imnvs on 2011-10-14
Okay, so I'm not as knowledgeable as many, and just went through the upgrade to 11.10.  As soon as I got that finished, after the restart, my computer loses wireless capability.  I look about and find that the "Broadcom STA wireless driver" will not activate and I suspect that has something to do with it.  The log (/var/log/jockey.log) is full of information, but I'm not sure what I'm looking for or where to go next.  Help please?

---

### Post by imnvs on 2011-10-14
This is still not working.  I have followed as much of the advice I can find around here, but nothing seems to help.

---

### Post by cblah001 on 2011-10-14
Here is what I did to get mine working. Hopefully it works for you.

In Terminal:
sudo apt-get remove bcmwl-kernel-source

Now go to "Additional Drivers" in your settings (or search additional drivers and click on it). You should see "Broadcom STA Wireless Driver" as something that is not activated. Click it and click activate. It should download what you just removed and properly activate it.

This was a solution I came up with by altering this solution ([http://www.ubuntubuzz.com/2011/09/fixing-broadcom-43xx-wireless-card.html](http://www.ubuntubuzz.com/2011/09/fixing-broadcom-43xx-wireless-card.html))

I hope that helps!

---

### Post by cblah001 on 2011-10-14
BTW: I was also dealing with the issue where it would not activate initially so I think I had the same problem as you. I'm not trying to give you the same solution you already tried.

---

### Post by jarruda on 2011-10-14
I believe this driver needs to be reinstalled every time the kernel is upgraded.

If you do not have Synaptic installed (it is no longer installed by default as of 11.10), install that through the software center.

Then, open synaptic and search for "bcm".  You will see "bcmwl-kernel-source" in the list.  Mark this package for "Reinstallation" and apply.  Reboot.

With any luck it should now be working.  Good luck.

---

### Post by cblah001 on 2011-10-14
That's essentially what I am suggesting. They will probably still need to activate it. If it is not installed, it will install then activate automatically from the "additional drivers" menu. I didn't need to reboot but every system is a little different.

---

### Post by imnvs on 2011-10-14
cblah, you're a peach.  That worked.  Thanks a lot!  :)

---

### Post by joneberger on 2011-10-14
Thanks!  Worked for me.  What a ridiculous fix for a Linux OS.

---

### Post by novice_ubuntee on 2011-10-14
cblah001: thank you, thank you, thank you!! What a star!

---

### Post by cblah001 on 2011-10-14
Glad I could give back to the community.

---

### Post by nick3501 on 2011-10-15
BAM, this worked. Pin this, cblah saved the day

---

