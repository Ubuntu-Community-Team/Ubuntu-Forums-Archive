---
title: "USB memory stick mounting problem"
date: 2008-08-24
forum: Mandriva/Mageia
---

### Post by gnuvistawouldbecool on 2008-08-24
I'm using Mandriva 2008.1, and everytime I stick my memory stick in and try to open it, it says "permissions denied".  Nothing else, just that.  No problems in either XP or the most recent 8.10 alpha, or Puppy Linux.  It works fine if I insert it before booting the computer/OS but if I plug it in at any other time it gives the error every time.  Even with dolphin opened from CLI with superuser privileges it says it, so does anyone have any idea?

---

### Post by TeaAge on 2008-08-24
Hmm,

I think I had the same problem a time ago ... but I'm unsure how I solved it.
If you plug it it, a small USB Key Icon will apear in the controllbar. With a rightklick you can edit some preferences. Maybe you could find something settings there.
Or try to mount the stick per console and overright the permissions
```

chown -r user:groupe /mnt/yourUSB/

```

If this didn't help, you might ask someone else ... forum.mandriva.com

Regards,
TeaAge

---

### Post by AdamWill on 2008-08-24
Edit /etc/fstab and see if there's a line for the device. if there is, comment it out.

---

### Post by gnuvistawouldbecool on 2008-08-27
> **AdamWill said:**
> Edit /etc/fstab and see if there's a line for the device. if there is, comment it out.

Yep, that got it.  Interestingly I had noticed an error in verbose startup saying it failed to mount a drive, that must have been it.

Thanks.

---

### Post by AdamWill on 2008-08-27
If the drive is connected during boot it'll consider it to be a new permanent drive and try to add it to /etc/fstab . If possible it'd be good to disable this for USB stick-type drives but the problem is they're difficult to tell apart from, say, a new SATA hard disk (which obviously *should* be treated as a nwe permanent drive): they look very similar as far as the system is concerned. :\

---

### Post by lumos_aeternum on 2008-09-21
I don't know a ton about the interior of the Linux OS, but shouldn't there be a way to identify the difference between a SATA drive and one coming in through a USB or Firewire port?

---

