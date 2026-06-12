---
title: "Rythmbox"
date: 2010-12-16
forum: Multimedia Software
---

### Post by Gnome1984 on 2010-12-16
Rythmbox is not recognizing any ipod that hooked into my PC.  It had previously recognized the ipod but no longer does, also the ipod appeared on my desktop and list of drives.  I am thinking it is the ipod.  Is there a way to sync it manually with rythmbox so that i can eliminate the software as a potential problem?

---

### Post by gobbles414 on 2010-12-17
This is a copy of a reply which I recently provided to a similar question in another thread...

First, go Edit => Plugins, and make sure that all options relating to iPods and external audio players are selected.

Second, you may want to try creating a file called .is_audio_player to the root directory of your iPhone (include the dot at the beginning). That solution allowed me to transfer songs to my Motorola Droid. The dot at the beginning of the filename means that the file is hidden. In Ubuntu, you can temporarily activate the viewing of hidden files in Ubuntu's View menu. If you leave the .is_audio_player blank, Rhythmbox will copy your music the the iPhone's root directory. That could get annoying if you're trying to copy many songs. See [http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ) for information on how to transfer songs to folders in your iPhone.

You may also want to adjust the quality settings in Rhythmbox. The default quality settings for the transfer of songs in Ubuntu/Rhythmbox is 128 kbps MP3. I personally find that too low. I recommend that you navigate to Edit => Preferences => Music => Edit => CD Quality, MP3, and then replace what's there with the following:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0 bitrate=320 ! id3v2mux

Please, keep us up-to-date on your progress.

---

