---
title: "Banshee Import Playlist"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by sliPrix on 2008-02-06
I had a playlist in Banshee that I put a lot of time into that I would like to try and save.  Also as a beforehand note, I have my music located on a separate HDD, and the mount point for that is /media/sda1.  Also I am using Banshee 0.13.1

I exported the playlist from my library onto my desktop in the form of an .m3u and a .pls.  I removed all of the songs in my Banshee library to "refresh" it with new music I have added.  Next I clicked "Music>Import Music>Local Folder>Import Music Source>sda1>My Documents>My Music> iTunes Music>Open" and imported all of my music once again.  My playlists didn't return as expected.  So I chose the "Import Playlist" option from the Music menu and navigated to my desktop where the "playlist.m3u" was stored and selected to import it.  

Upon doing so, Banshee reported "Import Errors"under my music library.  The errors stated "Song is already in library /media/sda1/My Documents/My Music/iTunes/iTunes Music/Artist/Song".  So to simply state it, I don't want to add the songs to my library, I want to add the songs from my library to the playlist.  

Any help regarding this issue would be greatly appreciated.  Also if you know of a way to make banshee import my playlists from iTunes, that would be great too as I know they are usually exported as .txt!  Thanks in advance.

---

### Post by sliPrix on 2008-02-06
So after doing extensive research I figured out how to export my iTunes playlists to .m3u extensions. This was simply done using a utility in windows called "iTunes Export" which is available here [http://www.ericdaugherty.com/dev/itunesexport/]("http://www.ericdaugherty.com/dev/itunesexport/").  So back to my Ubuntu 7.10 partition I edited the .m3u files using gedit to change the paths from "D:\My Documents\My Music\iTunes\iTunes Music\ to /media/sda1/My Documents/My Music/iTunes/iTunes Music/ by using the find and replace feature in gedit.  The m3u playlists import flawlessly into Rhythmbox but still no luck in Banshee.  So for now I'll be using Rhythmbox to manage my music, but if anybody knows how to import these playlists into Banshee I'd love to know.  Also, has anybody heard of any plugins that feature the similiar artists or top songs by the artist like Banshee has?  I found lastrhythm which looks nice but it was said to be "in early stages but works for me" so I'm a little weary.  Thanks!

---

