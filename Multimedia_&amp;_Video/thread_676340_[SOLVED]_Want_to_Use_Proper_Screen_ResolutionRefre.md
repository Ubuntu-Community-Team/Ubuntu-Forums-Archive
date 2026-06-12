---
title: "[SOLVED] Want to Use Proper Screen Resolution/Refresh; Ideas?"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by dpaint4 on 2008-01-23
Just did a fresh install of 7.10. There may be other threads that apply to this issue, but I've combed the forums and I'm not at a level to recognize that similarity.

I'd like to use the proprietary drivers for my nVidia card, but when I enable them, only incorrect resolutions and refresh rates are available to me.

My monitor is 1280x1024 60Hz, and the highest available to me after reboot with the nVidia drivers is 1024x768 52Hz, which is incompatible with my monitor and creates a large warning message from my monitor across the content of the screen.

Is there a way for me to force the OS to use the proper, inaccessible resolutions?

---

### Post by jacob01 on 2008-01-23
yea there is a way but you have to use the terminal/command prompt and add the monitor values into your xorg  but im unfamiliar with nvidia cards so i cant really help you out any more than that i have only done that with an intel chip adn that was in 7.04 i believe the 7.10 xorg.conf is a bit different

---

### Post by dpaint4 on 2008-01-23
I'm happy enough editing xorg.conf in the terminal if somebody with 7.10 could tell me the way to open it up and get me started. I'm pretty confident I'd know which entries to add and where... and if I'm wrong it's just a fresh install I'm risking, so no biggie.

I think I did something similar to this a year or so ago, but I don't recall it and I've been away from Ubuntu since.

---

### Post by dpaint4 on 2008-01-23
I ended up not needing to edit the xorg.conf -- for me, it turns out I needed to look at the 'Screens and Graphics' window under the 'Administration' menu. I selected a monitor by my manufacturer with a *similar* model number since my exact model number wasn't available. This made my needed settings appear in the resolution dialog.

This seems like a sloppy fix, but I'm okay with it because it lets me use my screen at the correct resolution and refresh *with* the nVidia drivers, which I care about because I'm superficial and wanted eye candy from my OS.

So I'm marking this as solved.

---

### Post by squenson on 2008-01-26
Thank you dpaint4 for your post and your solution. I was struggling to use my DELL D2128 at a higher resolution than the deafult one (1024x768) and a search with the words "recognize" and "monitor" showed your post. I can now enjoy ubuntu at 1280x960 with no screen flickering!

Stephane

---

