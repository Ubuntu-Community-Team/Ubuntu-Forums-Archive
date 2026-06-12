---
title: "what is the most common dvd video format?"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by bluepowder7 on 2007-11-28
i'm trying to make a dvd that contains several avi video files.  most of the ones i burn actually play, but one doesn't.  oddly enough, when i compare the properties of the file that doesn't work against a file that DOES work, they use the same video and audio codecs, and the only difference that i can see is the audio bitrate (only a hair faster on the non-working file, but still under 128kbps).  on the computer, all the files work properly.

if i use ffmpeg or some other conversion program, what video output format is the simplest and most compatible with stand-alone dvd players?

dunno if it matters, but the non-working file is the last file that is burned on the dvd, and trying to replay that dvd back on the computer ALSO doesn't work.  does that mean i should try yet another burn, and add on a file called zzz.txt or something?  i've already made 3 coasters :(

---

### Post by bluepowder7 on 2007-11-30
eh, anyone at all???

---

### Post by eye208 on 2007-11-30
> **bluepowder7 said:**
> they use the same video and audio codecs
It could be the same codec, but with different settings. Most standalone players do not support all the advanced options that Xvid and DivX have to offer, e.g. Qpel (quarter pixel) and GMC (global motion compensation).

Edit: I should have read your last paragraph too. ;) Which DVD writing application was used to burn the disc?

---

### Post by bluepowder7 on 2007-11-30
> **eye208 said:**
> 
Edit: I should have read your last paragraph too. ;) Which DVD writing application was used to burn the disc?

(oh, i should clarify - that mysterious file #5 works fine on the PC, but after i burn it, i can't play it back from the dvd on the PC or on the stand-alone DVD player.  it's as if burning it onto a disc buggers up the resulting file - the "original" that's on the hard drive is still useable from the hard drive)

one of each.  first attempt was GnomeBaker or something like that - that was the worst since it made a dvd, but didn't actually make it - when i snooped in the detailed progress during burning, it said something about I/O errors, but at the end of the burn it made it seem like all got burned well - didn't say "burn failed".  of course, that disc ended up being full AND empty at the same time - had no files, occupying 3.4gigs in total.  coaster!!!

second try was the built-in Nautilus burning thing.  it burned 4 of the 5 files, which worked properly on the PC and stand-alone DVD player, but file 5 was a no-go.

third try was with Brasero, and on that one i even checked off the checksum and verify final burn options (though on verify, it barfed).  same results as with Nautilus, though.  4 out of 5, making it mostly coaster material.

all burns were at no more than 4x, and usually at the 2x to 2.5x range (i think).

these are all generic dvd blanks that i bought when i was in japan, but they've been good on all sort of other stuff like linux OS iso's and stuff.  i also tried a dvd-rw with gnomebaker at the very beginning, and that apparently is a waste of time - it'll erase the contents, but won't write anything worth a damn.  i ended up turning a GOOD dvd-rw with older avi's on it into a coaster.  i hate that program now...

---

### Post by michaelzap on 2007-11-30
Er... So do I understand correctly that you're trying to create a DVD that will play on regular stand-alone DVD players? If so, that's called "authoring" a DVD, and you can use DeVeDe or ManDVD to do that.

DVDs have a specific file structure (VOB and index files) and the videos are generally MPEG-2 and one of a couple specific sizes, frame rates, etc. The audio can be wav (huge but compatible), mp3 (small but doesn't play on all players), or ac3 (small and compatible). And of course your DVD needs to have a menu structure of some sort (visible or not), and it's nice to have chapters (and you can add alternative audio tracks and subtitles if you want those).

I use Avidemux to create my source files (audio and video as an mpg), which seems to be the best quality that I've been able to get in Ubuntu (comparable to Tempgenc on Windows). It has a template for creating DVD files as well. If you need more general info on DVD authoring, videohelp.org is a good resource.

---

### Post by bluepowder7 on 2007-11-30
well, one of the two DVD players that i have will play avi files from a dvd disc, even if it's not authored into the commercial DVD format (the other one plays only properly authored DVDs and Video CDs and that sort of thing).

so, maybe my question doesn't have an answer.  i guess i was asking:  aside from the standard DVD format that commercial releases are done it, what's the most typical encoding scheme / file format that most stand-alone DVD players will also handle, so that i can stuff my compressed videos onto one disc (4 to 6 movies on one), instead of having to lug around 4 to 6 individual discs if i wanna bring a selection of stuff to a friend's place or up to the cottage for a weekend.  it seems that a number of machines have firmware that'll read avi or mpeg or wmv, but which is most widespread?

i would assume that if i use Avidemux or some other DVD authoring software, i won't be able to cram 10 hours worth of media onto a single 4.7gig disc.

---

### Post by eye208 on 2007-11-30
I think there is no problem with the AVI formats you chose. Some time ago there was a well known problem in Linux regarding CD/DVD writing. It was called the "read-ahead bug". You can look up the details in Google. On some systems this bug would always render the last sectors of a burned CD/DVD unreadable. Jörg Schilling, the author of cdrecord, claimed it was a kernel bug in Linux. However, some other tools (e.g. cdrdao) were not affected by this bug. Back in those days I would burn all my CDs using cdrdao instead of cdrecord.

Tools that used cdrecord as their back-end usually worked around the problem by appending empty sectors to the ISO file, so the read errors would affect an unused area on the disc and all files were left intact. Gnome's default CD/DVD burning function (accessible from the context menu in Nautilus when right-clicking an ISO file) still works that way today. This is why you have to use the isosize tool when checking the MD5 checksum of such a disc. You needn't do that with discs that were written using cdrdao, because their content would be identical to the original ISO file without padding sectors at the end.

If your DVD writing tool uses cdrecord/dvdrecord, try to use growisofs instead or just append some data to the ISO prior to burning it. I think there's even an option in cdrecord/dvdrecord to do this on the fly, so the ISO does not need to be changed.

I didn't expect the read-ahead bug to still exist today, but your description matches it exactly.

---

### Post by michaelzap on 2007-11-30
> **bluepowder7 said:**
> well, one of the two DVD players that i have will play avi files from a dvd disc, even if it's not authored into the commercial DVD format (the other one plays only properly authored DVDs and Video CDs and that sort of thing).

I also have a DVD player like this, but I don't think there's any standard for such devices. I think that most of them play divx 5 and xvid files, but I've had a few that don't play for no apparent reason (recoding them works in these cases). You should review the specs of your specific DVD player to see what can be played on it, and you might also investigate whether there's a newer firmware available for it that would give you more options.

---

