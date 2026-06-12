---
title: "!! Help with Skype on Linux !!"
date: 2006-04-26
forum: Multimedia &amp; Video
---

### Post by gummylindz on 2006-04-26
Hello! I'm a new user of Linux and I'm not doing too badly, hehe, but I do have one small but very annoying problem, involving Skype (a program for phone calls, chats...).

The problem I have is this:

During a call, and only every so often (it's happened three times now) I start hearing this buzzing interference that doesn't let me hear the other person on the line. They can hear me but I can't hear anything. It happenes periodicaly and each time for longer. I've tried hanging up and calling again and this works the first few times, but afterwards, when trying to call, it says "problem with sound device". Oh, I also uninstalled the program and installed it again. No luck.

This never happened on windows before... How can I fix it?

Please, help!
Lindsey

---

### Post by Ensnared on 2006-04-26
This happens because Skype is a dinosaur ;) It uses OSS instead of ALSA, which makes it cause several known issues with sound. The Skype developers have acknowledged it (a couple of years ago I believe) and "are working on it", but apparently there's some third party involved in the slow progress.

Anyway, there's a site dedicated to Skype for Linux resources, and includes skype_dsp_hijacker, which is a launcher for Skype. The details aren't really important if you just want it to work - what matters is you run Skype by running skype_dsp_hijacker instead, which in turn will run the actual program.

More information and downloads can be found at the [Skype for Linx Resources](http://juljas.net/linux/skype/) site.

---

### Post by gummylindz on 2006-04-26
golly well you struck me dumb there. i'm gonna check out that site. and by the way i only managed to follow what you were tlaking about.... im a new user and a bit ](*,)

---

