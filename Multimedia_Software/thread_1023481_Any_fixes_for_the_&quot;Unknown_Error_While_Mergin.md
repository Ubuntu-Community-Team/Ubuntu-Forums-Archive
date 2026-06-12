---
title: "Any fixes for the &quot;Unknown Error While Merging&quot; error in OGMRip?"
date: 2008-12-28
forum: Multimedia Software
---

### Post by mb_webguy on 2008-12-28
I'm trying to backup a couple of my DVDs, and prefer to rip to either a mkv or mp4 with h.264 video and AAC or AC3 audio.  I usually use OGMRip for this, but since upgrading to Intrepid OGMRip always fails with an "Unknown Error While Merging" message.  I've seen a couple of Launchpad error reports mentioning this, but they don't offer anything by way of a fix.  I found one blog article that said that this could be fixed by installing the Jaunty versions of the ogmrip and libogmrip packages, but when I tried it made no difference.  I also tried installing the Hardy packages (since I didn't have this problem under Hardy) but that didn't work either.

Has anyone else had this problem, and (more importantly) has anyone found a fix?

---

### Post by XenonTW on 2008-12-30
Same problem here...I'm using Intrepid and ogmrip 0.12.2. I also tried to update to the Jaunty version (0.12.2.ubtuntu003) but it doesn't help.

Error message: "Unknown Error While Merging"
omgrip log:

```
Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16384:12242.
Setting audio delay to 0.080s.

Video stream: 1366.948 kbit/s  (170868 B/s)  size: 215130200 bytes  1259.040 secs  31477 frames

Audio stream:  128.000 kbit/s  (15999 B/s)  size: 20144108 bytes  1259.007 secs
mkvmerge -o /home/whatever/test/whatever/080412_1657.mkv --command-line-charset UTF-8 -d 0 -A -S /tmp/video.Q724MU --language 0:ger --language 1:ger --sync 0:80 -D -S /tmp/audio.I5WLMU --language 0:eng --language 1:eng --sync 0:80 -D -S /tmp/audio.7Z5KMU --language 0:ger --sub-charset 0:UTF-8 -s 0 -D -A /tmp/subp.NBBLMU --chapter-language und --chapter-charset UTF-8 --chapters /tmp/chapters.PN4KMU --title 080412_1657 
mkvmerge v2.0.2 ('You're My Flame') built on May  3 2008 17:17:05

Error: The file '/tmp/subp.NBBLMU' has unknown type. Please have a look at the supported file types ('mkvmerge --list-types') and contact the author Moritz Bunkus <moritz@bunkus.org> if your file type is supported but not recognized properly.

```

It seems that omgrip creates random filenames and mkvmerge doesn't accept it. But i really don't understand why it depends on the ubuntu version?!

Anyone an idea?! It seems to be a common problem

---

### Post by XenonTW on 2008-12-30
update: the problem is the subtitle when I choose vobsub instead of srt it works well

---

### Post by TwistedLincoln on 2008-12-30
For me, updating to the Jaunty version didn't solve the problem.  However when I updated the "mkvtoolnix" package (which contains mkvmerge) to the Jaunty version, all was well.

They should probably change the dependencies on the ogmrip deb package to reflect a specific minimum version of mkvtoolnix.

---

### Post by XenonTW on 2009-01-05
mh I tried to update mkvtoolnix but when I add the jaunty sources it shows me the same mkvtoolnix version (2.0.2-1.1) like before with Intrepid so I can't update. I did a resinstallation but no change.. same error..

Which mkvtoolnix Version do u use?

---

### Post by XenonTW on 2009-01-06
ok I installed mkvtoolnix directly from the mkvtoolnix source

[deb http://www.bunkus.org/ubuntu/intrepid/ ./]("deb http://www.bunkus.org/ubuntu/intrepid/ ./")

and now it's working without any problems.. i might be helpful for someone..

---

