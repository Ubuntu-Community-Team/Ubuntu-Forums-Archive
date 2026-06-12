---
title: "Disabling nForce2 GART"
date: 2006-01-03
forum: Multimedia &amp; Video
---

### Post by Scuddie on 2006-01-03
My motherboard has an "issue" where the video card becomes unstable if there is AGP acceleration in driver form.  GF4 Ti 4200 8x, and an FX5500 both yield the same results.  On XP, I would get a BSOD, varying from 2 seconds to 5 minutes from the time Windows started.  This was directly influenced by the BIOS settings.  8x AGP, FW and SBA enabled, and 1.5 AGP volts would last no longer than 5 seconds, while 4x AGP, FW and SBA disabled, and 1.7 AGP volts lasted a bit more than 4 minutes.  

Thru experimentation, I found out that when I removed the GART driver, the problem flat out went away, and my games still ran at their fullest performance.  Even though RivaTuner reported PCI speeds and all features disabled, I noticed no difference whatsoever.  I thought this problem was due to conflicts with XP SP2's "better GART driver", but I was wrong.

So here I am, setting up Ubuntu for the third time, and things seem a bit more mature than Hoary.  I am happy in this area, but it seems my GART driver problems remain.  I did the usual gathering of drivers, specifically nvidia-glx.  When I typed "sudo nvidia-glx-config enable", I was ofcourse noted that I would have to restart X server.  I dont know how to restart X, so I simply restarted my PC.

When Ubuntu began to boot again, the startup took forbloodyever...  But that's for another topic :p.  When the loading completed, I was expected to be greeted by the login splash screen, but I was only harassed by a plain white screen and a frozen PC.  I waited 5 minutes to see if it would come back, but no luck.  Soft off wasn't responding, so I had to hold down the power button to turn it off, and I rebooted into recovery mode.  I typed in "nvidia-glx-config disable", and rebooted into normal mode, with everything except glx working again.

So, with that said, is there an easy way for me to remove GART from the nvidia driver set?  If anyone knows the solution to the root cause (besides buying a new PC), I wouldn't mind hearing that either ;).

Thanks, and forgive the long post.

---

### Post by mcduck on 2006-01-04
in /etc/X11/xorg.conf there's a line like '#UseInternalAgpgart  no' or something like that. I think that with nForce2 motherboards you have to remove the '#', so do try and reboot (or Ctrl-Alt-Backspace to restart X).

---

### Post by Scuddie on 2006-01-04
Thanks for the idea, but I looked in xorg.conf and there was no line like that.  I did some snooping around, and apparently that's a flag for ATI cards to use an alternate GART driver.  I tried adding the flag myself, and set a yes and no, and both times it failed.

Oh how I wish there was a way to disable AGP acceleration...  Somebody should know the answer.  Perhaps GART is part of the glx suite and not the nforce2 suite?  I would love to start using linux again, but until this is fixed, I cannot.

---

