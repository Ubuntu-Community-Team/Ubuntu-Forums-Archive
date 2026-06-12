---
title: "Aspect ratio change by the remote"
date: 2009-07-26
forum: Mythbuntu
---

### Post by reformy on 2009-07-26
Hi all
I have a hauppauge PVR 150 mce kit, with this remote:
[http://www.mythtv.org/wiki/Image:MCE-Remote-2-v1069.jpg]("http://www.mythtv.org/wiki/Image:MCE-Remote-2-v1069.jpg")
All works fine.

The color buttons in the bottom of the remote don't do anything at the moment. I want to configure them to do stuff. Specifically, I want one of them to change the aspect ratio while watching recordings.
I assume that I need to change the /home/[user]/.lirc/mythtv file. But how? what is the "config" for aspect ratio?

Thanks
Yair

---

### Post by Caps18 on 2009-07-27
I use my remote to change aspect ratio, but it takes a few button presses.  It would be nice if one button could be programmed to zoom in or stretch the picture.

I have to use the Windows button on my remote that brings up a menu, press down 6 times, right once, down 5 times, enter to zoom

---

### Post by newlinux on 2009-07-27
I'm not at my machine right now, but I believe the default key to cycle through zoom/fill modes is the "w" key and for cycling aspect ratios "Ctrl+w". These bindings can change in the key editor in the frontend or mythweb and then you can map them to a button in your lirc config file. If you want to map them to buttons you currently don't use make sure those buttons are recognized by LIRC (you can test this with irw). If they are not, you will need to add those buttons to your lircd.conf file...

---

### Post by reformy on 2009-07-28
> **newlinux said:**
> I'm not at my machine right now, but I believe the default key to cycle through zoom/fill modes is the "w" key and for cycling aspect ratios "Ctrl+w". These bindings can change in the key editor in the frontend or mythweb and then you can map them to a button in your lirc config file. If you want to map them to buttons you currently don't use make sure those buttons are recognized by LIRC (you can test this with irw). If they are not, you will need to add those buttons to your lircd.conf file...

Thanks! Worked beautifully.
I used irw to get the name of the buttons, and discovered the key binding screen in my mythweb.
I even managed to fix the volume-buttons problem I had - u had to press them again and again to change the volume, instead of one long press...

---

