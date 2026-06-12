---
title: "Application to play system sounds"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by kriukov on 2008-02-28
I use VLC as my default player. However, it looks like it does not have a CLI. In one of the applications (psi) I would like to play the sound events. Entering "vlc" in the "player" line (and saving it) makes VLC start a new window every time a sound event is played! In Ubuntu Sound configuration window sounds can be played without any extra player windows popping up. I tried to use "top" to find out which process is started when it plays, but it just says "gnome-sound-pro" is running (it can't even be executed from command line). I tried different things with vlc, like 'vlc "%s" &'... nothing helps. Should I use a console player or is there a hidden Gnome player that does that?

---

### Post by erginemr on 2008-02-29
There is one CLI sound player coming with "sox".
To install:
```
sudo aptitude install sox
```
To play a sound file:
```
play /usr/share/sounds/phone.wav
```

Another CLI sound player is "moc".
To install:
```
sudo aptitude install moc
```
To play a sound file:
```
mocp -p /usr/share/sounds/phone.wav
```

Both "sox" and "moc" can play WAV, OGG, MP3, etc.

---

### Post by kriukov on 2008-03-01
Thank you! I had moc but it didn't work for me. However, sox did the job.

---

### Post by adhuvi on 2008-05-16
I had no problems using sox to play ogg files. i recently updated to hardy, i installed sox again and when i type 

$ play ya.ogg

i get 

play soxio: Failed reading `ya.ogg': unknown file type `auto'

even though the file is in the same folder i'm working. does anyone have an idea of what can be happening?

---

### Post by erginemr on 2008-05-16
I don't know what the problem is, and this will sound like a cheesy response, but I suggest you to try moc as well. It has a very nice GUI (an ncurses interface I guess) to play music for a console application.

---

### Post by adhuvi on 2008-05-16
I already solved this problem. Turns out that when I installed sox using apt-get install i still needed some libraries. I found out using adept, then i installed: libsox-fmt-all, which installs all available libraries. Then i only had to restart the konsole (i'm not sure why, but it didn't work if i didn't) and everything was back to normal!

---

### Post by kerry_s on 2008-05-16
you might also have aplay, it's part of alsa, use to use it for startup sound on a minimal install. use> locate aplay
read the> man aplay
for info

---

### Post by adhuvi on 2008-05-16
Yes, i looked for aplay and i have it, but when i do: 

$ aplay ya.ogg 

a horrible noise comes out, i don't know why. I would try to find out what is wrong if sox wasn't working properly already ;)

---

### Post by kerry_s on 2008-05-16
> **adhuvi said:**
> Yes, i looked for aplay and i have it, but when i do: 

$ aplay ya.ogg 

a horrible noise comes out, i don't know why. I would try to find out what is wrong if sox wasn't working properly already ;)

i think i see the problem, it doesn't do oog.
```
-t, --file-type TYPE    file type (voc, wav, raw or au)
```

ohh well

---

### Post by adhuvi on 2008-05-16
[QUOTE=kerry_s;4976092]i think i see the problem, it doesn't do oog.

it doesn't do ogg either :D thanks!

---

