---
title: "Audacity crashes on file activity"
date: 2011-03-01
forum: Multimedia Software
---

### Post by rpeters on 2011-03-01
Using updated KDE Trinity 3.5.12 Maverick on an i386 Toshiba Satellite laptop.  Installed Audacity 1.3.12-7 from Ubuntu repository.

First I set up Audacity's preferences. Host device is ALSA (the only choice). The temp directory exists and is writable.

Case 1: Start Audacity. Try to load an mp3 file. Audacity crashes. Command-line shows:
```
~$ audacity
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653
Segmentation fault
```

Case 2: Select an mp3 file in Krusader and open with Audacity.
The file opens. I do a minor edit and try to export (as ogg, for example). Audacity crashes.

I tried to get around the problem by compiling from audacity-src-1.3.12-beta source but ran into this:
```
configure: WARNING: "Missing support in pa_mac_core.h"
configure: WARNING: "Missing support in pa_unix_oss.h"
configure: WARNING: "Missing support in portaudio.h"
configure: error: "Your version of portaudio does not include required functions"
configure: error: ./configure failed for lib-src/portmixer
```

Any suggestions?

[Edit, 4 March] Unsuccessfully tried to install an earlier versioned deb file.  Ended up using Wine to install Audacity 1.2.6 for Windows - it works and is enough for my purposes.

---

### Post by Leo Damascus on 2011-03-05
I'm having the exact same problem, but using stock Ubuntu without KDE.

---

### Post by rpeters on 2011-03-06
Maybe there's a problem with Audacity 1.3.12-7, which is a beta version (I never had that problem with earlier ones).  My plan is to wait for the next stable version and see if that fixes it.

---

### Post by Leo Damascus on 2011-03-06
Can't be that.  I rolled back Audacity and the problems persisted.  Given that the beta used to work, that should have fixed it if it was purely an Audacity problem.

---

### Post by rpeters on 2011-03-07
> **Leo Damascus said:**
> Can't be that.  I rolled back Audacity and the problems persisted.  Given that the beta used to work, that should have fixed it if it was purely an Audacity problem.

What version of Ubuntu did you run when the beta worked, and what do you run now?  I'm using 10.4.

---

### Post by Leo Damascus on 2011-03-11
I was using Ubuntu 10.10 in both cases.  And actually, I just solved my problem.  In my case at least, Audacity was having a conflict with the gnome2-globalmenu.  Once I ditched that sucker, Audacity behaved normally.
I don't think such a problem would follow into KDE, though, so in retrospect my problem is likely different from yours.  Any chance you're using a Mac-style menu in KDE?  If so, try disabling it and see if that helps.

---

### Post by rpeters on 2011-03-11
I'm using the KDE classic-style menu.  Will wait and see how it goes after upgrading to Natty.

---

### Post by knitmom on 2011-03-11
I'm having issues with audacity too!  It just started.  I used it a few days ago with no problem.  I can't close the splash screen.  When I try to do file close, it hangs up and eventually have to do a forced quit.  When I open it in other users, I can import a file, but I can't edit it.  The forced quit is consistent when I try to exit the program.

Was there a recent update in the last few days?

---

### Post by knitmom on 2011-03-11
Oh, I'm running Audacity 1.3.12-beta.  Is it possible to roll it back to the previous version?  I've now gotten the splash screen to close in my primary user, but I can't edit the sound file once it loads!!!  I use audacity at least twice a week to edit my sound files.

---

### Post by rpeters on 2011-03-13
Not the most satisfactory solution, but for the nonce you can use Wine to install Audacity 1.2.6 for Windows.  I'm hoping that the next stable version, installed under Natty (11.04), will have solved the problems.

---

