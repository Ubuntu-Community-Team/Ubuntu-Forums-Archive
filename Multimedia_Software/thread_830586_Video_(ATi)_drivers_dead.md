---
title: "Video (ATi) drivers dead?"
date: 2008-06-16
forum: Multimedia Software
---

### Post by Mako Eyes on 2008-06-16
I've been messing around with both the open source ATi drivers and the proprietary ones and after doing a variety of simple tests, I became more pleased with the open source driver results (better full-screen video playback, etc) so I settled on them. These are the ones that were installed automatically when I installed Ubuntu Hardy.

I've been reading [tseliot's thread](http://ubuntuforums.org/showthread.php?t=515573) about installing the drivers but the methods hardly worked to my satisfaction. I did a little research on his [envy](http://www.albertomilone.com/nvidia_scripts1.html) project and decided to give it a whirl since I could do a simple "envyng --uninstall-all" if anything goes wrong.

Booting to the desktop gave nothing more than a white screen, but I could tell the drivers were at least a partial success as my ring application switcher worked under Compiz. Other than the ring switcher, I couldn't really do much else. So I rebooted and tried the "envyng --uninstall-all" command in recovery mode.

Well, I must have did something wrong, because I noticed that I was unable to enable Compiz when I got back. Whenever I try, it prompts me to install the proprietary (fglrx) drivers. Those run Compiz, but also bring their undesired effects to my card with them.

I've tried messing with the Proprietary Drivers Manager, un/installing the drivers using Synaptec, and rebooting--each in every order possible. Nothing worked.

There's no way this is irreversible; there has to be some way to get the open source drivers up and running again. I'm just at a complete loss as to how. I'll keep looking for solutions, but so far I'm running into blanks. Are they actually gone, or are they just "broken?" Maybe this is Compiz' fault? I have no idea...

I should mention that I'm running a Sapphire Radeon X800 Pro PCIe. If there's any more information you need, just say so.

Thanks.

EDIT: This is odd... I also just noticed some of my global keyboard shortcuts do not work. They worked fine before this ordeal (I use them quite often), but I cannot see how it would cause that to happen.

EDIT 2: Hm. It seems the Gecko embedded media player is also busted. This is very strange.

---

