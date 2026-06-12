---
title: "sudo service lightdm stop"
date: 2013-05-18
forum: Multimedia Software
---

### Post by Tesseract007 on 2013-05-18
I'm trying to exit x windows using the command sudo service lightdm stop. But after I push enter all I get is a blinking cursor? I tried running command's but the cursor just goes one line down and blinks that's it. I can type commands but nothing happens. If anyone can help I would really appreciate it.

---

### Post by lisati on 2013-05-18
Please use the default font size for your posts. If you need to adjust it to make it easier to read, you can easily adjust your browser settings, using the Ctrl and + keys.

---

### Post by deadflowr on 2013-05-18
Are you sure you're using lightdm?

You might be running gdm, or maybe kdm if using kubuntu.

I know there are others, but these are the ones I'm most familiar with.

---

### Post by steeldriver on 2013-05-18
I think what you're seeing is normal - 'sudo service lightdm stop' kills the GUI, but it doesn't replace it by a tty on virtual terminal #7

If you want a text console, you need to switch to one of the other virtual terminals - Ctrl-Alt-F1, Ctrl-Alt-F2, ... Ctrl-Alt-F6

If you really need a console on VT7 for some reason, you can start one manually after you log in at one of the *other* VTs, e.g. log in on VT1 (Ctrl-Alt-F1) and then execute

```
sudo /sbin/getty -8 38400 tty7 &
```

and then switch back to VT7 with Ctrl-Alt-F7

---

### Post by Tesseract007 on 2013-05-18
So there's different VT's I didn't know that. I was in one where you couldn't run commands. Okay I'll try booting into the one you suggested.

---

### Post by Tesseract007 on 2013-05-19
I hit the alt-ctrl-f2 I think it said tty then stopped the x windows somehow and ran the nvidia driver. Now it works.

---

