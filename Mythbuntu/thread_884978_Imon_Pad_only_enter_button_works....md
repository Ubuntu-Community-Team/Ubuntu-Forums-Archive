---
title: "Imon Pad: only enter button works..."
date: 2008-08-09
forum: Mythbuntu
---

### Post by Markus72 on 2008-08-09
Hi,

I just upgraded to Mythbuntu 8.04 and everything works fine - except my remote.
I have the imon pad + vfd and both is recognized and working.
Even if I use irw, all remote control buttons are producing some result (except the pad, but it's clear how to fix).

But when I try to use my remote with MythTv, only the enter button has an effect.

I already tried that generation of dynamic button mapping feature from the control center without success.

Any idea what's wrong?

Thanks in advance
Markus

---

### Post by Markus72 on 2008-08-09
I have to correct myself. It's not only the enter button. Also up and down, record, play, audio up and down work.

But that seems to be all. No escape no eject, no aspect ratio, no menu...

Do I have to make my own mapping?
I hoped there would be some button mappings... :-(

Markus

---

### Post by Markus72 on 2008-08-13
Nobody knows where to edit the mapping?

---

### Post by drlabel on 2008-08-22
how did you put it to work i can't

---

### Post by Markus72 on 2008-08-22
Hi,

you can use the mythbuntu control centre to select your remote and to create a dynamic initial button mapping.

After that change to the .lirc directory located in your user's home directory.

There you can find all the mappings in the file named 'mythtv'.

Better make a copy before changing it.

If you like to test your remote, use the command irw and press some buttons.

Still, I have some issues with the pad. When I found a rock solid solution, I'll post it.

Do you still have problems with your remote?

Markus

---

### Post by Neon Dusk on 2008-08-22
As Markus72 says the mappings are held in ~/.lirc/mythtv
Check that the names you get from irw match up to the mythtv file. i.e. if the command from irw when you press up returns 'UpArrow' then the mythtv section for Up should be something like :-
```

begin
    remote = <remote name>
    prog = mythtv
    button = UpArrow
    config = Up   
end

```

---

