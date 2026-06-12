---
title: "how to play music without a monitor"
date: 2011-01-10
forum: Multimedia Software
---

### Post by drummert on 2011-01-10
I have a desktop pc with ubuntu 10.10 which is connected to my hifi installation.
With my laptop i login with "ssh -X" to the desktop pc and start banshee to play music stored on the desktop pc.
(the banshee userinterface is shown on the laptop and the sound goes to the hifi installation)
This works only when there is a monitor connected to the desktop pc, when i disconnect the monitor the sound is gone.
Is there a way to play music without the monitor ? 
 
thanks,
Drummert

---

### Post by lykeion on 2011-01-10
Maybe I misunderstand you, but why don't you just ssh without X11 forwarding and use a command-line music player? 
There are lots of CLI players available: cmus, moc, herrie, mplayer, mpg123, mpg321, mp3blaster, etc

---

### Post by drummert on 2011-01-10
hi lykeion
 
I never tried a CLI player but i will try that, good idea. I hope the sound works with such a CLI player.
But if it works I still search for a solution to use a GUI player, not everyone at home likes a CLI interface :).

---

### Post by drummert on 2011-01-10
same problem with a CLI player.
When the monitor is connected the music goes to the hifi, when the monitor is disconnected the sound is gone.

---

### Post by samfuzz on 2011-01-10
you should try mpd
it 's perfect for your needs
[http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)
there are a lot of clients (with GUI or not) for various OS

---

### Post by 741Baus on 2011-01-10
Hi Drummert, In Pulse Audio volume control-input devices is it set to <all except monitors> ?

---

### Post by drummert on 2011-01-11
hi samfuzz and 741Baus,
 
It works after disabling gdm, found some usefull information on these sites:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1078659](http://www.uluga.ubuntuforums.org/showthread.php?t=1078659)
[http://fooninja.net/2010/07/29/text-boot-in-ubuntu-lucid-lynx-10-04-disabling-gdm/](http://fooninja.net/2010/07/29/text-boot-in-ubuntu-lucid-lynx-10-04-disabling-gdm/)
 
l never heard of mpd but after a short overview it looks like a much better solution than the one i have at the moment.
( it works but when I use a GUI mediaplayer performance of the GUI isn't very good )

gonna try it as soon as possible...
 
thanks !

---

### Post by aeiah on 2011-01-11
the beauty of mpd is it's server/client interface. sure, you could ssh into your desktop and launch the cli mpd client ncmpcpp but there's nothing stopping you installing sonata, a gui mpd client on your laptop and controlling the mpd server on the desktop with it.


incidentally, the issue you were facing was probably because the xserver wasn't starting with no monitor plugged in, and so GDM wasn't starting, and so the audio wasn't initialised. 

mpd is certainly the way to go. probably with sonata on the laptop or a web user interface

---

### Post by drummert on 2011-01-11
mpd rules !

---

