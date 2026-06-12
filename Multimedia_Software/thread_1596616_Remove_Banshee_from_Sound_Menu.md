---
title: "Remove Banshee from Sound Menu"
date: 2010-10-14
forum: Multimedia Software
---

### Post by sojyujai on 2010-10-14
I was playing with Banshee and installed the banshee-extension-soundmenu package to get the Banshee control in the Indicator Applet Sound Menu. 
 
I had so many problems with Banshee crashing and using up my system resources that I decided to stop using it.  I deselected the Sound Menu option from Banshee's Preferences>Extensions, then I uninstalled the banshee-extension-soundmenu package. 

However after this the Sound Menu is still showing the Banshee control.  Is there a way to get rid of it?

Thanks

---

### Post by sojyujai on 2010-10-14
Well, completely uninstalling Banshee seems to have done the trick...

---

### Post by RSparker on 2010-10-17
For the record, the entries of each individual player on the sound menu are stored in ~/.cache/indicators/sound/familiar-players-db.keyfile

You can either delete it and all the entries will be gone or selectively edit each entry.

---

### Post by sojyujai on 2010-10-17
Thanks, that's where it is.  It will come in useful when I try again to get Banshee working.

---

