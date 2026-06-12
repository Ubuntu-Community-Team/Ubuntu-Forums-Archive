---
title: "Ubuntu 12.04+ PB TE11HC LCD dimming doesn't work."
date: 2013-02-19
forum: Mobile Technology Discussions (CLOSED)
---

### Post by dzincha on 2013-02-19
Hi.
Just installed 3d laptop with ubuntu 12.04. 1st was without problem. 2nd has problem with wifi. 3rd had problems with wifi and still has problem with dimming. On display it shows brightness bar, but don't change intensity of backlight. 
Here is the output from terminal:

ance@ance-EasyNote-TE11HC:~$ ls /sys/class/backlight
acpi_video0 intel_backlight
ance@ance-EasyNote-TE11HC:~$ lsmod | grep video
uvcvideo 67203 0 
videodev 86588 1 uvcvideo
video 19068 1 i915
ance@ance-EasyNote-TE11HC:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic-pae root=UUID=7339d58a-236e-49d4-8b88-bc73d443ab8b ro quiet splash vt.handoff=7


Also tried to change grub. Didn't helped.

---

### Post by dzincha on 2013-02-19
> **dzincha said:**
> Hi.
Just installed 3d laptop with ubuntu 12.04. 1st was without problem. 2nd has problem with wifi. 3rd had problems with wifi and still has problem with dimming. On display it shows brightness bar, but don't change intensity of backlight. 
Here is the output from terminal:

ance@ance-EasyNote-TE11HC:~$ ls /sys/class/backlight
acpi_video0 intel_backlight
ance@ance-EasyNote-TE11HC:~$ lsmod | grep video
uvcvideo 67203 0 
videodev 86588 1 uvcvideo
video 19068 1 i915
ance@ance-EasyNote-TE11HC:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic-pae root=UUID=7339d58a-236e-49d4-8b88-bc73d443ab8b ro quiet splash vt.handoff=7


Also tried to change grub. Didn't helped.
Just got update from update manager- restart - ok.
During the day there were no any updates available.

---

