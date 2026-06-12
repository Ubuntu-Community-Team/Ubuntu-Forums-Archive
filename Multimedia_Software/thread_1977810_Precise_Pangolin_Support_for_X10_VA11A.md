---
title: "Precise Pangolin Support for X10 VA11A"
date: 2012-05-10
forum: Multimedia Software
---

### Post by gocoder on 2012-05-10
Hi, all. I'm running Xubuntu 12.04 Precise Pangolin on my home desktop PC.
My problem is that I have a X10 video capture USB device, VA11A, to capture video wirelessly. That device works OK using Hardy Heron on another PC. I want to update that OS to 12.04.
The video USB device says (to the kernel) that its ID is [0733:0430].  I've researched USB devices with that id and in the driver code, I've found two devices that have the same id: IntelPCCameraPro (spca505.c) and UsbGrabberPV321 (spca506.c).  The code is set up use the IntelPCCameraPro configuration but my X10 device, VA11A, is the UsbGrabber.  Code changes should be simple: comment out the ID line in spca505.c and uncomment it in spca506.c.
Is there an easy way to "make && make install" the respective .ko modules? Dependencies are preventing me from invoking make at the gspca level or above unless I go to the top source directory. Going to the top is too much as I get a make install error in another area.
I want to use LKMs so migration to the next OS version is easier.
Thanks in advance.

---

### Post by jervin2 on 2013-02-15
Did  you ever make any progress on this?

---

