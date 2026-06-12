---
title: "Web Controlled music player"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by colonel_panic414 on 2007-08-28
Ok, I have this one computer that has all of my music. I like to listen to music while I'm studying or doing homework. But, my computer desk has just enough room for my computer, and nothing else. 

So, I work either on my bed or another table. What I want to know is, is there any media player/server program that will give me control through a web interface? As in, my computer plays the music like normal, but I control it through a web page on a handheld, such as a Nintendo DS.

Thanks!

---

### Post by saj0577 on 2007-09-06
try 
gnump3d mate.

```
sudo apt-get install gnump3d
```


Saj

---

### Post by colonel_panic414 on 2007-09-17
Thanks, but I'm not having any trouble finding streaming servers. I just want a program that will give a web interface to control a media player on my desktop. As in, if I pull up the interface with a Palm or PocketPC etc,,, It will act as a remote control for my computer's media player program.

---

### Post by Phreakazoid on 2007-09-17
You could try MPD ([http://www.musicpd.org]("http://www.musicpd.org/") - version 0.12.2 is in APT in Fiesty) or XMMS2 ([http://wiki.xmms2.xmms.se/index.php/Main_Page]("http://wiki.xmms2.xmms.se/index.php/Main_Page") - in APT for Gutsy, but not any previous releases).

Both of these music players run as a daemon process which can be controlled remotely by clients. These clients can be a program or a web interface, or pretty much anything you want.

Hopefully this helps.

---

### Post by colonel_panic414 on 2007-09-19
I decided to use mpd along with a small web client made for cell phone/portable browsers. But, I had a problem.

Synaptic/apt-get all freeze during installation, with this text
```
Setting up mpd (0.12.2-2ubuntu2) ...
Stopping Music Player Daemon: not running or no pid_file set.
Starting Music Player Daemon: ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

```

And hangs there. So, I had to close it, and when I re-opened/re-ran any of these commands, this is what I got:

```
taylor@UbuntuBox:~$ sudo apt-get remove mpd
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[1]+  Killed                  sudo dpkg --configure -a
```

Of course, when I run the dpkg command, it gives me the same hanging terminal. I don't know what to do, because now synaptic is apparently broken.

---

