---
title: "Multimedia Keyboard With Amarok"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by SRGT. DeGreene on 2008-03-01
I cant seem to make my Multimedia keys on my keyboard work in Amarok, but they work in Rhythm Box But I don't like Rhythm Box so that's kinda useless. I need help.

---

### Post by logos34 on 2008-03-02
Settings>configure shortcuts

or >global shortcuts

one of thw two should work

---

### Post by rainwalker on 2008-03-02
Try installing the KeyTouch app. I've been using it since Edgy and it's great! It's not in the repos, though, but do a quick google search for it and you'll be set

---

### Post by SRGT. DeGreene on 2008-03-02
neither of those worked but if this helps at all i have a **compaq presario sk-2700** keyboard

---

### Post by rainwalker on 2008-03-03
KeyTouch didn't work? You don't have to choose exactly the same keyboard, just one close to it.

---

### Post by SRGT. DeGreene on 2008-03-03
yea i picked this one:**SK-2800C** but it was a few models after mine. but it still didn't work

---

### Post by bdoe on 2008-04-27
I'm in the same situation. I have an HP Presario dv9830us laptop running Hardy, and I can't get Amarok to recognize the multimedia keys. Ubuntu recognizes them, and every multimedia application I've tried appear to use Ubuntu's keyboard shortcut settings, but Amarok seems to march to the beat of its own drummer. It uses its own shortcut mapping, ignoring Ubuntu's, and it won't recognize nonstandard keys.

Edit: I found a solution. Download [this](http://linux.softpedia.com/get/Multimedia/Audio/amaroK-Scripts/Gnome-Multimedia-Keys-28328.shtml), unarchive it, and place the resulting folder somewhere, like in your home directory. /usr/shared/ might work as well. Run the python script, and Amarok will use your Gnome keyboard shortcuts properly. Add it to your startup list under "Sessions" for it to run each time you log in.

---

