---
title: "Organize Files Shared To LG TV"
date: 2019-08-18
forum: Multimedia Software
---

### Post by Old Newville on 2019-08-18
Hello Ubuntu community!

I'm hoping someone can point me to a way to better organize the way my files display on shared devices.

I currently use my Ubuntu box to share audio, video and photo files on a home network.  I got an LG TV and it plays shared files very well.  I have a collection of music CDs, along with various podcast-type files and other information programs. They're all saved in some type of audio file format, i.e., wav, mp3, flac, etc.

However, the file list that appears on the TV combines all of these files together.  When I click on "MUSIC" it displays music and info programs together.

I'd like to separate the music files from the "info" program files so that I'm not rummaging through a huge list to find that CD I want to listen to.

Actually, the same thing happens with the "PHOTO" link on the TV.  It displays family vacation pictures along with all of my Gnome wallpaper pics.  It gets annoying to have to sort through that.

The TV seems to scan the PC for every kind of audio or photo file it can find.

Any ideas on how to improve this?  Do I fix it at the source or the TV?  The TV allows me to create playlists, but creating separate playlists for dozens (maybe 100s) of music CDs isn't very feasible.

Source is a Dell machine running Ubuntu 18.04 LTS.  Client is an LG TV.

Any suggestions would be appreciated!

---

### Post by TheFu on 2019-08-18
Seems like a TV issue. Which protocols does the TV support?  Look in the manual.

Just some thoughts which might not be relevant to your specific TV model. I don't have a TV anymore. We switched to a projector a long time ago so watching TV would be less common and an "event."

Most smart TVs should support DLNA.  There are standards for this stuff that most media centers (Kodi/Plex/Windows) require:
```

Movies/Title (YYYY)/title-year-res.mkv
TV/Title (YYYY)/Season 1/Show-101-EpTitle.mkv
Music/Genre/Artist/Album/##-Title.ext
Photos/YYYY/MM-Event Name/
```

Movies and TV are really stuck in that layout.  Most Media Center Servers will merge many disk into a single view for clients, so if you need 20 disks to hold your BlueRay collection:
```
M1/Title (YYYY)/
M2/Title (YYYY)/
M3/Title (YYYY)/
....
M20/Title (YYYY)/

```
Same for all the other types of media. Multiple disks aren't an issue. No need to use any funky file systems to merge disks into a single virtual file system.   The YYYY and () are optional, they just help with title scrapers. You can manually help, if needed.  I don't use () since those characters break my scripts and I avoid any spaces or other funky characters in directories or files for a similar reason. I don't want management scripts broken over a stupid apostrophe.

Music is pretty free form (so you can do almost anything), but if you do an Genre/Artist/Album/##-Title.ext I think you'll be happier most of the time.  Soundtracks don't fit, so make a soundtrack Genre.  Singles with mixed artists don't fit either.  **EasyTag** will let you convert to that Music layout using tags - or add tags based on the directory layout.

Same for Photos, but if you organize by at least the year, you'll be happier in 40 yrs as memory fades.  Knowing the year is really very helpful.  I've had to organize my dead parents photos.  Dad labelled almost everything, but Mom didn't. Lots of photos of people important enough for a 35mm photo, but not important enough to know their names/relationship.  Grandkids get interested in that stuff about every 20 yrs.  ;)

---

### Post by SeijiSensei on 2019-08-19
I use **minidlna** on my server to export file shares, and my LG TV see those shares as I defined them. What software are you running on the Linux box to share files with the TV?

---

### Post by Old Newville on 2019-08-27
Thanks to both for your thoughtful replies.  

I'm using Rygel as a dlna/upnp server, and file sharing in Ubuntu seems to show up as well.  I will explore MiniDLNA.  I've been using SoundJuicer to rip CD's, and it numbers each disc and track.  That's what I don't get!  Even when a client shows the numbers, it tends to read it as 1, 11, 12, 13... 2, 20 21, 22, etc.   Before I checked in on this forum, I had the idea of shutting down Rygel to see if file sharing would turn up on the TV instead.  BTW, I have a smaller TV running a Roku box and I have pretty much the same problem there.  If I choose "Album," it displays all the albums (folders) without the artist name.  Choose artist, and you loose the variety discs, as TheFu pointed out.  

Will keep tinkering and post my solution here.  Thanks again!

---

### Post by TheFu on 2019-08-27
For audio files, the metadata is almost always stored inside the file itself, so if the data being displayed doesn't reflect the correct data, then I'd say you have a ripping problem to solve.  For many popular audio formats, EasyTag will let you set tags at multiple layers across 1 or thousands of files.

---

### Post by Old Newville on 2019-09-05
I can now mark this thread as solved.

After researching various options - tinkering with rygel.conf and reading the LG support site as well as other DLNA forums -- it looks like the easiest solution is the tag editor!   The Fu was onto something.

I installed Kid3-qt via Synaptic from the Ubuntu repository, after a quick search turned up more than a dozen likely candidates.  Kid3-qt offers many options for editing metadata, but I took the easy road -- I simply edited the track titles to insert a number at the beginning of each one.  And my TV now displays the tracks in the correct order.  If you spend some time reading the generous help document, you can learn how to pull in CD images from various sources to dress up the track display interface.

It also allows for batch editing of metadata, so you don't need to go track by track but can change whole directories.  I went folder by folder and got through my whole collection fairly quickly.  Now I run it immediately after I rip a CD onto my Music drive, and the songs display in the correct order.

---

