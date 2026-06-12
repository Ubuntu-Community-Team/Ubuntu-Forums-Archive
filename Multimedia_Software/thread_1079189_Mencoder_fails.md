---
title: "Mencoder fails"
date: 2009-02-24
forum: Multimedia Software
---

### Post by Config122 on 2009-02-24
While ripping mencoder fails  :mad:..shows error in resampling..I want a command so that i can rip a Title and skipping those bad sectors..

---

### Post by andrew.46 on 2009-02-25
Hi Config122,

Can you post the full command that you used and the terminal output from this command?

Andrew

---

### Post by Config122 on 2009-02-27
Hi !!:p
The command i used was

**[COLOR="Red"]mencoder dvdnav://1 -dvd-device g: -of lavf -lavfopts format=flv -ovc lavc -lavcopts vcodec=flv:vmax_b_frames=0:vbitrate=1000 -oac mp3lame -ofps 15 -srate 44100 -channels 2 -noskip -mc 0 -nocache -o "D:\dark_knight.flv" [/COLOR]**

and the output i got was(sorry i was getting problem with the attachment)

[COLOR="red"][B]DVDNAV stream read error
a52:crc check failed
a52:error at resampling[/B][/COLOR]
:mad:

---

### Post by andrew.46 on 2009-02-28
Hi Config122,

> **Config122 said:**
> 
The command i used was
```
mencoder dvdnav://1 -dvd-device g: -of lavf -lavfopts format=flv \
-ovc lavc -lavcopts vcodec=flv:vmax_b_frames=0:vbitrate=1000 \
-oac mp3lame -ofps 15 -srate 44100 -channels 2 -noskip -mc 0 \
-nocache -o "D:\dark_knight.flv" 
```

Can I ask what this is:

```
-dvd-device g:
```

as it looks like some sort of windows drive? Do you have access to the original dvd or are you trying to use an iso? I ask mostly because it is sometimes easier to rip from the dvd *first* and *then* transcode from that ripped movie.

Andrew

---

### Post by Config122 on 2009-03-01
Hi Andrew!!!

The drive which i selected was a DVD drive..I am trying to rip directly from the DVD.. **-dvd-device g:** is itself a path to that DVD..

---

### Post by andrew.46 on 2009-03-02
Hi,

> **Config122 said:**
> 
The drive which i selected was a DVD drive..I am trying to rip directly from the DVD.. **-dvd-device g:** is itself a path to that DVD.. 

So can you just rip the movie from the dvd to start with? Syntax would be:

```
mplayer dvd://1 -dumpstream -dumpfile batman.vob
```

Just to see if this avoids the a52 error.

Andrew

---

### Post by Config122 on 2009-03-03
Hi,
Thank you for the help.

As you have suggested we can dump the dvd stream to a file(using, mplayer -dumpstream ..) but i want the files to be ripped to different formats like AVI, MP4, WMV etc. which i think can be done through mencoder only and not the mplayer.

So can you please suggest if we can skip the bad sectors while ripping or if is there any way to combine all different parts of dvd ripped for the same title (i.e. If we rip Title 1 from dvd and it has bad sectors at chapter 19 out of 23 chapters then next time i start ripping it should concatenate with first part (1 to 19 chapters) and another part with (20 to 23) chapters. 

Thanks and Regards,
Config122

---

### Post by andrew.46 on 2009-03-03
Hi Config122,

> **Config122 said:**
> 
As you have suggested we can dump the dvd stream to a file(using, mplayer -dumpstream ..) but i want the files to be ripped to different formats like AVI, MP4, WMV etc. which i think can be done through mencoder only and not the mplayer.

True, but it is easy enough to use mencoder or FFmpeg from the vob file that you have created. In fact this what I usually do myself as in my experience this seems to eliminate a lot of read errors from dvds and dvd drives. (BTW it is a small point and perhaps overly pedantic point but taking a movie from a dvd and placing it unaltered on to your computer is 'ripping', altering a movie to another format is 'transcoding'.)

Transcode will allow you to perform both ripping and transcoding in one commandline but unfortunately Ubuntu versions of Transcode are pretty much out of date and Transcode itself is not paricularly user-friendly.

> So can you please suggest if we can skip the bad sectors while ripping or if is there any way to combine all different parts of dvd ripped for the same title (i.e. If we rip Title 1 from dvd and it has bad sectors at chapter 19 out of 23 chapters then next time i start ripping it should concatenate with first part (1 to 19 chapters) and another part with (20 to 23) chapters. 

Unfortunately I am not aware of any software or techniques that will accomplish this.

All the best,

Andrew

---

### Post by Config122 on 2009-03-03
Hi Andrew !!!
 
Is there any way to pipe mplayer dumpstream with mencoder transcoding ?
Any alternate way to give output of mplayer to mencoder for conversion??

config122

---

### Post by mc4man on 2009-03-04
Out of curiosity did the straight 'mplayer dumpstream' that Andrew  suggested work with DK? (able to bypass the few unreadable sectors in title 1 - I believe there's 64 or 96 over a few cells 

Did you try your mencoder command without the dvdnav prefix? (mplayer in dvdnav mode and probably by extension mencoder have some issues with resampling audio streams on dvds and reading *some* sp disks

edit:
(also, just in terms of this title, you can't use anything that attempts to parse the whole disk. the latter half or so is all garbage with 'illegal' .ifo's. (for the most part can't be 'read', will hang many apps

---

### Post by andrew.46 on 2009-03-04
Hi Config122,

> **Config122 said:**
> Is there any way to pipe mplayer dumpstream with mencoder transcoding ? Any alternate way to give output of mplayer to mencoder for conversion??


I have not personally tried this although I believe it can be done with mkfifo. A better way IMHO is to use transcode and direct the output to FFmpeg. Others will be more skilled with this technique than me as I am still learnng Transcode :-).

Andrew

---

### Post by Config122 on 2009-03-05
Hi mc4man,

I totally agree with you, that using dvdnav gives resampling error..I have tried with the "dvd://" command also but it is not ripping the Disney DVD that i brought..(RATATOUILLE)..

"dvdnav://" rips the Disney DVD.

Is there any way to rip the Disney DVD using (**mencoder dvd://**)

The error i get by using "DVD://" using Mencoder for Disney DVD is

"**ac-tex damaged at 1 4**"

Can you tell me the reason why dvd:// cannot read the Disney DVD
or a way to avoid this error using mencoder itself.

Thanks and regards.

---

### Post by mc4man on 2009-03-05
It's been a long time since i looked at rata..., it did have an interesting sp (structure protection
The reason the dvdnav can play (dump) is it gets the proper navigation info where dvd://1 probably tries to read all the cells.
In this case there are some 'bogus' (encoded with errors) cells preceding the movies actual start.  

Here's how the ifo says to playback (cell 1 -> 2 -> 7 (7 is actual start

> ******* Start playback VTST 6 , 1   TTN 1  (1:51:02)  Title 1...
******* Playing Program 1, Cell 1 (0:00.12) (Chapter 1)
	-> sprm(7:Chapter number (or PGN)) = 1 (0x0001)
        Cell 1: Executing cell command 2.
  -- cell 2 : if ( gprm(4) == gprm(9) ) then { LinkCN Cell 4 }
	if ( 0 == 2 ) : false.
******* Playing Program 1, Cell 2 (0:00.12) (Chapter 1)
	-> sprm(7:Chapter number (or PGN)) = 1 (0x0001)
        Cell 2: Executing cell command 3.
  -- cell 3 : if ( gprm(4) != gprm(9) ) then { LinkCN Cell 7 }
	if ( 0 != 2 ) : true.
******* Start playback VTST 6 , 1   TTN 1  (1:51:02)  Title 1...
******* Playing Program 1, Cell 7 (0:55.00) (Chapter 1)
	-> 

edit:

this works so if you could tell mencoder to start 4mb in ...

```
vobcopy -v -n 1 -b 4mb -l -F 16
```

---

### Post by Config122 on 2009-03-06
> **mc4man said:**
> It's been a long time since i looked at rata..., it did have an interesting sp (structure protection
The reason the dvdnav can play (dump) is it gets the proper navigation info where dvd://1 probably tries to read all the cells.
In this case there are some 'bogus' (encoded with errors) cells preceding the movies actual start.  

Here's how the ifo says to playback (cell 1 -> 2 -> 7 (7 is actual start



edit:

this works so if you could tell mencoder to start 4mb in ...

```
vobcopy -v -n 1 -b 4mb -l -F 16
```

Thanks for the reply.

As per my knowledge "dvd://"  uses libdvdread and "dvdnav://"  uses libdvdnav. Is there any patch or some other way so that libdvdread could ignores the bogus cells of a movie and continue ripping.

Thanks and Regards.

---

### Post by mc4man on 2009-03-06
As far as mplayer, rata and dvd://

 ```
mplayer dvd://1 -ss 5
```

---

