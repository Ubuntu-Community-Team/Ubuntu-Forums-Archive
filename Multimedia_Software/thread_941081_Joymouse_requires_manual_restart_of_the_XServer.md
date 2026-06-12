---
title: "Joymouse requires manual restart of the XServer"
date: 2008-10-07
forum: Multimedia Software
---

### Post by mightyape on 2008-10-07
Hi there!
I am currently setting up a box for my grandfather. As he is a well advanced in years (he is 87 years old), he has to use a joystick instead of the mouse, because its easier to handle for him. I managed to enable joystick control by the use of the joymouse package, which actually works nicely. There is only one problem...

I enabled automatic login into his gnome desktop, because its easier for him, if he is not prompted for a password or anything. I also added the launch of joymouse into the sudoers file, so I can start it automatically. I not know why, but it does not work, unless I restart the xserver. I am prompted for the password and afterwards, when I restart joymouse it works perfectly. I guess it has something to do with the automated login, but I can not figure it out how to solve this little problem. I am very thankful for advice in advance!

Best regards from Innsbruck,
Stefan

---

### Post by mightyape on 2008-10-15
*push*
Anyone? I kept dealing with the problem, but could not find any suggestions :-(

Thanks a lot!

Stefan

---

### Post by gcbzzzz on 2009-01-15
where did you find this package? it's not on my repositories.

You *might* have better luck with the joystick Xorg module.

it's bugged as hell. Here, it restart Xorg everytime I move any stick (only the buttons are safe). But it might work for you.



apt-get install xserver-xorg-input-joystick
man joystick

good luck.

---

