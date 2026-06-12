---
title: "[SOLVED] Sound in Web Browser"
date: 2008-09-27
forum: Multimedia Software
---

### Post by CholericKoala on 2008-09-27
Hi, I have a Razer Barracuda Soundcard, using the CMI8788 sound driver in HH.  My sound works and plays back music in Totem, but there is no sound in web browsers (ie from Youtube).  All of my sound settings are on Analog since that is the only one that plays back sound on the test.  What should I do for sound in every application?

---

### Post by wolfen69 on 2008-09-27
try
```
sudo apt-get install libflashsupport
```

---

### Post by CholericKoala on 2008-09-27
Nothing but analog works.  System sounds dont work and neither do applications.  Only Totem works for some reason.  When I test all the drivers, only analog makes sound.

---

### Post by markbuntu on 2008-09-27
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by steveneddy on 2008-09-28
> **markbuntu said:**
> [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

that link looks promising.

---

### Post by CholericKoala on 2008-09-29
Hmm, I tried logging in as a new user, but to no avail.  I can still play Totem music and login sounds work (through the login window app, not system sounds).  I don't know why sound would only work for certain apps.  There is still no sound for firefox or system sounds.  Thanks for the link though.

---

### Post by markbuntu on 2008-09-29
SKip down to the Multiple Application Sound Sharing Section and start there.

---

### Post by CholericKoala on 2008-09-29
Well it appears that system sounds and web browser sounds are connected to my mobo sound card, as opposed to my other sound card, that I want all the sound to go to.

---

### Post by CholericKoala on 2008-09-29
Fixed, I installed all of the libraries that they wanted me to, and now I just use the "Default Soundcard" app to switch between my soundcard and the mobo sc.  Thanks

---

### Post by markbuntu on 2008-09-30
I have a guide here about setting up multiple sound cards that can help you use them more effectively, like both at once:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

