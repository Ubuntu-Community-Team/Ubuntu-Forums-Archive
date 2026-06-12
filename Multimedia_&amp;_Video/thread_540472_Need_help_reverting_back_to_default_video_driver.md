---
title: "Need help reverting back to default video driver"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by Prime Nova on 2007-09-01
I looked around some and found other posts dealing with getting nvidia drivers working, but I couldn't quite find anything that told how to remedy my specific problem. What happened is I was about to look through the different desktop effects (or something similar to that) when it told me I needed to activate my nvidia driver to be able to use the 3d effects I believe, so I said ok and then restarted. Now it won't boot into the GUI at all (something to do with "The X Server" I think?), but after clicking ok to the crazy gray prompt on a solid blue background, I can still log in and type in commands, just text only. It seems pretty obvious that the driver screwed something up, but I have no idea how to change it back to the default one that was working originally.

If someone could lend me a hand here, and type out the instructions as clearly as possible (very new to linux) I'd greatly appreciate it.

Thanks in advance.

---

### Post by yabbadabbadont on 2007-09-01
Boot into recovery mode.  There should be an option for it on your grub boot menu.  If you don't see a boot menu (because Ubuntu is the only OS on the machine), then hit the escape key when you see the grub message.  To reset your X config to its default installed state, run
```
sudo dpkg-reconfigure -p high xserver-xorg
```  (you may not need the 'sudo', but it should work anyway)

---

### Post by Prime Nova on 2007-09-02
Thanks a ton, it worked perfeclty

---

### Post by sccrstvn93 on 2007-10-27
when i try to reconfigure it says that a customized configuration will be overwritten. I know that, it swhy i am doing this. Is there a way to get around it?

---

### Post by yabbadabbadont on 2007-10-27
Did you include the "-p high" option?  If not, try again with it.  If so, rename your /etc/X11/xorg.conf file, then try again.  Example: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.borked
```

---

