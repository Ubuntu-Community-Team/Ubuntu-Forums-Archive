---
title: "Bypass low graphics mode prompt"
date: 2013-02-14
forum: Multimedia Software
---

### Post by jsandbrook on 2013-02-14
I'm running Ubuntu 12.10 64 bit with an ATI graphics card connected over hdmi to the TV in my living room. Using it there works great. 

I'd like access to my computer remotely, though, so toss on ssh/vnc/WOL. That works great too.

Except, when I  WOL with my TV turned off, Ubuntu throws up the "running in low graphics mode" prompt and won't start the display manager. Using startx through ssh half works (my desktop never fully loads..probably fixable) but some strange guttural sound plays through my  system which can't be good for it. I don't like that solution.

I'm looking for a way to keep Ubuntu's boot behavior the same while my TV is on (auto-detect/use the correct resolution) yet ignore warnings when my TV is off.  Maybe, say, fallback to some  defaults I can configure myself. Is this possible?

---

### Post by sapper6fd on 2013-04-02
*** Bump ***

I'm going to bump this thread as I'm having the exact same issue.  Was this ever resolved?

Cheers,

Sapper

---

### Post by jsandbrook on 2013-04-03
You're going to kill me. Yes, but I'm not sure how. I swear it was still happening just last week. 

When I saw your post, I decided to try one last potential solution before replying and added a 'vga=893' option to my linux boot command. Booted with my TV off, no problem.

I decided to confirm that was the fix so I removed the option, updated grub, and rebooted. The TV was off but it still booted just fine.

I must've updated something along the road that's causing it to work now. You might try using the vga option (893 is for 1920x1080. There are other values [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers")) but I don't think it was the solution.

Just to be complete, I added:
   GRUB_CMDLINE_LINUX="vga=893"
to /etc/default/grub, ran update-grub, and rebooted

---

