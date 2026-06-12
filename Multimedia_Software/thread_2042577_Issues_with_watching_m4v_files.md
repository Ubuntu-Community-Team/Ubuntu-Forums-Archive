---
title: "Issues with watching m4v files"
date: 2012-08-14
forum: Multimedia Software
---

### Post by DLeaser07 on 2012-08-14
Hello,
New to Forum, used Ubuntu for a while. Not a programmer, I'm just a shade-tree-tech.

Here is the issue:
For  years, when I purchase a movie/tv show, I used Handbrake to cope a .m4v  to my system and watch it with either Totem(MPlayer) or VLC, depending  on my mood. Both worked. No problems. 3 months ago, I upgraded to Ubuntu  12.04 from Ubuntu 11.10. I lost the ability to copy multiple videos from Handbrake. I do not know why. I finally got it so that I could back  up my Firefly series and after that, I was unable to watch ANY DVDs or  watch any movies that I had copied that had been encrypted before I copied them.

MPlayer and VLC both tell me that the movie is encrypted and I am missing the decrypter.
I decided that I had messed with my OS to much, so I started over. I have Mplayer, VLC, and Handbrake reinstalled along with the Ubuntu Restricted Extras on my 64-bit Ubuntu 12.04 OS and those are the only changes I have made to the fresh OS.

Help  me Obi-wan Kenobi, you're my only hope. I have enough knowledge to know  where to type, but not enough to know WHAT to type. I have the  restricted extras installed and updated. I was not made aware of any  problems with the install or update.

---

### Post by papibe on 2012-08-14
Hi DLeaser07. Welcome to the forums ):P

Try installing ffmpeg from medubuntu and the extra libraries for aac. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+aac").

Tell us how it goes.
Regards.

---

### Post by mc4man on 2012-08-14
> **DLeaser07 said:**
> Hello,


MPlayer and VLC both tell me that the movie is encrypted and I am missing the decrypter.
 I have Mplayer, VLC, and Handbrake reinstalled along with the Ubuntu Restricted Extras on my 64-bit Ubuntu 12.04 OS and those are the only changes I have made to the fresh OS.



Open up a terminal & paste this in, press enter on keyboard
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```
It should install libdvdcss2 from medibuntu

---

### Post by DLeaser07 on 2012-08-15
Thanks [[COLOR=#DD4814]**papibe**[/COLOR]]("http://ubuntuforums.org/member.php?u=774785")!

I looked into the ffmpeg and the extras. I did not have the ffmpeg, so I found a walk through and got it installed. The Extras though, I presume you are referring to the restricted-Ubuntu because all searches that I've done lead to that. I have those already. I even got the medibuntu and installed those as well. 
You're link, however, was not of much use. It told me I did not posses the permissions to view that thread. :(
Thank you for your assistance so far! I'm at least one step forward. :P

---

### Post by DLeaser07 on 2012-08-15
Mc2Man,

I have already preformed that step. I preformed it again, just to be sure, and still no go.
I updated and restarted after doing it the second time, just to be on the cautious side. any other suggestions?

thanks!

---

### Post by DLeaser07 on 2012-08-15
I have the restricted extras and the medibuntu. I have the libdvdread4, and the libdvdcss4. Should the libdvdcss4 be libdvdcss2?

---

### Post by mc4man on 2012-08-15
Your orig. post was a bit confusing, (to me), so that's why I quoted specifics.
So your current issue isn't watching commercial dvds or ripping/encoding them but instead is watching your previously ripped/encoded files? (or disc's??

---

### Post by DLeaser07 on 2012-08-15
Actually it is both.
I purchase a movie, I rip it to have a back up and be able to watch it on my computer.

Now I can no longer watch commercial DVD OR the Backup I made of it.
So it's both. (Sorry for any confusion, by trying to make it super clear, I seemed to have mucked it up more :( )
I'll be checking what codecs I need for VLC for the different files later today(since I'm at work) and will be downloading/installing the specific Codecs to see if that will work.
(I was unaware that you could look up what Codecs the file is wanting or I would have done that first).
Any other suggestions would be greatly appreciated. 9 hrs after joining the community and I've gotten so much closer to fixing this. It's a wonder why everyone doesn't do this...

---

### Post by mc4man on 2012-08-15
As far as DVD playback & vlc 

Start vlc in a terminal, then try to play a dvd (media > open disk > play
See what shows up in terminal
(before you even start please open your home folder > view > show hidden files > look for a folder named .dvdcss & delete it if you have one.

---

### Post by DLeaser07 on 2012-08-15
mc4man, before I do that.
update, I've tried a few different movies they are working again. however movies such as Live free, Die Hard still wont play, and neither will titan AE. I can understand that there might be some extra DRM stuff on Live Free, but Titan AE?? that was a fan flick from way back when? why is it still having problems? I'll do as instructed and get back with results.

Thanks! it's nice to have at least 90% of my collection back...

---

### Post by mc4man on 2012-08-15
> **DLeaser07 said:**
> I've tried a few different movies they are working again. however movies such as Live free, Die Hard still wont play, and neither will titan AE. I can understand that there might be some extra DRM stuff on Live Free, but Titan AE?? that was a fan flick from way back when? why is it still having problems? I'll do as instructed and get back with results.

Thanks! it's nice to have at least 90% of my collection back...

If there is any structure protection on Live free, Die Hard it would be minor & certainly nothing to prevent playback. Same for Titan AE.
(I've only seen a handful of dvd titles that couldn't be played on Linux, if I look around I probably have LF around here somewhere. I have a couple of thousand so many are in boxes

Try deleting the the .dvdcss folder, you may have corrupted or wrong keys in there for those 2 titles
(there is no issue deleting that folder, if concerned just rename it - .dvdcss.bak


Edit: was on a shelf - this is the widescreen release, region 1, with both pg-13 & unrated,  volume label is LIVEFREE_OR_DIEHARD_BRANCH
No issue playing - no structure protection, ect.

> ~$ vlc
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x1be1738] dbus interface: listening on dbus as: org.mpris.MediaPlayer2.vlc
[0x1b0c108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: LIVEFREE_OR_DIEHARD_BRANCH
libdvdnav: DVD Serial Number: 37418D50
libdvdnav: DVD Title (Alternative): LIVEFREE_OR_DIEHARD_BRANCH
libdvdnav: Unable to find map file '/home/doug/.dvdnav/LIVEFREE_OR_DIEHARD_BRANCH.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0002993e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00029ce5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00029d55
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00029e2e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0002aa8b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00037286
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003d50dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003db1af
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 1
libdvdnav: Suspected RCE Region Protection!!!

---

