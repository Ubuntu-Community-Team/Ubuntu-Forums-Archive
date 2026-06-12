---
title: "Monitor turning off on logout with DVI/ATI/FGLRX"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by chorca on 2006-11-05
This all started when i got my new screen. I was previously using an old Dell P1110, a 21" Sony Trinitron FD tubed monitor. It worked over the VGA port, and I hadn't had any problems operating it.

Just recently, as i've gotten more into photography, i've looked for a better screen as the old 21" has been getting washed out and almost unbearable. A friend got me a deal on a 22" Samsung LCD (225BW), and i was using it in windows for awhile, as i do most of my photo work there.

I decided to test it out in linux later that week, wondering if it would be able to handle the 1680x1050 resolution. I had previously been using the fglrx driver on my ATI X800XT PCI-Express card, and it had been working flawlessly. I was even running Beryl just fine. The new monitor utilized the DVI port, and i went ahead and stayed with that, as it offered a higher quality picture.

Upon booting Ubuntu, i modified my xorg file to properly see the monitor, and from there, i was able to boot into Gnome fine, at the proper resolution. However, i then decided to login to an XGL setup on the machine to test how the screen looked in Beryl. Upon clicking logout, the screen went blank, sat there for a few seconds, then shut off. I pressed ctrl-alt-del to get the machine to reboot, and after it came back, i tested the same problem, it did the same thing. I elected not to use Ubuntu for a bit, as the release was quite close to coming out.

So just today, i downloaded the Edgy final release CD, installed it clean, set up fglrx, and i'm having the exact same problem. I had chatted with a friend earlier who mentioned that it seemed that the video card was not outputting any parameters to the screen after logout, and the screen was therefore shutting off. I tried using the open-source ati/radeon driver, and it does not have this problem. I also tried fglrx using a VGA cable instead, the problem does not occur. The problem only happens while using fglrx with a DVI cable, and upon logout, or switching to a Virtual Terminal screen.

I have checked the logfiles for X and not found anything out of the ordinary, no errors or anything. I want to use 3d acceleration, however, it appears the open-source driver does not support my card as it is PCI-E, and the fglrx issue with logouts is more than annoying. I'd like to know if anyone else has had this problem. I've notice a lot of posts around the forums through my searching that deal with X not coming up at all on a DVI screen, but those seem to be a different problem, as mine only happens when X is reloaded upon logoff.

Any help would be appreciated, i'll do my best to get any logfiles necessary.

---

