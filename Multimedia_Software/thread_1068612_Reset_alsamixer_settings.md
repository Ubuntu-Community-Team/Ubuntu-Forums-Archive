---
title: "Reset alsamixer settings"
date: 2009-02-13
forum: Multimedia Software
---

### Post by riksweeney on 2009-02-13
Hi,

I added a .asoundrc file to my home and now they're permanently stored in my alsamixer, and there are quite a lot of them. I've deleted the .asoundrc file but they're still in the alsamixer after I reboot. Is there anything I can do to fix this?

Thanks

Richard

---

### Post by narcisgarcia on 2010-04-30
This can help you:

[http://ubuntuforums.org/showthread.php?t=237096](http://ubuntuforums.org/showthread.php?t=237096)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

And/or deleting soundcard settings for alsa:
```

sudo mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.bak
sudo invoke-rc.d alsa-utils restart

```

markbuntu has been maintaining a detailed guide for sound troubleshooting:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

