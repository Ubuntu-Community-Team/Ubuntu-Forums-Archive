---
title: "Changing Video Card - how to change drivers"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by bamend on 2006-08-11
I'm getting a used ATI 9200 SE from a friend and want to change out my ATI Radeon 128 pro.  After physically switching out the card, how do I get Ubuntu to recognize the new card and load the new drivers?  I've noticed all the talk about loading the fglrx driver from ATI and the incompatabilities with cards like the ATI 9200 SE.  What do I need to do to get the 3D acceleration working?  I think I may be okay since I didn't have a fglrx capable driver to start with so I didn't have any of those drivers loaded.  

I won't do any 3D gaming.  I just want to load the eye candy like xgl and compiz on my computer.

---

### Post by tseliot on 2006-08-11
Plug in the new card then boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

Then install the ATI driver

---

### Post by Tom Brokaw on 2006-08-13
I'm going to be moving from a Nvidia 5900 to an ATI 9800 Pro.  Do I need to do the same thing, or will the process be more involved?

I have the Nvidia card set up with Nvidia drivers, 3D enabled, etc.

---

### Post by tseliot on 2006-08-13
> **Tom Brokaw said:**
> I'm going to be moving from a Nvidia 5900 to an ATI 9800 Pro.  Do I need to do the same thing, or will the process be more involved?

I have the Nvidia card set up with Nvidia drivers, 3D enabled, etc.

Yep, same thing.

Then you can uninstall the nvidia driver.

---

### Post by Tom Brokaw on 2006-08-13
OK, thanks.

[edit] This is probably a question for another thread, but I'm also going to be swapping motherboards out - will Ubuntu adapt, or should I do a clean install a la Windows?

---

### Post by tseliot on 2006-08-13
> **Tom Brokaw said:**
> OK, thanks.

[edit] This is probably a question for another thread, but I'm also going to be swapping motherboards out - will Ubuntu adapt, or should I do a clean install a la Windows?

No reinstallation is required. Linux is different from Windows :D

---

### Post by bamend on 2006-08-15
I just did this but my xorg.conf file still has my other graphics card listed on it.  Should my old card still be listed?  Does it make any difference?

---

### Post by tseliot on 2006-08-16
> **bamend said:**
> I just did this but my xorg.conf file still has my other graphics card listed on it.  Should my old card still be listed?  Does it make any difference?

did you unplug your previous card?

---

### Post by bamend on 2006-08-16
Yes.  The new card is in the system now.  I uploaded the ATI driver and it works fine and lists my new card in the dialog box.

---

### Post by tseliot on 2006-08-16
> **bamend said:**
> Yes.  The new card is in the system now.  I uploaded the ATI driver and it works fine and lists my new card in the dialog box.

Then it's ok. It's not a problem if the name of your old card appears in your xorg.conf. It's just an identifier.

---

