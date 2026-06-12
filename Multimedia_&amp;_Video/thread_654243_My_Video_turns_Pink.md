---
title: "My Video turns Pink"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by 89vision on 2007-12-30
Occasionally while watching video on my laptop the video inside vlc or totem will suddenly turn pink and only the sound works.  It is quite annoying as I have to reboot in order for it to work again.  I am running Gutsy and I am suspecting it has something to do with compiz because this never happened with Feisty.  I have attached a picture of what it looks like.  Anyone else had this problem?

---

### Post by fart_flower on 2007-12-31
Sounds like you're using an nVidia graphics card.  This is a known issue which the latest nVidia drivers supposedly fix.  However, these drivers are not in the Ubuntu repositories.

A quick fix is to press ctrl+alt+f1 to get to a full screen terminal, then return back to the desktop with ctrl+alt+f7.  However, for me at least, the above only works properly when desktops effects are turned off.  If I try it with effects on, I only get a (working) mouse pointer on a black screen when returning to the desktop.

---

### Post by 89vision on 2007-12-31
Thanks for the reply!  Hopefully these new drivers are added to the repos soon, im tempted to go d/l the new one and install it manually.

---

### Post by chewearn on 2007-12-31
> **89vision said:**
> Thanks for the reply!  Hopefully these new drivers are added to the repos soon, im tempted to go d/l the new one and install it manually.

Rather than wrestling with manual nvidia install, you might want to try [envy]("http://albertomilone.com/nvidia_scripts1.html")

---

