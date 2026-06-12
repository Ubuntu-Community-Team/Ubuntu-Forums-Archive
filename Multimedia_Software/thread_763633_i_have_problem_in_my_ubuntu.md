---
title: "i have problem in my ubuntu"
date: 2008-04-23
forum: Multimedia Software
---

### Post by elonlon on 2008-04-23
hello
i had a problem but my ubuntu installation was successful but i cannot use X since my monitor will only take a specific resolution, so i can only boot in rescue mode.
what can i do?

and thanks...:):):)

---

### Post by tomd123 on 2008-04-23
In safe mode, go to system, preferences, screen resolution. Pick your resolution/refresh rate and reboot.

---

### Post by elonlon on 2008-04-23
how i can know how much Hz i have?

---

### Post by pietjanjaap on 2008-04-23
Start in recovery mode then in terminal:
sudo dpkg-reconfigure xserver-xorg 

Choose vesa driver
and
the size of the screen you want to use.(disable all the others)
and
 save xorg file


Now the screen is in default, and you can boot.
Now you can start again and install the driver of your videocard, or envy(automatic).

---

### Post by elonlon on 2008-04-23
form start lets see if i right i open my computer and select Ubuntu
after this i press Esc the i select recovery mode
after this i see blue screen there i select fix xorg
then i write sudo dpkg-reconfigure xserver-xorg
after this i choose vest driver
then i write the size screen i want
then i do save xorg file

thats is right?

---

### Post by elonlon on 2008-04-23
this what i need to do?...

---

### Post by elonlon on 2008-04-23
ahh i mean that i enter root not xorg

---

### Post by elonlon on 2008-04-24
someone please help me

---

