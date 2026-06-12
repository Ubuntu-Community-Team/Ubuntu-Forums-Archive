---
title: "Music and Android playlist sync"
date: 2012-03-27
forum: Multimedia Software
---

### Post by kinsago on 2012-03-27
Hi all.

I apologise if this has been posted already but I've been searching for hours and am now losing my mind (and my hair!!!).

I have and ubuntu computer and an android phone. Actually, I have 2 android phones - 1 of which is my wifes and I'm not allowed to play :(

Anyway, I have music on pc and I can put it on phone. This is simple. I have playlists of music on pc which I want to transfer to phone - this is not so simple. 

Currently Banshee will sync a playlist if I select the playlist in the sync menu. However, banshee is extremely slow and frustrating. It also doesn't support drag-and-drop which is far faster. (Dragging and dropping a playlist copies the music but not the playlist). I can manually set up playlists through banshee once the music has been copied but again this seems counter-productive

My other choice at the moment is Rhythmbox. However, Rhythmbox exports as .pls (not m3u which android supports). This has made further testing difficult.

Clementine is another I've experimented but it doesn't have great support for playlists beyond basic loading and saving from a file.

Hopefully I'm just missing something obvious...

---

### Post by drenze on 2012-04-26
Try creating the file .is_audio_player in the root of the sdcard you transfer your files to. That should take care of it. Below is the contents of my .is_audio_player file.

Hope this helps.
---

name="My Android"
audio_folders=Music/
video_folders=Video/
audiobook_folders=AudioBook/
output_formats=audio/mpeg,audio/mp4,audio/flac,audio/ogg,audio/aac
playlist_formats=audio/x-scpls
playlist_path=Music/Playlists/

---

### Post by kinsago on 2012-05-09
> **drenze said:**
> Try creating the file .is_audio_player in the root of the sdcard you transfer your files to. That should take care of it. Below is the contents of my .is_audio_player file.

Hope this helps.
---

name="My Android"
audio_folders=Music/
video_folders=Video/
audiobook_folders=AudioBook/
output_formats=audio/mpeg,audio/mp4,audio/flac,audio/ogg,audio/aac
playlist_formats=audio/x-scpls
playlist_path=Music/Playlists/

Thanks, I'll give it a try over the next day or so

---

### Post by kinsago on 2012-05-10
Right. Tried that and still no cigar.

I think that the media programs lack the functionality I'm after. Perhaps I need to learn to write a plugin to do the job

---

### Post by k1nch on 2012-08-15
I'm having the same issue as well...

My computer is on Ubuntu 12.04 and have a Samsung Galaxy S3. I've tried Rhythmbox, Banshee, and Clementine. I prefer Clementine, so if someone knows a tweak for it, that'd be great.

I don't have an SD card, but I can get one if absolutely necessary.

---

### Post by billjank on 2012-08-20
I'm in the same boat - got a Nexus 7 and love it, to the point where I'm really interested in ditching the entire Apple ecosystem. So, I dug out a pretty recent laptop, wiped it, installed Ubuntu 12.04, moved over files. 
 
In general, I love the experience.

BUT - it drives me batty that it's way easier to move content and playlists to/from my iPhone than it is to even access my Nexus 7.

---

### Post by sammyjk on 2012-12-31
Easy answer is that android is now using a new file system that doesn't play well. What they want you to do is upload all you're music to the cloud and play from there, using their streaming player, right now there is no work around to sync directly. I have had some success with connecting my phone as usb device. In rhythmbox you can drag the contents of a whole playlist onto the device then right click the device and create new playlist, then place all the songs on that playlist from your device. You CANNOT drag a whole playlist onto the device. And this trick, while it works, only works once, that is to say the next time you connect your device it wont register that it has a playlist on it, but you will see the music on it. Hope this helps and if anyone else finds a good work around, please post it.

Edit : You will need to manually put at least one MP3 in the music folder of your android device first. Also the right click--sync library method also works this way.

---

### Post by bowhat on 2013-01-26
Use rhythmbox. Use the script provided here:
[http://ubuntuforums.org/showthread.php?p=12475542](http://ubuntuforums.org/showthread.php?p=12475542)

It prompts you for all your rhythmbox playlists and lets you pick which ones to sync. Moves the files over. Creates a playlist on the device as well. It is a sync not a copy -- so other music files on your device on the Music folder get removed.

Could not be any easier. After many hours of searching that did the trick for me. Wish it was publicised more so that I did not have to waste that much time.

---

