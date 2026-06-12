---
title: "Rhythmbox + iPoone = No music in iPod Library (sometimes)"
date: 2010-12-12
forum: Multimedia Software
---

### Post by asuastrophysics on 2010-12-12
Hey all,

I've been having a little bit of trouble trying to get rhythmbox to actually copy music to my iphone. While it will say "transferring songs" and then it will say "complete", if I try to unplug the USB, I get "no songs in library". 

If I connect the USB cord and then disconnect it briefly, all of my music comes back to my iphone's itunes....weird. 

Any thoughts or ideas?

---

### Post by gobbles414 on 2010-12-12
First, go Edit => Plugins, and make sure that all options relating to iPods and external audio players are selected.

Second, you may want to try creating a file called .is_audio_player to the root directory of your iPhone (include the dot at the beginning). That solution allowed me to transfer songs to my Motorola Droid. The dot at the beginning of the filename means that the file is hidden. In Ubuntu, you can temporarily activate the viewing of hidden files in Ubuntu's View menu. If you leave the .is_audio_player blank, Rhythmbox will copy your music the the iPhone's root directory. That could get annoying if you're trying to copy many songs. See [http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ) for information on how to transfer songs to folders in your iPhone.

You may also want to adjust the quality settings in Rhythmbox. The default quality settings for the transfer of songs in Ubuntu/Rhythmbox is 128 kbps MP3. I personally find that too low. I recommend that you navigate to Edit => Preferences => Music => Edit => CD Quality, MP3, and then replace what's there with the following:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0 bitrate=320 ! id3v2mux

Please, keep us up-to-date on your progress.

---

