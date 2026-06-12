---
title: "[SOLVED] How to export a mythtv recording to mpeg2?"
date: 2008-12-17
forum: Mythbuntu
---

### Post by ub40d on 2008-12-17
My mythbuntu box has only a DVB-T tuner (Hauppauge
wintv nova t stick), which until a year ago was used
with a windows box. The Hauppauge-supplied windows
software was appalling but it produced .mpg files
which were essentially what came over the antenna. The
files produced by mythtv and stored in its
/var/lib/mythtv/recordings directory are still called
.mpg but are substantially larger for the same show. I
seem to understand (from
[http://www.mythtv.org/wiki/index.php/User_Manual:Introduction](http://www.mythtv.org/wiki/index.php/User_Manual:Introduction)
)that mythtv uses a format called Nuppelvideo which is
some kind of motion jpeg; if so, no surprise that the
files are larger (and that frame-accurate ff/rew is
easier).


I would like to be able to backup mythtv-acquired
recordings to external storage using that same mpeg2
format in which they were broadcast, with NO
re-encoding whatsoever, save perhaps a lossless mpeg2
to mpeg2 "obey the cutlist" on the fly. (I assume the
original mpeg2 can be losslessly recovered from the
Nuppelvideo motion jpeg, hopefully without too much
cpu tax since it seems a lightweight thing while it
records from tv.) What tool can I use for this?

I have found the Mytharchive plugin and have read the
instructions at
[http://mythtv.org/wiki/index.php/MythArchive](http://mythtv.org/wiki/index.php/MythArchive) . After
some fiddling (including some stuff discussed here
[http://ubuntuforums.org/showthread.php?t=610856](http://ubuntuforums.org/showthread.php?t=610856) such
as the infamous .ICEauthority) I managed to produce a
DVD (with menus etc) with mytharchive. Not bad.

However I am still not able to produce just a pure,
non-transcoded mpeg2 output file.

I have also installed nuvexport (via synaptic) but all
the options I see (many of which are disabled) involve
transcoding. I see nothing that lets me export as raw
mpeg2. 

I have also seen a recent thread about Mythexport; but
that, too, seems to do only transcoding.

Am I missing something?

I am not interested in the fact that there may exist
more efficient encodings: I'd just like to store the
original raw mpeg2 digital video as sent by the
broadcaster, with no loss of quality, and in a format
that I know I can play on my other computers and
standalone devices.

Thank you

---

### Post by SiHa on 2008-12-18
Firstly, you will find that the .mpg recorded from a DVB-T is just that, an MPEG2 file. Nupplevideo files have the extension .nuv. If you use one of the inbuilt transcoders, it will output a .nuv file. I think the wiki you refer to was written in the days of having to encode the output from a standard TV capture card. As you say streams that are broadcast in MPEG2 will be recorded as just that. The seektables that enable accurate searching are stored in the mysql database.

FWIW, I find that the recorded files are a similar size to those I used to get on my Digifusion PVR.

Anyway, lossless transcoding (for removing a cutlist) can be done very easily - it's built into MythTV.

Go to Setup > Setup > TV Settings > Recording profiles > Transcoders

It is possible to create a new lossless transcoding profile, bit I can't seem to get anything new to display in the list of available jobs.

So, what I did was edit the 'High Quality', and check the 'Lossless transcoding' box.

Now, go to Media Library > Watch recordings, highlight the one you want to transcode, and arrow right. Select Job Options > Transcode > High Quality.

A short time later (5-10 mins) you will have an .mpg file, untranscoded with any cutlist you have created removed. Note, this will not remove commercials that have been flagged unless you import them into the cutlist (in 'Edit' mode press 'z').

Cheers,

Simon

---

### Post by ub40d on 2008-12-20
Brilliant! Thanks a lot for your very clear instructions. I tried
them out on several files and everything worked first time.

At first I wasn't sure where the untranscoded file would end up
but I soon found out that it just replaces the original file. (It
goes to a ".tmp" file while it's being processed, then the
original is deleted and the .tmp renamed.)

A few minor issues:

1) Do you also find that this process kills the teletext
subtitles? I started with a file that definitely had them and
ended up with one that doesn't. I didn't see (never mind touch)
any options about subtitles / captions in the transcoding menu.

2) I'm glad to see that I can have several of these lossless
transcodings running at the same time: I start one, then I go to
the next file, edit out the commercials, start that too etc. Is
there any status screen that tells me whether any of these
processes are still running? (Even better would be a
little "busy" flag next to all these other mysterious icons for
the recording.)

3) Once a file has been "untranscoded", the new file no longer
has the cutlist icon (logically enough). Do you have a trick for
distinguishing the files you've already processed in this way
from the ones that have just been recorded and still need the
full treatment of ad removal and untranscoding?

Thanks a lot for your help already!

---

### Post by SiHa on 2008-12-21
Sorry - I should have mentioned that the transcoded file replaces the original!

1) Teletext - Sorry, never use it.

2) The only thing I know of is in the Information > System Status page, there's a job queue. This updates once a minute I think, so jobs don't appear immediately.

3) Afraid not, sorry. I agree, this would be useful though. I suppose if you set auto comm-flagging in the recording profiles (I think it's the default anyway). When you've "untranscoded" a recording, the comm-flag icon will disappear.

---

### Post by ub40d on 2008-12-21
1) ok, then I'll ask a more specific question in another thread for that.

2) hmmm, I checked it out and was a bit confused. It listed two programmes due for commercial flagging that not only had already been flagged, I had already cutlisted and transcoded them half an hour ago. Never mind anyway, even if it worked it's a status page that's too deeply buried in menus to be useful in normal usage.

By the way, I noticed that there is a per-recording icon that means "I'm working on this, doing commercial flagging". It would be great if that icon could also be activated while doing the transcoding jobs... Maybe worth digging into the source for that...

3) You're a clever chap! I like it!

Thanks a lot again.

---

