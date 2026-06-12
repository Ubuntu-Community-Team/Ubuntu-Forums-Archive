---
title: "blender3D vs GNOME: overlaping"
date: 2008-02-17
forum: Multimedia Production
---

### Post by joaoramos on 2008-02-17
hey folks,

everytime I run blender3D on my ubuntu 7.10, GNOME overlaps the desktop over it (I guess).
if I want to perfectly run blender3d, I have to shut down compiz fusion but, well, it sucks.
I'm portuguese, so I'm sorry for my bad english. any help?

---

### Post by leg on 2008-02-17
Not sure what you mean I have blender running with compiz and it all works fine. So if it works here I don't see why you shouldn't get it working ok. What do you mean by overlaps the desktop?

---

### Post by joaoramos on 2008-02-17
well, it looks like the desktop is always 'refreshing' over blender interface (bad english, I know) - I run blender and, 1second later, its interface is overlapped by my desktop, so I have to move my mouse in order to see blenders interface again, as if my ubuntu desktop was in a higher layer and blender was behind it. sorry, I really suck in english lang.

---

### Post by KoRnholio on 2008-02-17
I second this.  What happens is that if you have a bottom panel, Blender will think it has that space to use, when it doesn't.  Most apps end right above the panel, but Blender doesn't.  Thus, the bottom of Blender is always cut off unless you take off your bottom panel.

---

### Post by joaoramos on 2008-02-17
I have no bottom panels. I shut down awn and the default ubuntu bottom panel but both windowed and fullscreen blenders still not run correctly.

edit: for the record, I'm running ubuntu on a ati radeon x1450 (envy drivers).

---

### Post by crush304 on 2008-02-17
> **joaoramos said:**
> I have no bottom panels. I shut down awn and the default ubuntu bottom panel but both windowed and fullscreen blenders still not run correctly.

edit: for the record, I'm running ubuntu on a** ati radeon x1450** (envy drivers).

3d apps are not working with the ati drivers with compiz enabled.

---

### Post by joaoramos on 2008-02-18
right :(
still, is there any ways to run blender with ati without shutting down compiz?

---

### Post by thedaemon on 2008-03-03
There is a problem with blender's menu items. It is set as "blender -w" for both fullscreen and windowed mode. it should be "blender -p 10 10 1280 1024" or which every your resolution is. the 10 10 part tells it to start the window 10 pixels down and right and draw it 1280 x1024. So fix this for whatever resolution you need.

---

### Post by eye208 on 2008-03-03
> **thedaemon said:**
> There is a problem with blender's menu items.
This has been fixed in Gutsy.

---

### Post by caricc on 2008-03-03
Did you load blender from Blender's website or from the repositories in Ubuntu? If from the website try removing it and use the version, 2.45, from the repositories. Then use the window icon and not full screen. It loads both. I am using it with 7.10 and I have no problems with it at all.

---

### Post by thedaemon on 2008-03-03
2.45 is in the backports, 2.44 is in the default repositories. eye208, not for me.

---

### Post by eye208 on 2008-03-04
> **thedaemon said:**
> eye208, not for me.
Did you do a clean install of Gutsy or an upgrade from Feisty?

---

