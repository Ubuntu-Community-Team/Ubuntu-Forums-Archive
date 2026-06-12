---
title: "Integrated Graphics Question (please help)"
date: 2008-10-11
forum: Multimedia Software
---

### Post by d.justins on 2008-10-11
I'm not sure if people don't know, or just decide not to answer, but i have read many threads concerning this issue and just have to bring it up again. I have an intel integrated card that is supposed to have 256M of memory, but it seems Ubuntu only allocates 8M. It is on a laptop, so i don't have a choice about my video card. I don't have an option in my BIOS to adjust this. I tried the option i xorg.conf, but it did nothing. Using ubuntu is awesome... but when you go to play a movie while hanging out with your friends and it doesn't work, you look like a retard. (and then they make fun of you for not running windows.) 
So, for the sake of Ubuntu's reputation and mine, can someone please help me find a solution?

---

### Post by madmetal on 2008-10-11
which chipset does your card have and also does it have 256mb of dedicated memory or shared? do you have drivers installed?

---

### Post by d.justins on 2008-10-11
#  Graphics Processor / Vendor   Intel GMA X3100 Dynamic Video Memory Technology 4.0
# Video Memory 358 MB
# Total Available Graphics Memory 358 MB 

I was wrong about the memory before, my mistake. 

I only have what installed when in installed Ubuntu (hardy). I couldn't find any other drivers. Thanks for such a quick reply

---

### Post by madmetal on 2008-10-11
what's your problem with the card? 
try to search the forums for possible solutions and drivers..
about movie playback , do you have multimedia codecs installed?

---

### Post by d.justins on 2008-10-11
I get an

> X11 error: BadAlloc (insufficient resources for operation)1.1% 0 0 

error when i try to play the videos. Yes i have all the necessary codecs installed. 

I tried playing with mplayer, totem, and VLC player. The programs start, then quickly crash. When i run mplayer from terminal, the above error fills up the terminal, yet i can hear the audio. 

i tried installing xserver-xorg-video-intel and it says i'm up-to-date.

---

### Post by madmetal on 2008-10-11
here is a thread with the same problem and a possible solution..
[http://ubuntuforums.org/showthread.php?t=680485](http://ubuntuforums.org/showthread.php?t=680485)

do you have 3D effects enabled?

---

### Post by d.justins on 2008-10-11
Ok, so i found that there are issues running Compiz with the i965 and playing a video. I went into my appearance settings, and for some reason, no radio button was selected. I'm not sure why that was, but i clicked normal. That allows Avant Window Manager (which i prefer) to work, but no video. I clicked None visual effects, disables AWN, but videos work fine. 

I found this thread

[http://ubuntuforums.org/showthread.php?t=684770](http://ubuntuforums.org/showthread.php?t=684770)

which lead me to even think of that. That thread is old and i'm wondering if there is a fix to it yet. 

It will be annoying to switch the settings everytime i want to watch a video, but i can manage. Is there any way i can automate this?

---

