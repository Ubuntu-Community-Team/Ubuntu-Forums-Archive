---
title: "Can't get Nvidia card to work on Dell with integrated graphics"
date: 2010-05-25
forum: Multimedia Software
---

### Post by PiotrOz on 2010-05-25
I have a PCI graphics card, Nvidia Geforce FX 5500, but can't get it to work and need help. I have 10.04 installed on a Dell Dimension 3000, P4, 1Gb RAM, integrated graphics.

I installed 10.04 without the card in the machine, then shut down and plugged the card in and booted it up again (BIOS setting is 'onboard' for integrated graphics, 8Mb; only other option is 'auto').

Checking the hardware drivers I can see the recommended Nvidia drivers (v173, not yet activated) and lspci gives me the integrated as well as the Nvidia listing:

01:02.0 VGA compatible controller: Nvidia Corporation NV34 [GeForce FX 5500] (rev a1)
00:02.0 VGA compatible controller: Intel Corporation 8286G Integrated Graphics Controller (rev 02)

So far so good, but that's where it ends.

Changing the BIOS setting to 'auto' turns the screen off on reboot, both for the monitor connected to the VGA port of the Nvidia card and for the monitor connected to the VGA port of the motherboard. I have to shutdown, take the card out and set the BIOS back to 'onboard' to be able to boot again (and shutdown, plug the card back in and boot up again to get back to where I was).

Activating the recommended hardware driver and rebooting (still with BIOS set to onboard) gives a blank screen (screen is still on and there may have been a flash of the purple screen with the ubuntu logo); nothing else happens no matter how long I wait. Rebooting doesn't help, it turns off the screen; same result for booting in recovery mode.

I can get to the GRUB bootloader and when I replace 'quiet splash' with 'nomodeset' I manage to boot again with the monitor connected to the VGA port of the motherboard, but am not anywhere closer to getting my monitor working on the Nvidea card.

This is where I'm stuck. Any suggestions? I've tried a lot of random things, but no progress so far.

---

### Post by PiotrOz on 2010-05-27
Bump, anyone? Rather not go back to Windows ...

---

### Post by jmarz on 2010-05-27
something in what fixed my system might be of help to you...maybe , maybe not..:guitar:


thanks to those that posted about it - I finally got my set up fixed so I don't have to mess with the low res graphics notice

one member posted this-
[1) Hold down Shift while booting to get to grub.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.
]]

I just let it go to grub and then hit the e key

use the dn arrow to get to the line that has the quiet splash
use arrow key to get to the words quiet splash and delete them and type in nomodeset
then do #3

after the reboot I still did have the low graph notice.

so i went to synaptic and removed all nvidia drivers -
used the search there to find it fast
did a reboot and still had the notice.

went back into synap and reloaded all nvidia stuff- clicked to sort by newest

and reinstalled a lot of the nv stuff from the top of that list - unless the description made me think it wasn't what i needed

did a reboot then - and finally it all worked and no stupid notice.


good luck I hope it works for you- I've been messing with trying to fix mine on & off for a month or so

Dual boot Ub 10+ with XP

---

### Post by PiotrOz on 2010-05-27
Thanks, I'll fiddle around with the drivers as soon as I get home tonight.
 
I did the first part and it got me to boot again, but only with the monitor attached to the VGA port of the integrated graphics, not with the NVidia card which is what I am trying to get to.
 
I think the main problem is changing the BIOS setting from onboard to auto (no other option).

---

### Post by PiotrOz on 2010-05-28
No luck, anyone any other suggestions?

---

### Post by PiotrOz on 2010-05-30
Bump again.
 
I got the card to work for the 2nd monitor with Windows installed so it's not a faulty card. Back to Ubuntu now, installed 10.04 with the card in the machine and BIOS set to 'onboard' ('auto' didn't work in Windows either, so I'm just going to try to get the card to work for the 2nd monitor with Ubuntu).
 
lspci shows the card, but still a blank screen ... suggestions on next steps?

---

