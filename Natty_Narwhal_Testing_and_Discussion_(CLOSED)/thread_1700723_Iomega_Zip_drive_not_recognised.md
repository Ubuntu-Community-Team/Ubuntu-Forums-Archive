---
title: "Iomega Zip drive not recognised"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2011-03-05
I'm trying to access some files on a zip disk but natty is ignoring the drive. It shows up via lsusb but that's all. Does anyone know why?

---

### Post by cariboo on 2011-03-11
I saw this when you posted it, but I just found my usb zip drive ( I have a parallel zip drive too), I just plugged it in, and it took a few seconds to recognize the disk. It wasn't auto mounted, but right-click on the icon and selecting open, opened the contents in nautilus.

---

### Post by macroshaft on 2011-03-11
> **cariboo907 said:**
> I saw this when you posted it, but I just found my usb zip drive ( I have a parallel zip drive too), I just plugged it in, and it took a few seconds to recognize the disk. It wasn't auto mounted, but right-click on the icon and selecting open, opened the contents in nautilus.

I have no icon to click on.

---

### Post by cariboo on 2011-03-11
What does dmesg look like after you plug the device in? 

I only tried the zip drive on my netbook, I'll try it on a couple of other systems running Natty tomorrow.

---

### Post by Starks on 2011-03-12
I'm surprised people still use zip drives.

---

### Post by cariboo on 2011-03-12
I keep mine around for the same reason I keep a 3½ and 5¼ floppy drives on the shelf, every once in a long while someone needs to get some data off of a zip or floppy disk.

---

### Post by macroshaft on 2011-03-12
> **Starks said:**
> I'm surprised people still use zip drives.

Some of us are poor enough that we have to take whatever we can get when backing up!

---

### Post by ranch hand on 2011-03-12
> **macroshaft said:**
> Some of us are poor enough that we have to take whatever we can get when backing up!
Yes to that brother.

---

### Post by r-senior on 2011-03-17
@macroshaft: I'd be very interested to see your syslog output when you plug the drive in and remove it. In particular whether it's the same problem as:

[http://ubuntuforums.org/showthread.php?t=1707388]("http://ubuntuforums.org/showthread.php?t=1707388")

This would manifest itself as failure to mount, not visible with 'lsusb' (in fact lsusb may hang while the device is connected) and messages like this in your syslog:

"... usb 2-3: device descriptor read/8, error -110"

If you do get the same errors, I'd also be interested to know if a 2.6.37 kernel fixes it.

---

### Post by macroshaft on 2011-03-17
> **r-senior said:**
> @macroshaft: I'd be very interested to see your syslog output when you plug the drive in and remove it. In particular whether it's the same problem as:

[http://ubuntuforums.org/showthread.php?t=1707388]("http://ubuntuforums.org/showthread.php?t=1707388")

This would manifest itself as failure to mount, not visible with 'lsusb' (in fact lsusb may hang while the device is connected) and messages like this in your syslog:

"... usb 2-3: device descriptor read/8, error -110"

If you do get the same errors, I'd also be interested to know if a 2.6.37 kernel fixes it.

This turned out to be a faulty drive, I can write to disks in windows but they show up as unformatted afterwards in Maverick. Using a different drive I was able to read from the discs in both Maverick and Natty.

---

