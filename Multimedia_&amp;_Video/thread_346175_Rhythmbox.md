---
title: "Rhythmbox"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by curry on 2007-01-25
i would like to be running rhythmbox because i like the interface and the organization because i have such a large audio collection. My collection comes from itunes in OSX and XP so i have both MP3 and M4a audio files. I can get mp3 to play under the wav setting, but i cant get the m4a to run under any of the settings. How do i set up rhythmbox to play these files?

---

### Post by curry on 2007-01-25
Ttt

---

### Post by curry on 2007-01-25
anyone?

---

### Post by 3rdalbum on 2007-01-26
I don't have any unprotected AAC files, so I haven't tested it out on Ubuntu. Are these files ones that you downloaded from the iTunes Music Store, or ones that you ripped from CDs yourself?

If they are ones you ripped from CD, then you should be able to play them if you have the "gstreamer0.8-faad" package installed.

If you got them from the iTunes Music Store, then you must go into iTunes, burn them to audio CD, then rip the audio CD into MP3, Ogg or Flac.

---

### Post by rururudy on 2007-02-05
I use Ubuntu and had to install (among other packages) the gstreamer plugin for AAC decoding. I installed numerous packages, the final one was gstreamer0.10-plugins-bad.
[B] sudo apt-get install gstreamer0.10-plugins-bad
[/B]
Other things I installed before Rhythmbox played AAC (m4a) files were these:
[LIST=1]
[*] sudo apt-get install faad
[*] sudo apt-get install libfaad2-0
[*] sudo apt-get install gstreamer0.10-plugins-bad-multiverse 
[*] sudo apt-get install gstreamer0.10-plugins-base
[*] sudo apt-get install gstreamer0.10-tools
[*] sudo apt-get install gstreamer0.10-plugins-ugly
[*] sudo apt-get install gstreamer0.10-plugins-bad
[/LIST]

Viva monkeybrains.net!

---

