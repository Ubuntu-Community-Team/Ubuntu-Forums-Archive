---
title: "Is that's it? (Regarding enabling Nvidia driver)"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by Amorphous_Snake on 2007-04-19
I went to System/Administration/Restricted Driver Manager, checked the nvidia driver, was asked to put the CD, did so, installed the 96xx (I don't know) driver, was asked to restart my PC, did so, and it's done.

Is that all I have to do? I have a GeForce 4 MX 440 card. I used to have problems with openGL when I install the driver without adding (NvAGP "0") in the xorg.conf file. I ran an openGl screensaver and the system didn't freeze or anything.

But there is no nvidia settings in the applications menu.

Is there anything I need to do?

---

### Post by Amorphous_Snake on 2007-04-19
I am having strange things with my screen. As if the screen is not refreshing fast enough, when viewing websites.

Edit: The above problem is definitively from the Nvidia driver as I unchecked it from the restricted drivers list and restarted, now everything looks normal.

I HATE this card.

---

### Post by Erlander on 2007-04-19
In terminal enter:

```
nvidia-settings
```

You can also add it to your menu through System/Preferences/MainMenu.

Rob

---

