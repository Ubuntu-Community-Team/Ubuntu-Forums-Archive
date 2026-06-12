---
title: "pulseaudio shows output, but no sound from speakers"
date: 2008-06-20
forum: Multimedia Software
---

### Post by darkmessenger88 on 2008-06-20
hey everybody, 

I've read the forums for a while, trying to find a solution to this problem, but I think that it is different from other peoples', so I'll post it here.

I have pulseaudio installed, running ubuntu 8.04 installed via wubi. All of my programs route their audio to pulseaudio, which then sends it to my speakers. I know this setup works, because I can send that to a pulseaudio server running on another computer, and all of the sound comes out there. But when I tell the server to output to my laptop speakers (I have a gateway MA7), I don't hear anything with or without headphones plugged in. In pulseaudio, I can view the sound output levels, and when I'm playing a song, the levels bounce up and down accordingly. When i adjust the volume on the keyboard, the levels change. But I don't actually hear anything.

I believe that the problem lies in my expanding the size of my /usr folder. the wubi tool didn't actually copy any files when I ran it, so I just did 
cp -R usr.backup/ usr/
I had several problems because the guid bit was no longer set on files. I couldn't use sudo, or other things. I fixed the permissions on them, and i removed the backup. 

Is it possible that a file in /usr with incorrect permissions/bits set could cause me to have no sound come out of my speakers?

Any ideas?

thanks in advance,

darkmessenger88

p.s. I know the speakers still work because I can boot up a live CD and hear sound without touching anything.

---

### Post by markbuntu on 2008-06-20
Pretty much all your user configs are in usr/share. padevchooser is the pulseaudio  device chooser. It is in usr/share.

---

### Post by Diffusr on 2008-09-20
I have the exact same issue. Pulseaudio acknowleges ati soundcards, shows output levels, displays applications running playback ...but no sound from the speakers. Does anyone have a clue?

---

### Post by markbuntu on 2008-09-20
You can Open the PulseAudio volume control and see if the audio streams from your applications are playing to the proper output device. You can look in my guide for further troubleshooting advice:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Diffusr on 2008-09-21
This was the fix for me:
sudo gedit /etc/asound.conf and comment out or delete the code that doesn't relate to pulseaudio.This uncorrupts the file, save and close. Right click on speaker icon in system tray and open volume control. Under preferences ensure PCM track is visible and raise its level/unmute - hey presto sound works!
Make sure firefox is using flash10 plugin, disable flash9 if it's still there and flash (youtube etc) works great with pulseaudio.

---

