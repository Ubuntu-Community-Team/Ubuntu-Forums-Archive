---
title: "Gimp Query"
date: 2009-05-13
forum: Multimedia Software
---

### Post by Samilong on 2009-05-13
I've been using The Gimp (currently 2.6) since I began using Ubuntu (5.10). Just recently, however, (since 8.04) I've hit a problem...

In Ubuntu, the two panels that open alongside the main Gimp window ('Layers/Channels/Patterns' and 'Toolbox') remain on top when an image opens. Previously, the image used to open on top. 

I have checked the various options, and the panels are NOT set to 'Always On Top'. I suspect it may have something to do with the way Gnome handles the package. If I use the Kubuntu desktop, the two panels disappear beneath the image as they should. Xubuntu, Edubuntu and Ubuntustudio all have the same fault - if it is a fault.

I'm not a fan of the Kubuntu desktop; can anyone help resolve this so that I can go back to using The Gimp in Gnome?

---

### Post by xc3RnbFO8P on 2009-05-13
> In Ubuntu, the two panels that open alongside the main Gimp window ('Layers/Channels/Patterns' and 'Toolbox') remain on top when an image opens. Previously, the image used to open on top.
I think its normal.

---

### Post by djbushido on 2009-05-13
Yeah, just been testing that myself, it's definitely normal. The only fix would be to up the resolution to try and fit the image, or get a new moniter. Or, go into the GIMP code and figure out where it decrees that the toolbox is always on top.

---

### Post by adrianx on 2009-05-13
Edit > Preferences > Window Management
Select "Normal window" in the drop-downs for "Hint for the toolbox" and "Hint for other docks".
Restart Gimp

The window behaviour should be back to "normal".

---

### Post by Samilong on 2009-05-13
> **adrianx said:**
> Edit > Preferences > Window Management
Select "Normal window" in the drop-downs for "Hint for the toolbox" and "Hint for other docks".
Restart Gimp

The window behaviour should be back to "normal".


Thanks... that's sorted the problem. You're a genius! =D> =D> =D> =D> =D>

---

