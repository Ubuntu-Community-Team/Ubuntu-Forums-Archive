---
title: "dvd ripping"
date: 2010-09-28
forum: Mythbuntu
---

### Post by Turbocopter on 2010-09-28
I just started loading my system with my dvd collection.  So far no real issues except that every Disney DVD that I have tried to rip end with the ripper dumping after a few minutes.  I have loaded 90 dvds so far with no issues, now with the Disneys it kicks me out of the rip with every disc.  If I go back to non-Disney discs it rips fine again.  Any special codecs or permissions patches that you have to have to do Disney stuff?

---

### Post by klc5555 on 2010-09-29
> **Turbocopter said:**
> I just started loading my system with my dvd collection.  So far no real issues except that every Disney DVD that I have tried to rip end with the ripper dumping after a few minutes.  I have loaded 90 dvds so far with no issues, now with the Disneys it kicks me out of the rip with every disc.  If I go back to non-Disney discs it rips fine again.  Any special codecs or permissions patches that you have to have to do Disney stuff?

The myth ripper is OK, but can't do a lot of stuff. You need a full array of ripping tools to handle everything.

The problem with a lot of Disney/Sony discs is that they show the ripper a large number of titles, like 99, of which 98 are wrong and fragmentary, and most rippers (including Myth's) can't tell which is the one valid title. Dumb analog DVD players, however, have no trouble following the one valid title.

One workaround is to play the disc using VLC. While the disc is playing, correctly, you can right-click on the video window and from there VLC will tell you which title of the 99 is playing. 

This exact title is the one you rip, either using VLC itself for the rip, or, if you prefer somewhat higher maximum quality than VLC can deliver with its 8192 maximum bitrate, then using some other 3rd-party tool like HandBrake to handle that title.

---

### Post by Turbocopter on 2010-09-29
Thanks for the info.  That does help my understanding.  Does Handbrake rip in ISO format or another one that supports the menu support on the DVD?  I read that the next release of Mythbuntu will have full ISO support.  I wonder if it will also play files ripped with Handbrake?

---

### Post by klc5555 on 2010-09-29
> **Turbocopter said:**
> Thanks for the info.  That does help my understanding.  Does Handbrake rip in ISO format or another one that supports the menu support on the DVD?  I read that the next release of Mythbuntu will have full ISO support.  I wonder if it will also play files ripped with Handbrake?

The current version 0.9.4 rips only to MP4. The earlier version 0.9.3 (which is a tad difficult to find nowadays) does MP4 and AVI. Of course, the DVD menu is dropped --only the actual ripped title is in the file. 

I have no particular difficulty playing these files in Mythvideo. Though since I tend to use Mythtv 0.21 and I tend to output to AVI, I normally use mplayer as an external player in Mythvideo to handle the playback. Mythtv 0.21's internal player doesn't do AVIs. Later versions of Mythtv's internal player are supposed to be able to handle HandBrake's formats directly.

When outputting from HandBrake with a bitrate of 8192 (same as VLC's maximum) I've found the video quality of the HandBrake file, in those cases where I've been able to compare, to be somewhat superior not only to a VLC rip, but also to a "Perfect" ripped .vob file done with Myth's ripper., at least in my own opinion. I never use the "ISO" rip option in Mythtv.

Note that once the proper title number in a Disney/Sony disc has been identified by VLC, Myth's own ripper can frequently do a satisfactory "Perfect" rip of that specific title when you have directed the ripper to it.

---

### Post by Turbocopter on 2010-09-29
> **klc5555 said:**
> The current version 0.9.4 rips only to MP4. The earlier version 0.9.3 (which is a tad difficult to find nowadays) does MP4 and AVI. Of course, the DVD menu is dropped --only the actual ripped title is in the file. 
 
I have no particular difficulty playing these files in Mythvideo. Though since I tend to use Mythtv 0.21 and I tend to output to AVI, I normally use mplayer as an external player in Mythvideo to handle the playback. Mythtv 0.21's internal player doesn't do AVIs. Later versions of Mythtv's internal player are supposed to be able to handle HandBrake's formats directly.
 
When outputting from HandBrake with a bitrate of 8192 (same as VLC's maximum) I've found the video quality of the HandBrake file, in those cases where I've been able to compare, to be somewhat superior not only to a VLC rip, but also to a "Perfect" ripped .vob file done with Myth's ripper., at least in my own opinion. I never use the "ISO" rip option in Mythtv.
 
Note that once the proper title number in a Disney/Sony disc has been identified by VLC, Myth's own ripper can frequently do a satisfactory "Perfect" rip of that specific title when you have directed the ripper to it.
 
My friend built his mythbox a few years ago and it took him forever to work it all out, but he wrote a lot of his own code to do it.  One of the things I thought was cool about his from the beginning was that his collection was the full dvd with menus and extras, so that has for better or worse become my benchmark.  
 
The very last thing you said was that if vlc played it first and recognized the correct title number that the myth ripper may rip after that satisfactorily?  Do I have to call up the myth ripper somehow from vlc to get that to happen or just playing it once in vlc may do the trick?  If you could explain that a little better I would be very appreciative.  I am totally green when it comes to Mythbuntu and linux in general.  I am a total newby.
 
I am very interested.  Thanks so much for your help.  I look forward to hearing more.

---

### Post by klc5555 on 2010-09-30
> **Turbocopter said:**
> My friend built his mythbox a few years ago and it took him forever to work it all out, but he wrote a lot of his own code to do it.  One of the things I thought was cool about his from the beginning was that his collection was the full dvd with menus and extras, so that has for better or worse become my benchmark.  
 
The very last thing you said was that if vlc played it first and recognized the correct title number that the myth ripper may rip after that satisfactorily?  Do I have to call up the myth ripper somehow from vlc to get that to happen or just playing it once in vlc may do the trick?  If you could explain that a little better I would be very appreciative.  I am totally green when it comes to Mythbuntu and linux in general.  I am a total newby.
 
I am very interested.  Thanks so much for your help.  I look forward to hearing more.

While playing any portion of the movie in VLC you may right-click on the playing window. In the drop-down menu complex that appears you can navigate to playback and title. This will give you the number (between 1 and 99) of the title on the disc that is playing. Say "56" (or whatever). This is the title number you need for your ripper, whichever one you use. You are now done with VLC (Unless you want to do the rip with VLC itself. And in that case one of the numerous online guides can show you how to use the convert/save functions in VLC --the Linux version works very similarly to the Windows version.)

Run whatever ripper (including Myth's) you care to use. When it scans the disc, it will default to the number of "longest" of the 99 titles on the disc as being the one to rip. The one thing you can guarantee is that will be the wrong title, and will give you a scrambled video and audio jumble. Change your ripper to the correct title number, as previously determined. If using myth's ripper, also click it over from "ISO" rip (which is pretty useless to begin with, as the "iso"s it produces cannot in turn be backed up onto plastic in playable fashion) to "PERFECT". Set the audio to AC3 (if desired) and attempt the rip of the correct title number.

Now Myth's ripper is fairly fussy, and may still bomb out for a whole host of reasons, including slightly dirty discs or discs with imperfections, or for no clear reason at all. But it should still be the first one you rely on, as Myth will also attempt to give the resulting .vob file a frame index in the database, so that you may pause, ff, and back up in your ripped video as you would in any other Mythtv recording.

If the myth ripper fails, then you go to one of your preferred 3rd party rippers, including VLC itself, from which you can rip the title (most easily) to an .mpg file, one that in turn can be added to Mythvideo and frame-indexed like most other manually added recordings.

---

### Post by tgm4883 on 2010-09-30
> **klc5555 said:**
> 
Run whatever ripper (including Myth's) you care to use. When it scans the disc, it will default to the number of "longest" of the 99 titles on the disc as being the one to rip. The one thing you can guarantee is that will be the wrong title, and will give you a scrambled video and audio jumble. Change your ripper to the correct title number, as previously determined. If using myth's ripper, also click it over from "ISO" rip (which is pretty useless to begin with, as the "iso"s it produces cannot in turn be backed up onto plastic in playable fashion) to "PERFECT". Set the audio to AC3 (if desired) and attempt the rip of the correct title number.


hmm. Now I don't use the mythtv ripper as I don't have optical drives in any of my mythboxes, but wouldn't the ISO option give you full menus and extras? 

> **klc5555 said:**
> 
Now Myth's ripper is fairly fussy, and may still bomb out for a whole host of reasons, including slightly dirty discs or discs with imperfections, or for no clear reason at all. But it should still be the first one you rely on, as Myth will also attempt to give the resulting .vob file a frame index in the database, so that you may pause, ff, and back up in your ripped video as you would in any other Mythtv recording.

If the myth ripper fails, then you go to one of your preferred 3rd party rippers, including VLC itself, from which you can rip the title (most easily) to an .mpg file, one that in turn can be added to Mythvideo and frame-indexed like most other manually added recordings.

I rip my disks on my desktop PC to h264 and I am able to ff, rw, skip. Is there something I am missing here?

---

### Post by klc5555 on 2010-09-30
> **tgm4883 said:**
> hmm. Now I don't use the mythtv ripper as I don't have optical drives in any of my mythboxes, but wouldn't the ISO option give you full menus and extras? 

Maybe, if it worked. But the original poster's problem was that the ISO rip doesn't work with these wonderful Disney/Sony 99-track discs. Hence this thread. 

I also tend not to use the ISO option in general, because its output doesn't appear to be easily archivable onto a backup DVD. "PERFECT" output .vobs are at least easily transcodable and archivable as needed, as are most 3rd-party rips. And I usually don't give a bleep about extra features. But that's just me.


> **tgm4883 said:**
> I rip my disks on my desktop PC to h264 and I am able to ff, rw, skip. Is there something I am missing here?

Well, h264 is only one of many, many options. For AVIs that I've ripped with HandBrake 0.9.3 or made with transcode, I often have to use the -idx option in mplayer as the external viewer to have full navigation options. With MPEG-TS or MPEG-PS stuff that I've done with VLC, once added to mythvideo (again, this is 0.21, as I wrote earlier) I have to build my own index by: mythtranscode --mpeg2 --video --buildindex -i[filename]. Likewise, whenever the mythripper has given me an unusable index (the fairly frequent 30-minute index for a 2-hour feature film) I've tended to rebuild the frame index in the same fashion with mythtranscode.

Otherwise, jumping around in videos freshly added to Mythvideo for me just tends to produce the index OSD message "00:01 of "00:01" and bops me back to the start of the playback. I suppose Mythvideo 0.22 and/or 0.23 have eliminated much of the messiness of importing 3rd-party rips.

---

### Post by tgm4883 on 2010-09-30
> **klc5555 said:**
> Maybe, if it worked. But the original poster's problem was that the ISO rip doesn't work with these wonderful Disney/Sony 99-track discs. Hence this thread. 

I also tend not to use the ISO option in general, because its output doesn't appear to be easily archivable onto a backup DVD. "PERFECT" output .vobs are at least easily transcodable and archivable as needed, as are most 3rd-party rips. And I usually don't give a bleep about extra features. But that's just me.
[QUOTE=klc5555;9908636]

Hmm, I'm not quite sure I understand. Are the ISO's that it produces not valid image files?


Well, h264 is only one of many, many options. For AVIs that I've ripped with HandBrake 0.9.3 or made with transcode, I often have to use the -idx option in mplayer as the external viewer to have full navigation options. With MPEG-TS or MPEG-PS stuff that I've done with VLC, once added to mythvideo (again, this is 0.21, as I wrote earlier) I have to build my own index by: mythtranscode --mpeg2 --video --buildindex -i[filename]. Likewise, whenever the mythripper has given me an unusable index (the fairly frequent 30-minute index for a 2-hour feature film) I've tended to rebuild the frame index in the same fashion with mythtranscode.

Otherwise, jumping around in videos freshly added to Mythvideo for me just tends to produce the index OSD message "00:01 of "00:01" and bops me back to the start of the playback. I suppose Mythvideo 0.22 and/or 0.23 have eliminated much of the messiness of importing 3rd-party rips.[/QUOTE]

Must be fixed in 0.22 and 0.23 then.

---

### Post by flactemnad on 2010-11-04
I know this is a bit late, but maybe it will help the next person.  For those Sony & Disney company videos I use VLC player to watch the DVD and see what titles are being played for the main feature and extra features.  Then use K9copy to open the disc and select only those related titles and features that I want, like subtitles, extra language tracks or whatever.  Then rip that to an ISO file.  You then have a playable movie with the audio and subtitles available through the on screen menu options.  Most DVDs I buy are fairly easy for me to put into the on-system library, but Sony & Disney are always working on new ways to stop me from viewing their products.  (I've nearly stopped purchasing their releases due to the pain that they are to process!)

---

### Post by klc5555 on 2010-11-04
> **flactemnad said:**
> I know this is a bit late, but maybe it will help the next person.  For those Sony & Disney company videos I use VLC player to watch the DVD and see what titles are being played for the main feature and extra features.  Then use K9copy to open the disc and select only those related titles and features that I want, like subtitles, extra language tracks or whatever.  Then rip that to an ISO file.  You then have a playable movie with the audio and subtitles available through the on screen menu options.  Most DVDs I buy are fairly easy for me to put into the on-system library, but Sony & Disney are always working on new ways to stop me from viewing their products.  (I've nearly stopped purchasing their releases due to the pain that they are to process!)

The other reason I never rip to .iso (other than the fact I tend to find the extra "features" to be obnoxious) is that the .iso files which the mythtv ripper makes (at least through 0.21 --I'm not aware that this has changed), while perfectly playable by mythvideo, cannot in turn be burned onto plastic as a backup and be playable. On the other hand, the "Perfect" rips (which also automatically include all the subtitles and language audio tracks, selectable from the onscreen menu) can easily be archived onto plastic as a playable .iso by using Devede or similar.

This is also the reason I tend to use VLC to find the correct "title" on those annoying Disney/Sony discs, but only use VLC as a last resort to do the actual rip. The max picture quality that VLC can deliver to a rip seems to be somewhat less than, say, handbrake or the mythtv ripper. But more importantly, while all VLC rips I've done of whatever format play fine in mythvideo, I've never been able to, in turn, successfully create an .iso for backup from a VLC rip. Mencoder always seems to bomb out at about 10%. I've never had this issue with handbrake's output, nor with a .vob file created by the mythtv ripper in "Perfect" mode.

---

### Post by Turbocopter on 2010-11-06
Hi all,
 
     I got it all figured out.  A friend told me that he uses two free programs on his window machine if the the mythbox ripper does that.  First DVDFAB, then DVDShrink to convert them to no compression ISO's.  Then he transfers them to his mythbox converted already.  Since I have fully networked my machines now, I put my mythbox behind my entertainment center and make all adjustments on my windows machine.  I also transfer any discs I rip on my windows machine using the above method, open my mythbox window on my windows machine and drag the newly ripped dvd ISO into that window and in a few minutes it is in its new home.  It is working perfectly without having to physically touch the mythbox at all.  Perfect!  Thanks for all your input and help!
 
Problem Solved

---

### Post by dakota34 on 2010-11-06
2nd dvd shrink, I use it in xp running in virtualbox to copy & shrink my dvds into 4.5 GB ISOs b4 transferring to a NAS, haven't been able to find a linux equivalent.

---

### Post by rhpot1991 on 2010-11-08
> **dakota34 said:**
> 2nd dvd shrink, I use it in xp running in virtualbox to copy & shrink my dvds into 4.5 GB ISOs b4 transferring to a NAS, haven't been able to find a linux equivalent.

Try k9copy, dvdrip, or makemkv (this one not in ubuntu).

You can also make ISOs pretty simply with gddrescue: ddrescue /dev/dvd name.iso name.log

If you add the log file then you can stop and resume ripping at any time.

---

