---
title: "dvd::rip What am I doing wrong?"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by utah23 on 2008-03-25
Greetings!

I've searched ubuntuforums, and any how-to's on dvd::rip on Google but I am stumped.  Transcode will only encode the first .vob of any multi-.vob file.  Let me explain: any title that's over 30 minutes gets broken into a 1GB .vob and the remainder.  For some reason, transcode won't append the other .vob in the resulting .avi.

I've tried each chapter mode while ripping and made sure my target size is one file, 9160MB.  There's plenty of space on the hard drive and I've gone so far as to reinstall Gutsy, all the latest codecs, and fixed other dvd::rip errors that have come up.  I tried to specify the frame range to be encoded but (I think) if the frame end is on the other file, it won't matter.

I've checked the Rip command(s) and noticed the number "1024" in it somewhere so is that a file size limit set for ripped titles?  Can it be changed at all?

Can anyone help and tell me what I'm doing wrong?

Thank you.

Note to Moderators: I'm not sure what happened but I meant to post this in the Multimedia thread.  So sorry!

---

### Post by dawg on 2008-03-26
Let me get this right, you've got an 8GB dvd and you want to rip it to a 9GB file, or was that just a typo and you're gunning for a 900 meg file?  Are you trying to rip a TVSHOW series or an actual movie?  I run dvd::rip on my laptop and it takes roughly 30 mins to copy the dvd to my HD and then about another 1 and a half hours to encode the move to a 1400 meg file.

---

### Post by utah23 on 2008-03-26
It wasn't a typo, I apologize I didn't explain myself better.  I thought that by playing with transcode options I could get the result I wanted: I changed the target size to the largest size thinking that would tell transcode to merge both .vob's.  They are 30-minute or so tv shows and ripping each episode isn't a problem (as long as the episode is 30 minutes or less), since they don't get ripped into two files.  I don't care so much to have an .iso of the whole disc nor for any menus, subtitles, other languages, etc.  I'm using MythDVD to hold all of 11 seasons and I've looked into making Myth play part 2 immediately after part 1 of said episode but there's a noticeable pause.

So far I've tried encoding using different codecs to no avail.  :confused:

---

### Post by xc3RnbFO8P on 2008-03-27
You can use [Avidemux]("http://www.getdeb.net/app/Avidemux")
In Avidemux open Vob no. 1  index it and append (nr. 2 will be added)
Now you can encode the episode by choosing codec on the left.

---

### Post by utah23 on 2008-03-28
Avidemux did append both .vob's but, for some reason, the video is playing 2x.  I've ripped the episode again and got the same result.  (Each .vob, when viewed before the append, plays without any hitches, btw.)

Could it be with my codecs?  I've followed every step when installing every restricted format I needed and everything is up-to-date.

I guess I could start from scratch again: reinstall Gutsy, update, install codecs, install Myth but methinks I'll end up with the same problem.  Could hardware affect anything?  A bad sector?  Bad block of RAM?

:confused:

---

### Post by xc3RnbFO8P on 2008-03-28
I am sure it is a codec problem.
Solution no. 2, use [Devede]("http://www.getdeb.net/app/DeVeDe"):
Choose dvd> convert to mpeg, Add files
I find it easer to use file manager to drag and drop the Vob's  into Add box in Devede.
See if Myth play's it.

---

### Post by utah23 on 2008-03-28
Thank you but my problems must be elsewhere.  I fire up Devede and it hangs.  I could see the file being created but it stops at 14.6MB.

Could the .vob's be corrupted somehow?

---

### Post by xc3RnbFO8P on 2008-03-29
> **utah23 said:**
> Thank you but my problems must be elsewhere.  I fire up Devede and it hangs.  I could see the file being created but it stops at 14.6MB.

Could the .vob's be corrupted somehow?

One way to see if it is, play the vob from terminal with vlc,totem or mplayer.
Vlc and totem you just have to type the name of the player.
Mplayer you type: mplayer /home/your folder/.. to the .vob and return, gives you more information than Vlc and Totem.

---

### Post by utah23 on 2008-03-29
MPlayer interrupted by signal 11 in module: decode_video

That's what I get.  Bad RAM it is, then?

I'm sorry for taking so much of everyone's time.

I found this: [http://tinyurl.com/27ldlv](http://tinyurl.com/27ldlv)   to build BadRAM (assuming, of course, the errors are on the same addresses).  If not, then my 8-yr old Mushkins need to be replaced.

---

### Post by xc3RnbFO8P on 2008-03-30
> If not, then my 8-yr old Mushkins need to be replaced

That explain a lot, and your computer 8 years old to? What is your CPU Mhz? 
Replacing Ram alone wont solve the problem
> I was also having problems with mplayer crashing
MPlayer interrupted by signal 11 in module: decode_video

[COLOR="Silver"]it helped if I turned up the RTC max freq: (As root):

% echo 1024 > /proc/sys/dev/rtc/max-user-freq

Alternatively, you can add this line to sysctl.conf:

dev/rtc/max-user-freq=1024

Then run:

/etc/init.d/sysctl reload

to make the changes permanent. Running as root seems to help considerably as well.
[/COLOR]
**I also noticed that if I had framedropping set to 'hard' then mplayer would immediately crash. Using framedropping 'enabled' instead fixed the problem.**

---

### Post by utah23 on 2008-03-30
:) Yeah, well, it's been stable until now.  Sure I overclocked the 1100 T-bird and was dual-booting Hoary with XP.  I've gone solely with Gutsy only recently (and have since throttled down my overclocking) so you could say I'm a (very) late adopter.  Can't really blame a guy for using the same hardware if it works, now can you?  :)

Luckily, the good news is Mushkin still sells PC133 RAM.

---

### Post by xc3RnbFO8P on 2008-03-30
No I won´t  :)
Let us now if it works.

---

### Post by utah23 on 2008-04-02
Ah, shucks.  My mobo gave up.  :mad: Twas' a good motherboard she was; another KT7-RAID bites the dust.  Now I'll never find out what I did wrong.

Thank you, everyone, for your input.  I'll be back.  :)

---

### Post by utah23 on 2008-04-05
Hooray!  It works.

Well, it looks like it may have been either the RAM or mobo.  I'm leaning toward the motherboard, however, since that failed.  I've upgraded almost everything: CPU, RAM, mobo, and power supply.  I had to stick with PATA, sadly, since I just got a 500GB drive weeks before the 'incident'.

Now I've just got one small problem: any video takes a long time to load (even a 546MB episode).  There are no other problems, I'm happy to report (ie. choppy playback, mismatched audio/video tracks).

I've questions whether any issues exist when playing media on an x86 install on an AMD64 x2 machine but I guess I can search the docs and forums.  :D

UPDATE:

Everything now works like they're supposed to.  RAM speed was incorrectly set and the Cool N' Quiet option was enabled.

Many, many thank yous to everyone that helped. :D

---

