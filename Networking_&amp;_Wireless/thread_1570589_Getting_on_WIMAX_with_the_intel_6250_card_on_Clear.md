---
title: "Getting on WIMAX with the intel 6250 card on Clear/Sprint"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by version7x on 2010-09-08
Good morning all!

I've recently picked up a netbook with the intel 6250 wireless chip in it. [ From what I've read]("http://ubuntuforums.org/showthread.php?p=9705976"), I should be able to get it up and running on WiMax, but I can't quite seem to get the job done.

[Here's the link to the official instructions]("http://www.linuxwimax.org/Download?action=AttachFile&do=get&target=wimax-announcement-v1.5-2.txt"), but they're for fedora.

Does anyone have any feedback on getting this to work?  Wifi works great, but I bought the thing for WIMAX!

Thanks in advance!

M

---

### Post by version7x on 2010-09-26
Ok,  I've made a bit of progress here....

I've upgraded to Ubuntu 10.10.  The nice thing about this is that now I believe the firmware/microcode is included by default in the new kernel.

I've now got wmx0 showing up in my ifconfig info:

```
 ifconfig wmx0
wmx0      Link encap:Ethernet  HWaddr 00:1d:e1:31:b7:c3  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

dmesg looks to approve:
```
[   12.205582] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.205756] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.205803] iwlagn 0000:07:00.0: setting latency timer to 64
[   12.206552] iwlagn 0000:07:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84

```

So that leads me to believe that I only need to compile the user space tools to proceed.  I've compiled all of the tools according to the instructions on linuxwimax.org.  The compiles seem to be completing without issue.  However, when executing the wimaxd daemon, I see the following in syslog...
```
Sep 26 19:58:24 net-book wimaxd[1660]: Initializing...
Sep 26 19:58:24 net-book wimaxd[1660]: Waiting for driver...
Sep 26 19:58:26 net-book wimaxd[1660]: Driver is up - 
Sep 26 19:58:26 ]net-book wimaxd[1660]: wimaxd event: driver up
Sep 26 19:58:27 net-book wimaxd[1660]: wimaxd event: Device-Scape library failed to be loaded
Sep 26 19:58:27 net-book wimaxd[1660]: Configuration error - 
Sep 26 19:58:27 net-book wimaxd[1660]: wimaxd event: AppSrv is exiting
Sep 26 19:58:27 net-book wimaxd[1660]: AppSrv exiting...
Sep 26 19:58:27 net-book wimaxd[1660]: Closing...

```

I've googled all over for someone working on this.  I've tried to see if there was a binary package in the works or a more detailed set of instructions that might show me what i'm missing.  I found a site in russian that seemed to indicate that the kernel/modules were good - and I was just lacking the userspace tools as  i had supposed, but thats about it.

Does anyone have any information at all on getting an intel 6250 wimax card up and running?

---

### Post by quantumtom on 2010-12-15
I'm in basically the same boat. But, I can connect to the old EV-DO (3G) network. I can't seem to get the WiMax (4G) network to show up, though, even when I can see it on Windoze from the same physical geographic location.

---

