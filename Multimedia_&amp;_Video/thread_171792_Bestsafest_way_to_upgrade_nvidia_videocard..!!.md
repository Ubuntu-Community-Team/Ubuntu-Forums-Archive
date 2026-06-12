---
title: "Best/safest way to upgrade nvidia videocard..???!?!"
date: 2006-05-07
forum: Multimedia &amp; Video
---

### Post by mrazster on 2006-05-07
Lo fellas..!!

I'm about to upgrade my 5600 card to a 6600GT and I'm wondering what would be the best way to do it, driver wise.
Can I just smack in the card and it'll all be fine...or do have to reinstall the drivers..??
If reinstall is needed....can I just start the install and it will remove the older ones, or do I have to remove them manually?

I have installed latest ones(8756) from nvidiasite with there installer...using **method2** in [*THIS*](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy) HOWTO.


Thnx in advance..!!

---

### Post by tseliot on 2006-05-07
Swap the graphic card, turn on your computer and type:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mrazster on 2006-05-07
Thnx alot...much apreciated..!!

---

### Post by mrazster on 2006-05-07
Well I got it installed. BUT...it didn't work with ```
sudo dkpg-reconfigure xserver-xorg
```command.....atleast not as expected.
I pointed it to the nvidia drivers...it found my 6600GT e.t.c ....but when I rebooted and made ```
glxinfo
``` in terminal I got SGI drivers loaded...and roughly 800fps in glxgears.

However...I went back to CLI and killed X...and reinstalled the driver...wich also removed ther "older ones" .....everything went fine...now it loads Nvidia GLX 1.4....and I'm currently a happy camper  :p :p ....with roughly 7k fps in glxgears.

---

### Post by lonce on 2006-10-15
I have this exact issue right now.  How do I reinstall drivers from command line.  I used automatix the first time.  I just upgraded my video card from 5500 to 6200 and my FPS in glxgears was cut in half literally.  I want to uninstall all my Nvidia drivers and reinstall them but not sure how to do it.  How did you do it mrazster?

---

