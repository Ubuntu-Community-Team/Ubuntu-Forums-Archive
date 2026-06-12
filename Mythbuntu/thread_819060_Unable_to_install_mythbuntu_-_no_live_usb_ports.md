---
title: "Unable to install mythbuntu - no live usb ports"
date: 2008-06-05
forum: Mythbuntu
---

### Post by vbmds on 2008-06-05
I'd like to install mythbuntu onto my HTPC but have hit a rather show-stopping issue. None of the USB ports are live after the initial boot menu selection so I am unable to interact with the Installer. 

Now before the obvious is stated, I do not have a PS keyboard or mouse that I could plugin instead. 

So, any ideas how I can complete an install using only USB peripherals?

---

### Post by tgm4883 on 2008-06-05
> **vbmds said:**
> I'd like to install mythbuntu onto my HTPC but have hit a rather show-stopping issue. None of the USB ports are live after the initial boot menu selection so I am unable to interact with the Installer. 

Now before the obvious is stated, I do not have a PS keyboard or mouse that I could plugin instead. 

So, any ideas how I can complete an install using only USB peripherals?

Thats quite interesting.  I installed with USB keyboard and mouse just fine.  What brand/model are yours?  Did you verify your ISO, burn at slow speed and verify your burn?

---

### Post by vbmds on 2008-06-05
Thanks for the response...

The keyboard is a Viewsonic multimedia keyboard, The mouse is a Logitech MX1000

The CD has been verified, the 1st CD was corrupt as a matter of fact, but this one passed inspection.

I should clarify that I am trying to use the Front USB ports - running off USB headers of the motherboard, not the rear ports as they are obscured by the the entertainment unit.

---

### Post by superm1 on 2008-06-05
In your BIOS you probably have to turn on legacy USB mode.

---

### Post by vbmds on 2008-06-05
Sorry to say, legacy USB mode is on. 

I've had no issues installing XP and XPMCE on this machine with this keyboard and mouse on these ports. 

I've managed to plug in a USB extension cable into a rear port, and have plugged in the mouse, and then the keyboard, rebooted, but alas still neither keyboard or mouse functions when plugged in.

---

### Post by vbmds on 2008-06-05
A quick update, I've downloaded the AMD64 ISO again and burned it to CD, but alas still no USB ports...front or back.

---

### Post by murchball on 2008-06-05
Just to confirm, the keyboard and mouse work fine during the install, but not after you reboot, correct? You could try installing ssh during the install and then connect over the network to see what the problem is.

---

### Post by tgm4883 on 2008-06-05
> **murchball said:**
> Just to confirm, the keyboard and mouse work fine during the install, but not after you reboot, correct? You could try installing ssh during the install and then connect over the network to see what the problem is.

That doesn't appear to be the problem, he says it doesn't work after the initial boot menu.


Two things I would try.  First, after it boots up unplug and then replug in the usb keyboard/mouse.  If that doesn't work, try the alternate cd?

---

### Post by zarsi on 2008-08-26
I had same problem.

I went to bios and changed USB Key/Mouse control from OS to BIOS and it solved keyboar issue.

However loading is still ending to prompt and I won't get LiveCD running.

---

### Post by boushley on 2008-10-11
I have the same problem as the original poster.  Installed mythbuntu.  Wanted to get it running, gave it a couple of days and played around with it everything seemed great, but discovered that usb mouse doesn't work when I started wanting to use it.  I don't have a ps2 mouse, luckily I had been using a ps2 keyboard.

If you know of anything that fixes this, let me know.

---

### Post by ewhelan on 2009-03-15
I am having a similar problem. I installed mythbuntu 8.04 and had no issues with my usb keyboard and mouse. I upgraded to 8.10 and I have had my usb ports turn of as soon as it boots up ever since I installed it. I have tried both disabling and enabling my my legacy usb support it does not seem to matter. Sometimes if I hit my numlock key right before the bootup finishes I can keep the usb ports form turning off but does not always work.

---

