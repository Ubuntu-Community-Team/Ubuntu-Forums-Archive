---
title: "New plymouth updates, can no longer boot normally"
date: 2011-01-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-01-21
I just received five plymouth package updates. Now, attempting to boot normally just gives me a black screen with a flashing cursor. I attempted booting three times, all with the same result.

I can, however, do a recovery mode boot, select netroot, and start gdm. So, natty is not broken, just plymouth.

Tim

---

### Post by Harry33 on 2011-01-21
> **ratcheer said:**
> I just received five plymouth package updates. Now, attempting to boot normally just gives me a black screen with a flashing cursor. I attempted booting three times, all with the same result.
I can, however, do a recovery mode boot, select netroot, and start gdm. So, natty is not broken, just plymouth.
Tim

I have updated today plymouth to the most recent version (0.8.2-2ubuntu10), but I do not have any issues with it.
Booting fine and fast.
I have 64-bit architecture, nvidia-current and the default "gfxpayload=keep".

---

### Post by zika on 2011-01-21
> **ratcheer said:**
> I just received five plymouth package updates. Now, attempting to boot normally just gives me a black screen with a flashing cursor. I attempted booting three times, all with the same result.

I can, however, do a recovery mode boot, select netroot, and start gdm. So, natty is not broken, just plymouth.

Tim
For the time being, You could do the thing I'm doing all the time to prevent plymouth of starting, without uninstalling:

move```

plymouth.conf
plymouth-splash.conf
plymouth-log.conf
plymouth-stop.conf
```
from /etc/init to some safe place...

---

### Post by mc4man on 2011-01-21
> just gives me a black screen with a flashing cursor.
_Sometimes_, on a desktop, that is caused by a kernel panic (on laptops a panic is likely to also cause flashing lights.

If you have a desktop there are various ways as mentioned above that may give you a better boot w/ possibly full or partial text output.

Here for nvidia I remove vt.handoff=7 and the quiet, splash to get full start to finish text on boot.

---

### Post by ratcheer on 2011-01-21
Thanks, everyone.

Tim

---

### Post by lucazade on 2011-01-21
> **mc4man said:**
> _Sometimes_, on a desktop, that is caused by a kernel panic (on laptops a panic is likely to also cause flashing lights.

If you have a desktop there are various ways as mentioned above that may give you a better boot w/ possibly full or partial text output.

Here for nvidia I remove vt.handoff=7 and the quiet, splash to get full start to finish text on boot.

same issue here with Nvidia.
is there a bug report?

---

### Post by plun on 2011-01-21
> **zika said:**
> For the time being, You could do the thing I'm doing all the time to prevent plymouth of starting, without uninstalling:

move```

plymouth.conf
plymouth-splash.conf
plymouth-log.conf
plymouth-stop.conf
```
from /etc/init to some safe place...

Well.....  Plymouth works for the first time for me since months after following your advice  ...;)   (pure nVidia)

---

### Post by ratcheer on 2011-01-21
Well, another hour and 17 more updates, including grub2, and now my system boots normally, again. What a roller coaster!

Tim

---

### Post by ratcheer on 2011-01-21
And there was yet another update of several plymouth packages this afternoon, about four hours after the first set.

Tim

---

### Post by Harry33 on 2011-01-22
Right, the newest version is 0.8.2-2ubuntu12. 
See here:
[https://launchpad.net/ubuntu/natty/+source/plymouth/0.8.2-2ubuntu12](https://launchpad.net/ubuntu/natty/+source/plymouth/0.8.2-2ubuntu12)

---

### Post by kyleabaker on 2011-01-22
> **zika said:**
> For the time being, You could do the thing I'm doing all the time to prevent plymouth of starting, without uninstalling:

move```

plymouth.conf
plymouth-splash.conf
plymouth-log.conf
plymouth-stop.conf
```
from /etc/init to some safe place...

This got my default boot to go past a blank screen, but then I was prompted with a "your video drivers don't support 3D" message and told to change sessions. I clicked change sessions and it started both Unity and Gnome Panels both.

I've uninstalled the restricted nvidia drivers now and am working with the open source ones. Thanks for fixing my boot again though!

---

### Post by mc4man on 2011-01-22
As an aside to this - if on nvidia and not caring for the splash then the latest grub should provide a better text boot, it should now not be using the vt.handoff=7 if splash is disabled in boot line

---

