---
title: "Brasero missing files"
date: 2010-08-27
forum: Multimedia Software
---

### Post by egalvan on 2010-08-27
Running Lucid 64bit.

when I try to copy an audio CD using brasero, I get these messages.
(see screenshots)



"ubuntu-restricted-extras"   is already installed
I can play commercial DVD's OK, 
so what is missing?

---

### Post by Jahid65 on 2010-08-28
i think you are using Kubuntu (kde) desktop. isn't there k3b(cd/dvd burner) installed? it should be installed by default. try k3b.

---

### Post by egalvan on 2010-08-30
> **Jahid65 said:**
> i think** you are using Kubuntu (kde)** desktop. 


No, this particular laptop is strictly 64-bit Lucid Gnome.
I have not installed KDE (yet)



> isn't there k3b(cd/dvd burner) installed? it should be installed by default. try k3b.

Sorry, this is not a question of finding something else...

brasero should be working on a basic install, 

the cd in question is a basic, non-DRM/DCAA/HDCP/CSS-encumbered **audio CD** disc.

so my question is, based on the error screens...
can anyone tell me
**what am i doing wrong, or what is missing on this system?**


(OK, I'm *really* bothered by the fact that WinXP has allowed me to copy this audio CD.
I want my Lucid to work as well :confused: )

---

### Post by Yellow Pasque on 2010-08-30
It sure looks like KDE to me. At any rate..
```
sudo apt-get install icedax
```

---

### Post by StratosHF on 2012-04-14
> **Temüjin said:**
> It sure looks like KDE to me. At any rate..
```
sudo apt-get install icedax
```

This worked for me (Ubuntu 10.04 LTS Lucid Lynx).

Thank you.

---

