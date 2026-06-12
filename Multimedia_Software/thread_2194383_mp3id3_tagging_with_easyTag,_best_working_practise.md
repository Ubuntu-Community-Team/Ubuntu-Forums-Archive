---
title: "mp3/id3 tagging with easyTag, best working practise?"
date: 2013-12-18
forum: Multimedia Software
---

### Post by bugbear6502 on 2013-12-18
Since there seems little sign of rhythmbox's broken handling of "comment" tags being fixed ([http://ubuntuforums.org/showthread.php?t=2188626](http://ubuntuforums.org/showthread.php?t=2188626))
I am looking round for an alternative solution. EasyTag seems widely recommended, so I downloaded it.

I am struggling to find good documentation, but I am also confused as to the intended "mode of use".

START SIDEBAR
My rhythmbox working practice was to put "new" mp3 files, with some basic tags assigned using a perl script + eyeD3,
into the root of my Music directory. The mp3 files are mainly capture spoken word comedy, with metadata coming
from the EPG files.

I would then edit the tags in rhythmbox, assigning episodes to "albums" (actually series), setting years and so on.

Finally, I would use fileorganizer plugin to move/make a nice filename.
Sadly, Rhythmbox tends to corrupt comment tags (where I was storing episode synopses) and fileorganizer
needs a different python version, and no long works in 13.10.
END SIDEBAR


So - I tried opening up easytag at the root of my tree, and it "took a while" to gather the existing tags. Around 20
seconds (and I only have around 1400 files so far).

This is not very nice when I just wish to add-and-tag 4 or 5 new files.

Can anyone recommend a working practise? Should I put new files in a separate sub directory to tag them?

 BugBear

---

### Post by echotech2 on 2013-12-18
I use EasyTag.  I put new files in a separate directory (I named it "Pending"), tag files, fix up filenames as required, (I like my MP3s tagged "Title - Artist"), then move to the desired directory.  Yes, EasyTag can be a little slow if you have a lot of files in a directory.

---

### Post by ajgreeny on 2013-12-18
Give puddletag a try; it's in the repos.

I have looked at audio **tagtool**, **easytag** and **puddletag**, and find it difficult to decide which I like most; they all seem to have their odd idiosyncrasies, so try them all to see which you think does what you want.

---

### Post by bugbear6502 on 2013-12-18
> **echotech2 said:**
> I use EasyTag.  I put new files in a separate directory (I named it "Pending"), tag files, fix up filenames as required, (I like my MP3s tagged "Title - Artist"), then move to the desired directory.  Yes, EasyTag can be a little slow if you have a lot of files in a directory.

That sounds most plausible, and is what I'd guessed at.

It reminds me of "old school" Unix, where the documentation told you *exactly* what each command did
but not how the (rather clever and thoughtful) authors intended the commands (and features thereof)
to *combine* as a functional set.

 BugBear

---

### Post by tgalati4 on 2013-12-18
You need to turn off automatic scanning in *easytag*.  Look in preferences.  Modified or new tracks show up in red and require saving before you quit easytag.

---

### Post by bugbear6502 on 2013-12-18
> **tgalati4 said:**
> You need to turn off automatic scanning in *easytag*.  Look in preferences.  Modified or new tracks show up in red and require saving before you quit easytag.


I'm still very hazy on the Browser/Scanner relationship, and also the fact that the (important) rename function
seems to occupy a tiny dialog, a bit like "save as" in most software.

Where's the "automatic scanning" setting (just looked, can't find it), and what does it do?

Browser seems to have a file mode and a tree mode, but the file mode is a file tree, whilst
the tree mode navigates via the very data that you're editing.

I feel I'm missing an "overview" that would place all these pieces into a coherent (and easy to use) framework.

I'm sure easytag is convenient to use, simply because so many people say so!

 BugBear

---

### Post by tgalati4 on 2013-12-18
Settings==>Preferences==>Uncheck "Load on startup the default directory"

Because your home directory is the default directory and the load is usually set as default, it scans your entire home directory and that can take a long time.  Now you can browse to a specific music directory that needs work and any files in Red have not been recently resaved with correct ID3 tags.  It's a handy system for keeping tabs on which tracks have been fixed and which need fixing.

---

### Post by bugbear6502 on 2013-12-19
OK, I'm nearly where I need to be; one last (hopefully) question on selection.


Is there any way to select ALL the songs from either a sub-set of albums (say 2 of 6) or a subset
of artists (for scanning/editing)

 BugBear

---

### Post by tgalati4 on 2013-12-19
Not really.  You can use the search filter and check "Tag Only" and put in the Album name and a bunch of tracks will show up.  Unfortunately, there is no way to rank the Album names (alphabetical or reverse alphabetical), so you have to use the mouse to click on the tracks or shift-click to select blocks of tracks.  Once you have a bunch of tracks selected, you can modify the ID3 tags and save them with the new information.  You could add a special keyword in the comments and then use that for future searching or to keep track of which tracks have been marked up.

---

### Post by TheFu on 2013-12-19
> **ajgreeny said:**
> Give puddletag a try; it's in the repos.

I have looked at audio **tagtool**, **easytag** and **puddletag**, and find it difficult to decide which I like most; they all seem to have their odd idiosyncrasies, so try them all to see which you think does what you want.

I've been using the tag editor built-into **Clementine** (music player). It has a simple, multi-select interface.  Wish that titles could automatically sequence following the track no.  Anyway, it is another option to try out, but hardly a best solution.

---

### Post by bugbear6502 on 2013-12-20
Empirical testing (on a copy of a subset of my data) has shown:

In "Tree" (aka File/Directory) browsing, clicking a new directory loads new files,
and loses any edits you have made to old files. There is
no warning about this. Is this an option somewhere?

In "Artist and Album" browsing, changes *are* retained
as you click between various artists and albums.

However I can find no easy to (assuming you've change a handful 
of files scattered between a dozen albums from a selection of hundreds)
to easily save all your changes. The only way seems to be to select
ALL albums, then select ALL tracks, and save all tracks, at which point
saving an unchanged track is a no-op. This gives the correct results,
but has a performance issue (the displayed track list, which may be large,
is recalculated after every file-save).

The workround is to save each change as you go along, which is not
very convenient or elegant.

Have I missed an easy way out of this? I simply want to be
able to tidy up faulty/missing metadata in a collection
of around 1300 tracks, 100 albums, 40 artists.

It shouldn't be this hard.

 BugBear

---

### Post by tgalati4 on 2013-12-20
I use Control-S to save files before I leave a directory.  Yes, you are correct, changes are lost if you don't save them after you make them.  That is why the files show up in red.  Red files need to be saved otherwise any changes will be lost.  This is inconvenient for your workflow, but that is the way *easytag* works.  And you are correct, scanning large directories or saving large directories can take some time.

---

