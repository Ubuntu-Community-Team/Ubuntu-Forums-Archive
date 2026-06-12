---
title: "[SOLVED] How to record five adjacent shows and then split them out?"
date: 2008-12-22
forum: Mythbuntu
---

### Post by ub40d on 2008-12-22
I am interested in a documentary that consists of five episodes,
originally broadcast once a week. Now there's a channel that, in a
couple of days, will broadcast all five one after the other.

I always start the recordings 5 minutes early and end them 5 minutes
late, so as not to miss the beginning and end of the show if they are
not broadcast at exactly the right time (or if our clocks are slightly
off, though that's less likely these days).

Since I have only one tuner, this means the scheduler will only let me
record every other show, saying that the ones in between conflict with
their neighbours. Fair enough.

Now, I see that I can record all five by doing a manual override for
the first and saying start 5 mins early but end 5 + 4 * 60 = 245 mins
late. This will give me one gigantic mpeg file with all five shows.

Now the questions:

1) How can I split this into five separate recordings using the
cutlist editor? 

My answer so far: take a backup of the file before editing it, then
edit out everything but the first show, then copy the result to show1;
then restore the backup, edit out everything but the second show, copy
to show2; etc. But if there is one way of setting cut points and then
saying "split the file at those points" then I'd like to hear about
it.

2) How do I retain all the metadata for the other 4 shows, which I
currently have in the "scheduled recordings" screen but which will
disappear once these shows expire without having officially been
recorded? 

I guess it must be possible to back up something that's in the
database right now and reinject it in later in a slightly different
form...

3) Once I do have the five separate mpg files, how do I "reattach"
them to the metadata from point 2? 

I guess it should be possible to give them names matching their
original starting time and then they might be picked up, but I don't
know if the system keeps indexes that need to be rebuilt.

Long term solution of course will be to buy a second tuner!

Thanks

---

### Post by crez79 on 2008-12-22
I would say the easiest would be to remove the start early end late rule and have it record each show as usual. I think it has a standard amount it tries to start early and end late, but if there are conflicts it will record on time. There is also another setting that forces always early/late. I would try to adjust this one. You may be able to edit the times for just these shows. Otherwise you could change it before and then back afterwards.

If the plan is to keep these shows forever, You would transcode them to save space. Then the metadata could be added in the videos section.

If the plan is to watch it once or twice, I would leave it as a big mass of shows. It seems to be too much work to keep them as separate recorded tv files if just to watch and delete them. Maybe I am just lazy. :)

---

### Post by fatmonk on 2008-12-23
What platform are you recording from and what tuner card do you have?

If its a card that supports the 'multirec' functionality like a Nova-T 500, thn ethat would be your best solution.

You set the tuner up to be able to record multiple programmes from the same tuner.

So long at the programmes are on the same multiplex (they must be if they are consecutive programmes on the same channel), then Myth will use 'virtual tuners' to record each programme and in your case will flip-flop back and forwards between two virtual tuners to accomodate your recordngs.

Multirec is set up in the main backend set up under 'tuners' - I don't remember the exact menu options and button presses, but when your tuner is listed you have a button in the lower right oft the screen that access another screen to allow you to change the maximum number of recordings on a particular tuner - increase that above 1 to enable multirec.

-FM

---

### Post by ub40d on 2008-12-23
@crez79: sorry, but it doesn't seem as if the suggestion in your first
paragraph would solve my problem (recording each show without
accidentally missing one or two mins at the start/end of each because
it ends in another file). As for the rest, I tend to keep these things
forever without transcoding, on the basis that if they're good enough
to watch then they're worth keeping at the original quality, not in
degraded form. Maybe just me, as you say.


@fatmonk: YOU'RE MY MAN!! Yes, that's the ideal way of doing it. I
don't have the nova t 500 (that's the dual tuner one, right? in fact I
had my eyes on it just for this purpose, but it was out of stock at pc
world when I went there to get it) but I have a single-tuner nova usb
stick. Anyway, I went looking for your multirec option and enabled it
and now the scheduler lets me schedule the overlapping shows without
conflicts. YESS!!! Now I'm just testing this out with some rubbish
shows just to check that it actually works and if it does then it's
problem solved! Thanks a lot!


For the record here's the whole rigmarole of menus to go through to
get to that setting, and I'm not surprised you couldn't remember it by
heart :-)

main > 
utilities/setup > 
setup > 
mythbuntu [takes you to the mythbuntu control centre, different gui] > 
mythtv configuration > 
launch mythtv setup [will ask for permission to close mythbackend] > 
[drops you automatically into...] main > 
2. capture cards > 
DVB:0 [or whatever the id of your capture card is] >
recording options >
max recordings >
[changed this from 1 to 2]

---

### Post by ub40d on 2008-12-23
OK, it didn't quite all go according to plan.

I did schedule two brief adjacent shows (from bbc news) without problems and they did both record. I could even see, in "watch tv", that the dialog box mentioned two tuners being in use simultaneously during the overlap period. So far so good.

However when it came to watching the recordings, they both contained only audio: the video was all black in both of them.

Even worse: I went into "watch tv" to check whether it was a quirk of the bbc news channel at this time, and everything was black (audio but no video) on live tv too. But what about other channels? ALL channels now had no video! Damn! I disconnected the usb stick tuner and reconnected, in an attempt to reset its hardware, but it did no good: still no picture anywhere. I rebooted the whole computer and... still audio only on all channels of live tv. Damn!

I went in and disabled the "2" (multirec) turning it back to 1, and still audio only.

I deleted the DVB:0 device from the capture cards screens and reinstalled it (BAD IDEA!) and still no joy. Rebooted, too. Now I'm in a situation where I don't get ANYTHING, no audio, no video. At the frontend menu, where it says "watch tv", if I do that then it flickers for half a second and it STAYS at the menu--it doesn't even go into full-screen tv mode at all (with or without image). Helllp...

What should I do to at least get regular tv back? Any diagnostics I can run to figure out why I no longer get a signal? Is there a way to force rescanning of the hardware and autodetection and reinstallation of the usb stick tuner?

---

### Post by ub40d on 2008-12-23
Now going one by one into all the setup screens of the backend setup. Redoing scanning of all the frequencies since that was all lost when I (foolishly) uninstalled the dvb card. Hopefully this might give me back the regular channels...

---

### Post by ub40d on 2008-12-23
OK, situation back under control again. Brought the tuner back to a working state just in time not to miss the next scheduled recording at 1200... phew.

For future reference:

1) when reinstalling the dvb tuner from the backend setup's "capture card" menu option, after going through the screens of "capture card" you must also go through the other screens and in particular perform a rescan of all the frequencies because it will have forgotten all its channels.

2) the Hauppauge Nova-T stick works with the (only) setting that mentions dvb, but the name that appears where it says "that should be the name of your card" says something totally different---I can't look it up right now because I'd have to stop the backend to check. But it still works.

Back to the original problem: either I have to tweak some other option (besides changing the max number of simultaneous recordings from 1 to 2) or perhaps the Nova-T is not able to do multirec. Though one wonders why---we're not even talking of different channels on the same mux, here it's the same damn channel being recorded to two files. Jury still out.

I'll try more experiments when the box is not recording.

---

### Post by fatmonk on 2008-12-23
Hmm, I had a similar problem the first time I adde multirec as I also added it as an afterthought. I thought I'd just done something silly so deleted and added again from scratch and all came good.

It's looking more like changing an existing setup to multirec could have 'issues', unless you managed to make the same slip-ups I assumed I had made first time.

I wouldn't imagine the problem was with the Nova-T, it might be worth trying it again by removing the tuner (when your clear of scheduled recordings again!) and re-adding it with multirec settings from the start and see if that behaves any different.

-FM

---

### Post by ub40d on 2008-12-23
OK, thanks FM. Once the box is idle again I'll give your suggestion a go and then report on how it went.

---

### Post by ub40d on 2008-12-23
> **ub40d said:**
> 
2) the Hauppauge Nova-T stick works with the (only) setting that mentions dvb, but the name that appears where it says "that should be the name of your card" says something totally different---I can't look it up right now because I'd have to stop the backend to check. But it still works.


Details were:

you select
card type: dvb dtv capture card v3.x
dvb device number: 0  (nothing else can be selected)

it responds with
frontend id: dibcom7000pc

where the explanatory comment instead says
when you change this setting, the text below should change to the name and type of your card. if the card cannot be opened, an error message will be displayed.

Instead it does not mention hauppauge nova-t anywhere.


Anyway, in 2. CAPTURE CARDS I nuked the existing entry as you (FM) suggested and re-entered the above info. VERY STRANGELY, the next screen already had the max no of recordings set to 2 instead of 1. ?????? very suspicious

Then I went into 3. VIDEO SOURCES and created a new video source. BUT nothing then appeared in the listing (where there is an entry to create a new video source). Again confusing.

Then in 4. INPUT there was by now already an entry for "dvb:0 dvb-input -> none". I selected that, pressed enter and got to the "connect source to input" screen from where I did, once again, a full scan for channels.


Now, results:

1) in "upcoming recordings", do adjacent recordings on the same channel conflict (as they did before multirec)? NO, they are scheduled to record even with the overlap. GOOD.

2) when I watch live tv, do I get both audio and video? yes, and on all channels. GOOD. That's clearly better than this morning.

3) what about a test recording of two adjacent programmes, with overlap?
OK, doing it now. Already looks better than this morning, because if I go into "watch tv" while it's recording I get audio and video; and also if I go into media library / watch recordings and I go into the one being recorded, I do get audio and video there too. So that's definitely progress. One thing however has changed: it used to be that, when I went into watch tv during a recording, I'd get a dialog box saying something like: hey you, there's a recording going on, all tuners are busy, so if you want you can watch the thing being recorded, which is channel XX, otherwise tough. And even this morning I got this dialog, and during the overlap it said there were TWO (virtual) tuners in use. Now, however, I don't get that dialog box any more at all. No idea why.
Anyway, as I was writing all this, we got to the stage where the second overlapping recorded started, so I went in and checked (with both still recording) that the same piece of video appeared in both files, and it did. So I think we can declare this thing as fully working! GOOOOOD!!!

Thanks a lot once more. If you hadn't written again, I probably would have never tried uninstalling and reinstalling the tuner again and I would have never discovered that it can in fact do multirec.

This feature is going to be very useful!

I'm marking the thread as solved.

---

### Post by ub40d on 2008-12-25
OK, the multirec is now working fine and as far as
I'm concerned it's the best possible solution for
this issue. Thanks again Fatmonk!

Going back to my original 1-2-3 questions, though,
here are a few further notes on related things I
discovered in the meantime. I write these down as
notes for myself for the future, but hope they may
be useful to others too.

Assume you managed to record a couple of minutes
of each of the episodes, just to catch the
metadata (title, description etc) in the database
of stored recordings. Assume you also have a big
mpg file with all five episodes, because they were
broadcast all together another day. How can you
replace the incomplete mpgs with complete ones
extracted from the big file?

Just to keep your sanity, put bigfile.mpg next to
the others in /var/lib/mythtv/recordings. You may
also want to create symlinks with sensible names
to the other files you're going to deal with,

 ln -s 1234_2008xxxxxxxxxxx.mpg ep1.mpg
 ln -s 1234_2008xxxxxxxyyyy.mpg ep2.mpg
 ln -s 1234_2008xxxxxxxzzzz.mpg ep3.mpg

and so on.

By the way: how do I find out the mapping between
those funny numeric starttime names and the actual
names of the shows? By asking the
database. Connect to the database with

  mysql --user=mythtv --password=xxx mythconverg

and then write a simple sql query such as

 select title, subtitle, basename from recorded where title like "myshow" ;



Then the obvious thing to do would be

 cp bigfile.mpg ep1.mpg
 cp bigfile.mpg ep2.mpg
 cp bigfile.mpg ep3.mpg

(That's assuming you have enough free disk space
to do all of them; otherwise you may have to
complete processing each file in turn before
moving to the next.)

NB you may have to "sudo" some of the file
commands above, if permissions for your current
user don't let you do the writes.

Then you might expect to be able to trim head and
tail of edit each of the episodes (throwing away
4/5 of the big file each time) from within
mythtv's excellent editor. BUT THIS WON'T WORK
because, as I originally suspected, some index is
not up to date after we changed mpg files under
the system's feet. The editor won't work if you
try. Even playback will be problematic (won't even
reach the whole 5 hours of the new file).

Solution:

 mythcommflag -f 1234_2008xxxxxxxxxxx.mpg --rebuild --clearcutlist

and after that you can go into the frontend (media
library > watch recordings) and edit the file as
usual, and later losslessly transcode it to shrink
it down, as per

 [http://ubuntuforums.org/showthread.php?t=1014315](http://ubuntuforums.org/showthread.php?t=1014315)

---

