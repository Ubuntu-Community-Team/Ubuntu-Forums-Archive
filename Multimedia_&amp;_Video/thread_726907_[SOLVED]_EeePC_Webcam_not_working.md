---
title: "[SOLVED] EeePC Webcam not working"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by bandit36 on 2008-03-17
The webcam on my EeePC worked fine until I tried to install a video grabber.  I followed the instructions on ([http://ubuntuforums.org/showthread.php?t=369881](http://ubuntuforums.org/showthread.php?t=369881)) and I ended up losing my integrated webcam.  It still shows up in lsusb but isnt mounted(?) as /dev/video0

The lsusb command gives:
> 
Bus 005 Device 003: ID eb1a:2761 eMPIA Technology, Inc. #<- webcam
Bus 005 Device 002: ID 0951:1606 Kingston Technology 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000


when I try a modprobe em28xx I get dumped back at the prompt with no warnings (success I guess), but when I try 'sudo modprobe uvcvideo' I get the following:
> 
FATAL: Error inserting uvcvideo (/lib/modules/2.6.22-14-generic/uvcvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)


When I open dmesg I get this:
> 
...
[  715.616000] uvcvideo: disagrees about version of symbol video_devdata
[  715.616000] uvcvideo: Unknown symbol video_devdata
[  715.616000] uvcvideo: disagrees about version of symbol video_unregister_device
[  715.616000] uvcvideo: Unknown symbol video_unregister_device
[  715.616000] uvcvideo: disagrees about version of symbol video_device_alloc
[  715.616000] uvcvideo: Unknown symbol video_device_alloc
[  715.616000] uvcvideo: disagrees about version of symbol video_register_device
[  715.616000] uvcvideo: Unknown symbol video_register_device
[  715.620000] uvcvideo: disagrees about version of symbol video_device_release
[  715.620000] uvcvideo: Unknown symbol video_device_release


can anyone help me revive the webcam?

---

### Post by bandit36 on 2008-03-20
I just tried "sudo modprobe uvcvideo" on a whim and go t the following:
> WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/v4l2-common.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/v4l1-compat.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/videodev.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/compat_ioctl32.ko': No such file or directory
FATAL: Error inserting uvcvideo (/lib/modules/2.6.22-14-generic/uvcvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)
I did a "locate v4l2-common.ko" and got no results so my thought is to find and replace these files.  Can anyone point me in the right direction?

---

### Post by bandit36 on 2008-03-20
Think I might have found a solution, but will have to wait til morning.

1 - booting EeePC w/ usb stick I used to install Ubuntu
2 - copying /lin/modules/2*/kernel/drivers/video to external HD
3 - booting back into Ubuntu on my EeePC and copy/pasting from external HD to SSD

I'm sure there's a high-speed method that doesn't require all this booting, but it's currently beyond my ability and I know how to do this.  Will post results in the AM.

---

### Post by bandit36 on 2008-03-21
SUCCESS!!!  It wasn't as 1, 2, 3 as I had hoped, but it worked.

After copying the /video directory from the usb stick to my hard drive I noticed that the .ko files icons had a little x on them and I still got the same errors when I tried "modprobe uvcvideo".  I figured it had something to do with the .ko files so I did some research on them and found the "depmod" command.

Step 1 - Copy original .ko files to hard drive from USB stick
Step 2 - sudo depmod
Step 3 - modprobe uvcvideo
Step 4 - Yay! I solved my own problem!

---

### Post by ggravier on 2008-06-14
Bandit,

Any chance you could make the files you copied available somewhere? I wiped my Xandros installation to put Ubuntu instead... BEFORE copying the whole contents... and I don't feel like going all over the same process again. :)

Gilles.

---

