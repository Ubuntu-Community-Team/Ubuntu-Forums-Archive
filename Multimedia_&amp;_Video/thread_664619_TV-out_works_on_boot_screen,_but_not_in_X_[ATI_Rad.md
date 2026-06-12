---
title: "TV-out works on boot screen, but not in X [ATI Radeon]"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by Creap on 2008-01-11
I have a ATI Radeon X1050 RV370 (lspci says "Sapphire X550 Silent", I don't get these version numbers.) When booting my machine I get a very clear image on both my monitor and TV, with the boot prompt and then the ubuntu startup splash, all in colour. Then the TV goes blank (blue). 

I've tried using ATI's installer and Method 2 (about 10 times each) at: [cchtml wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually") but glxinfo still shows Mesa drivers being used and nothing showing on the telly. Once, with the ATI-installer, I got the TV-out to work decently, but then I couldn't change the resolution (!) on my monitor with those drivers, so I had to reset my xorg configuration. I also tried [RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") with the TV-out info suggested at [ArchWiki]("http://wiki.archlinux.org/index.php/ATI#TV_out"). This gives me a **black-and-white** (perhaps since it's NTSC only, and my TV is PAL) clone of the top-left 800x600 pixels of my desktop.

This is driving me mad :confused:

---

### Post by lvleph on 2008-07-10
I have a similar problem except that mine is on a laptop, and I don't have a laptop monitor. So I am really SOL if I can't get this to work. Any suggestions?

ATI 200m
Highest resolution for my TV is 1024x768. 
I tried to alt+f1 so I could change resolution, but that does not get me to command line. 
I also don't see GRUB when starting, eventhough I am doing a dual boot (I thought I might have this problem). However, I very clearly see a splash screen. I think this is a resolution issue, but I am not sure how I am going to fix that.

---

