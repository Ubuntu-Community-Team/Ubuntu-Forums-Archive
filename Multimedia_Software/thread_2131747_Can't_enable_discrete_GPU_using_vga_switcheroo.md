---
title: "Can't enable discrete GPU using vga_switcheroo"
date: 2013-04-02
forum: Multimedia Software
---

### Post by nicocarbone on 2013-04-02
I recently upgraded (clean install) to Ubuntu 13.04 from 12.10. Everything works much better except for one thing: switchable graphics.

It was already messy in Ubuntu 12.10. Having a MUXed hybrid Intel Ironlake/AMD 5650m notebook, which is unsupported by Catalyst drivers, my only option was open-source drivers and vga_switcheroo. Even if performance was sub-optimal and I have to restart X every time I wanted to change GPUs, it worked. But now in Ubuntu 13.04 switching to discrete GPU is completely broken.

The first thing is that switching to discrete GPU the way I used to (in a terminal "echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch" and logout) now makes the X-server crash when I log out. I reported a bug about it: [https://bugs.launchpad.net/bugs/1162526](https://bugs.launchpad.net/bugs/1162526)

Using a nasty workaround posted by Vangel Ajanovski in askubuntu ([http://askubuntu.com/questions/142506/hybrid-graphics-on-ubuntu-12-04-switching-to-discrete](http://askubuntu.com/questions/142506/hybrid-graphics-on-ubuntu-12-04-switching-to-discrete)) I managed to swich to the discrete GPU, but the backlight of the notebook display is off and can't be turned on. It kinda works through HDMI, though. I also reported a bug about this: [https://bugs.launchpad.net/bugs/1163418](https://bugs.launchpad.net/bugs/1163418)

Finally, I discovered that when I am using the Integrated GPU, X-server thinks there is something connected to the DisplayPort. Not only there is noting connected, but this port only works when I am using the discrete GPU, which is properly turned off. Another bug report: [https://bugs.launchpad.net/bugs/1163425](https://bugs.launchpad.net/bugs/1163425)

Have anyone experienced similar problems? Does anyone have any solution? I really don't know where to start debugging this issues.

Thanks you.

---

### Post by fixr on 2013-05-29
I'm having the exact same issues on a intel i915/ATI 5650 combo (muxed) with vga_switcheroo. Trying to switch to DDIS results in freeze. The workaround you linked to didn't make the trick for me. I think it must be something with the new kernels. I noticed you were running 3.8.0-15-generic, I'm on 3.8.0-19-generic (default on 13.04) and just updated to 3.8.0-22 which doesn't work either. I'll attempt to downgrade to older kernels when I get the chance.

Have you found any solution yet?

---

### Post by howefield on 2013-05-29
Thread moved to the "*[I]Multimedia & Video*[/I]" forum

---

### Post by fixr on 2013-05-29
A little update: the "nasty trick" did it for me as well, it's just that I wasn't connected to HDMI the first time I tried, because it turns out, booting up lightdm with the HDMI connected also results in a freeze. I have no idea where to follow from here.

For future references, I'm on a HP Envy 14-1110nr.

---

