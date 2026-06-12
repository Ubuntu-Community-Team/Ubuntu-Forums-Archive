---
title: "save video settings"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by ryana on 2007-08-31
I've seen other people post similar things to this, but nothing has fixed this for me. When I restart my computer the video settings are set to 1024x768. I do a 'sudo nvidia-settings' and change resolution to 1152x864, press 'apply', press 'Save to X Configuration File'. Then the screen is the right size....until I restart and it reverts to 1024x768. How can I make this setting actually save after reboot?

If it matters I have nvidia geforce 5500fx video card.

---

### Post by wolfen69 on 2007-09-01
in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

