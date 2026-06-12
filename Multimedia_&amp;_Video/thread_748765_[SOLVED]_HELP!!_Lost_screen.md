---
title: "[SOLVED] HELP!! Lost screen"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by djmoore85 on 2008-04-07
Hey yall, I love Ubuntu, I just finished wiping both my hard drives and doing a fresh install of this OS so I have no windows left on my laptop. Now I have a slight issue. When I boot up I get a dark green screen with red lines in random places running vertical. I can boot as root in recovery mode, I uninstalled envy, but  still have same issue. I have the LiveCD I can boot up to explore the files and folders for my HD, so I can manipulate files from there. Any help is appreciated. Oh, these issues started when I was attempting to get Compiz working again since the new install, and I think I may have messed something up in the restricted drivers manager when I selected the ATI option whle I use envy as well.

---

### Post by nick_h on 2008-04-07
Try reconfiguring your xserver with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by djmoore85 on 2008-04-08
Thanx man I appreciate it, looks like I have my screen back. I'll be more careful when messing with the video drivers now.

---

