---
title: "No audio from 10.04 using VMware Fusion"
date: 2010-08-13
forum: Multimedia Software
---

### Post by rmcellig on 2010-08-13
I am using the following:

iMac 24" running 10.6.4
VMware Fusion Version 3.1.1 (282344)

I also installed the restricted media packages.

I am using Firefox 3.6.8

What should I do to get this working?

I am trying to listen to the files on my web site. [www.mcran.com](www.mcran.com) The Radio shows tab.

---

### Post by lidex on 2010-08-14
> **rmcellig said:**
> I am using the following:

iMac 24" running 10.6.4
VMware Fusion Version 3.1.1 (282344)

I also installed the restricted media packages.

I am using Firefox 3.6.8

What should I do to get this working?

I am trying to listen to the files on my web site. [www.mcran.com](www.mcran.com) The Radio shows tab.
Is audio fine otherwise? You may want to try gecko-mediaplayer. Scroll down to section 2 here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by rmcellig on 2010-08-14
I went to the sound preferences and tested the alert sounds. They work great. But other than that, no sound. What can I check to make sure that the sound is working?

---

### Post by lidex on 2010-08-14
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by rmcellig on 2010-08-14
Thanks lidex!

I did what you described above. What do I do now?

---

### Post by lidex on 2010-08-15
Did you try adjusting your levels there? Many times they are muted by default.

---

### Post by ubaddn on 2010-11-03
. in another situation like yours
(restricted openware replacing flash player)
I found the sound strangely relative to mac's sound;
ie, if you full-blast mac's volume,
then ubuntu.firefox's volume will be normal .

---

