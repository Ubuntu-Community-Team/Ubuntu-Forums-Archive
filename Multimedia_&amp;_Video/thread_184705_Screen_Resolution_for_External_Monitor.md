---
title: "Screen Resolution for External Monitor"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by jvoegele on 2006-05-30
I have just installed the Dapper release candidate on my IBM ThinkPad laptop.  This laptop is connected to a docking station with an external CRT monitor.  Unfortunately, with Dapper I am only able to get 1024x768 screen resolution on the external monitor, which I know is capable of doing at least 1600x1200.

In Breezy, I was able to run ```
sudo dpkg-reconfigure xserver-xorg
``` after which I could set the sync ranges appropriately, and I was then able to get full 1600x1200 resolution.  In Dapper, however, I am not able to get this resolution even after reconfiguring or even copying the xorg.conf file over directly from my Breezy installation.

Can anyone tell me why, even with an identical xorg.conf file I am able to get full resolution in Breezy but not in Dapper?  My only guess is that it is probing my monitor for its capabilities, but that the probed values are for the attached LCD instead of the external CRT, but why would it work this way in Dapper but not Breezy?

Any help would be greatly appreciated.

Thanks!

---

### Post by brsseb on 2006-05-30
I think you need to construct your own modeline in the monitor section, so that it overrides the default 1024x768-resolution. You need to consult your monitors specs for that (ususally you can get a hint of the correct values by looking at the xorg.0.log-file after a boot).

---

### Post by jvoegele on 2006-05-30
[QUOTE=brsseb]I think you need to construct your own modeline in the monitor section, so that it overrides the default 1024x768-resolution. You need to consult your monitors specs for that (ususally you can get a hint of the correct values by looking at the xorg.0.log-file after a boot).[/QUOTE]

Thanks for the response, brsseb, but I'm afraid it's a little over my head.  I will try to Google and see if I can't figure it out.

Does anyone know why this would be necessary for Dapper but not for Breezy?

---

### Post by Krash1201 on 2006-05-30
I am having a similar problem with my thinkpad, only the resolution on my external monitor is lower than the lcd on my laptop.  i am giong to try [this tutorial]("http://ozlabs.org/~jk/docs/mergefb/").  its dated to breezy, but its worth a shot.  let me know if it works for you.

---

