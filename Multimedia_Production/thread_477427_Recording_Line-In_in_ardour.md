---
title: "Recording Line-In in ardour?"
date: 2007-06-18
forum: Multimedia Production
---

### Post by linuxmann on 2007-06-18
Is there any way i can record things using my sound card line in with ardour? It seems ardour is not reconizing my line in port. i tried many things to make ardour record from my line in port, but none of them worked.  My Sound Card mixer says i have an "intel 82801AA-ICH (alsa mixer) type sound card. Help? if you need anymore details i will try to provide you with some.

---

### Post by gashcrumb on 2007-06-18
If I remember correctly this card defaults to recording from mic in.  To change it (this may not be accurate as this is from memory) you right-click on the gnome mixer applet (the speaker icon), select "Open Volume Control", then when the mixer appears, click on Edit/Preferences and check everything in the "Select tracks to be visibile" window.  Click "Close" and you should now have a Recording tab, click on that and likely you'll see that mic-in is selected, check the box under Line in and you should be all set.

---

### Post by Rexbron! on 2007-06-18
Actually, if you are using ardour then you have to use JACK. If you have qjackcontrol installed, click on the patchbay button and connect line-in to one of the buses (I think that is what they are called) in a running Ardour session.

---

