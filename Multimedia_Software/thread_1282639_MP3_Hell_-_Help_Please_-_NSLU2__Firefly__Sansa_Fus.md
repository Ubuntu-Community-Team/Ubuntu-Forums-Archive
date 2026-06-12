---
title: "MP3 Hell - Help Please - NSLU2 / Firefly / Sansa Fuse"
date: 2009-10-04
forum: Multimedia Software
---

### Post by Bivvy on 2009-10-04
With hindsight I would not have done things this way, but here I am - in need of any (constructive) advice or support I can receive!

I have  Roku Soundbridge streaming music from an NSLU2 Network Storage Unit with the music stored on a USB disc drive.  The NSLU2 has Linux installed on it and I am using the Firefly Media Server software to stream the music.

Firefly uses the XML files created by Itunes to manage playlists so I have been using Itunes on Windows XP to manage the files.

I recently bought an MP3 player - couldn't afford an Iplayer and can't say I am keen to feed the Apple empire, so bought a Sansa Fuse.  It doesn't work with Itunes, so I moved to Winamp and spent a considerable time rebuilding palylists and sorting out the metadata in my MP3 files so the Fuse and Winamp worked together.  I also download podcasts which are then stored on the Fuse.  I have still gad to stick with Itunes to maintain the Firefly playlists.

I don't have a pictures on the Fuse yet, but might in the future.  

I've now made the leap to Ubuntu Linux (Juanty) - Fantastic.  Why did I wait so long, but...

Winamp does not appear to be available.  I've tinkered with some of the other MP3 software but nothing does quite what I need it to:

I have no no problems mounting the disc from the NSLU2 on the computer which is now running Linux, but how do I

[LIST=1]
[*]Download and play MP3 files on the computer
[*]Download podcasts and play them on the computer
[*]Manage playlists
[*]Sync the music / podcasts and playlists with the Sansa Fuse
[*]Use the playlists with Firefly
[/LIST]
A single integrated solution would be best, but a piece of software that does 1-
5 and a second that does 6 would be manageable.

Thanks in advance.

Chris

---

### Post by tgalati4 on 2009-10-04
When you run rhythmbox doesn't the sansa just show up?

For podcasts you can use rhythmbox, though I use gpodder:

sudo apt-get install gpodder

Gpodder will sync podcasts to a specific folder on any mp3 device, you just have to specify the directory in preferences.

Banshee also supports podcasts:

sudo apt-get install banshee

Both rhythmbox and banshee support smart playlists and you can pull those playlists into an mp3 player.

---

