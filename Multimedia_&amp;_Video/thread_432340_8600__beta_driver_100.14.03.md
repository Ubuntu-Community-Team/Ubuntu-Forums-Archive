---
title: "8600 / beta driver 100.14.03"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by acorrigan on 2007-05-03
I got a NVIDIA 8600 last week.  Previously I had a 6600 and used envy to get up to date drivers in Ubuntu.  Since then I haven't been able to boot directly into Linux (the screen goes black once X loads) and have to choose recovery mode  (or whatever it's called) in grub.  When I did this I downloaded and installed the beta driver which supports the 8600 [http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html) and from there I could do /etc/init.d/gdm start (or something like that) to load X and get to the login screen where things work okay except I think things are a little weird due to being in recovery mode.  When I reboot, I still can't boot directly in the non-recovery mode, since otherwise the screen just goes black.

What can I do?  How do I make it so I can boot into Ubuntu normally without going through recovery mode.  Is there any plans for the 8600 to be supported by Ubuntu 7.04 directly or by Envy?

---

### Post by guggenheim on 2007-05-07
I have the exact same problem, using my 8600GT. I hope this is due to a dodgy beta driver from Nvidia, and that the problem will be solved when they release a proper version.

The funny thing is that it works perfectly when starting X directly after running Nvidias installer... but it is when the system is rebooted that the screen goes blank (doesn't even seem to get any signal).

Could this be due to that some kernel modules are not beeing loaded?

---

### Post by arn0n on 2007-05-08
same problem here.
i compared the output of lsmod before the NVIDIA installer, and after, and it seems that the installer removes the nvidia module (?!) and that's the thing that enables it to work. weird, isn't it?

anyway, edit the gdm script in /etc/init.d, and add the line 'rmmod nvidia' as the first instruction there. this did the trick for me.

if anyone comes up with a better solution than this awful kludge, let me know.

---

### Post by casi on 2007-05-09
Same for me, it doesn't work.
I hope they will fix this soon...

:\

---

### Post by arloth on 2007-05-18
> anyway, edit the gdm script in /etc/init.d, and add the line 'rmmod nvidia' as the first instruction there. this did the trick for me.

after booting to recovery mode, compiling/installing the beta driver, and then editing the kdm file in my case, it did in fact work.  yay!  

There are still some glitches though, I don't get a splash screen on startup or shutdown, and it seems to hang on shutdown maybe the power management stuff isn't right, but who knows.  I'm not sure if the not shutting down properly isn't caused by something else yet.. one problem at a time. ;-)

edit: i'm using gigabyte's 8600GTS  i'm not sure if that may have bearing on other people's success with these beta drivers yet.

---

### Post by fwilliams on 2007-05-27
I had similar problems with the 8800GTS.  A solution:

I had to use an alternate install cd, because the install from the live cd would not finish.

Do not add additional screen resolutions during install!

Use symatic (or whatever) to download the libc development libraries and headers (ie. libc6-dev), they are needed for the following:.
[http://www.ubuntugeek.com/how-to-fix...acy-users.html](http://www.ubuntugeek.com/how-to-fix...acy-users.html)

Hope it helps, before I found that link I was having no luck.

---

