---
title: "Audacious broken"
date: 2008-05-27
forum: Multimedia Software
---

### Post by q_mar on 2008-05-27
I've been trying to get my sound card to work properly and was playing with the mixers under the sound menus.

Now th problem i have is that Audacious will not play. It will open up fine and open a file, but when you hit play nothing happens. All other players work as do the gnome sounds as well as all the tests under the sound menu.

I have tried:
Trying all the different mixers in both audacious and the sound menu
Reinstalling audacious
Reinstalling audacious with --purge in the command
Removing all the related packages in synaptic and reinstalling them.

i've run 
aplay -l
and
lspci -v

Everything seems happy there i get my sound card listed.

I am now officially out of ideas can anyone help?

Thanks in advance

---

### Post by ubuntu-freak on 2008-05-27
Have you tried Audacious in another user account? Create one if yours is the only account.
 
Nathan

---

### Post by q_mar on 2008-05-27
Ok, audacious works perfectly in my new user account "bob".

do we know why this happens and how to fix my other account? or should i just set up a new user account?

Thank you!

---

### Post by q_mar on 2008-05-27
Got her fixed.

Took the audaciouis directory under
"/usr/bob/.config/audacious"
and copied it to the same location in my account overwriting the previous files.

thanks again

John

---

