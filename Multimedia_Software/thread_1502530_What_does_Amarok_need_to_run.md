---
title: "What does Amarok need to run?"
date: 2010-06-05
forum: Multimedia Software
---

### Post by fester225 on 2010-06-05
I downloaded Amarok 2.3.0, and it says all my music files have errors. Movie Player plays all my music files just fine.

Amarok is known to require more files than what Synaptic downloads automatically, so I ran 'apt-get build-dep amarok' and got many more files. The results are still the same.

What files does Amarok require to run?

---

### Post by cybrsaylr on 2010-06-05
Try putting this code in terminal:
> sudo apt-get install libxine1-plugins

---

### Post by lidex on 2010-06-05
And/or:
```
sudo apt-get install --reinstall phonon-backend-xine libxine1-ffmpeg
```

---

### Post by fester225 on 2010-06-06
Thanks guys! Amarok now agrees the files are OK and is playing them. Unfortunately it isn't outputting any sound.

Does anybody know what files I need to get Amarok to output sound?

(You'd think all the files required to use the program would be included in the install package.) :(

---

### Post by lidex on 2010-06-06
Did you restart program?
Make sure that you have selected xine as backend in the 'System Settings->Multimedia->Backend' Tab

Could also try:
```
sudo apt-get remove phonon-backend-gstreamer
```

---

### Post by fester225 on 2010-06-06
Thanks everybody! I got it going (using GStreamer)!

Using all the sources I could find, if I were going to install Amarok again, I'd run the following in Terminal;

sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get install amarok
sudo apt-get build-dep amarok
sudo apt-get install libxine1-plugins 
sudo apt-get install --reinstall phonon-backend-xine libxine1-ffmpeg
sudo aptitude install phonon-backend-xine
sudo aptitude install phonon-backend-gstreamer
sudo apt-get install libxine1-ffmpeg gstreamer0.10-plugins-ugly
sudo apt-get install kubuntu-restricted-extras


I don't know why, but there's something about all the fonts loaded by kubuntu-restricted-extras which finally made Amarok work.

---

