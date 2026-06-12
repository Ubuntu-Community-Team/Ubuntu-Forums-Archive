---
title: "IBM Thinkpad R31 problems"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by goke on 2006-07-24
I just installed Ubuntu onto my IBM Thinkpad R31.  Everything seems to be running great except I get a squealing sound out of my computer and the trakpoint sometimes jumps around on me.

Assuming from past experience and the fact that the graphics are really choppy on my computer when they shouldn't be; I think I'm having trouble with my graphics driver.  I looked around online and found a program called XFree86 that people said did the trick, but I coulnd't get it to install.  I've got very limited experience with Linux (I've used a bit of Fedora Core 3) so I probably just don't know how to install it.

Anyway, the Device Manager says I've got an 82830 830 Chipset, just a standard onboard Intell chipset, nothing special.  But I know it has more power than what my comp is currently giving me. My CPU is obviously taking on all the graphics because it strains even when running a screen saver.

Any help on installing a graphics driver would be greatly appreciated.  Also if anyone knows how to get the trackpoint working I'd much appreciate that as well.

Thanks,
~Goke

P.S. For some reason I can't change the permissions on many of my system files.  How can I set myself as Owner?

---

### Post by pjmcswee on 2006-08-30
Hey I have Unbuntu on my R31 as well you have to add the line 
i8042.nomux=1 in the grub.conf file see: [http://www.low-cost-computing.com/ThinkPadR31MouseProblems.shtml](http://www.low-cost-computing.com/ThinkPadR31MouseProblems.shtml)
its for fedoracore but it applies.

---

