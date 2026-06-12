---
title: "GF 6600 LE on Amilo laptop / Weird behavior."
date: 2010-11-07
forum: Multimedia Software
---

### Post by gewone on 2010-11-07
Hi!

I installed maverick (Ubuntu 10.10) on my fiance's laptop. It's an FSC Amilo M3438G. It has an integrated Nvidia Geforce 6600 chip. After installation, Ubuntu recommended me to do tested proprietary drivers from Nvidia themselves. I got this popup box you know. I installed them, figuring I'd get better performance in SuperTux and similar than by using default (vesa?) drivers.

Now, X works fine. However, When I press CTRL+ALT+F1 (or any other low F key for consoles) I get this freeze-looking picture on my screen, and I'm stuck. Say I do CTRL+ALT+F2..F3..F4, all the same picture. Up until I (re)visit X by doing CTRL+ALT+F8 (or whichever higher F key my X was attached to). Then I'm back into GNOME, and it looks fine.

Second time I run across this annoying image, is when I click 'Shutdown'. This ugly disorted picture is shown the ~20 seconds until the computer is shut of. Irritating.

I'm no expert, so it would be awesome if you guys could try pinpointing me to the most probably cause for this 'behavior'. Perhaps it's some known issue? I attach a DSC photograph from how the screen looks when I try to escape into console.

---

### Post by ajgreeny on 2010-11-07
Having installed the nvidia driver, did you subsequently configure it with **nvidia-cfg**, or whatever the command should be?

I don't know how much that might change things; I have an ati card so no way to even check.

---

### Post by gewone on 2010-11-07
Actually, first I had not run nvidia-xconfig.
My xorg.conf then looked like this, but with 'nvidia' and absent comment marks.

[http://pastebin.com/3ru8KVbM](http://pastebin.com/3ru8KVbM)

I just now changed nvidia->nv and commented out glx lines.
Now X works properly. However, I can't use fancy Compiz stuff ;(

Would really like to see it working.

---

### Post by gewone on 2010-11-08
Wow. Things move fast around here. One single day and thread dropped ~5 pages. Unlikely I'll have any more response w/o a little bump. So, here goes! ^^

---

