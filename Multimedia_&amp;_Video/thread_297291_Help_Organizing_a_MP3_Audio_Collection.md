---
title: "Help Organizing a MP3 Audio Collection"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by henriqueqc on 2006-11-10
A couple of years ago, back in my "windows" days, I began organizing my music collection. I have a couple of albums and was passing them to mp3. Now I was hoping to finish that project. 
I used to follow a list of tasks to each CD and it was:

1) Ripp the CD to mp3.
2) Collect some information from freedb.org. (using the ripping software).
3) Normalize/Clipping correction using MP3Gain.
4) Get more detailed information for the tags from CDDB.
5) Write the tags.
6) Rename the files.

I was very critical about the tags. All files had the same information: Artist - Album - Year Release - Track Name - Track Number - Total Track Number - Total of CDs - Number of CDs. And I think was about it. I deleted all the other fields that may have come up during the CDDB lookup so the collection would homogeneous and "clean".

The file name also had a rule:
artist/album/cd#-track#-track-name.mp3

Now I'm using Linux and I was looking for software to help me continue organizing my collection.

I found Picard that uses the MusicBrainz database. And it does the tagging  very well I use albumart-qt to collect album covers.

But I'm still looking for programs to normalize the files and edit the tags after Picard did it's thing. Also the filenames contains spaces and capital letters I would like to rename them to lower case and remove the spaces adding "_" characters, I could write a script but I think someone already did it.

I'm curious to know how do you organize your collections. What naming patterns do you use and what programs.

Cheers.

---

### Post by kalixiri on 2006-11-11
I use **quodlibet** as my music player. I'm quickly annoyed by huge monolithic apps like AmaroK and most other media players. I like it because it stays out of my way and plays WavPack flawlessly.

You can use [rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") for ripping your CD's. I could never get the FreeDB lookup to work right (not that I care, most of my CD's are obscure classical discs) but I feel as safe ripping with it as Exact Audio Copy on Windows. If only it had Cuesheet support, I would totally satisfied.

For tagging I use **exfalso**, which comes bundled with quodlibet. There is a CDDB plugin available in the **quodlibet-plugins** package. Exfalso can do all of that underscore->spaces and caps->lowercase stuff. I'm in Xubuntu right  now and Thunar has a really great Bulk Rename feature if I'm just working with a few directories.

I've almost given up on the metadata issue. As I said, my music interests are primarily classical, and there is not much support for the kind of metadata that classical music performances require. (Conductor, Orchestra, types/periods of a piece, movements as opposed to track numbers). Multiple performers is usually a nightmare, either you have a title field 100 characters long that doesn't fit on your screen or a bunch of pseudo tags like "key" or "piece" that are useful but poorly supported. For my pop/contemporary music, I just use a basic artist/album/01_songtitle.blah system.

---

