---
title: "Installed new ATI driver - screwed system. How can I get old one back?"
date: 2009-02-10
forum: Multimedia Software
---

### Post by Shakedown on 2009-02-10
So, I installed the new ATI proprietary driver and now my graphics card ain't working (err, the screen is weird looking).  Luckily I can SSH in from my laptop and remove the ATI driver, which allows me to boot into low-graphics mode.  So how can I get my old driver back?  I don't think the problem is an xorg.conf file problem, since I've swapped several in and out and that doesn't work (and it doesn't look like it would be an xorg.conf problem anyways).

Can I go through Syanaptic/APT and get another driver that will work, or will those just give me the newest one, which is what I have?  Although, I did get the driver from the ATI site rather than through repositories...

Thanks for the help!

---

### Post by redroad55 on 2009-02-10
What happens if log in another account? post back

---

### Post by xeddog on 2009-02-10
If you downloaded the ATI driver from their website, go to /usr/share/ati and look for a file like "fglrx-unintstall.sh".  If it is there:

sudo sh ./fglrx-uninstall.sh

That should remove the proprietary driver.

xeddog

---

### Post by Shakedown on 2009-02-10
> **xeddog said:**
> If you downloaded the ATI driver from their website, go to /usr/share/ati and look for a file like "fglrx-unintstall.sh".  If it is there:

sudo sh ./fglrx-uninstall.sh

That should remove the proprietary driver.

xeddog

Yes, I've uninstalled the driver this way, but now I don't have any driver.

---

### Post by Shakedown on 2009-02-10
So I've installed the previous release of the ATI driver, version 8.54.3 (the newest is 9.1) - don't know if that's what I had originally.  It seems I've made some progress - my dual monitors are working and I'm not in low-graphics mode, and the AMD CCC recognizes the driver and works properly.

But, clearly everything is not working - dragging windows causes the windows to just skip around, and when I run "fglrxinfo" I get this:

"X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  160 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10"

I'll Google this error, but any further advice?

Thanks.

---

