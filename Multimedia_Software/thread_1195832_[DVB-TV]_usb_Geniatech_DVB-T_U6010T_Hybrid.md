---
title: "[DVB-TV] usb Geniatech DVB-T U6010T Hybrid"
date: 2009-06-24
forum: Multimedia Software
---

### Post by gargoyle297 on 2009-06-24
Hi all,
I at least fired my windowsXP installation and now I play-work vith Ubuntu. I still have a problem to check-out: my usb tv card.
I got it working perfectly with TotalMedia software on XP and, actually, its vendor-name is "Empire usb 2.0 Pen dual TV".
When I tried to connect this usb card to Ubuntu it wasn't able to recognize it.
The command lsusb returned me:
"Bus 001 Device 005: ID 6000:eaec"
  and this signature do not match with the "Empire usb 2.0 Pen dual TV" signature.

I checked other forums and now I know that that numbers correspond to the  "usb Geniatech DVB-T U6010T Hybrid" numbers (I got a confirmation on the Geniatech site, it's a rebrand).

Can I get it work with Jackalope (9.0.4)? Do you know about workarounds? I took a look at "linuxtv.org" and the geniatech model I have is neither in the supported list nor in the not-supported list. In few words is never mentioned. I tried the standard tv4linux support but it doesn't work. Koffeine says 'no tv device'.

Any idea or suggestion?

Thanks a lot

Norberto

---

### Post by ddrichardson on 2009-06-24
Plug it and type```
dmesg
```In a terminal.

See if the system recognises it - normally it requires a firmware file.

---

### Post by gargoyle297 on 2009-06-25
Thanks for the answer,
this is the printout (condensed)

gargoyle@gargoyle-dell:~$ dmesg -c

gargoyle@gargoyle-dell:~$ lsusb
Bus 001 Device 010: ID 6000:eaec 
...
...
... 

gargoyle@gargoyle-dell:~$ dmesg
[10775.616178] usb 1-4: new high speed USB device using ehci_hcd and address 10
[10776.081374] usb 1-4: configuration #1 chosen from 1 choice

I supposed the need of a firmware file but... what is the correct one?

---

### Post by ddrichardson on 2009-06-25
Does google give any firmware links for this model?

---

### Post by gargoyle297 on 2009-06-26
these are the results:

[http://www.geniatech.com/pa/u6010t.htm](http://www.geniatech.com/pa/u6010t.htm)

[http://www.dtvforum.info/lofiversion/index.php/t58717.html](http://www.dtvforum.info/lofiversion/index.php/t58717.html)

none of them talking about firmware files or ubuntu compatibility.

I try to write to the geniatech's contact
I'll let you know

---

### Post by gargoyle297 on 2009-06-26
I've found, in the Geniatech site, the XP drivers for the usb stick.
I inspected the archive file and the driver's file name are all prefixed with 'U6000all'.

Maybe the driver could be useful for all the 6000 models... i don't know

Do you know something about ubuntu firmware files for other kind of Geniatech usb sticks?

Thanks

---

### Post by ddrichardson on 2009-06-26
Sorry no I don't, I have two USB sticks - one is Freecom and one is an Avermedia Chip.  Both are picked up by HAL but it requests a firemware, so I put the firmware in /lib/firmware.

---

### Post by gargoyle297 on 2009-07-01
I wrote the Geniatech support contact email address but ...
Who knows? 'spes ultima dea'.... (latin for "Hope is the last goddess")

Any suggestion?

---

### Post by Ron-In-Kerrville on 2009-07-07
Hi, I have the same problem.  It works fine in XP, but cannot get 6010 to be
seen in the USB slot.  I'll be checking this thread to see what answers you
get from Geniatech.  Thanks.

---

### Post by gargoyle297 on 2009-07-09
Sorry Ron,
it seems to be no reply from geniatech....

Why don't you try too?
It could be a chance...

---

