---
title: "removing amarok"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by rygar on 2007-05-07
I installed Ubuntu, then later installed KDE to try it out, which installed Amarok with it.

When I try to remove Amarok, it tells me that kubuntu-desktop needs to be uninstalled as well.

Why can't I uninstall Amarok without uninstalling KDE?

---

### Post by dunklegend on 2007-05-07
How are you trying to uninstall it?

---

### Post by rygar on 2007-05-07
if i try via add/remove programs, it tells me to use synaptic since other programs depend on it

if i try via synaptic, it tells me other programs depend on this....  so i always click no, because i dont really want to uninstall kde, even though i use gnome most of the time.

in fact, the same is true for most KDE applications--i run into the same problem when trying to remove kaffeine.

---

### Post by aysiu on 2007-05-07
*kubuntu-desktop* isn't a real package.

It's just a pointer to all the default programs in a Kubuntu installation.

Once you remove one of the default programs, the pointer no longer has any meaning.

---

### Post by rygar on 2007-05-07
so are you saying i can safely remove kubuntu-desktop as well?

one last question--i don't use adept, because i don't use kde that often.  but adept seems to make a distinction between "purge" and "remove", a distinction not made in gnome's package manager, at least i dont think.  what's the difference?

---

### Post by aysiu on 2007-05-07
I don't know the answer to your second question, but it is safe to remove *kubuntu-desktop*.

Warning: if you want a better guarantee that your upgrade to the next version of Kubuntu is smooth, you should keep *kubuntu-desktop* installed. Read more [here](https://help.ubuntu.com/community/CommonQuestions#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812).

---

### Post by rygar on 2007-05-07
this is dumb!  i don't want to run into problems updating KDE in the future, but i do want to uninstall amarok!

---

