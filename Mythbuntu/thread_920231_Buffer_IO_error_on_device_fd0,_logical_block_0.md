---
title: "Buffer I/O error on device fd0, logical block 0"
date: 2008-09-15
forum: Mythbuntu
---

### Post by dsbw on 2008-09-15
So I've got [this ]("http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=419")fancy new mobo (to replace my ATI one which wasn't working).

And I can boot my machine but I thought it would make more sense to do a clean install.

Unfortuntely, I get this error:

Buffer I/O error on device fd0, logical block 0

After about 30 of those, I drop to initramfs.

If I suppress the FDD in the BIOS then I don't get the error messages, I just drop directly to initramfs.

How farked am I?

---

### Post by SniperKIng on 2008-09-15
Hey dude i too had this error along with many others about a month ago like you said removing floppy in BIOS fixes it.

Have you tried turning acpi off? this fixed all the errors with my board

---

### Post by dsbw on 2008-09-15
> **SniperKIng said:**
> Hey dude i too had this error along with many others about a month ago like you said removing floppy in BIOS fixes it.

Have you tried turning acpi off? this fixed all the errors with my board

I haven't. I'll try that now.

---

### Post by dsbw on 2008-09-16
OK, I don't have a "turn off ACPI" option. I tried a few things and still get initramfs.

There's an ACPI suspend type, turned that from S3 to S1, disabled all the Wake Ups, Power on by KB/MS--left HPET enabled...disabling now...no change....]

(*,) [expletive deleted]

---

### Post by SniperKIng on 2008-09-16
Ok ill guide you through it mate.

Switch on your pc and wait for the grub menu to load with the list of operating systems.(You may have to press escape a couple of seconds after switching on,it should say at the bottom to press esc.)

The find mythbuntu (likely the top option) and press E then you need to press E again on one of the options its the line with (Quiet Splash) at the end i think its the middle option.

Next at the end of the ling next to quiet splash add acpi=off then press enter and then the B key.

See if the works.Let me know how it goes mate

---

### Post by dsbw on 2008-09-17
Oh! You mean turn ACPI off on the install?

OK, thanks, let me try that now.

---

### Post by dsbw on 2008-09-20
> **SniperKIng said:**
> Ok ill guide you through it mate.

Switch on your pc and wait for the grub menu to load with the list of operating systems.(You may have to press escape a couple of seconds after switching on,it should say at the bottom to press esc.)

The find mythbuntu (likely the top option) and press E then you need to press E again on one of the options its the line with (Quiet Splash) at the end i think its the middle option.

Next at the end of the ling next to quiet splash add acpi=off then press enter and then the B key.

See if the works.Let me know how it goes mate

I'm installing from scratch, here. "acpi=off" doesn't seem to have any effect from the install command line.

---

### Post by dsbw on 2008-09-22
All right, so is there a chance that I can get mythbuntu installed if I use an alternate CD or something? Or should I return this mobo?

Anyone?

---

### Post by SiHa on 2008-09-22
I had similar problems, whereby I just couldn't get an install to complete from CD.

I got around it by installing from a flashdrive, using this guide[COLOR="Blue"]: [InstallationUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick#head-a45f469b0b7ec2750cdedce449b76003c391416d")[/COLOR]

...and taking the manual approach. In the long run, I found this the best option for any install - using USB2.0 the whole install only takes about 5 mins - much, much faster than from CD!

Now there is the LiveUSB creator, so it might be even simpler.

---

### Post by dsbw on 2008-09-28
I don't freakin' believe this, but this BRAND NEW motherboard won't freakin' boot from a flash drive. WTF?

I got: floppy, HD, CDROM, ZIP100, USB-FDD <--floppy disk drive, USB-ZIP, USB-CDROM, Legacy Lan--and my personal favorite: LS120.

But, no, no freakin' USB drive.

Now WTF am I supposed to do?

---

