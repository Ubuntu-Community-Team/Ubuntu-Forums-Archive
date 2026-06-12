---
title: "Copied Myth recordings but not mythconverg db. Anything I can do?"
date: 2009-11-09
forum: Mythbuntu
---

### Post by Crusty Juggler on 2009-11-09
I stupidly didn't backup my mythconverg database when upgrading to 9.10 and lost it.  Is there any way I can make my backed up recordings usable?

---

### Post by SiHa on 2009-11-09
There is a script called 'find_orphans.pl' that should be in the 'contrib' (/usr/share/docs/contrib IIRC) directory. It has a wiki page: [http://www.mythtv.org/wiki/Myth.find_orphans.pl](http://www.mythtv.org/wiki/Myth.find_orphans.pl), but mythtv.org seems to be having problems at the moment.

As I understand it, this should go through your recordings and add any that it finds to your database. Unfortunately, I don't think you'll get meaningful filenames, just the usual'2901_2009100102015.mpg'

Or, just copy them to your videos directory. At least that way you can watch the recording to see what it is, and edit the metadata to give it a sensible name.

---

### Post by klc5555 on 2009-11-09
> **Crusty Juggler said:**
> I stupidly didn't backup my mythconverg database when upgrading to 9.10 and lost it.  Is there any way I can make my backed up recordings usable?

The script you use is myth.rebuilddatabase.pl 

It will go through the unlisted recordings it finds in the storage directory indicated, and will add them to your mythconverg, one by one. The recordings will be usable.

However, the results will not be seamless. There are some less-well-documented aspects to the script. For each recording, as it runs, the script will allow you to type in title/subtitle/contents information. If you don't have this info at your fingertips (and who does?), it will just list things by file name. You can add later the title/subtitle information for each recording later from the "Watch Recordings" menu, but (unless this has changed in 0.22) not the content synopsis.

The script will indicate the channel number according to mythtv's four-digit channel convention, but will offer you the opportunity to change this. _Do not_ change the channel number, as the script will re-name the file to match, and while the recording will play fine, it will become indigestible to utilities like mythtranscode.

Finally, the script will offer to build an index for the recording using mythcommflag. While this works fine for recordings from analog sources, the resulting indexes will not be usable on digital recordings. Dvb recordings will have to have their indexes built separately and individually after-the-fact, using the command "mythtranscode --mpeg2 --buildindex -c  -s [or -i]" For which, see the mythtv wiki page on mythtranscode.

---

