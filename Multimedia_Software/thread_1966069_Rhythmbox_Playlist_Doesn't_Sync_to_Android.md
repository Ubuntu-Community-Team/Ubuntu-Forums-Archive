---
title: "Rhythmbox Playlist Doesn't Sync to Android"
date: 2012-04-26
forum: Multimedia Software
---

### Post by drenze on 2012-04-26
Hi. I'm having an issue syncing playlists to my HTC Incredible (runs Android OS) using Rhythmbox 2.96 (I also had this issue with earlier versions, but updated to the latest version before posting).

To sync with Rhythmbox, I did the following:

[LIST=1]
[*]Created the playlists to sync.
[*]Configured my phone to sync those playlists.
[*]Sync.
[/LIST]
What happens is that Rhythmbox copies all the files over, then copies the playlists over, and reports success. When I access my music player, it shows that all the music files copied over, but when I view the playlist, it does not show all the tracks that were copied over. When I open the playlist file, it reflects what my player is telling me. However, I can validate that all the music files have copied over into the right place. As an example, I have one playlist with 57 tracks, but the playlist on the phone only shows 9 tracks. However, I can find all 57 tracks on my phone's SD card.


I had a similar issue with Banshee, which is why I switched over to Rhythmbox (that, and I was getting ready to upgrade to 12.04LTS). However, Banshee would not copy the files over in the first place.


One thing that I have done is to make certain that the only characters in the filenames/pathnames are [A-Za-z0-9_- ].


Thanks.

---

### Post by sammyjk on 2012-12-31
Head hear, I posted a simple work around -> [http://ubuntuforums.org/showthread.php?t=1947982&highlight=sync+android+rhythmbox](http://ubuntuforums.org/showthread.php?t=1947982&highlight=sync+android+rhythmbox) ):P

---

### Post by bowhat on 2013-01-26
Actually, head here for the best solution that I found: 
[http://ubuntuforums.org/showthread.php?p=12475542](http://ubuntuforums.org/showthread.php?p=12475542)

It prompts you for all your rhythmbox playlists and lets you pick which ones to sync. Moves the files over. Creates a playlist on the device as well. It is a sync not a copy -- so other music files on your device on the Music folder get removed.

Could not be any easier. After many hours of searching that did the trick for me. Wish it was publicised more so that I did not have to waste that much time.

---

