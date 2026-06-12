---
title: "Rhythmbox Displaying Incorrect Genre"
date: 2009-03-22
forum: Multimedia Software
---

### Post by kinsei on 2009-03-22
I have recently switched over from Windows and am trying to get everything working the way I am used to in Ubuntu.

For years I have built a massive mp3 collection that has grown to over a terabyte.  I have been very good at organising all of my files and tagging them with all appropriate information over the years using Tag&Rename so my collection shows up properly in different mp3 players and devices.

I delete all tags and then regenerate them when I add them to ensure all remnants of earlier tags are gone.  I do NOT write unicode information into them as this has caused various issues over the years.  Every single mp3 program and mp3 playing device has worked flawlessly with my collection...until Ubuntu.

When I import my music into Rhythmbox player it magically starts inventing all sorts of genres that are nowhere to be found in the actual ID3 tags.  About 80% of the imported files display correctly with the Genre that I have set, but about 20% of them have many many different genres appear associated with them and I have no clue where it is pulling these values from.  I have installed Tag&Rename into Ubuntu using Wine and the genres display correctly when viewing the files with it.  If I select properties within Ubuntu on the file, genre is not one of the values displayed.  So I am not positive if the issue is one with Ubuntu or Rhythmbox, but I am willing to bet it's with Rhythmbox.

It almost seems like Rhythymbox has preconfigured Genre's for specific artists, but that doesn't really seem to make sense either because some artists have specific albums (and even individual tracks within albums) show up incorrectly when everything else is displayed properly.

Has anyone run into this situation before?  Is it a bug?

---

### Post by jpeddicord on 2009-03-22
That's weird. RB should be pulling the tags right from the files (or asking GStreamer to do so, anyway). The only reason I can think of that the tags are off could be that you have a plugin that tries to fetch them for you. You could try installing [EasyTag]("apt:easytag") and checking the tags manually on some of the files.

---

### Post by Richard85 on 2010-06-01
I have had issues with Rhythmbox in the past for exactly the same reason! What's worse is when I try to retag something in rhythmbox or easytag, rhythmbox just sets the tags back to what it thinks they should be! It's incredibly annoying! I've tried deleting the id3 info completely with EasyTag and then retagging it but to no avail rhythmbox is stubborn and wants to display file info its way.

---

### Post by Richard85 on 2010-06-01
I found something on the interwebs trying to solve this rhythmbox problem

[http://savvyadmin.com/rhythmbox-id3-tag-issues/](http://savvyadmin.com/rhythmbox-id3-tag-issues/)

The author says there seems to be a problem with ID3v1 and ID3v2 tags.

---

