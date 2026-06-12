---
title: "Copying cd collection to harddisk: boxsets"
date: 2009-12-04
forum: Multimedia Software
---

### Post by God Of Atheism on 2009-12-04
I'm copying all my cds to my harddisk in flac format, which all goes fine using the Rhythmbox rip button. However, there is one point of contention: double albums (or triple, quadruple or boxsets consisting of even more).

The format I use is:
~/Music/[artist directory]/[album directory]/[track number - track title].flac

Especially since Rhythmbox displays a disc number when showing the disc information, I'd expect it to also do something with that when ripping the disc, at the very least keeping that information somewhere such as in the tag (I don't know whether the tag format for flac files supports that, but when clicking on properties of an already ripped file it is displayed so it seems it does) However, when choosing a double album from the library, the tracks are sorted by track number, regardless of disc, which is annoying.

Nevertheless, since I can sort by date added, I can, as long as I take care first to rip the discs in order, get the tracks in the correct order (this will of course be fubared if I ever do a reinstall without copying the old library and instead reimporting). However, sometimes it does happen that two n-th tracks on different discs within the same boxset have the same title. In this case, when copying the second disc, I will be asked whether to overwrite the track from the earlier disc (the example I encountered was track 6, `Du Nordavind' on the double cd Aspera Hiems Symphonia / Constellation / My Angel by Arcturus and I expect to encounter this also by some of my classical boxsets). For this situation I really want the disc number to be part of the filename. How do I do this?

I found a solution from [here](http://ubuntuforums.org/showthread.php?t=1031063) pointing to [this](http://www.soundunreason.com/InkWell/?p=594), but it's a rather inelegant one. I want whatever program I use to rip to do it already. I've tried editing the library_layout_filename key for Rhythmbox using gconf-editor, but to no avail. Changing it in anyway just resets the filename to nothing in Rhythmbox. Besides, I also don't have a clue how I should present the disc number (I tried %tD and %D) nor whether Rhythmbox can recognise it at all.

Apart from Rhythmbox, I also looked into Asunder, but it didn't even list the disc number at all. So which program should I use that does behave nicely, preferably non-kde since I don't want to add all the kde libraries? Only a single directory for an album, but with a distinction between different discs within the album.

---

