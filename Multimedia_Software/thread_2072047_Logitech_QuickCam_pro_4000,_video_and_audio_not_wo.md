---
title: "Logitech QuickCam pro 4000, video and audio not working together"
date: 2012-10-17
forum: Multimedia Software
---

### Post by NHerby on 2012-10-17
Hi,
2 weeks after my first steps in the linux word, I've managed to sort out most of my problems thanks mainly to this forum.
But I still have 2 problems I cannot fix by myself and here's one of them:
I have a webcam logitech quickcam pro 4000 that works fine under windows =D>. This webcam has a built in microphone that I need to use.
Taken separately, the microphone and the webcam works. I use the sound recorder to test the mic and cheese for the webcam.
lsusb gives that:
```
Bus 001 Device 004: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
```And a dmesg | tail after plugging the webcam gives this:
```
~$ dmesg | tail 
[   24.891013] eth0: no IPv6 routers present 
[  241.670564] Allocated vmalloc buffer of size 462848 at vaddr=ffffc9001666b000 
[  241.670648] Allocated vmalloc buffer of size 462848 at vaddr=ffffc9001674f000 
[  246.171332] vb2_vmalloc_put: Freeing vmalloc mem at vaddr=ffffc9001666b000 
[  246.171356] vb2_vmalloc_put: Freeing vmalloc mem at vaddr=ffffc9001674f000 
[  283.069958] usb 1-1.6: USB disconnect, device number 4 
[  285.310993] usb 1-1.6: new full-speed USB device number 6 using ehci_hcd 
[  285.498999] pwc: Logitech QuickCam 4000 Pro USB webcam detected. 
[  286.048195] pwc: Registered as video0. 
[  286.048252] input: PWC snapshot button as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/input/input14
```But I start having problems as soon as I try to use the mic and the webcam at the same time. In skype, when I start a video call, my buddies can hear me but the webcam sends a black image.
If I start an audio recording with the sound recorder and launch at the same time a gstreamer-properties:
```
~$ gstreamer-properties  
(gstreamer-properties:2650): Gtk-WARNING **: Unknown property: GtkDialog.has-separator  
(gstreamer-properties:2650): Gtk-WARNING **: Unknown property: GtkDialog.has-separator 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink' 
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink' 
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink' 
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink' 
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink' 
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc' 
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc' 
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc' 
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon' 
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc' 
libv4l2: error turning on stream: Aucun espace disponible sur le périphérique 
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(2230): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1: 
system error: Aucun espace disponible sur le périphérique]
```And after that, nothing works anymore ; no sound, no video. If I unplug and plug back the device and dmesg | tail:
```
~$ dmesg | tail 
[ 1676.915503]  [<ffffffff812d6e77>] ? apparmor_socket_sendmsg+0x17/0x20 
[ 1676.915509]  [<ffffffff8152a3c4>] do_sock_write.isra.10+0xd4/0xf0 
[ 1676.915512]  [<ffffffff8152a443>] sock_aio_write+0x63/0x90 
[ 1676.915517]  [<ffffffff8117780a>] do_sync_write+0xda/0x120 
[ 1676.915521]  [<ffffffff812d7e28>] ? apparmor_file_permission+0x18/0x20 
[ 1676.915526]  [<ffffffff8129d58c>] ? security_file_permission+0x2c/0xb0 
[ 1676.915530]  [<ffffffff81177db1>] ? rw_verify_area+0x61/0xf0 
[ 1676.915533]  [<ffffffff811781cd>] vfs_write+0x16d/0x180 
[ 1676.915536]  [<ffffffff8117843a>] sys_write+0x4a/0x90 
[ 1676.915541]  [<ffffffff81663442>] system_call_fastpath+0x16/0x1b

```
The only way to get things back is to reboot the computer.
While searching for a solution, I found 2 other threads about the exact same issue:
[http://forums.fedoraforum.org/showthread.php?t=275261](http://forums.fedoraforum.org/showthread.php?t=275261)
[http://ubuntuforums.org/showthread.php?t=1604372](http://ubuntuforums.org/showthread.php?t=1604372)
But none of them received any answers :-(
For now, I have to stay under windows just because of this problem :-x so you can imagine how much I will appreciate any help.
For info, I use the 12.04 LTS - 64bit and my mobo ids a brand new Gigabyte Z77X-D3H

---

