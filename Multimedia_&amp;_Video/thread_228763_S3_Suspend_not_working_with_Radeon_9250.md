---
title: "S3 Suspend not working with Radeon 9250"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by Dimitry Fayerman on 2006-08-03
I can not get S3 suspend working.
My system is AMD 64 Athlon and Radeon 9250.
in Ubuntu 6.06 i386.

It goes to S3 suspend mode fine but can not come back.

Initially after S3 restore the computer would freeze, screen would show different color patterns.

After playing with acpi-support the computer now reboots on S3 resume.

I was trying to execute vbestate save as described here:
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/11919]("https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/11919")
but getting the following error:

Get video state buffer size failed
Allocated buffer at 0x11010 (base is 0x0)
ES: 0x1101 EBX: 0x0000
Save video state failed

I have ati driver in xorg.conf.

Any help is greatly appreciated.

---

