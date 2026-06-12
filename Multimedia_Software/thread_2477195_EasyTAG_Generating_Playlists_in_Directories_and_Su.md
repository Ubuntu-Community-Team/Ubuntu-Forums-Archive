---
title: "EasyTAG: Generating Playlists in Directories and Subdirectories"
date: 2022-07-17
forum: Multimedia Software
---

### Post by piattj on 2022-07-17
Yesterday I used the generate playlist tool, and with one click generated a playlist for each directory and sub-directory in the USB drive I use for my car stereo. The directory structure I use is Artist then Album. So, in the "John Coltrane" directory, there appeared an "A Love Supreme" m3u playlist in that folder for that album, a "Ballads" m3u playlists in that folder for that album, etc. There also appeared a "John Coltrane" m3u playlist in the higher-level "John Coltrane" directory, containing all songs on all the albums by him.

I wasn't happy with something about the playlists (I don't remember what), so I searched from the root directory of the drive and deleted all the m3u files to try again. But I haven't been able to get EasyTAG to repeat that recursive playlist-generating behavior. I don't remember what particular settings I used (I didn't mess with them that first time anyway), and I'm definitely not imagining that it happened, because in my trash I still have all the playlist files.

Does anyone know what settings, or combination of settings, allows you to create playlists for all the audio files in a folder, and it's subfolders, in one operation?

---

### Post by TheFu on 2022-07-17
I use easytag, but never for playlists.  Those are trivial to create with 'find'.

```
$ find /path/to/top/of/music-tree  -type f -iname \*3 > all-music.m3u 
```

With find, you can filter based on any part of the directory or filename and generate playlists.
I think you'll find that having absolute paths, like the find command above does is a terrible idea. What you really want is for the list of files in the m3u playlist to be relative from the files.

So, I will create a per-album playlist in the same directory as the album and save it in that same directory 
and
I will create a per artist playlist in the artist's directory.
These have been working for my playback tool that uses playlists. It also works when I copy the different files over to my phone to play disconnected.

For other players, I point them at the top of the library and let them create "smartlists" based on the id3 tag data.  mpd and most media center programs like plex and kodi/osmc and Jellyfin work with this, if they support the file type. That's were Plex really sucks. It supports very limited audio file types whereas the others seem to support everything from flac to vorbis.

One of my weekly auto-created playlists looks for "greatest/best of" and a few other key terms to build a playlist for general use by non-fans.  They don't have to hear those special, unknown, songs that never were on the radio, but there are some many great songs that fans of the artist will know and enjoy - say like  Van Halen's "Ice Cream Man" which everyone of my age and background knows.

---

### Post by piattj on 2022-07-20
Thanks. The code line you included doesn't create playlists in album directories and also in higher-up artist directories, though, does it?

---

### Post by TheFu on 2022-07-20
> **piattj said:**
> Thanks. The code line you included doesn't create playlists in album directories and also in higher-up artist directories, though, does it?

I leave that for you to solve. It isn't hard and there are plenty of examples.
The playlists created by the 'find' example will work anywhere on the system.

m3u files are really bonehead and any Unix system has plenty of text/file tools to create any that you need.  A web-search with "create m3u files in each directory" as the search term finds many solutions. Some are '1-liners', but there are some that are a bit longer to aid readability.

Saw this post a few hours later: [https://www.howtogeek.com/812027/linux-tree-command/](https://www.howtogeek.com/812027/linux-tree-command/) which shows how to run a command in every directory that is found.  This would be a fairly easy way to create an m3u file in every subdirectory on a system and place the output file where you like.

Did you even run the command and look at the created file?

---

