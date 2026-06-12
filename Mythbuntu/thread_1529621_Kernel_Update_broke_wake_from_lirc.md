---
title: "Kernel Update broke wake from lirc"
date: 2010-07-12
forum: Mythbuntu
---

### Post by psiegel on 2010-07-12
I have a mediacenter usb remote (mceusb) that I use to operate my mythbuntu box.  I set it up to suspend to ram via the power button using the instructions here:

[http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM](http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM)

Basically it involves enabling wake from USB in /proc/acpi/wakeup, running irexec, and configuring lirc to call irexec with the hibernate command.  It works great.  Or it did work, until I applied the recent update to kernel version 2.6.32-23.  Then it stopped waking up.  It would still hibernate just fine when running, but I could only wake it up by pressing the power button.  When in hibernate mode, the IR receiver just appears to be dead, its light doesn't even blink when I press buttons on the remote, like it's not even getting any power.

I rebooted into the older kernel (2.6.32-22), and lo and behold it worked great again.  I've since uninstalled the updated kernel and this is a fine work-around for me.  I have no reason to really need the updated kernel.  However, I wanted to report this to whoever the right person or group might be.  I wasn't sure who that was though, so I started here.  If this is not the right place to report the issue, can someone redirect me?  Thanks.

Paul

---

### Post by superm1 on 2010-07-12
> **psiegel said:**
> I have a mediacenter usb remote (mceusb) that I use to operate my mythbuntu box.  I set it up to suspend to ram via the power button using the instructions here:

[http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM](http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM)

Basically it involves enabling wake from USB in /proc/acpi/wakeup, running irexec, and configuring lirc to call irexec with the hibernate command.  It works great.  Or it did work, until I applied the recent update to kernel version 2.6.32-23.  Then it stopped waking up.  It would still hibernate just fine when running, but I could only wake it up by pressing the power button.  When in hibernate mode, the IR receiver just appears to be dead, its light doesn't even blink when I press buttons on the remote, like it's not even getting any power.

I rebooted into the older kernel (2.6.32-22), and lo and behold it worked great again.  I've since uninstalled the updated kernel and this is a fine work-around for me.  I have no reason to really need the updated kernel.  However, I wanted to report this to whoever the right person or group might be.  I wasn't sure who that was though, so I started here.  If this is not the right place to report the issue, can someone redirect me?  Thanks.

Paul

Paul:

File a bug using this command:

```
ubuntu-bug linux
```

Make sure you indicate it's a regression.

---

### Post by nonoitall on 2010-07-27
Just thought I'd pipe in and let you know you're not the only one affected by this issue. :smile:

---

