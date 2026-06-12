---
title: "Logitech Quickcam Problems"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by Ph0B1uS on 2007-09-12
I have a Logitech quickcam express that's giving me a lot of grief.

Everything works until I try and aquire images from the camera, my kernel oopses then and it affects usb_core too.
At first I thought this was a problem with the qc-usb so I tried downloading the latest version of the source from sourceforge (dated 2006 but still) and compile.
The problems did however persist so I'm pretty much betting it's a bug in the nForce4 usb handeling that's responsible for this.

I've had this problem with every kernel I've tried but the cam works like a charm in windows which pretty much rules hardware issues out.

Note that I cannot plug any more usb devices in than those I had before the oops, well I can but it won't do me any good as they're not recognized nor are the fact that somethings even in the port.

Has anyone else experienced anything like this?
Are there people out there that has conquered this problem?




This is what syslog says when the problem occurs:

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: Oops: 0000 [#1]

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: SMP 

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: CPU:    0

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: EIP is at usb_kill_urb+0x25/0xca [usbcore]

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: eax: 000001d0   ebx: d49b6dc0   ecx: 385f7065   edx: eeb81a68

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: esi: d3b1038c   edi: dcef3260   ebp: d401a21c   esp: ec1e5f60

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: ds: 007b   es: 007b   ss: 0068

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: Process wish (pid: 4494, ti=ec1e4000 task=f4141550 task.ti=ec1e4000)

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: Stack: f8860655 f0e6e288 eeb81a68 d3b10000 d3b1038c 00000001 dcef3260 f8e7cc76 

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel:        d3b10000 d46cfa80 f8e7da36 00000008 c015ae41 dfa610c0 d46cfa80 dff72a80 

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel:        00000000 ec1e4000 c01589aa 00000008 0a3c74f0 b69fa064 c0102c11 00000008 

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: Call Trace:

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: Code: ff ff 89 d8 5b c3 57 53 89 c3 83 ec 14 85 c0 0f 84 b2 00 00 00 8b 40 20 85 c0 0f 84 a7 00 00 00 8b 40 30 85 c0 0f 84 9c 00 00 00 <83> 78 24 00 0f 84 92 00 00 00 8d 43 04 e8 56 22 a2 c7 b0 01 fe 

Message from syslogd@hostname at Tue Sep 11 17:11:43 2007 ...
hostname kernel: EIP: [pg0+944587207/1070019584] usb_kill_urb+0x25/0xca [usbcore] SS:ESP 0068:ec1e5f60

---

### Post by w4ett on 2007-09-13
The Quickcam Express is supported out of the box in Feisty 7.04....especially by use of Camorama....I've used it with AMSN too. Others have had quite good experiences with this cam too.  See:

[http://ubuntuforums.org/showthread.php?t=501478](http://ubuntuforums.org/showthread.php?t=501478)

Quite possibly you should install a generic kernel and test it against the basic O/S without any modifications.

Just a thought.

---

### Post by Ph0B1uS on 2007-09-14
> **w4ett said:**
> The Quickcam Express is supported out of the box in Feisty 7.04....especially by use of Camorama....I've used it with AMSN too. Others have had quite good experiences with this cam too.  See:

[http://ubuntuforums.org/showthread.php?t=501478](http://ubuntuforums.org/showthread.php?t=501478)

Quite possibly you should install a generic kernel and test it against the basic O/S without any modifications.

Just a thought.

I'm running the latest debian kernel because ubuntus kernels doesn't work with my NIC (3c905).

There is a module included out of the box but camorama and aMSN gives me above described oopses so I'm betting chipset bug.

---

