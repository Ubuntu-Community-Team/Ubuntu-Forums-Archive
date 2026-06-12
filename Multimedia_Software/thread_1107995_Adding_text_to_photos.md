---
title: "Adding text to photos"
date: 2009-03-27
forum: Multimedia Software
---

### Post by VastOne on 2009-03-27
I have over a hundred photos that I need to add a GPS text to the bottom of each or to overlay the GPS to the photo.

I tried gimp and adding text via a layer but it does not show up.

ANy suggestions as to what app to use to do this?

---

### Post by aeiah on 2009-03-27
gimp will work. text can get some getting used to. you should be able to create a new layer, check that your font size is big enough (a large photo with an 8px font will be more or less invisible) and away you go.

of course, if you have over a hundred photos then you'll want something nicer. you should check out imagemagick. how are your bash scripting skills? on the command line you can tell imagemagick to overlay specific text in a font/size/colour/location of your choice onto the photo. you could construct a script that overlays the same text onto every single photo or takes the gps data from a list you've got

---

### Post by Therion on 2009-03-27
I've not used it, but **GNU Paint** (synaptic or Add/Remove) has a simple option for that.  I know you can do it in Gimp, I just don't know how.

---

