---
title: "Please help! Absolutely STUCK with ATI radeon 3dfx, I already tweaked it, it went bad"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by amaurynieto on 2006-12-31
Hello there! i've been using ubuntu for some time now, and I enjoy it thoroughly,
recently I copied over windows, and just started a brand new fresh ubuntu Edgy, 
and followed this tweak to make my ATI Radeon work:

From [www.beginningubuntu.com/dapper_tips.html](www.beginningubuntu.com/dapper_tips.html)

"Use proprietary 3D drivers
OK, here's the deal. Open source drivers for your 3D card are provided "out of the box". No further work is needed and they're installed by default.
      The problem is that these only provide 2D. For optimized 3D graphics (to use the flashy XGL desktop, or to play 3D games), you're going to need the proprietary drivers. "Proprietary" in this case means closed source. That's bad. On behalf of the open source community, I ask that you only install these drivers if you absolutely have to. Otherwise just stick with the open source drivers, which will do all you need and are a LOT more stable than the proprietary drivers (you'll probably kill your Hibernate/Suspend feature by installing the proprietary drivers, for example).
      Better still, write to Nvidia or ATI and ask them to release fully open source drivers.
      ATI cards: Open Synaptic and search for xorg-driver-fglrx and fglrx-control. Install both. When installation has finished, open a command-prompt and type sudo aticonfig --initial (note there are two dashes before initial). Reboot your machine.
      Nvidia cards: Open Synaptic and search for and install nvidia-glx. When installation has finished, open a shell window and type sudo nvidia-xconfig. Then reboot.
      Test your new 3D configuration, after reboot, by selecting one of the OpenGL screensavers (System -> Preferences -> Screensavers). AntSpotlight is pretty cool. If it runs smoothly then everything has worked."


The problem is I messed it up and now every time I do aticonfig --initial, I get:

root@Ubuntu:~# aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

Please help!!! 
I want 3d to work.

Thanks, A.

---

