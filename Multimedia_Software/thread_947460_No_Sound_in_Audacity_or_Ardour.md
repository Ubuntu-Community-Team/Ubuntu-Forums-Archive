---
title: "No Sound in Audacity or Ardour"
date: 2008-10-14
forum: Multimedia Software
---

### Post by OneRingShort on 2008-10-14
I'm looking at editing some music, so I installed Audacity on Ubuntu as I was familiar with the program from previous uses.  However, after I installed it and tried to playback what I was editing, there was no sound.  I was able to play music in my media players, but Audacity wasn't playing anything.

I checked around on the forums and saw someone mention a program called Ardour, so I installed that and found it had the same problem.

From what I understand, there is something I need to configure or download to allow audio playback?  I'm not very experienced when it comes to audio, so I'm not exactly sure what it is or what to look for.  I thought everything I needed would be downloaded with the program in Synaptic.

Any ideas what I'm missing?  Thanks in advance.

Matt

(Potentially) Useful Information:
OS: Ubuntu Hardy Heron
Audacity Version: 1.3.4-beta (from repository)
Ardour Version: 2.3

---

### Post by markbuntu on 2008-10-14
Try this guide, it has a lot of links to info you should know. Especailly about getting ardour or audacity to work. it is quite long and there are whole sections you could probably skip but get all the packages and read the sections after the packages list and the jack section for getting ardour to work. Once you see what ardour can do, expecially along with the other jack applications, you won't want to use audacity again.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by OneRingShort on 2008-10-14
I checked out that link and downloaded all the Pulseaudio and ALSA packages.  I also tried setting the Sound Preferences to all ALSA, but it removed all audio, so I put them back to Autodetect.

Judging by the look of Ardour, I think I will like it a lot more, I just gotta get it working first.

---

### Post by markbuntu on 2008-10-14
You really need to read through the guide and follow the links, especially the jack section if you want to get ardour dialed in.

---

### Post by OneRingShort on 2008-10-14
Alright, I took another look at the howto, read over the whole thing, just to make sure I wouldn't miss anything.  Unfortunately, I still can't figure what I'm doing, as I'm afraid I barely understand what he is saying.  My knowledge on sound based technology is very limited, and when I try to configure things the way they say, the menu's are either not present, or somehow things get worse (for instance, losing all my sound when changing sound preferences to ALSA).

I'm sorry if I'm making this more complicated than it needs to be.

Matt

---

### Post by markbuntu on 2008-10-15
Have you rebooted since you downloaded all those packages?
You really need to do that for them to work properly. Also, it is a good idea to not have any sound applications running, especially flash in firefox and audacity, when you make changes to the sound configuration. It may stop some changes from taking place or you may get error messages if some application is using the sound card when you try to change things around.

---

### Post by OneRingShort on 2008-10-15
I followed your suggestion about restarting, and I'm not sure if it solved the problem or not.  I was going through the (huge) list in my Sound & Video directory and tried Hydrogen, which works flawlessly (didn't test it before, so I'm not sure if its independent of the others or not).  I then tried both Audacity and Ardour and now get different errors.  Audacity now refuses to play, saying I should check my sample rate and sound output device, and Ardour just refuses to play.

---

### Post by markbuntu on 2008-10-15
Did you start jack before you started Ardour?

There is a link to info about getting Audacity working in my guide.

---

### Post by OneRingShort on 2008-10-15
No, I didn't have Jack running.

I tried running the JACK Control application, but every time I try to start it, it doesn't respond, and I have to force quit it.  I take it this is an important app and this will be a problem? In which case I take it I should just reinstall it?

From what I gather from your guide, I need to then configure it, and run it before I do any editing, and close it before I run regular media players?

---

### Post by markbuntu on 2008-10-15
Yes, jack is the key to using hydrogen and rosegarden and ardour and a bunch of other very high quality recording applications. You should really read through my guide a little more carefully and look in the links. 

Then you can get everything working all the time with the sole exception of Audacity which has its own problems with sharing the sound.

---

### Post by OneRingShort on 2008-10-15
I'm trying to configure Jack according to two of the links you listed, but every time Jack Control starts up, it immediately locks up.  I've tried reinstalling it, as well as removing it completely, and installing again.  However, it still locks up.  I'm not sure of how to get it running to a point where I can try to configure it.

I tried running it from the terminal, but all I got was:
```
Warning: no locale found: /usr/share/locale/qjackctl_en_US.qm
```

---

### Post by markbuntu on 2008-10-15
You need to start jack from jack control which is where you need to set jack up from. It is in Applications/Sound and Video.

---

### Post by OneRingShort on 2008-10-15
Thats what I initially tried, but every time it just locks up.  I can't figure out how to get it running.

[EDIT]: I restarted the computer, and that seemed to fix that problem.  I'll let you know how things turn out.

---

