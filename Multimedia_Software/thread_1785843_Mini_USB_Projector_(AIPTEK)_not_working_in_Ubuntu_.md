---
title: "Mini USB Projector (AIPTEK) not working in Ubuntu 10.04"
date: 2011-06-18
forum: Multimedia Software
---

### Post by ellaivarios on 2011-06-18
Hi everyone,

I am running Ubuntu 10.04 as my main OS, and I also have Windows 7, Windows XP, Windows Vista, and Ubuntu 11.04 (yes multiple boot, and YES I need them all, especially the windows variants, except Ubuntu 11.04 (that's just my partition to test new Linux versions) - I'm a teacher so I need to use various old programs and virtualbox does do me all favors, nor does compatibility features in windows), on a Dell Inspiron 9400, Duo Core 1.98Ghz, 2GB RAM, ATI X1400 128MB Graphics.

I recently purchased a mini (pocket) USB projector made by AIPTEK. The model is RVT6, and it is great because it's LED powered up only by USB and tiny. It works fine under all the aforementioned windows installations, even inside a virtual box with Windows XP. But I want to be able to use it in Linux, and it does not work in 10.04 nor 11.04. The USB Projector has a switch at the back, and the switch can make it go into Projection mode, or it turns it into a Firmware-type USB stick that loads itself as a virtual cd Drive from where the user can install the drivers. These are windows-based drivers however. They do not work under Wine. The Projector works fine within virtual box running Windows XP, but I lose a few frames due to performance lag here and there when I play videos.

When I type lsusb in the terminal, I get:
Bus 001 Device 008: ID 08ca:2137 Aiptek International, Inc. 

So Ubuntu recognizes the device, of course, otherwise it would not work in virtual box either.

Is there any driver to export the VGA to USB for Linux?

My thoughts are that since Linux "sees" the device, it does not know which driver to assign to it. Does it have to do with **SISUSBVGA**? And how do I use it?

Or is it that perhaps I should (also) try updating Xorg.conf? although I can't find it anymore (is it not required?). If I have to update or create **Xorg.conf**, should it be under **/usr/lib/X11/xorg.conf.d **? And what should I write in there? 

Finally, if I do get Linux to recognize the projector, how can I make it project either as a "mirror", an "extended screen", etc. of my monitor, and what can I use as a switch or launcher/script/command to turn it on or off?

Any help from anyone would be greatly appreciated.

I am not an advanced user like most of the Linux Gurus in here so be patient with me.

Thank you so kindly,

Dimitris

---

