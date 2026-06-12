---
title: "Microsoft LifeCam VX-6000 Help revisited"
date: 2009-12-28
forum: Multimedia Software
---

### Post by WildeBeest on 2009-12-28
I'm having a problem getting my VX-6000 to work.
I've followed **all** the threads that I have been able to find.

Following the instruction of compiling the Microdia drivers, sudo insmod ./sn9c20x.ko outputs the following message:
```

insmod: error inserting './sn9c20x.ko': -1 Cannot allocate memory

```

When I insert the web cam, dmesg gives me the following:
```

[261692.936040] usb 1-2: new high speed USB device using ehci_hcd and address 7
[261693.071970] usb 1-2: configuration #1 chosen from 1 choice
[261693.072586] gspca: probing 045e:00f4
[261693.137051] sn9c20x: OV9650 sensor detected
[261693.137704] gspca: /dev/video0 created
[261693.138058] gspca: probing 045e:00f4
[261693.138064] gspca: intf != 0
[261693.256359] 7:2:1: cannot get freq at ep 0x84
[261694.584528] 7:2:1: cannot get freq at ep 0x84

```

Anyone have any ideas what else I could try?

---

### Post by WildeBeest on 2010-02-02
Bring back up.
 
Still have the same problem.

---

### Post by WildeBeest on 2010-02-02
Cheese gives me the following:
```
libv4l2: error reading: Invalid argument

```

gstreamer-properties:
```
Video for Linux 2 (v4l2): Could not get buffers from device '/dev/video0'.

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not get buffers from device '/dev/video0'. [v4l2src_calls.c(1404): gst_v4l2src_capture_init (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src3:
error requesting 2 buffers: Cannot allocate memory]

```

Skype:
```
libv4l2: error reading: Invalid argument
```

Someone must be able to help me.

---

### Post by WildeBeest on 2010-02-03
why can't I ever get any help on these forums?

---

### Post by qwelm on 2010-03-09
I'm in the same boat as you.  Did you ever find a solution?

---

### Post by beyercj on 2010-04-21
Try my post on this thread [http://ubuntuforums.org/showthread.php?t=921153&highlight=LifeCam+VX+6000&page=3](http://ubuntuforums.org/showthread.php?t=921153&highlight=LifeCam+VX+6000&page=3)

---

