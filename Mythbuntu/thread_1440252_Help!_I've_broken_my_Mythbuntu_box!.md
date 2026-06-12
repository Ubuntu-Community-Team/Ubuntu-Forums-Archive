---
title: "Help! I've broken my Mythbuntu box!"
date: 2010-03-27
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-03-27
I'm running Mythbuntu 9.10, and have just use the update manager to automatically install all the latest security fixes etc.

This seemed to go OK, but it told me I needed to reboot, so I did. After the reboot, once Myth frontend tried to start, it told me it couldn't connect to the database.

So I rebooted again in case that would help, and now it won't run at all.

The boot up process gets as far as a screen entitled "GNU GRUB version 1.97~beta4"

This gives me a series of options, the first of which (selected by default) is "Ubuntu, Linux 2.6.31-20-generic". This is unexpected, as in the past it's just booted up without giving me any options of what it's going to boot into.

But worse than that, I can't get past that screen. It tells me to press enter to boot into the selected OS, and pressing enter does nothing. Nothing else I press does anything either. I did wonder if maybe at that stage it can't communicate with the wireless keyboard I use, so I plugged in a USB keyboard and that didn't work either.

Is this as serious as I think it is? Is there anything I can do to fix it short of a complete reinstall?

Thanks
NM

---

### Post by dsbw on 2010-03-27
This probably won't help BUT just in case: I had a similar situation a few weeks ago, not related to updates. I have a couple of USB TB drives hooked up to my machine and one of my kids had disconnected one of them.

This caused weird bootup issues that made it look like the drive had crashed. Plugged it back in and all was well.

---

### Post by SiHa on 2010-03-27
I've found that the GRUB (the bootloader you're seeing) can get it's knickers in a twist, and sometimes forget that it's supposed to auto-select an entry without showing a menu, usually after something like an unexpected shutdown. Normally though a successful boot will correct things.
I've also had the same thing with a wireless k/b not being recognised by GRUB.
Have you tried ensuring that (legacy) USB keyboard support is enabled in the BIOS?

---

### Post by NautiusMaximus on 2010-03-28
Thank you so much, SiHa, your helpful suggestion has solved the problem.

I checked the BIOS, and USB keyboard support was indeed disabled. I enabled it, and then I was able to get past the GRUB screen with the USB keyboard.

The system then booted just fine right as far as the MythTV front end. Worryingly, I then couldn't control it at all, either with my wireless keyboard or the wired USB keyboard. So I pressed the reset switch, disabled USB keyboard support again, and then everything just worked.

All a bit strange, really, given that my wireless keyboard is connected via a USB dongle, so I'm not sure how that manages to work if USB keyboards are disabled.

Still, no matter. It does work, which is the main thing, so I don't need to reinstall the OS, which I have to say is not something I was looking forward to. Now I can spend the day gardening instead, which is really going to be vastly more fun.

Thanks again!

---

### Post by SiHa on 2010-03-28
> **NautiusMaximus said:**
>  Now I can spend the day gardening instead, which is really going to be vastly more fun.


Me too, sorting out the vegetable patch for the little'uns...:D

---

