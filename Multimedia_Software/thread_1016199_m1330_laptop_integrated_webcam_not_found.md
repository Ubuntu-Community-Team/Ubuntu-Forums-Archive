---
title: "m1330 laptop integrated webcam not found"
date: 2008-12-19
forum: Multimedia Software
---

### Post by kaushd on 2008-12-19
hi all,

my laptop (dell m1330) integrated webcam was working fine a couple of days ago on hardy. However I fired up skype today & there is no video device detected. I get the same result with cheese & ekiga.

Ive tried searching online but cant find any troubleshooting guides. I've installed easycam, but it also cant find any video devices.

i'm still a beginner, so don't know what outputs to provide. i'm thinking this could be a hardware problem. any ideas?

kay@laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

TIA

-EDIT- I've just booted from my Hardy CD into an Ubuntu live session, and still get the same result. I'm now totally out of ideas and thinking this is a problem with broken hardware. Can anyone provide any useful suggestions or help isolate the fault?

---

### Post by greenpeace on 2009-05-09
I'm having the same problem with my m1330... I've just upgraded to ubuntu 9.04 and the webcam no longer works with any application.

/dev/video0 doesn't exist.

the little blue light by the camera no longer flashes when I boot up.

the webcam worked fine with Skype, Cheese and Camerama... but no joy now.

lsusb gives:
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I think the top one is the webcam, but not sure.

can anyone give me any pointers on this?

---

### Post by greenpeace on 2009-05-12
...it's "magically" started working again in Cheese and Skype... which is great.  

Nothing with Camorama, still says "could not connect to video device (/dev/video0).  Please check connection"

but, I don't use Camorama anyway, so happy happy happy.

---

### Post by broken tibula on 2010-06-13
I'm having this problem, and it hasn't magically fixed itself for me yet...  Any suggestions?

---

