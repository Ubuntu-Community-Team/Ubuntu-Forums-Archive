---
title: "Old recordings?"
date: 2012-05-12
forum: Mythbuntu
---

### Post by AlecJ on 2012-05-12
I have in my /recordings folder MPEG's that date back to 06/01/11
but myth can only see recordings back to 15/2/12. 
There were a few changes to the system and I guess the older recordings are not in the data base, is there a way to put them back in?

---

### Post by Akriss on 2012-05-12
This page has your name all over it. =)

[http://www.mythtv.org/wiki/Find_orphans.py]("http://www.mythtv.org/wiki/Find_orphans.py")

Hope it helps =)

---

### Post by nickrout on 2012-05-12
> **AlecJ said:**
> I have in my /recordings folder MPEG's that date back to 06/01/11
but myth can only see recordings back to 15/2/12. 
There were a few changes to the system and I guess the older recordings are not in the data base, is there a way to put them back in?

It is not easy to put them back in, and the recommended method is to shift them into mythvideo.

---

### Post by klc5555 on 2012-05-12
There also still exists on the wiki an  older Perl script, myth.rebuilddb.pl, that was designed for the purpose of inserting old mythrecordings into a mythconverg database lacking entries for them.

See: [http://www.mythtv.org/wiki/Myth.rebuilddb.pl](http://www.mythtv.org/wiki/Myth.rebuilddb.pl)

Read the instructions incorporated in this script carefully if you choose to use it. It was a lifesaver for me at one time, but I haven't used it in more than a couple of years and I'm not certain current versions of Perl still support it. It should still work OK on mysql, at least through 5.1, but does have quirks. In particular, it was developed prior to Myth 0.21, and so must be run individually on each directory that TV storage is on. As it chugs along file by file, it will give you an opportunity to add metadata for title:subtitle --if you don't have this information, the database entry will be created under the mythtv filename, and you'll have to edit the metadata later from the frontend. The keyframe index for the file (for jumping forward/backward) will likely not be correct, and mythcommflag --rebuild or mythtranscode --mpeg2 --buildindex will likely have to be run on these added recordings at some later time. And, even though you may correctly add the duration of each program file, e.g. "1 hr" or whatever, the recordings index will list the show as something like "9:00 AM - 11:00 PM" But this is just a cosmetic issue.

When the script runs it's very, very slow. If you have many recordings, a run on a directory may an hour or two. But, if the script runs, when it's done the end result is that the missing recordings are in mythconverg, even if you do have to massage the metadata and some of the frame indexes.

So give it a go, if you wish. Your mileage may vary, and run a backup of your mythconverg database before firing this thing up if you choose to try it.

---

### Post by nickrout on 2012-05-13
> **klc5555 said:**
> There also still exists on the wiki an  older Perl script, myth.rebuilddb.pl, that was designed for the purpose of inserting old mythrecordings into a mythconverg database lacking entries for them.

See: [http://www.mythtv.org/wiki/Myth.rebuilddb.pl](http://www.mythtv.org/wiki/Myth.rebuilddb.pl)



Woo I am pretty sure this script is well deprecated. Use with extreme caution.

Be aware the mythtv database guru Michael Dean always recommends transferring to the videos part of mythtv. He should know and I would never go against his advice on dB issues.

---

### Post by klc5555 on 2012-05-13
> **nickrout said:**
> Woo I am pretty sure this script is well deprecated. Use with extreme caution.

Be aware the mythtv database guru Michael Dean always recommends transferring to the videos part of mythtv. He should know and I would never go against his advice on dB issues.

For once, we agree :)

But unlike many an old once useful script on the wiki, this one has not been scrubbed, implying it is likely not to be any more hazardous now than it ever was. So, if the OP has eaten all his vegetables, done an up-to-the-minute mythconverg backup (and knows how to restore from it if necessary), and is willing to take personal responsibility, he may want to give it a go.  

The script may need an extra Perl module or two installed than Mythbuntu supplies by default. When I used to use this script, I also noted that it tended to need to be run sudo, and that on occasion would not take its command-line options --these options sometimes had to be edited into the script itself. A bit quirky.

---

