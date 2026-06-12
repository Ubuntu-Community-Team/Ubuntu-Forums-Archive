---
title: "Help with mounting network USB drive"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by SketchyClown on 2009-02-16
Hello,

I have searched the forums and have not found the answer I'm looking for yet.

I have a generic external USB 3.5" hard drive, formatted NTFS, that auto mounts just fine as "New Volume" when connected directly to my laptop and allows read/write access to all folders.

I recently bought a Belkin  F5D8235-4 N+ wireless router. This router has a USB port on the rear for connecting a single USB drive or up to 4 USB drives with the use of a USB hub. Drives need NTFS/FAT, which mine is.

From the manual:

"Alternatively, you do not need to install the Storage Manager in order to
access your storage device. Open a file explorer window and type in the
address field:
\\192.168.2.1\DeviceName
where “DeviceName” is the name that was assigned to the storage
device."

So, that sounds simple enough to me. 

In Nautilus -> Network I see Windows Network -> Belkin but then I get an error "Unable to mount location - failed to retrieve share list from server".

If I do as the manual says and type in "\\192.168.2.1\New Volume" I get the error that "Nautilus cannot handle this type of locations".

Hopefully I have described things clear enough for one of you guru's to tell me what a n00b I am and what I am doing wrong.

---

### Post by SketchyClown on 2009-02-17
Bump

---

### Post by SketchyClown on 2009-02-18
Anyone?

---

### Post by SketchyClown on 2009-02-19
Problem solved! I guess I should read the quote from the manual a little closer. When they say "DeviceName" and not "Device Name" that should have been my first clue that having "New Volume" as two words rather than a single would not work right.

Reformatted and renamed the drive to a single name, and voila! Instantly accessible.

---

### Post by grappler on 2009-07-05
Hi SketchyClown

I am very impressed by your piece of detective work. I have one of these Belkin routers with a USB hub for a hard drive and a fat32 formatted hard drive connected. I've renamed the hard drive to a single word as you suggest, How were you then able to connect under linux to the hard drive?

---

