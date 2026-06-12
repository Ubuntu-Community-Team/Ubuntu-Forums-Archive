---
title: "Photo: 2 nVidia GPUs - 2 XScreens - 3 displays - one weird one. Reasons?"
date: 2010-05-04
forum: Multimedia Software
---

### Post by SiliconS on 2010-05-04
I've got a three-screen desktop running from two nVidia GPUs. One GPU is   embedded in the motherboard (nForce 750a SLI) and one runs on PCIe   (GeForce 9500 GT).

On a fresh install of 10.04 I managed to get all three screens working   with Compiz if I disabled Xinerama and created two X Screens. The X   Screen for the 9500 had Twinview and the 750a stood alone with its own  panels. It's a minor  inconvenience not being able to move windows  across the whole desktop,  but it's workable.

After the first reboot though, things have gone weird. The screen  connected to  the 750a (On the left in the photo below) shows the Ubuntu  Lucid login  background and all applications and panels are hidden  behind it. The  mouse pointer moves over the screen perfectly though.

[IMG]http://i301.photobucket.com/albums/nn78/SiliconS/Misc/DSC_0011.jpg[/IMG]

When I shut down, the purple image briefly disappears to reveal the   desktop on the weird screen.

Is there a simple reason why that screen is being covered with that   login image, or does this look like an xorg.conf problem, or some  fundamental issue with my configuration?

I'm running the latest nVidia driver as suggested by the Hardware  Drivers facility.
When I boot the machine I get an error briefly appearing saying  something like 'error probing nForce SMB2' but otherwise it works OK.  (If that's important information then I'll write it down next time I see  it.)

---

### Post by SiliconS on 2010-05-25
Might I be permitted a small *bump*?

Could the purple desktop be caused by an errant CPU process? Could I kill that process manually to close that wallpaper? Ideas would be gratefully received.

Edit: Further info, a few hours later.
Just booted into Ubuntu again to see whether anything's changed. Now the left screen shows the normal desktop background and I can move the mouse cursor over to it, but the screen doesn't respond to any mouse clicks. Is there anything I can do with the keyboard to try and get that X screen to show some sort of response to input?
If I click on that stuck desktop and press Ctrl-Alt-Down (which should open out the desktop cube), the mouse cursor disappears temporarily until I release the Ctrl-Alt buttons. It seems as though the normal desktop is there, but hidden behind my desktop wallpaper.

---

### Post by BbUiDgZ on 2010-05-28
> **SiliconS said:**
> 'error probing nForce SMB2'

you could look [here](http://www.ubun2.com/question/545/error_probing_smb2_while_booting_ubuntu_desktop_1004) for info on that error

---

### Post by SiliconS on 2010-05-29
Thanks for the suggestion, BbUiDgZ. I'd explored various ideas, and I think I'd found those bug reports that referred to error messages with ACPI conflicts at start-up. None had worked though.

However, I've found a solution! I was Googling again this morning and read something somewhere that mentioned Compiz as a possible source of conflicts, so I tried disabling advanced desktop effects and my left screen is back to normal again. Yay. I can use my two X screens again and the world is good. I've gradually tried enabling various effects and at one point the screen got stuck again, but with experimentation I've managed to get the Compiz Desktop Cube working again, which is really the only mechanism that makes a big difference to usability for me.

Now I can finish setting up Ubuntu for productivity again. :D

---

