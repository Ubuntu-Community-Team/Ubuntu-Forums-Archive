---
title: "Robust Library / Playlist Management for Portable Devices"
date: 2013-01-12
forum: Multimedia Software
---

### Post by nosehat on 2013-01-12
Hi,

Sorry in advance for the lengthy post!  I want to be really clear about the functionality I'm asking about.

I'm wondering if there is any software available for Ubuntu that allows for seamless and automatic playlist management on portable devices.  Something that would allow me to have a large music library on my computer (with songs in a bunch of big playlists based on genre, mood, etc) and when I copy a subset of this library to a portable device, it would automatically create m3u files on the device with only that subset of the playlists that are actually on the device?

My current solution is this:  

I have a Sansa clip that mounts in MSC (USB) mode.  I've got a folder on my computer, separate from my big music library, that mirrors the files and directory structure of the Clip and its SD card.  I use Banshee, and I've set this mirror folder as Banshee's music library folder.  Banshee is great at managing playlists, so when I copy an album from my big library to the mirror folder, I can put the songs into my various playlists.  If I delete an album from the mirror folder, Banshee will automatically remove those songs from any playlists they might be on.  

When I'm ready to sync the mirror folder to my actual Sansa Clip, I "Export" all the playlists in Banshee, which makes m3u files in the mirror folder on my comptuer.  I then run a Python script I wrote to synchronize the mp3 files and folders between the Clip and the mirror folder.  The script also *translates* the exported m3u files so they will work on the Clip (Banshee writes the path information Linux style, and the Clip expects Windows style paths).

This current solution does work, but it's more work than it should be, and it seems really hacky to me.  Also, it means I need to maintain two different music libraries-- my main big one, and the subset that is on my portable player.  Also, when I remove an album from the Banshee/Clip library, I lose the songs' playlist information.

Basically, I'm looking for music library management software that will have the same functionality with my portable mp3 player that Calibre has with my Kindle.  Calibre will show my computer's full library of ebooks and allow me to tag them as I please.  When I plug in the Kindle, I can move books on or off the device, and a plugin will create "Collections" (the ebook version of playlists) automatically based on how they are tagged in the big library.

Sorry again for the long post.  I hope this is clear!

---

### Post by nosehat on 2013-01-13
I'm guessing that the lack of replies suggests that there is no solution for this.  Too bad.

---

### Post by tgalati4 on 2013-01-13
I've used conduit for managing playlists between players.  It requires some setup.

---

