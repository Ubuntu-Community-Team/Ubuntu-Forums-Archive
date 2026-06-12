---
title: "DLNA sort order (Sony BDP + rygel)"
date: 2010-11-26
forum: Multimedia Software
---

### Post by bilbo1234 on 2010-11-26
I just got a Sony BDP-S370 bluray player that supports DLNA, and it has been an "adventure". I tried several DLNA servers with mixed results: MediaTomb (not recognized by the BD player even after reading howtos here), minidlna (recognized but glitchy mp3 playback), ushare (not recognized). Finally I found Rygel which is recognized and even transcodes my ogg files! It's just what I was looking for.

My problem is that the files don't show up in a sensible order on the BD player. For example, when selecting an album I don't see the files in anything close to the right order (they are obviously named to be in the correct order lexicographically). I finally verified that the files are displayed in decreasing order by their **inode** number! Weird!

I don't know who is responsible for this ordering -- it could be rygel assigning IDs in this fashion, it could be the gnome tracker since rygel gets its information from the tracker. I'm not sure. Using wireshark I have verified that rygel sends out the DLNA responses in even a different order, so the BD player is sorting according to *something*...

Has anyone had experience with this? Technically I could restructure my file system so that the inodes are nice and tidy, but it would be a pain in the butt.

Are there any hidden rygel/tracker options? (I couldn't find any.) Has anyone had better experience with this BD player? I am so close to having a perfect music setup with this DLNA business, it is frustrating! As a last resort I will downgrade to rygel 0.3x which didn't use the tracker and only used the filesystem organization.

Thanks in advance for any suggestions..

---

### Post by 01000111 on 2010-12-03
I got the same player a few days ago, but can't get Rygel to show any files.  The player sees the Rygel server, but every folder says "no playable files".  I have been able to get a few .mpg files to play in the player using Windows Media Player 11, but not with Rygel.  How did you do it?

Using --log-level=5 I see that when it goes to harvest my media dirs, the harvesting is cancelled...

** (rygel:6959): DEBUG: rygel-media-export-harvesting-task.vala:118: Harvesting of uri file:///home/gcg/Videos/test was cancelled
** Message: 'file:///home/gcg/Videos/test' harvested



THanks.

---

### Post by bilbo1234 on 2010-12-03
> **01000111 said:**
> I got the same player a few days ago, but can't get Rygel to show any files.  The player sees the Rygel server, but every folder says "no playable files".  I have been able to get a few .mpg files to play in the player using Windows Media Player 11, but not with Rygel.  How did you do it?


Looks like you are using the media export plugin. In my experience it is very slow, since it rescans the metadata for each query. I have had success with the tracker plugin (after installing and pointing gnome tracker at the right things).

However, I can't get mp3s to play directly (as I have been able in other DLNA server). They play transcoded to LPCM, which is fine but seems like a waste of CPU cycles since I know the BD player can play MP3. Since rygel is the only thing I've found that transcodes my ogg files, I am sticking with it.

Also, I have not gotten *any* DLNA server to successfully play video files on this device. While I would like this to work eventually, music is a higher priority for my purposes than video. So if you are only interested in video, I regret that I don't know how to help..

I have tried what seems like a dozen DLNA servers now, and I can report my findings if you're interested. They all have their quirks when talking to this device, it seems.

---

