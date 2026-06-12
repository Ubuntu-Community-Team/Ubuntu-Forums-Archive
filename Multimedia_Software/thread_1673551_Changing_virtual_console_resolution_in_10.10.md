---
title: "Changing virtual console resolution in 10.10"
date: 2011-01-22
forum: Multimedia Software
---

### Post by milkfilk on 2011-01-22
I installed 10.10 server and the resolution is too high on the virtual consoles (all of them).  Over VGA, the high resolution shakes and has noise.  I just need to bump it down to 1024x768 or something like that.

I've done this many times with the vga= option to the kernel but grub2 seems to have deprecated that (and you have to recover or edit the line).  I read through a lot of posts and threads and tried many things but I'm out of ideas.

I've tried changing 00_header in the grub.d to to the set gfxpayload=keep trick.  I've tried
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=800x600x16
in /etc/default/grub

I've successfully changed the grub boot resolution (so I'm doing something right) but it seems to do something weird right before spawning the console.  There's a flashing cursor at the proper resolution and some messages right after grub is gone.  Then the console spawns at the high resolution.  So I thought fbset is firing or something.  But it wasn't on my system.  So I played with fbset for a while anyway and was able to scale the resolution down but it doesn't make the monitor change resolutions.  It just sorta crops it from the 0,0 upper left hand corner of the screen.

If I could make fbset fire a monitor resolution switch so that my monitor reported 800x600 instead of 1680x1050 (real resolution change) then I could just add it to rc.local and be done with it.  I'd also like to understand the lifecycle here.  Does grub or something else just auto-switch up to the highest resolution when spawning the vty's?

Any advice or things to try appreciated.  Btw, my graphic chip is built-in to my i5 CPU (Ironlake), dunno if that makes any difference.

**Update**: Solution was very odd.
First, you don't need to mess with 00_header anymore.  Just set in /etc/default/grub:
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

But also change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"

Run: update-grub2; reboot

I think nomodeset was preventing it from switching to highest resolution.  When I took out nomodeset and rebooted, the crazy-high resolution came back.  So I'm fairly confident that was the problem.  I tried to really only make one change at a time because I wanted to know what the problem actually is from a vanilla install.  This was a vanilla install of 10.10 btw.  I had selected no packages and only had done an "apt-get install openssh-server".  Hope this helps someone.

---

### Post by kosiara on 2011-03-03
Thanks :) Your solution saved my day. I was struggling with the same problem. After loading grub resolution was vga, but after a few seconds it changed to too high and i wanted to have 640x480 on the main tty.

---

