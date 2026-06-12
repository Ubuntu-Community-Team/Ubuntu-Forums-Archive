---
title: "Music Library gets all messed up (Hardy)"
date: 2010-01-05
forum: Multimedia Software
---

### Post by rwigle on 2010-01-05
I have been experiencing this problem over the last few years and I am at a loss.

I have been trying to build a Music Library and can't seem to get things right. Most CD's are classical music. I have had a number of problems when I try to transfer a CD to the Music Library. For example:

1. Using Rhythymbox (0.11.5), if two tracks on a CD have the same title "Andante" then one of them gets ignored or overwritten.

2. I tried EasyTag (V2.1.4) and Banshee to sort out the tags. Within these apps things initially looked OK, but then if I try to play with Rhythmbox, the library seems all messed up. examples: I have an album with just one track now (all others seem MIA)
Another has just three (all others are MIA).

So two questions:

Q1: Could I have messed this up further by trying Banshee 1.4.3 (I guess the Music Library is handled differently)???

Q2: I think I will just start all over using ONLY Banshee OR Rhythmbox or ??? Is there a way to remove my whole Music Library (both the ogg files and any files that point to them) as a starting point?

Thanks in advance.

Another example:

In Banshee I have a Brandi Disterheft Album which shows just three cuts (9--11). The properties of track 9 show the location as .../Unknown Album/09. Track 9.ogg, but if I look in that folder I see the files for tracks 1--8. I am very puzzled here.

---

### Post by boombox1387 on 2010-01-07
Not sure how helpful I can be, but I'll try :)

Did you ever try importing from the CD with Banshee? or did you just try to change the tags?  If you only changed the tags, then Banshee shouldn't have moved anything around in your music library folder (~/Music), and it may not have even saved the tag changes to the actual track - it may have only stored the changes in its own database, which is stored in a hidden folder inside your home folder (~/.config/banshee-1/banshee.db).  The Banshee options you want to look at are:
    Copy Files to Media Folders when Importing
    Write Metadata to Files
    Update File and Folder Names

These can all be found in Edit > Preferences, though things might be a little different in yours because I'm using the development version of Banshee.

If you're going to use Banshee exclusively, I would recommend checking all of these boxes.  If you just want to use Banshee for fixing tags, you should at least make sure "Write Metadata to Files" is checked.

Also, Rhythmbox can be set to watch your Music folder for changes.  This option can be found in Edit > Preferences > Music tab > Watch my library for new files.  If you check this box, Rhythmbox should be able to find your music even if you rip it from a CD with Banshee.

It probably wouldn't be a bad idea to use one media player exclusively, though.  Personally, I like Banshee, but it's really up to you.  Hope this helps, let me know if you have more questions/problems.

---

### Post by rwigle on 2010-01-12
It seems that my problem arose largely because I was switching back and forth between Rhythmbox and Banshee to import CDs. When Rhythmbox reads a CD that it can't identify, it puts the ogg files in a folder called "Unknown Album". If you retag it, the folder name remains unchanged. (The title is changed in the rhythmbox settings in .local/share/rhythmbox/.)

By contrast, if you import an album that Banshee can't identify, and  change the Album name tags of all the tracks, Banshee renames the folder holding the music. The interaction of the two seems to have been the source of my confusion.

Now I am just using Banshee, and I have had no further problems.

P.S. I used to use EasyTag as well, just to confuse things further.

---

### Post by boombox1387 on 2010-01-12
Glad things seem to be working out better for you.

---

