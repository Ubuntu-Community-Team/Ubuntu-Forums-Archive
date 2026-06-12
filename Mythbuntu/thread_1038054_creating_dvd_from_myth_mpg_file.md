---
title: "creating dvd from myth mpg file"
date: 2009-01-12
forum: Mythbuntu
---

### Post by enchesss on 2009-01-12
what is the best way to create a dvd from a 5 Gb tv recording?

is the mpg file created by myth ok or does it need to be converted?

should the file be edited or can it be shrunk onto a 4.7Gb

---

### Post by tgm4883 on 2009-01-12
use mytharchive, thats what it's there for.  You will be able to tell it to remove commercials, so you might be able to get down to the right size.

---

### Post by klc5555 on 2009-01-12
> **enchesss said:**
> what is the best way to create a dvd from a 5 Gb tv recording?

is the mpg file created by myth ok or does it need to be converted?

should the file be edited or can it be shrunk onto a 4.7Gb


First, you can create a cutlist which will mark your recording's index to skip the commercials.

See here: [http://mythtv.org/wiki/index.php/Removing_Commercials](http://mythtv.org/wiki/index.php/Removing_Commercials)

Then you can set up and use Mytharchive to convert your recording into a DVD with commercials removed. See here: [http://mythtv.org/wiki/index.php/MythArchive](http://mythtv.org/wiki/index.php/MythArchive)

If your recording is analog, Mytharchive should work perfectly. In setting up Mytharchive you will have an easier time of it if you set Mytharchive's temp working directory to something in your user's home directory-- /home/<your_username>/mytharchivetemp   --or some such.

If your recording is dvb (from digital cable or similar), then Mytharchive may initially work perfectly, imperfectly, or not at all, depending on your specific setup. If you try it and experience dvb difficulties, they can usually be troubleshot.  

Alternatively, you can use 3rd party software for this purpose. A  frequently found combination is the encoding/muxing/demuxing tool DeVeDe to create the *.iso file (homepage: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)) and then using k3b to burn the *.iso image to DVD. This pair of programs are useful for occasions when Mytharchive has you banging your head against the wall on dvb recordings, because of audio sync or other issues.

Good luck! :)

---

### Post by SiHa on 2009-01-12
+1 for DeVeDe. I can't get Mytharchive working at all with my (DVB-T) recordings.

---

### Post by netslacker on 2009-01-12
are we looking for a "playable DVD" ? ie, one that will play in a DVD player? if so, then yes - the recording will have to be converted since a 5GB file is most likely HD and cannot play in a regular DVD player.

Correct me if I'm wrong, but mytharchive does not convert files, it only archives them.  To get a show to a playable DVD you must use DVD authoring software that can convert it and create the proper DVD formatted files.

---

### Post by klc5555 on 2009-01-12
> **netslacker said:**
> are we looking for a "playable DVD" ? ie, one that will play in a DVD player? if so, then yes - the recording will have to be converted since a 5GB file is most likely HD and cannot play in a regular DVD player.

Correct me if I'm wrong, but mytharchive does not convert files, it only archives them.  To get a show to a playable DVD you must use DVD authoring software that can convert it and create the proper DVD formatted files.

You're wrong. :)

When Mytharchive works, it does the whole enchilada: runs mythtranscode to cut commercials and/or massage audio, ffmpeg to encode/mux/demux to the necessary encoding profile, dvdauthor to set up the menus, chapters, etc., and growisofs/mkisofs (or with Ubuntu that awful wodim/genisofs nonsense unless you replace it) to create the .iso and burn it to disk as a garden-variety playable DVD.

I've found Mytharchive to be essential, easy-to-use, and nearly flawless for making DVDs from analog recordings of whatever length.

For dvb recordings, once I got Mytharchive 0.21 working with them at all, I found that I could only use Mytharchive to make DVDs (and archives) of recordings whose individual length was not longer than about 40 minutes (i.e. an hour show with commercials cut). And then, only if I cut the commercials by hand ahead of time by running mythtranscode --honorcutlist --mpeg2 -c -s  from a terminal. Dvb recordings longer than about this approximately 40 minute limit, or ones which I didn't cut ahead of time would experience progressively unacceptable audio sync on the final DVD as the playbacks get nearer the end. Never could get a solution for this.  

So, for anything dvb that I want to archive that's longer than 40-ish minutes without commercials (all movies, for example), I now just automatically go through the extra steps to run DeVeDe to build the *.iso and then k3b to burn the disk.

Cheers! :)

---

### Post by netslacker on 2009-01-12
> **klc5555 said:**
> You're wrong. :)

When Mytharchive works, it does the whole enchilada: 

Well, I stand corrected!! ;)  I've always pulled shows off of myth onto my windows or mac to convert them, but now I see it should be much easier than that, good to know...

---

### Post by enchesss on 2009-01-14
Unable to get mytharchive to work.

Have installed Devede and recoded the mpg mythtv recording file. It resized to about 2Gb and created an iso.


Saved the iso to teh desktop and right click - burn iso image and it plays in dvd player.


Thanks for help - will let you know if can get mytharchive working.

---

