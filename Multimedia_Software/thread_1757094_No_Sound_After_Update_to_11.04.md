---
title: "No Sound After Update to 11.04"
date: 2011-05-13
forum: Multimedia Software
---

### Post by HDTimeshifter on 2011-05-13
I have no sound after upgrading to 11.04. Sound control panel and test speakers emits no sound. The new music player won't play sounds from music CDs either.

ALSA info is at:  [http://www.alsa-project.org/db/?f=595728f2ec27954eba52e0b6250d327765fb4cc7]("http://www.alsa-project.org/db/?f=595728f2ec27954eba52e0b6250d327765fb4cc7")

---

### Post by maizuddin35 on 2011-05-13
did you already check the sound preferences ?

---

### Post by HDTimeshifter on 2011-05-13
Yes, that's where I tried the Test Speakers.

---

### Post by hemebond on 2011-05-13
If you install Gnome Alsa Mixer and enable "Alernate Level to Surround Out" do you get sound from your speakers?

---

### Post by HDTimeshifter on 2011-05-14
Where is "Alernate Level to Surround Out"?  I can't find that option anywhere in the GUI or a menu.

---

### Post by lidex on 2011-05-14
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

What is your make/model/motherboard?

---

