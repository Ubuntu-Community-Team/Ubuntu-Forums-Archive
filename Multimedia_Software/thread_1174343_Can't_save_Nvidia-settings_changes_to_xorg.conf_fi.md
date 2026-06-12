---
title: "Can't save Nvidia-settings changes to xorg.conf file with driver 173.xx..."
date: 2009-05-30
forum: Multimedia Software
---

### Post by zachthejones on 2009-05-30
Yep, that's about the problem I've got. I got my hands on a nice 'lil LCD monitor, but it can't handle the higher resolution which is default with my nVidia FX 5200 card. I got the 173 driver istalled (the correct one for that card), but when I go to save the adjusted monitor settings to the xorg.conf file (so it can boot up on my LCD screen - I'm having to make the adjustments on my old CRT...ugh...) - the program just shuts down. I made sure nvidia-settings had permission by running it with this command:

> gksu nvidia-settings

I even did it through a terminal so that I could see what the output was, but nothing...

Here's the deal, I need to get my computer to boot up in a 1440x900 resolution...can I edit that into the xorg.conf file manually? Or does anyone know of a way to fix this bug? Is there another way to save the "current" nvidia settings to the xorg.conf file?

---

### Post by pastalavista on 2009-05-30
You could try ```
sudo dpkg-reconfigure xserver-xorg
```If that doesn't fix it, you could try to install the driver with envyng ```
sudo apt-get install envyng
``` and then run ```
sudo envyng -t
```

---

### Post by zachthejones on 2009-06-06
thanks man! I actually ended up getting it to run using this:

```
sudo nvidia-settings
```

for some reason my computer didn't like the 'gksu' command. not sure exactly what was going on there....but it worked fine with 'sudo'.

---

### Post by RedRat on 2009-06-06
> **zachthejones said:**
> thanks man! I actually ended up getting it to run using this:

```
sudo nvidia-settings
```

for some reason my computer didn't like the 'gksu' command. not sure exactly what was going on there....but it worked fine with 'sudo'.

The command should be "gksudo nvidia-settings", not gksu. I think that was part of your problem. Sounds like you solved it though.

---

### Post by SneakPeak on 2010-01-09
Hi

```
gksudo nvidia-settings
```

Worked for me but (I think) I had to save the nvidia-settings-rc in both the root folder and my home folder.

Cheers

Sneaks

---

