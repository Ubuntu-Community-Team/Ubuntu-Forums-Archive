---
title: "Nvidia GTX760M"
date: 2013-11-30
forum: Multimedia Software
---

### Post by anbuck on 2013-11-30
I have an MSI GE40 latop with an Nvidia GeForce GTX760M.  When running the nouveau drivers, Ubuntu doesn't recognize external monitors regardless of whether they are attached to the SVGA port or the HDMI port.  When I install the proprietary Nvidia drivers (have tried various versions including 319 or 319-updates), I only see my mouse cursor on black screen after I login.  All I want to be able to do is use external monitors.  How can I accomplish this?

Thanks!

---

### Post by Bucky Ball on 2013-12-07
*Thread moved to** Multimedia & Graphics**.*

Try installing arandr and see what that picks up.

---

### Post by Yellow Pasque on 2013-12-08
If it's an Optimus setup (it probably is), you can't just install the nvidia driver or you will bork the intel driver. You need to install Bumblebee and then you may be able to use HDMI:
[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html)

---

### Post by anbuck on 2013-12-12
Thanks for the help guys.  I tried randr and bumblebee and neither helped my external monitor issue, however after the installing the latest set of system package updates, I can now use external monitors with the regular nouveau driver.  I may not be utilizing the nvidia GPU, but at least I've got external monitors, which is really what I needed.

---

### Post by Bucky Ball on 2013-12-12
If you consider the thread solved, please mark it that way to help others by following the link in my signature. Thanks. ;)

---

