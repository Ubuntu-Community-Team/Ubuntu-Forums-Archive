---
title: "Can't Install: Now what?"
date: 2008-09-30
forum: Mythbuntu
---

### Post by dsbw on 2008-09-30
I'm trying to install Mythbuntu on [this motherboard]("http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=419").

The problem is I get dumped to initramfs. 

I got some good advice to boot from a USB flash drive, but believe it or now, that option's not available in the BIOS! Booting from USB CD-ROM is a BIOS option but doesn't seem to work. 

I'm not sure how to proceed. Install Windows and then install Mythbuntu over it? Alternate CD?

---

### Post by SiHa on 2008-10-01
I suspect it should boot from using USB CD-ROM. Have you checked the flashdrive is actually bootable? Have you got another PC you can put it in - you won't do any harm, all it will do is boot to the installer menu, at which time you can just shutdown.

---

### Post by dsbw on 2008-10-01
> **SiHa said:**
> I suspect it should boot from using USB CD-ROM. Have you checked the flashdrive is actually bootable? Have you got another PC you can put it in - you won't do any harm, all it will do is boot to the installer menu, at which time you can just shutdown.

I've tested out the flash drive and the USB CD-ROM on different machines, and both work. 

For whatever reason, this mofo mobo won't boot from any USB port. The ports do work, however, as I have plugged in a mouse to them.

---

### Post by SiHa on 2008-10-02
I've seen quite a few people report that the alternate CD works when the Live CD doesn't

Also, something I tried as a last resort when I couldn't boot from USB...

I used the **same** drive to burn the ISO on one machine, and install from on the other. This worked on the Live CD, where using different drives didn't, and I couldn't boot from USB. I would have mentioned this before, but forgot until now.

---

### Post by dsbw on 2008-10-03
OK, what I learned was that the board does boot from flash drives, but you have to: 

a) plug them in before powering on
b) Make sure it's the right brand (there's no list of what works, and I had a plain-jane Kingston 2GB that *didn't*
c) Go into the BIOS hard-drive priority setting in the BIOS, and give the drive top priority. 

Also, if anyone comes fishing, the standard video driver worked, but had a terrible case of the jaggies. The driver that EnvyNG installed worked fine, but I haven't run it through its paces yet. I haven't tried going to the latest NVidia driver, though.

---

