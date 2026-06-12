---
title: "Failed to start x server (ATI mobility)"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by adrigen on 2007-03-04
Hi,

As a result of trying to set up my 3d card, the X server doesnt work anymore.

I have an ATI mobility chip, but I think I tryed to install some regular ATI package from the synaptic package manager and now I cant boot ubuntu. 

It gives me a message saying  x server is not set up correctly and drops me at a terminal prompt. Is there any way I can start ubuntu to remove the package?

Any suggestions at all?

Thanks in advance,
Adrian

---

### Post by timjayko on 2007-03-04
did you try booting into safe graphics mode

---

### Post by adrigen on 2007-03-04
I didn't expect to have to ask this but after an extensive search, I must ask:
How do I boot in safe graphics mode?

Thanks, Adrian

---

### Post by adrigen on 2007-03-04
The only way I have figured out how to start in safe graphics mode is to boot from cd.
I can boot from CD in regular mode with out any probs though. I want to be able to change the settings on the hd install though.

---

### Post by lemoniceblock on 2007-03-04
Just a guess, but when you go to the login window, try pressing alt+F1 or ctrl+alt+F1.  That brought me to a black screen with grey text and everything had to be done via commands.

---

### Post by adrigen on 2007-03-04
It does not get as far as the login window...

---

### Post by freeflyer57 on 2007-03-04
If you have a backup copy of your config file then use this command.

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

then:
```
sudo shutdown -r now
```

If you need to find the backup file the best way is to access your hda1 with a live disk.

---

### Post by adrigen on 2007-03-04
You are a life saver and a legend!
Thanks a million (everyone),
Adrian

---

### Post by freeflyer57 on 2007-03-04
I have killed my computer many times now, while messing with Xserver.

---

### Post by ebichuhamster on 2007-03-05
what if i don't have a backup??

I don't it seems.  Or is it that you have to input the code on a specific folder? don't think so, b/c 'sudo' automatically sends you to the root directory.

Suggestions?

I have an NVIDA GeForce go6150

---

### Post by Lonthong on 2007-03-05
> **adrigen said:**
> I didn't expect to have to ask this but after an extensive search, I must ask:
How do I boot in safe graphics mode?

Thanks, Adrian

I also like to know the answer to above as well.

---

