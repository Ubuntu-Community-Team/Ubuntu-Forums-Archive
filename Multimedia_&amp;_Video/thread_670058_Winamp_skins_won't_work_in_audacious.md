---
title: "Winamp skins won't work in audacious"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by chocolatetoothpaste on 2008-01-17
For whatever reason, audacious won't load my winamp skins.  I downloaded them, move then to ~/.local/share/audacious/Skins, and I can see it listed in the skin browser, but when I click on it, the skin stays on the default.  This seems to be a random issue, since it worked before I reinstalled ubuntu.  But now, on a fresh new install, it doesn't work.  Wondering if anyone else has this issue, and if anyone's figured out a solution.  I am running audacious 1.4.5

---

### Post by notwen on 2008-01-17
Seems like I'm running 1.4.5 and I'm using skins w/o issue.  I'll have to double check when I get home and post back.  Have you tried multiple skins?  Are you using the .wsz archives or simply folders by chance?

---

### Post by disturbedite on 2008-01-17
i'm running audacious 1.4.5 and i can't even get it to "see" my skins in the skin browser/selector.  i have them in the proper directory...
it was this way with 1.4.4 too.

---

### Post by chocolatetoothpaste on 2008-01-17
> **notwen said:**
> Seems like I'm running 1.4.5 and I'm using skins w/o issue.  I'll have to double check when I get home and post back.  Have you tried multiple skins?  Are you using the .wsz archives or simply folders by chance?

I'm using .wsz, and yes, I've tried multiple skins.  I have a few ideas I'm going to try, I'll report what happens.  If anyone else has some ideas, please share...

---

### Post by disturbed1 on 2008-01-17
Not all skins will work. They have to be 2.x version or classic version. The skins for AOLamp usually don't work.

Choose a category and change the settings to display classic skins.

---

### Post by eleneithel on 2008-04-21
I realiza this thread is really, REALLY old, but I had this very same issue just now, and I thought this could be usefull to somebody else: After downloading winamp classic skins, change the extention to .zip instead of .wsz, then open terminal, type sudo nautilus, and navigate to usr/shared/audacious/skins and copy files.
Hope I'll save you some time =)

---

### Post by rangita on 2008-05-14
I'm having the original poster's problem on Hardy with Audacious 1.5.0: skins show up in the list, but when I click them, nothing changes.  It stays on whatever skin was previously selected.

This is separate from the other problem that was solved in this thread: making the skins show up in the list.  My skins show up in the list just fine, they just don't get applied.

I'm using a very old Winamp 2.x skin that works on XMMS.  I've tried WSZ and plain folders, forcing lower-case filenames, and converting the images from BMP to PNG.  No dice.

EDIT: Nevermind -- I was missing one file ("playpaus.png", the little symbol to the left of the time) that XMMS/Winamp could apparently get along without.  I copied one from the Refugee scheme and it works fine.

---

