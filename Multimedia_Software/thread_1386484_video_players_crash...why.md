---
title: "video players crash...why?????"
date: 2010-01-20
forum: Multimedia Software
---

### Post by unknown23 on 2010-01-20
i can not play any videos with any player in karmic

but, i need to!

what do i do?

---

### Post by Revolutionary101 on 2010-01-20
Did you try VLC media player? Plus I need more specifics than "i can not play any videos with any player in karmic". Do any error messages come up?

---

### Post by unknown23 on 2010-01-20
i tried mplayer, movie player, banshee, moovida media center vlc ....none of them work

as soon as i attempt to oad the video, the player crashes

is there something i can put into the terminal that will give you a clear idea what is happening?

---

### Post by Revolutionary101 on 2010-01-20
Type this into terminal

```
vlc
```

It will run vlc for you. When vlc opens try and play a video, but keep the terminal window open. Then terminal should display a bunch of information and it might explain why you are experiencing this. Copy and paste that information when it crashes.

---

### Post by unknown23 on 2010-01-20
shadowcast@shadowcast:~$ sudo apt-key add
gpg: can't open `': No such file or directory
shadowcast@shadowcast:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x9b5d140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x9e68420] pulse audio output: No. of Audio Channels: 2
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  105
  Current serial number in output stream:  106

---

### Post by Revolutionary101 on 2010-01-20
Open VLC and go to Tools>Preferences and click on the Video section. Click on the output listbox and change it to either Default or XVideo extension output. Is it set on X11 video output right now?

---

### Post by unknown23 on 2010-01-20
thank you very much

changing the setting was the key

havent tried any of the other player but vlc works now

---

### Post by Revolutionary101 on 2010-01-20
Glad I could help. Don't forget to mark the thread as solved. To mark it as solved go to "Thread Tools" and click "Mark this thread as solved".

---

