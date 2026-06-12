---
title: "Mytharchive 0.21 in the Gutsy backport: It's Alive!"
date: 2008-10-07
forum: Mythbuntu
---

### Post by klc5555 on 2008-10-07
I was unable to archive any DVB recordings in the Gutsy backport of Mytharchive 0.21, as archiving would terminate at the mythreplex –demux stage. After editing mythburn.py to supply the 4 missing lines required for Mytharchive to handle  liba52, as described by Psikotik here 
[http://ohioloco.ubuntuforums.org/showthread.php?t=728747&highlight=mytharchive+fails&page=3](http://ohioloco.ubuntuforums.org/showthread.php?t=728747&highlight=mytharchive+fails&page=3)
I found that most DVB archiving would still fail and terminate at the “growisofs” stage, unless I chose an encoding profile much smaller than the size of the DVD. If the archive was close to, or over the size of the DVD, the mythburn.log showed that the calculation for how much each recording needed to be reduced in size was producing a set of files too large for the DVD and growisofs would terminate with a “no space left on device” error.

In Hardy the solution for this problem is supposedly to upgrade genisoimage from 1.1.6 to 1.1.8 from  the deb package. This solution won’t work in the Gutsy backport because of failed libc6 dependencies.

What I did was to back up /usr/bin/growisofs, /usr/bin/genisoimage, and /usr/bin/mkisofs to growisofs.bak, genisoimage.bak and mkisofs.bak respectively, just in case. Then I got the plainest plain vanilla precompiled binaries of a similar vintage of mkisofs and growisofs that I could find, from the Slackware 12.0 packages of cdrtools2.01.01a23, available here [ftp://ftp.slackware.com/pub/slackware/slackware-12.0/slackware/ap/cdrtools-2.01.01a23-i486-1.tgz](ftp://ftp.slackware.com/pub/slackware/slackware-12.0/slackware/ap/cdrtools-2.01.01a23-i486-1.tgz)

and dvd+rw-tools7.0, available here [ftp://ftp.slackware.com/pub/slackware/slackware-12.0/slackware/ap/dvd+rw-tools-7.0-i486-2.tgz](ftp://ftp.slackware.com/pub/slackware/slackware-12.0/slackware/ap/dvd+rw-tools-7.0-i486-2.tgz)

After unzipping and untarring these two packages to some subdirectory, I simply copied the Slack 12.0 mkisofs and growisofs binaries to /usr/bin/mkisofs and /usr/bin/growisofs  Then, since Slack doesn’t have or use a genisoimage, I set two symlinks named “genisoimage” and “genisofs” in /usr/bin/ and had them both point to the Slackware mkisofs at /usr/bin/mkisofs

This seems to work. I’ve archived three DVDs now, that all range from 105% to about 130% of DVD capacity at SP, and they’ve all completed successfully, with results indistinguishable from those done on Mytharchive 0.20.2 on Gutsy. I haven’t done more test runs yet, because it takes Mytharchive 2-6 hours to process these things.

Something of a PITA, I know, but no effort is too great when it comes to archiving those precious 3 Stooges episodes.  Especially the Curly ones.

Cheers. :)

---

### Post by klc5555 on 2008-10-27
An addendum to my previous post.

With Mytharchive 0.21 patched as described before on the Gutsy backport, I have still occasionally encountered the situation where, with an archive of DVB-recordings close to, or a bit above the rated capacity of the DVD, Mytharchive miscalculates, slightly, the needed adjustment to each recording to make the archive fit on the DVD. So that the resulting .iso is just slightly larger than the capacity of the DVD.

In these cases, the replaced growisofs (7.0 or 6.1) fortunately does not simply terminate Mytharchive, as does the one included in the Gutsy backport, but burns the disk anyway. This results in an archive where the last 1-2 minutes of the final recording is truncated. 

Since the patched Mytharchive does not terminate, I was able to incorporate the following workaround: I made a 5-minute recording of DVB "dead air" and I add this recording as the final recording whenever I archive DVB recordings with Mytharchive. If Mytharchive miscalculates, I lose 2 minutes of "dead air". If Mytharchive doesn't miscalculate, 5 wasted minutes doesn't reduce the capacity of the DVD by any serious margin. Either way, Mytharchive 0.21 in the Gutsy backport remains usable for me for recordings from DVB sources.

Well, at least no less usable than Mytharchive 0.20.2 was.

Maybe this will end up helping someone.

Cheers! :)

---

