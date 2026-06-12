---
title: "Video card upgrade causes problems"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by kevin_hill54 on 2007-04-25
Hi

I have upgraded my video card from an old ATI to a X1550

The machine failed to complete the boot up process and locked up with a line across the Ubuntu logo.

I replaced the old card and tried to install the ATI drivers from ATI but the process failed with a missing file at the end of the install.

Now the old card does nothing and the new card shows a very distorted and cut off screen.

The live Edgy CD boots OK and has the graphics work so I figure that the settings are stuffed on my install.

How can I reset all settings to the original defaults?

---

### Post by spin2cool on 2007-04-26
two things to try: 
restore your old /etc/X11/xorg.conf file.  (if you didn't make a backup, the ati install may have, in that directory).  If you can't restore it, do the following from a command line:

```
sudo dpkg-reconfigure xserver-xorg
```

Step through it to set up your video drivers again.

You also might try using Envy (or the restricted drivers manager?) to install the ATI drivers.  Envy is here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by kevin_hill54 on 2007-04-27
Nothing worked!

I tried everything I could find and decided to upgrade to a clean install of 7.04.....

Wow...

That was easy.

All the video works and there is even a simple ATI install.

Now thats nice.

I think I might try my luck to install the TV card.

Thanks

---

