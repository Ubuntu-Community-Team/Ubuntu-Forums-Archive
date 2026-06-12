---
title: "Nvidia onboard Sound card not recognized"
date: 2010-11-06
forum: Multimedia Software
---

### Post by albert4545 on 2010-11-06
Ubuntu 10.04 LTS

Ok, from a mess of my own doing...
I had ignored my Ubuntu install for a while now because I had no sound, even though it acted as though I did when I ran applications (could see meter bars move and so on).  I later discovered that ALSA had my device (nvidia MCP61 high definition on-board) completely muted.  Checked off boxes and Wooo!  I had sound.  Only thing it sounded like my PC was in a watery tunnel.

After reading around I saw directions to use OSS4 instead.
I went out on the Ubuntu article to change it and while following along, it told me to "blacklist" the ALSA kernel modules, using the following command...

"sudo dpkg-reconfigure linux-sound-base"

I did that, and the result is now Ubuntu does not recognize my sound card at all, in fact says I don't have any.

Ok, what information do I need to get the search going?

Thanks,
Albert

---

### Post by lidex on 2010-11-06
Are you following that guide step-by-step? How is ubuntu saying you don't have a soundcard? What do you get for this:
```
sudo lshw -C multimedia
```

---

