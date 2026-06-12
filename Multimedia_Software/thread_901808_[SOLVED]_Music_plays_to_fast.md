---
title: "[SOLVED] Music plays to fast"
date: 2008-08-26
forum: Multimedia Software
---

### Post by madaved on 2008-08-26
hy there

got a very strange behavior. With running my mp3 on rhythmbox. they where playing at least 5times faster (with no sound) then it should.:confused:

Im running 8.04 on a MacBookPro but dont think this causes the problem.
Ive added the whole iTunes Lybrary to rhythmbox so far so good. Had to install 2 updates to ran the music...
[LIST]
[*]GStream ffmpeg video plugin
[*]Gstream extra plugins (plugins from the "ugly" set)
[/LIST]

everything worked just fine, but thought would like to try 
the gstransmit for AirTunes support. (from the site [el-tunes.com]("http://www.el-tunes.com/"))

after I installed this the described problem occurred. tried to run the mp3s in other apps like Noatum or Banshee Music Player. in those the files wont even play... very strange.

The sound should be okay, vids and flash on youtube 4example is no problem... 

Ive deinstalled all plugins and players. (excepted the gstransmit one dont know how). rebooted and installed again (except the gstransmit). but got the same problems...

someone has any ideas? im new to ubuntu... where can i see which files have been created during the gstransmit installation? some log files, maybe have to delete them by my self. (used GDebi Package installer to install)

thx 4 reading

---

### Post by madaved on 2008-08-27
Have solved the problem, but im not sure why..

deleted once again all plugins with gstream in it (synaptic package manager complete removal) also the rhythmbox, bunshee and Noatun.

after restart and re-installation the mp3s worked. hmmm glad it works now

cheers

---

### Post by tuxxy on 2008-08-27
Good stuff, mark your thread solved then now so people know not to click it.

---

### Post by kronepils on 2008-09-09
Hello.

What do you mean by solved? Does gstransmit work for you?
It doesn't work for me. I have the same problem with the fast and silent playing.

So does your music play through Airtunes now??

I have my gstreamer working, but not with gstransmit. I have to uninstall it to play music through gstreamer.
BTW, to uninstall a package type in a terminal:
sudo apt-get remove gstransmit


./Troels

---

### Post by Guruji on 2008-09-09
same problem here, had to uninstall gstransmit to get the files playing properly.
Does this gstransmit really work?!

---

