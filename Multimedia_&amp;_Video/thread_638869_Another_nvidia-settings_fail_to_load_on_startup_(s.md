---
title: "Another nvidia-settings fail to load on startup (still, after many troubleshoots)"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by mr. Fenwick on 2007-12-12
Hi there

Using Ubuntu for two months now and everything's gone well except for one issue that's beginning to cause frustration. All other problems I've managed to find in the forums and I'm writing here in desperation.

I have everything working as I want but: the changes I make in nvidia-settings do not stick. 

I've tried the following from other forum topics:

-opened nvidia-settings in root and saved to xorg.conf
-added "nvidia-settings --load-config-only" in the Startup section of the Sessions Manager

No deal.


Recently there've been some odd symptoms: 

Some resolutions I choose breaks the screen up into unresponding squares at the bottom of the screen, after it's timed out to revert back to the previous resolution all I get is a black screen with mouse.

At one point ubuntu told me at startup that the Settings Daemon didn't work, and after this the widgets weren't working either. (I had added screenlets to the startup list previously and it'd been loading fine until this once.)

Some strange error after running nvidia-settings in the console where it says it's unable to connect to the monitor and can't read settings from the nvidia-settings-rc file.


It seems to me that nvidia-settings is reading from one config file -- nvidia-settings-rc, but is writing to another -- xorg.conf. 

Would appreciate any ideas.

---

### Post by mr. Fenwick on 2007-12-13
bump

---

### Post by mr. Fenwick on 2007-12-13
bump

---

### Post by mr. Fenwick on 2007-12-15
Has anyone had similar problems miraculously vanish after a reinstall??

---

