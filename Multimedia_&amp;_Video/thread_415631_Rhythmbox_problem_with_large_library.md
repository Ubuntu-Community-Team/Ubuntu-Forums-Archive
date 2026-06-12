---
title: "Rhythmbox problem with large library"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by Fangs404 on 2007-04-20
I have a library of around 13000 mp3s (with about 2 wavs mixed in there), and Rhythmbox is having an issue loading them all.  It loads about 10.5k of them, but then it just seems to stop.  Is there some limit to the size of its library?  Am I missing a codec?  If so, how can I find out.  For reference, I used Automatix2 to install multimedia codecs.  I really like the interface because of its simplicity, but unless it can load my whole library, I'll need to use something else (recommendations?).  Thanks for any help!

---

### Post by mortalfunk on 2007-04-20
I'm having the exact same problem!

I have 12,000 songs in my library that Rhythmbox imported properly. However, it always freezes while searching for songs or even when I try to click the next button to skip a song.

In addition, it won't import any m4a files!

I'm looking for a good music player for Ubuntu that can handle large libraries!

---

### Post by RawMustard on 2007-04-20
Yeah me too, it really is a piece of crap software.  Every new version of gnome that comes out I start it up to see if it's any better and just laugh.  Who ever is coding it really hasn't got a clue it would seem!

---

### Post by bom28 on 2007-04-20
There are lots of alternative music players for gtk/gnome :
-quod libet
-banshee
-exaile
-listen
-gmusicbrowser (my favorite, though not to everyone's taste it seems :confused: )

and of course amarok that use qt/KDE

I found gmusicbrowser to be the fastest for a BIG library, though it doesn't support .m4a. (yet ?)

There is also mpd with various front-ends, that is probably faster but not enough features to my taste.

---

### Post by skatedawe on 2007-04-22
Im haveing the same problem, i havee like ~15k and every program crash when im dropping the folder on it. 
The only player that could handle it and was fast enough was xmms. im waiting for xmms2 to be released, they are working on it.
I will try the suggestions.

I have no need for .m4a. What is it the format anyway for?

---

### Post by Fangs404 on 2007-04-22
Well, I'm glad I'm not the only one having this problem.  I guess I'll start looking for an alternative.

---

### Post by Fangs404 on 2007-04-27
Hm, this is most peculiar.  My library contains 11568 songs.  foobar2000 recognizes and is able to play them all under Windows.  I've never had an issue with my music.  But no matter which program I try (I've tried gmusicbrowser, exaile, and rhythmbox), none of them recognize more than 10562 of my songs.

Could this be some codec issue?  I have the latest version of Automatix, and I used it to install my codecs for me.  What's especially strange is that the mp3s that aren't being added to the rhythmbox library play fine in rhythmbox when I open them individually.  They just aren't being added to the library.  Same with the other 2 programs I tried.

Does anyone have any idea what's going on?  For what it's worth, I'm running 32-bit Feisty.

---

### Post by disturbed1 on 2007-04-27
I would say you have some bad/malformed/unsupported files somewhere. If you're library is sorted like most peoples (/artist/album) import each artist folder by folder, and pay attention to the import errors until you find the corrupt or unsupported files.

For what it's worth, my library is just shy of 22,000 songs, with a mixture of ~70% ogg and ~30% mp3.

---

### Post by starkruzr on 2007-05-01
Just so everyone knows, I fixed the problem with Rhythmbox (and other gstreamer-based players) "skipping" m4a files and not playing them by copying one to my desktop and trying to play it in Totem.  Feisty then noticed it didn't know how to play it and invited me to install the correct codecs.  I did have to select the package that wasn't selected in order for it to work right.

Installing what I THOUGHT was libfaad didn't help, and neither did gstreamer0.8-faad.

---

### Post by jsnelli2 on 2007-05-01
I've got just shy of 30,000 songs (29,994)...all mp3.   No problems in Rhythmbox.....I have them on an external Seagate hdd.  They are arranged in a folder Music/Arist/Album.  I'm running Feisty (Edgy before that).  Never had a problem.  I also used Amarok before upgrading to Feisty (got uninstalled, just haven't put it back on yet).  Wish I had some idea on how to help you guys.  Could it be the way they are filed?

---

### Post by dangerousnerd on 2007-05-02
I recommend ditching Rhythmbox for the more stable [Banshee]("http://banshee-project.org/Main_Page") (you can get it from the repositories).  It still comes with all the cool stuff Rhythmbox does (including iPod support).  I have a large library too and have never experienced a problem using Banshee.  Hope this helps!

---

### Post by raintheory on 2007-05-21
What alternative player could I use that has DAAP support for sharing/streaming over network?

Rhythmbox works most times for me unless I've just added new music to my folders, then when it starts up it takes forever to get to where it scans the new files.  During this time i get TONS of errors because I have .nfo/.txt/.sfv/etc files in with the music files.  

Is there a way to tell rhythmbox to ignore certain file types while searching for new files?

---

### Post by isecore on 2007-06-05
> **dangerousnerd said:**
> I recommend ditching Rhythmbox for the more stable [Banshee]("http://banshee-project.org/Main_Page") (you can get it from the repositories).  It still comes with all the cool stuff Rhythmbox does (including iPod support).  I have a large library too and have never experienced a problem using Banshee.  Hope this helps!

I've been using Banshee for some time now and feel that Banshee is a weird change. It fixes most of the complaints that I've got with Rhythmbox all the while introducing new annoyances. The most annoying one is that Banshee is extremely slow in handling more than very few songs. Searching is horribly slow, and there's no automatic watching of a folder which means that each time you add new songs they have to be manually imported, and if you change folder/file names then you have to find and remove them, then re-import them.

Admittedly Rhythmbox is kinda the same problem. It supposedly watches a directory, but I've found that sometimes it refuses to import certain files/folders. I've seen it first import a folder fine, but then ten minutes later it's removing the same files/folder for unknown reasons.

All in all, I think that Gnome/Ubuntu/Linux needs a decent (read: WORKING!) musicplayer, since none of the ones I've tried does everything I want it to.

---

