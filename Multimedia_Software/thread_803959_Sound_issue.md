---
title: "Sound issue"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Ohwii on 2008-05-22
Hi guys,

I am using a t60 and the sound works but only in one application. Either in firefox flash videos or in exaile. i can not leave firefox open and then open exaile to listen to music. 

could anyone help please.

cheesrs 

oh wii

---

### Post by Allen111 on 2008-05-22
Same Problem.. 

If you have VLC I found a Fix for it..

Settings>Preferences>Click on Advance Options (On the right bottom corner)>Audio>Output Modules>Switch "Defualt" to Alsa



This doesn't fix the Issue with other Applications..

---

### Post by Ohwii on 2008-05-22
thanks for the quick fix everything bit helps 

just waiting for an exaile solution I guesse i just have to use alsa again.

cheers oh wii

---

### Post by Yellow Pasque on 2008-05-22
You need some sort of mixer. Pulseaudio should be installed by default on 8.04. Try going to System -> Preferences -> Sound and selecting PulseAudio for your outputs.

And if you get tired of ALSA, there's always OSS4..

---

### Post by Allen111 on 2008-05-27
Found fix if you still needed

> 
    sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
    sudo mkdir -p /tmp/.esd/
    sudo touch /tmp/.esd/socket 

---

### Post by Akiva on 2008-05-27
I'm having relatively the same problem. If I have Rhythmbox open, sounds from flash videos (such as YouTube vids), or sounds from any other application (such as Pidgin, etc.) won't play. 

I've tried every fix mentioned here, but nothing's working. Any other suggestions?

---

### Post by Akiva on 2008-05-27
Still having the same problems, it's getting rather frustrating now. Could this be a driver error or something? Does anybody have any suggestions? I'm a Linux newbie so I'm pretty lost on what to do right now heh.

---

