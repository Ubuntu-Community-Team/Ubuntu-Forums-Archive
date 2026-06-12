---
title: "VGA connector broken, how do I activate video card"
date: 2010-05-30
forum: Multimedia Software
---

### Post by B4r on 2010-05-30
Hi,

I'm running Ubuntu 10.04 on a PC with a NVIDIA video card. T

The monitor was connected to the PC via the onboard VGA port which is now broken. I tried connecting the monitor to the video card but nothing is happening. I assume since I was using the onboard video card the NVIDIA video card is not active.

Is there a way to activate the nvidia video card now that the regular vga connector is broken? 

Thanks,
Ben

---

### Post by BoneKracker on 2010-05-30
Did you reboot after connecting to the PCI video adapter?

---

### Post by B4r on 2010-05-30
Yes I did, still nothing showing.

---

### Post by BoneKracker on 2010-05-30
Hmmm... I don't really know then.  I can tell you the stabs in the dark that I personally would make.

I think the first thing I'd try would be to go into the BIOS setup and disable the onboard video.  Unfortunately, you can't do that with no monitor. :(

Next, I'd check the pins on the video cable, to make sure none of them are bent or broken as a result of whatever broke the connector.

If the cable is suspect, I'd try a different display.

If that wasn't it, I suppose I'd try removing and pulling out and putting back the PCI video adapter (or AGP or whatever it is), to make sure it's properly seated (since it wasn't in use before).

If I had sshd running, I might try to ssh in and see if the PCI video card is being recognized by the system (using lspci, lshw, and browsing around in /sys).

If the card's not even being recognized, I'd probably stick it in another computer to verify that it works.

If it doesn't work in another machine, then I'd try another card in the broken machine.

If it does work in another machine, then I might try the desperate move of resetting the BIOS to see if it would pick it up (in case it had previously been disabled or something).  There's usually a jumper on the motherboard for that, or you could simply pop out the CMOS battery, wait a minute, then pop it back in.

Beyond that, I don't know.  I suppose I'd replace the motherboard.

Hopefully you'll get some other suggestions too.

---

### Post by B4r on 2010-05-30
> **BoneKracker said:**
> Hmmm... I don't really know then.  I can tell you the stabs in the dark that I personally would make.

I think the first thing I'd try would be to go into the BIOS setup and disable the onboard video.  Unfortunately, you can't do that with no monitor. :(

Next, I'd check the pins on the video cable, to make sure none of them are bent or broken as a result of whatever broke the connector.

If the cable is suspect, I'd try a different display.

If that wasn't it, I suppose I'd try removing and pulling out and putting back the PCI video adapter (or AGP or whatever it is), to make sure it's properly seated (since it wasn't in use before).

If I had sshd running, I might try to ssh in and see if the PCI video card is being recognized by the system (using lspci, lshw, and browsing around in /sys).

If the card's not even being recognized, I'd probably stick it in another computer to verify that it works.

If it doesn't work in another machine, then I'd try another card in the broken machine.

If it does work in another machine, then I might try the desperate move of resetting the BIOS to see if it would pick it up (in case it had previously been disabled or something).  There's usually a jumper on the motherboard for that, or you could simply pop out the CMOS battery, wait a minute, then pop it back in.

Beyond that, I don't know.  I suppose I'd replace the motherboard.

Hopefully you'll get some other suggestions too.
Thanks a lot for your feedback. I will try your suggestions and let you know if anything works.

---

