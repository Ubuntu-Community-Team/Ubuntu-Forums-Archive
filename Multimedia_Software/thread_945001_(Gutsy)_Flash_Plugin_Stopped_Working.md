---
title: "(Gutsy) Flash Plugin Stopped Working"
date: 2008-10-11
forum: Multimedia Software
---

### Post by Vryko Lakas on 2008-10-11
The non-free Adobe Flash plugin for Firefox 2 was working (relatively) fine up through earlier today. Tonight it will not play anything. Once loading starts, the browser completely locks up. I've had problems in the past where it will sometimes freeze after watching a few videos and then trying to close the tab, but now it won't even get that far. 

I've tried the Complete Removal in Synaptic, then reinstalling it, and this did not fix the problem. I installed the version of Gnash that is in the repositories, but it won't play Youtube videos. 


Little help?

---

### Post by Cobraswordx on 2008-10-12
I´m having the same problem

---

### Post by gandaran on 2008-10-12
gnash won't work with youtube videos, remove gnash, swfdec or libflash if you have any of these installed then reinstall flashplugin-nonfree
update synaptic after removing the flashplugin-nonfree then reinstall

---

### Post by Vryko Lakas on 2008-10-12
> **Cobraswordx said:**
> I´m having the same problem
So I'm not the only one. I'm searching the bug reports to see if there's a known issue and fix or work-around. 

Thanks for the reply, gandaran. I did not have swfdec or libflash installed anyway. Unfortunately reinstalling the non-free plugin still did not fix the problem.

---

### Post by Vryko Lakas on 2008-10-12
Okay, that's weird. I haven't done anything different since trying gandaran's solution, but suddenly Flash is working again. Youtube videos work, I can load flash games, and so on. 
That's strange, and of course it would happen just after I filed a bug report. #-o 

I don't know what's different now and I can't speak for Cobraswordx, but I'm going to tentatively say that -my- problem is fixed. Given this problem, though, and other unresolved issues I've had with Gutsy, I'm going to upgrade to Hardy and hope its LTS status lets me use it reliably until the next LTS version. I wonder if it's worth it to re-download the iso for the latest Hardy release or just use my old "just after release" CD...

Should I leave the thread unresolved?

---

