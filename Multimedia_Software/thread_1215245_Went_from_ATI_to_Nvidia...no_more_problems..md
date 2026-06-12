---
title: "Went from ATI to Nvidia...no more problems."
date: 2009-07-16
forum: Multimedia Software
---

### Post by juelze on 2009-07-16
Ok, so I have a ATI 9800 Pro, but upon hearing that Nvidia offers better video performance in Ubuntu, I bought a 6600GT off of eBay.  So, I backup my stuff and reinstall Jaunty after installing my card.  Everything goes well, it detects my card and I update the driver to 180 and reboot.  Now I get nothing on my screen except black.  I reboot and go into GRUB and choose the "automatically fix video problems".  Alright, I'm back into Ubuntu.  Yay!  So now I try to adjust my resolution because it's currently at something god awful like 640x480 and if I go into System>Display it tells me "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use the graphics driver vendor's tool instead?"  So, I choose YES.  Nvidia X Server Settings pull up and I get "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just fun Nvidia-xconfig as root) and restart the X server".  However, I'm clueless as to what the heck this means.  Can anyone please help me out!!!

Any help is GREATLY appreciated.

-Juelze

---

### Post by merlinus on 2009-07-16
Did you try this, in a terminal:

```
gksu nvidia-settings
```

---

### Post by juelze on 2009-07-17
> **merlinus said:**
> Did you try this, in a terminal:

```
gksu nvidia-settings
```

No, I did not.  I should have put out a disclaimer that I'm sort of a n00b when it comes to Ubuntu as I've only been using it for the past 3 months.  However, I've committed to sticking with it, hence going from ATI to Nvidia.  I'm on my netbook right now, but I'll try that in a bit and let you know if it works.

Thanks!

---

### Post by juelze on 2009-07-17
I'm going to create another thread as the title make not provide as much assistance as I thought.

---

