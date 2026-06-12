---
title: "Keyboard mapping is impossible to restore"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Kobalt on 2011-04-05
Hi everyone,

I'm runing an up to date natty, and yesterday I took my netbook to hook it up at work: I connected my Dell USB keyboard, all went well. Until I unplugged it and restarted my netbook a while after: I can login, but right after GDM the keyboard mapping is completely messed up. It still seems to be a French azerty keyboard, but a lot of keys are mixed up (seems like it's still set for a desktop keyboard and not a laptop keyboard.
But I can't apply any settings as I can't type in my password. 
I've tried to search but found nothing on resetting this setting through a tty.

Can someone guide me?

Thanks :)

---

### Post by Quintilian on 2011-04-05
Does it go back to working correctly if you plug in a USB keyboard?

---

### Post by Kobalt on 2011-04-05
It does, but the whole point is to use it at work with a full keyboard, and away from office as a netbook, and change from one keyboard to the other with the mapping selector. But changing mapping from there doesn't do anything...

---

### Post by Quintilian on 2011-04-05
Can you use something like "onBoard" (on screen keyboard) to type your password in the prompt for your password? 

(I had to right-click on the applications toolbar and go to edit menus and under universal access I could enable onBoard to have it appear in the menu.)

Does doing it this way let you apply the settings and fix the keymap?

Edit: there's also a settings button that looks like it'll let you change the layout of the onBoard keymap in case it is French azerty as well.

---

### Post by Kobalt on 2011-04-05
Thanks for the tip, but even though I can reset the settings from the gnome keyboard utility, it still doesn't work and the keymap remains completely mixed...

---

### Post by cariboo on 2011-04-05
If you can get into your desktop with the on-screen keyboard, you should be able to go to System Settings in user switch menu, and change the keyboard layout there

---

### Post by Kobalt on 2011-04-06
> **cariboo907 said:**
> If you can get into your desktop with the on-screen keyboard, you should be able to go to System Settings in user switch menu, and change the keyboard layout there

I do, but yet the keyboard layout is unchanged... the layout is the one of a desktop keyboard, not a laptop keyboard.

---

### Post by cariboo on 2011-04-06
Don't you have the option to change the keyboard type? Like in the screenshot.

---

### Post by Kobalt on 2011-04-06
I do yes. 
I managed to correct the problem, by plugging the USB keyboard and changing the keyboard type to "Asus laptop", then "apply system wide". 
But it's really strange that, having the two layouts and being able to chose them from the keyboard selector doesn't do a thing, the USB keyboard layout is always active as long as there are two layouts...

---

### Post by Kobalt on 2011-04-06
Well guess what: if I reboot, the problem comes back. Keyboard layout is set to Asus laptop, but the layout is the one of a desktop...

---

### Post by Quintilian on 2011-04-06
Maybe you could try:
sudo dpkg-reconfigure console-data
although that looks like it might only help in consoles, if anything...

a workaround might be to use setxbkmap, perhaps in your .bashrc, so that it'll set the keymap you want at login. but that seems like the command line equivalent of System>Settings>Keyboard which you said didnt work. :/

---

### Post by Kobalt on 2011-04-06
I tried to reconfigure console-data, as well as keyboard-configuration... still not working.

---

### Post by Kobalt on 2011-04-07
I've solved the problem by deleting all the hidden config files in my home folder. But still a very strange behaviour...

---

