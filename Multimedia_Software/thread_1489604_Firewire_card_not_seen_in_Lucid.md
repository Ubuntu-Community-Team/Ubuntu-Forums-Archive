---
title: "Firewire card not seen in Lucid"
date: 2010-05-21
forum: Multimedia Software
---

### Post by skrap on 2010-05-21
I am having trouble setting Lucid up to capture video via my firewire card. Running 64 bit on desktop with 2g ram 


dmesg | grep -e firewire -e 1394
[    2.233016] ohci1394 0000:01:06.3: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    2.233023] ohci1394 0000:01:06.3: setting latency timer to 64
[    2.292047] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fdffe000-fdffe7ff]  Max Packet=[65536]  IR/IT contexts=[4/8]
[    2.300078] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    3.630134] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0000850000d50c25]
[    3.630204] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[001106005350d195]
[   17.031354] ieee1394: raw1394: /dev/raw1394 device initialized

Device is initialized and hot plugged but not recognized.  Im sure I'm missing something simple but just can' see it .  Any help would be appreciated.

---

### Post by brucewagner on 2010-05-21
I think I have this same problem.  ( Though I am using Lucid 32-bit version. )

---

### Post by gandaran on 2010-05-21
maybe you need to install some firewire software, type firewire in synaptic package manager search box. 
try installing dv4l or other video4linux software.

---

### Post by skrap on 2010-05-21
Gandaran

I have jackd installed and all other recommended software from synaptic. Still no camera when hot plugged.

---

### Post by skrap on 2010-05-23
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

I have checked all procedures stated in the link above also.  

# When a Firewire camcorder or camera is plugged in and powered up, the resulting hotplug event must be seen by the kernel and the device be identified as supported, and
# the software must be running with the appropriate privileges to be granted the necessary device permissions.

It seems my problem is in the fact that when I hotplug my camera it is not seen by the kernel.  Don't know where to look to troubleshoot.  My setup worked in 9.10

---

### Post by dino99 on 2010-05-23
looking around: [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/548513](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/548513)

[http://packages.ubuntu.com/fr/lucid/dvgrab](http://packages.ubuntu.com/fr/lucid/dvgrab)

---

### Post by brucewagner on 2010-05-23
Actually, I have since discovered that Kino CAN see the video coming in from the camcorder via firewire...   

However, it cannot seem to capture it.

I think the problem must be with Kino.  Perhaps Kino is designed to only capture video that is "played back" on the camera... and not video that is streaming in live (video that has not been recorded by the camera, but is coming in live).

---

### Post by skrap on 2010-05-24
Still no love.  It almost seems like a mount problem.  Please help.

---

### Post by blur xc on 2010-05-24
> **skrap said:**
> Still no love.  It almost seems like a mount problem.  Please help.

I have no idea, but I'm just throwing this out there because I need to do this every time I connect my camcorder up to the computer to import video, and I just found it on some Google search I was doing-

After they camcorder is plugged in and turned on, I have to "sudo chmod 777 /dev/raw1394" before I can do anything else wit it.

FWIW, mines a cheap sony mini-dv standard def. handicam.

Good luck.

BM

---

### Post by skrap on 2010-05-24
Im using a Canon Elura 80 Nothing special.  I did get the capture to work by entering dvgrab in terminal.  I still wonder if there is a GUI that would pop up when the camera is plugged in via firewire.
Not necessary now that I have figured out how to make it work.  But it would be nice. Especially for newbies.

---

