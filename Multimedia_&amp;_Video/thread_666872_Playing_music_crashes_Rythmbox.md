---
title: "Playing music crashes Rythmbox"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by Pethegreat on 2008-01-13
I have around 25gb of .flac files on my computer. I have used rythmbox for about a month now. Today I go to play a file, and rythmbox locks up and crashes. I tried exaile and it did the same thing. Now simple players like aqualung work fine, I tried uninstalling rythbox and reinstalling it, but it does not work. 

What is going on?

---

### Post by Pethegreat on 2008-01-14
bump. 

I may be looking at other alternatives if i can't fix this.

---

### Post by azad on 2008-01-14
Try Banshee, Listen and Exaile. There are many media players for you to try.

I personally love Exaile.

Cheers.

---

### Post by Pethegreat on 2008-01-14
> **azad said:**
> Try Banshee, Listen and Exaile. There are many media players for you to try.

I personally love Exaile.

Cheers.
Exaile does the same thing. I try to play a song and it crashes. 

Listen just sits, loads, sits some more, and vanishes. 

Banshee does the same as Exaile. I try to play something, and it locks up.

I can get very simple ones to work, but they do not allow me to import more than one song at a time.

---

### Post by Pethegreat on 2008-01-14
Now i get a playback error. it says "failed to connect to stream"

Completely removing rythmbox and all config files though synaptic and reinstalling does nothing.

---

### Post by RomeReactor on 2008-01-14
Hi. Try running it from the terminal:
```
rhythmbox
```
If it leaves any more error messages, please post them.

---

### Post by azad on 2008-01-15
Maybe your audio drivers are not properly installed. Are you able to play mp3 and ogg files proprerly?

Try other applications: Totem, Mplayer, Amarok, VLC, aTunes.

Is it just the audio players that are acting wierd? Have you tried other applications?

I've never seen such wierd things in Ubuntu. I've always thought playing media in Ubuntu is better than Windows or Mac (where there are no real alternative to iTunes).

I hope you get this problem resolved.

---

### Post by Pethegreat on 2008-01-15
> **RomeReactor said:**
> Hi. Try running it from the terminal:
```
rhythmbox
```
If it leaves any more error messages, please post them.
It says something about my theme not having some files to make it blend in. 

> 
Is it just the audio players that are acting wierd? Have you tried other applications?
I am unable to get audio in youtube videos or flash applications. 

I have been trying to get that to work. I followed [this]("http://ubuntuforums.org/showthread.php?t=661833") tutorial. I also followed [this]("http://ubuntuforums.org/showpost.php?p=3681791&postcount=8") post to try and get audio in flash to work. 

I have tried to undo as much of it as I can, but nothing has fixed this yet. 

> Try other applications: Totem, Mplayer, Amarok, VLC, aTunes.
Amarok is KDE only. MPlayer seems to be just for videos. I got VLC to work with my .flac files. 

I would like to get rythmbox working again. I miss the features that it had.

---

### Post by azad on 2008-01-16
KDE applications run well in Gnome. Although they look a little wierd sometimes. Give Amarok a spin.

You have a nice sound card. You must have ALSA/OSS enabled. Go to System > Preferences > Sound. Set the Sound Playback to ALSA or OSS and test each of them. See what works best for you.

Also, check if you need any restricted drivers. Maybe your sound card isnt properly installed. System _ Administration > Restricted Divers Manager.

And to get flash working properly, Uninstall Flash Player from Synaptic.
Download the Flash Player 9 for Linux from Adobe website and double click on the excutable to install.

Cheers mate.

---

### Post by Pethegreat on 2008-01-16
> Also, check if you need any restricted drivers. Maybe your sound card isnt properly installed. System _ Administration > Restricted Divers Manager.
I had it running for about a week before this happened. I looked on M-Audio's site. They don't have a linux version of the drivers I would need. 

> You have a nice sound card. You must have ALSA/OSS enabled. Go to System > Preferences > Sound. Set the Sound Playback to ALSA or OSS and test each of them. See what works best for you.
Hmmm, I set it to ALSA and rythmbox works though my card is listed as OSS. I got OSS 4.0 installed in order to get my 192 working. 

> And to get flash working properly, Uninstall Flash Player from Synaptic.
Download the Flash Player 9 for Linux from Adobe website and double click on the excutable to install.
I have the 64bit version of 7.10. I have a 32 bit emulation patch in place so I can get things going. This mat be more than just flash sound. I can't get system sounds yet I can get music. 

Well I got things working for now. I still don't have sound in flash/youtube, butI can live without it though.

---

