---
title: "Can't update Nvidia drivers"
date: 2009-06-26
forum: Multimedia Software
---

### Post by AceMilo on 2009-06-26
I have the 180 drivers for my nvidia 260 that are in the repo, and they work, but are very buggy and crash my system.  I would like to update to 185 and tried following the guide here: [http://ubuntuforums.org/showthread.php?t=990978&highlight=upgrade+nvidia+drivers](http://ubuntuforums.org/showthread.php?t=990978&highlight=upgrade+nvidia+drivers) but everytime it does not work.  I disable the 180 drivers, turn off gdm, install the drivers and that all works great, but once I reboot, it comes up with a grey error box about seeing the readme for information and then another grey box with radio buttons with options like run in low graphics for 1 session, restore backed up version, etc.  I can get back to the desktop from there but there is only 2d enabled.  I've tried a few times and it just refuses to work.  I'm back to where I was, I uninstalled the 185 and reinstalled the 180 that are in the repo but I really need new drivers.  What's going on, how do I upgrade the drivers?

I'm running jaunty 64 bit, geforce 260, intel dual core e8500.  If you need more info lemme know.

Any help is greatly appreciated.

Thanks.

---

### Post by starcraft.man on 2009-06-26
That's really peculiar. I've the exact same card (evga GTX 260 SSC) and am running 64 bit Jaunty. I did a manual install along the same lines (stop gdm, install, restart it) and I had absolutely no trouble at all (I'm running the latest 185, I didn't have any trouble with crashed with previous versions btw from repo or manuals). I'm a bit baffled, I mean there are no real differences in product across the manufacturers/editions. I've never had the error you describe either.

Do you have windows installed on this machine and does it give you any trouble in that with drivers installed? Apart from some sort of defect on the card, I'm a bit puzzled. Can you take this card out of the machine and verify it is working order in another machine, either Windows or Linux.

---

### Post by AceMilo on 2009-06-26
I tried to do the same thing on my old box which had a 6600 and it gave me the same error.  The card works fine in windows, I can update the drivers in windows just fine.

---

### Post by AceMilo on 2009-06-26
Ok so I played with it some more and it turns out I didn't properly deactivate the old driver that was in the repo.  I did that and redid the install and it worked fine.  The only question I have now is, when a new kernel comes out, what do I have to do, just reinstall the driver again?

---

### Post by starcraft.man on 2009-06-26
Ah ha, well there ya have it. 

As to your question, ya, on a new kernel, just run the manual install process again. I used to have a guide (I didn't write it) that got the installed driver to recompile with the new one upon installation but can't find it at the moment. Never usually get more than 3 or 4 kernel updates per 6 month distro anyway, not a big hassle.

Have fun.

---

### Post by AceMilo on 2009-06-26
Ya we just got one about 2 weeks ago so, no biggie.  If anything it will make me wanna check for new ones when a new kernel comes out.  Do I have to uninstall the one I have first when I upgrade to a new one or just install the new over the old?

---

### Post by starcraft.man on 2009-06-27
> **AceMilo said:**
> Ya we just got one about 2 weeks ago so, no biggie.  If anything it will make me wanna check for new ones when a new kernel comes out.  Do I have to uninstall the one I have first when I upgrade to a new one or just install the new over the old?

When you download a new kernel, it's not a patch. Your actually downloading a brand new complete kernel. So no, you never have to uninstall drivers from an old kernel, you just move to the new one and stop using the old one. Since each update is a complete fresh kernel, you have to reinstall binary drivers like the nvidia ones into it. You always have the old kernels left over, as you see on boot up their listed on GRUB (if a new kernel proves problematic, just boot the old one, it will still have everything). New one is always top (though you can edit the order).

As noted, when moving from one install method to another (i.e. repos to manual or such) on the same kernel, this isn't the case. Your best to remove first then install by new method.

I think that covers everything. Hope you enjoyed service on the forums. :)

---

### Post by AceMilo on 2009-06-27
No, I know about the kernel, I meant the drivers.  When a new kernel come out or a new version of the drivers come out, do I have to remove the old ones first before upgrading or can I install the new drivers over the old ones?

---

