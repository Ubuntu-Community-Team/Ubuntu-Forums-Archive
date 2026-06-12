---
title: "Sound failing after streaming audio through firefox"
date: 2008-06-27
forum: Multimedia Software
---

### Post by Larsj82 on 2008-06-27
Hi,

This is my first post in this forum as I normally find the help I need through other threads. 

I recently upgraded from Feisty 32bit to Hardy 64bit. I normally stream radio through the stand alone Real Player, but pretty much every time I stop the radio to watch a youtube clip or any other media with sound through firefox 3 the system will stop to output sound and the only thing that works is a complete reboot. Restarting X wont fix it.

If I restart realplay through the terminal I get the following output:
$ ./realplay

(realplay.bin:6202): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so: wrong ELF class: ELFCLASS64

(realplay.bin:6202): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so: wrong ELF class: ELFCLASS64
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
...etc for about 50 lines

I use Totem Web Browser Plugin 2.22.1 for media files and Shockwave Flash 9.0 r124 for flash.

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


I apologise if there is another thread about this, but I couldn't find one. Does anybody have an idea on how to fix this? 

Thanks

---

### Post by Vivaldi Gloria on 2008-06-27
I don't know about your problem but trying to fix pulseaudio following one of the following guides is a good idea:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

I used the second thread to fix all my sound issues but the first thread is newer. Note that some parts of the guides are 32bit (i386) only.

---

### Post by Larsj82 on 2008-06-30
Thanks. I have just given up and hoping for a fix in next release.

Noticed I dont need a reboot if I kill pulseaudio and restart realplayer (or wherever I want sound to from)

My temporary fix is the following line in a script and make a panel icon of it:

ps aux | grep pulseaudio | awk '{print $2}' | head -n 1 | xargs kill

Dodgy fix I know, but it works

---

### Post by markbuntu on 2008-06-30
Flash10 will fix your problem with sharing in pulseaudio, that is for sure. You really need to get flash 10. There are plenty of thread around about how to do that.

I use rythmbox to play streams and tunapie to get them. I also use streamtuner and xmms but it is a fairly complicated thing to get xmms working in 64 though streamtuner will play through totem in 64.

---

