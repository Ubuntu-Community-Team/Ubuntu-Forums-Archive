---
title: "Reverting back from Mythbuntu to Ubuntu themes"
date: 2009-08-09
forum: Mythbuntu
---

### Post by hundred1906 on 2009-08-09
I installed Mythbuntu onto Ubuntu. It all works fine except that I don't like the Mythbuntu desktop themes and want to get these back to the original (Jaunty Browns). Including the system start and close screens.

By computer is used both for MythTV and for normal desktop work.

Themes for additional users are a particular issue as the menu and layouts are quite different to Ubuntu.

Does anyone know or can help on how to revert without losing the MythTV installation setup or re-building the system from scratch?

This is a second post. Hopefully in the right forum this time.

---

### Post by NTolerance on 2009-08-09
For the desktop theme, just go to System->Preferences->Appearance and revert to the standard Ubuntu Human theme.  

The easiest way to revert the boot splash screen to default is to install StartUp-Manager:

```
sudo aptitude install startupmanager
```

To use it, go to System->Administration->StartUp-Manager.  You can change the Usplash theme from the "Appearance" tab.

---

### Post by misswham on 2009-08-09
All of a sudden I have mythbuntu.  I havent a clue what it is.  Can someone tell me how this got on my pc and what in the heck is it?

---

### Post by superm1 on 2009-08-11
So from the mythbuntu control centre, you can remove all the artwork and theming you don't like.

---

### Post by NTolerance on 2009-08-11
> **misswham said:**
> All of a sudden I have mythbuntu.  I havent a clue what it is.  Can someone tell me how this got on my pc and what in the heck is it?

We you recently installing software via Synaptic?  It's possible that Mythbuntu was selected by accident.

---

### Post by hundred1906 on 2009-08-13
> **NTolerance said:**
> For the desktop theme, just go to System->Preferences->Appearance and revert to the standard Ubuntu Human theme.  

The easiest way to revert the boot splash screen to default is to install StartUp-Manager:

```
sudo aptitude install startupmanager
```

To use it, go to System->Administration->StartUp-Manager.  You can change the Usplash theme from the "Appearance" tab.
Got that, thank you very much.

---

