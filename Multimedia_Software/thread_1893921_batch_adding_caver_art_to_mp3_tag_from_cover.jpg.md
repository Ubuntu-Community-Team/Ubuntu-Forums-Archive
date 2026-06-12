---
title: "batch adding caver art to mp3 tag from cover.jpg"
date: 2011-12-11
forum: Multimedia Software
---

### Post by BarryDocks on 2011-12-11
I have a large library of flac encoded audio files with the appropriate cover art image embedded in the metatag information plus stored in the album folder as cover.jpg.  I recently used a great little script called [flac2mp3]("http://projects.robinbowes.com/flac2mp3/trac") to convert the flac files to mp3 for my wifes ipod but this does not embed the cover art in the mp3 file it creates.  No matter I thought, so I just rsync'ed the cover.jpg to the appropriate mp3 folder.  Unfortunately, itunes does not read the cover.jpg file but apparently will read embedded cover art:(

I guess my question is, is there a tool that will automatically add the cover.jpg image to the metadata tag of the mp3 files within a folder? ideally from the command line?  There is a useful windows tool called [Mp3tag]("http://www.mp3tag.de/en/download.html") to do this but I would like to get it all done on my ubuntu server so that my wife only has to download the files.

Thanks!

---

### Post by papibe on 2011-12-11
There is a Python module called python-eyed3, and a command line tool (eyed3) that can handle adding images to mp3s. Both are in the Software Center.

Here's an [example]("http://askubuntu.com/questions/65323/bulk-export-embed-album-art-in-banshee"), and here's [project]("http://eyed3.nicfit.net/") page.

Hope it helps.
Regards.

---

