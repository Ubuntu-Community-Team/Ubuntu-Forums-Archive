---
title: "Kensington Videocam not recognized?"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by Endolith on 2007-11-10
I have a Kensington Videocam from ages ago.  I should probably just buy a new webcam, but I wanted to see if there was an easy way to get this one working, too.

Long ago I followed the directions on [www.geocities.com/trypt0/videocamsupport.html](www.geocities.com/trypt0/videocamsupport.html) ([Wayback machine archived here]("http://web.archive.org/web/20050702015231/www.geocities.com/trypt0/videocamsupport.html")), and upgraded the firmware.  (I have copies of all those zip files, by the way.)

It still works under XP.

[This page]("http://members.chello.nl/~j.vreeken/se401/") says it should be handled by the se401 driver, which is built into the kernel?

How can I test if the camera is working?  It is not seen by Skype beta, and I used to be able to capture from it in The GIMP in Windows in Acquire TWAIN mode, but I can't figure out how to do that in the latest GIMP.  xsane and gtkam don't seem to see it.

What else should I try?

---

### Post by Endolith on 2007-11-10
Oh, I see.

"The bad news is that upgrading the firmware will make your camera inoperable to Linux and Windows 9x. It is possible to change the Linux drivers to make your camera work properly."

"I have contacted Jeroen Vreeken, the author of for se401 device driver for Linux, and he told me that the older bios is completely different from the newer bios consequently, the current driver will not work with the newest firmware. Futhermore, he told me that the driver for the se402 should hypothetically able to work for this camera. So if you want to use your camera for Linux for now, you will have to use the older 9x firmware that Kengsinton provided and hold off using the unoffical Windows 2000 firmware on Linux."

---

### Post by lucio39 on 2007-12-16
Right! I also have a Kensington webcam, model #67015; the hardware is a Dell Latitude 610 with Ubuntu 7.10.
I've downloaded the se401 driver, but ...

I am rather new to Linux so where do I go from here? How do I compile the source code? A step by step assistance would be highly appreciated.
Thanks.

---

