---
title: "Sound from only one app"
date: 2006-01-21
forum: Multimedia &amp; Video
---

### Post by Aybara on 2006-01-21
J just get sound from one application at a time. If amarok uses my sound card I can't get sound from anywhere else...

In the multimedia systems selector I have ALSA set on both sink and source, though I really don't know why...

Any ideas?

---

### Post by Aybara on 2006-01-21
Just thought I'd add something here. I also installed mplayer following instructions on a webpage. The last step I did was:


sudo gedit /etc/mplayer/mplayer.conf
    * Find this line 
...
vo=x11,         # To specify default video driver (see -vo help for
...
    * Replace with the following line 
vo=xv,         # To specify default video driver (see -vo help for

Does this mean I have to have xv set at input in the multimedia systems selector? If I do that and press 'test', I get an error message. If I choose the X11++ option, however, I see a test sequence.

I haven't been able to play a video in mplayer yet. Could this have something to do with it?

---

### Post by happyponcho42 on 2006-01-24
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

---

### Post by Sutekh on 2006-01-24
You might want to check these links too

[Gnome - HOWTO multiple sounds at once]("http://www.ubuntuforums.org/showthread.php?t=101125")

[Have an audigy? Want multiple sounds without ESD? Do this!]("http://www.ubuntuforums.org/showthread.php?t=104388")

---

### Post by Sutekh on 2006-01-25
And another, this one just popped up with a new reply (check last pages for relevance to Ubuntu 5.10)

[http://ubuntuforums.org/showthread.php?t=44753]("http://ubuntuforums.org/showthread.php?t=44753")

---

