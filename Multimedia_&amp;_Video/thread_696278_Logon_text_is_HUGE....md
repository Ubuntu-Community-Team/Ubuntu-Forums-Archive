---
title: "Logon text is HUGE..."
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by jaime256 on 2008-02-13
I have my Ubuntu 64-bit connected to an Olevia 26 inch LCD, but when I get to the logon and type my username and password, they are very big. I just have to make sure I type everything correctly since I can't see it. I only see parts of each letter as I type it. This is similar to when I plugged my laptop to the vga on this LCD when I first started playing with Ubuntu. Now I'm using the DVI, but I have the same problem. I don't know if you can now connect a laptop to an lcd since I haven't tried it, but if it has please let me know. It didn't work for me back then so I stopped trying. NOTE: None of the live 64-bit cd's worked for me. Ubuntu, OpenSuse, Mandriva, Fedora Core 8. Use the alternate cd.

---

### Post by pdub on 2008-02-13
Have a look at your setting in usplash.

```
sudo nano /etc/usplash.conf
```

Check the resolution settings xres and yres. Maybe set them to something like 1024x768 if your display will take that resolution.

---

### Post by jaime256 on 2008-02-13
I just checked that file and it's already set at that. One more thing, Thanks for reminding me about the nano editor.

---

### Post by pdub on 2008-02-13
Did you look at System -> Administration -> Login Window

See if accessibility option are checked. Enable accessible login is usually not checked.

And yes, nano is handy.

---

### Post by jaime256 on 2008-02-14
Well the accessibility button is not checked as you mentioned. I went ahead and checked it and then rebooted, but it's all still the same. Nothing changed. Anything else you can think of?

---

### Post by pdub on 2008-02-14
Have a look at this link.

[https://bugs.edge.launchpad.net/ubuntu/+source/libgnome/+bug/118745/comments/30](https://bugs.edge.launchpad.net/ubuntu/+source/libgnome/+bug/118745/comments/30)

---

### Post by jaime256 on 2008-02-14
I just read the link, but all my stuff is fine once I log into the system. I'll just leave it alone for now. I don't want to start changing all sorts of stuff. Since it's just the logon I'm okay with that for now. In any case, thanks for your help. I have a feeling it may just be some drivers updates and quirks. I didn't have this problem on the 32-bit system that I can remember.  Now I installed and re-installed this stuff so much that I rather just enjoy it for the time being. Again, thanks.

---

### Post by pdub on 2008-02-14
I was playing with those setting on my system and managed to make the login text sooooo small that I cannot read it! So it does work. The fonts look fine everywhere else.

Now I have to go back an set the dpi back to 96, although with it this small no one will be able to shoulder surf my login name. :)

---

