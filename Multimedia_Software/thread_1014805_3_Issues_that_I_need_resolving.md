---
title: "3 Issues that I need resolving"
date: 2008-12-18
forum: Multimedia Software
---

### Post by wudsta on 2008-12-18
Hi All,

I've been dual booting Ubuntu and Windows XP for sometime now, due to my gaming requirements.  Their are still however 3 issues I have with Ubuntu that make me boot into my windows partition more than I'd like too.

I have an ATI 4850, and am using the newest ATI drivers that I downloaded from the AMD website. I am currently running Hardy.

First issue - Flickering video when viewing video in a window. I know this is quite a common problem with ATI cards in Ubuntu, and I have tried many different ways of trying to resolve this. The only way I have found to resolve the problem is to either disable Compiz, or to change the video output to X11 (which I'm not prepared to do as the video quality is just terrible). It's not a complete show stopper of an issue, as viewing the video in full screen eliminates the problem, but i would like the choice of being able to watch video in a window.

Second issue - I cannot enable Vsync whatever I do, I have tried enabling it in the CCC, enabling it via xorg.conf and also enabling it via Compiz options but I still suffer from visible tearing in both compiz and video playback. This is probably the most important issue for me, I find myself booting into XP to watch video on occasions as the tearing really annoys me.

Finally... This is a strange one, but if I update to the latest kernel via the update tool at actually stops x from working. I tried for a good 5 or 6 hours to fix it but ended up reverting back to the old kernel and switching off updates for the time being. I am tempted to give Intrepid a go to see if this would solve the problem, but I'm actually interested in understanding why the kernel update stop it working.

Well that's all my issues, if anyone could help me - or even just tell me their isn't a resolution at the moment then that would be great.

Thanks

Woody

---

### Post by wudsta on 2008-12-18
bumpety bump! :)

---

### Post by cariboo on 2008-12-18
I'll only deal with your third issue, as ATI and I don't get a long. If you are using drivers downloaded from ATI, every time you install a new kernel, you have to reinstall the video drivers.

With the drivers installed from the repositories, when a new kernel is installed, the installation script takes care of setting up the video drivers automatically.

Jim

---

### Post by wudsta on 2008-12-18
Thanks for the response. That's interesting, I didn't know that. However I did uninstall and reinstall the driver several times after I had update the kernel and X had 'broke', and it didn't resolve the issue.

Perhaps uninstalling the driver and the updating the kernel, then re-installing would work?

I may give this a try, but if it fails I'm back to re-installing again.

---

