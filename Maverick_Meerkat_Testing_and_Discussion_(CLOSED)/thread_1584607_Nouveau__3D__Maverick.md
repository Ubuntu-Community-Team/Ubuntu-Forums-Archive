---
title: "Nouveau / 3D / Maverick"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dominikvz on 2010-09-29
Hello, 

anyone know how to install and setup 3D support for nouveau drivers
on Maverick 10.10 ?

I want run compiz with nouveau, it is not working without 3D support ...

Please help ...

---

### Post by cariboo on 2010-09-29
All you should have to do is install libgl1-mesa-dri-experimaental, which is in the repositories, to get 3D with the nouveau drivers.

---

### Post by oasick on 2010-09-29
Thank you! now i have 3D acceleration and compiz with my nvidia FX 5900GT :guitar:

---

### Post by lancest on 2010-09-30
Yea! Finally able to dump the Nvidia driver and get Compiz effects in Ubuntu.

Saw it in Fedora 13 and wanted it bad. 

Now I'm free of the Nvidia related "title bar missing at boot issue" in the last few releases -that I was never able to finally solve.

---

### Post by Slug71 on 2010-09-30
I must have missed something. I thought 3D support with Nouveau was to be in Maverick by default?

---

### Post by liorwohl on 2010-09-30
is this libgl1-mesa-dri-experimental good for playing nexuiz? why using nvidia drivers and not this? (performance problems maybe?)
is it worth trying?

---

### Post by davideotape on 2010-09-30
> **Slug71 said:**
> I must have missed something. I thought 3D support with Nouveau was to be in Maverick by default?

The 'experimental' bit may explain why it isn't :)

---

### Post by dino99 on 2010-09-30
> **liorwohl said:**
> is this libgl1-mesa-dri-experimental good for playing nexuiz? why using nvidia drivers and not this? (performance problems maybe?)
is it worth trying?

you will get the answer if you try it on your system :P

---

### Post by dominikvz on 2010-09-30
Thank You mr. [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104"), You are King :-)
It is working !!!

---

### Post by Half-Left on 2010-09-30
> **liorwohl said:**
> is this libgl1-mesa-dri-experimental good for playing nexuiz? why using nvidia drivers and not this? (performance problems maybe?)
is it worth trying?

It's a pretty taxing game really on top settings but I had no problem playing Openarea on full settings.

---

### Post by lancest on 2010-09-30
Noticed Compiz scaling is smoother with Nouveau.
Gaming not important to me or I'd use Nvidia.

---

### Post by donniezazen on 2010-10-01
> **cariboo907 said:**
> All you should have to do is install libgl1-mesa-dri-experimaental, which is in the repositories, to get 3D with the nouveau drivers.

Thanks. I am now using desktop effects with nouveau. Is this being actively pursued or stalled as of right now?

---

### Post by Half-Left on 2010-10-01
This experimental driver really has come along nicely and Compiz is a lot smoother than what it was. I don't have the horrid performance issue with subpixel font rendering as well.

I'll keep this enabled in my Maverick install, since I use Lucid for main stuff and games.

---

### Post by donniezazen on 2010-10-07
I just installed Gnome-shell. Should i remove compiz and the nouvea 3D driver? Does it matter?

---

### Post by cariboo on 2010-10-07
You can't use compiz with gnome shell, but you do need composting to use it. Keep the nouveau drivers if everything works well for you.

---

### Post by donniezazen on 2010-10-07
Thanks. Everything is working smoothly as of now.

---

