---
title: "Help with burning DVD's with dvdauthor"
date: 2009-09-21
forum: Multimedia Software
---

### Post by onespeedbiker on 2009-09-21
Okay I finally found the problem. I have been trying to burn ffmpeg mpg files to a DVD using dvdauthor. The line commands are;

dvdauthor -o dvd/ -t dvd.mpg

dvdauthor -o dvd/ -T

The problem is the resulting DVD, when playing on a TV plays a widescreen video as fullscreen and cuts off the ends. DVD's made by DeVeDe don't have this problem and I converted an mpg file made by DeVeDe with dvdauthor and the problem occured again. Any idea how to fix this?

---

### Post by andrew.46 on 2009-09-21
Hi onespeedbiker,

> **onespeedbiker said:**
> The problem is the resulting DVD, when playing on a TV plays a widescreen video as fullscreen and cuts off the ends. DVD's made by DeVeDe don't have this problem and I converted an mpg file made by DeVeDe with dvdauthor and the problem occured again. Any idea how to fix this?

I have found that dvdauthor responds better if the input file has been processed by software like FFmpeg that specifically sets the aspect ratio. For FFmpeg this would be:

```
ffmpeg -i input.avi -target ntsc-dvd -sameq **[COLOR="Red"]-aspect 16:9[/COLOR]** output.mpg
```

even if the video is obviously 16:9. However if this is not an option dvdauthor allows you to arbitrarily manipulate the output with the *--video=video-opts* settings. From the man pages:

```

 --video=video-opts
      A plus (+) separated list of video options.  Dvdauthor will  try
      to  infer  any  unspecified  options.   pal,  ntsc,  4:3,  16:9,
      720xfull,  720x576,   720x480,   704xfull,   704x576,   704x480,
      352xfull,  352x576,  352x480, 352xhalf, 352x288, 352x240, nopan-
      scan, noletterbox, crop.  **[COLOR="Red"]Default is ntsc, 4:3, 720xfull[/COLOR]**


```

Note the defaults which sounds like your video. The settings fit in here:

```

dvdauthor -t -o dvd ***[COLOR="Red"]--video=16:9[/COLOR]*** -f output.mpg
dvdauthor -T -o dvd 

```

I will admit that I am relatively new to dvdauthor so I would not take this idea as authoritative but I would be tickled pink if this showed you a way to resolve your problem :).

Andrew

---

### Post by onespeedbiker on 2009-09-21
> **andrew.46 said:**
> Hi onespeedbiker,



I have found that dvdauthor responds better if the input file has been processed by software like FFmpeg that specifically sets the aspect ratio. For FFmpeg this would be:

```
ffmpeg -i input.avi -target ntsc-dvd -sameq **[COLOR=Red]-aspect 16:9[/COLOR]** output.mpg
```even if the video is obviously 16:9. However if this is not an option dvdauthor allows you to arbitrarily manipulate the output with the *--video=video-opts* settings. From the man pages:

```

 --video=video-opts
      A plus (+) separated list of video options.  Dvdauthor will  try
      to  infer  any  unspecified  options.   pal,  ntsc,  4:3,  16:9,
      720xfull,  720x576,   720x480,   704xfull,   704x576,   704x480,
      352xfull,  352x576,  352x480, 352xhalf, 352x288, 352x240, nopan-
      scan, noletterbox, crop.  **[COLOR=Red]Default is ntsc, 4:3, 720xfull[/COLOR]**


```Note the defaults which sounds like your video. The settings fit in here:

```

dvdauthor -t -o dvd ***[COLOR=Red]--video=16:9[/COLOR]*** -f output.mpg
dvdauthor -T -o dvd 

```I will admit that I am relatively new to dvdauthor so I would not take this idea as authoritative but I would be tickled pink if this showed you a way to resolve your problem :).

Andrew Andrew, thanks for the response, unfortunately it did not solve my problem. The problem is not the aspect ratio. First dvdauthor gives the following log after converting the mpg to vob files;

STAT: Processing dvd.mpg...
STAT: VOBU 3200 at 572MB, 1 PGCS
INFO: Video pts = 0.500 .. 1299.330
INFO: Audio[0] pts = 0.500 .. 1298.676
STAT: VOBU 3205 at 573MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
**INFO: Aspect ratio: 16:9**
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

also, one of the vob files is actually the mpg file and that file is still in 16:9 as. Finally the problem is not that dvdauthor turned the file into a 4:3 file; if it had the video would have been squished together. The video is 720 x 480 and the TV is 640x 480. what you usually see are black bars top and bottom that shrink the video down to size so it will fit. In this case the video remains 720x 480, but with no bars, the 720 width has the ends cut off (not squished as 4:3 would do) and only shows the middle 640 of the 720 width.

BTW, my experience is dvdauthor will not work at all, unless you specify an Aspect Ratio of either 4:3 or 16:9.

---

### Post by andrew.46 on 2009-09-21
Hi onespeedbiker,

> **onespeedbiker said:**
> Finally the problem is not that dvdauthor turned the file into a 4:3 file; if it had the video would have been squished together. The video is 720 x 480 and the TV is 640x 480. what you usually see are black bars top and bottom that shrink the video down to size so it will fit. In the case the video remains 720x 480, but with no bars, the 720 width has the ends cut off (not squished as 4:3 would do) and only shows the middle 640 of the 720 width.

Oops, my apologies for my fairly brain-dead response :(. I should never post late at night...

Andrew

---

### Post by onespeedbiker on 2009-09-21
> **andrew.46 said:**
> Hi onespeedbiker,



Oops, my apologies for my fairly brain-dead response :(. I should never post late at night...

Andrew No, don't apologise; it was not an un-intelligent response. Thanks!

---

### Post by mc4man on 2009-09-21
I recently made a couple of dvd's at sd for use in the living room (from 720p sources
While they looked fine on laptop (ws) I never did ck. on the regular tv.

(was actually more interested on how they looked on my son's hd tv, while not quite as 'good' as the orig., they came out excellent..

after seeing your post tried one on the regular sd tv and same thing, displayed fullscreen, no letterboxing.

I was about to re-rip and ck. the flags in PgcEdit when I decided to ck. the dvd player's setting.
The player was set to '4:3 pan and scan', which I think may be the default and  doesn't matter with commercial and or back up dvd's.

Changed it to '4:3 letterbox', re-inserted the dvd and it displays perfectly.

Maybe give that a try. ( though I'm going to still rip and ck.

---

### Post by onespeedbiker on 2009-09-21
> **mc4man said:**
> I recently made a couple of dvd's at sd for use in the living room (from 720p sources
While they looked fine on laptop (ws) I never did ck. on the regular tv.

(was actually more interested on how they looked on my son's hd tv, while not quite as 'good' as the orig., they came out excellent..

after seeing your post tried one on the regular sd tv and same thing, displayed fullscreen, no letterboxing.

I was about to re-rip and ck. the flags in PgcEdit when I decided to ck. the dvd player's setting.
The player was set to '4:3 pan and scan', which I think may be the default and  doesn't matter with commercial and or back up dvd's.

Changed it to '4:3 letterbox', re-inserted the dvd and it displays perfectly.

Maybe give that a try. ( though I'm going to still rip and ck. So that's what letterbox means, thanks hopefully that will in my search for a solution. I thought about a dvd player option, but the same avi converted by DeVeDe letterboxed fine with no change in settings. Also I have a $100 Dvd player that doesn't have a pan and scan feature.

---

### Post by mc4man on 2009-09-21
Probably not of much help, but info is info. 
Noting i used ffmpeg to convert and an app named Varsha to author (very basic authorer, may even use dvdauthor.

Anyway a quick rip and checking the domain stream attributes showed they had been set @ 16:9 ; automatic pan and scan : automatic letterboxing 

So with an older player (sony) being set at  automatic pan and scan the picture filled the screen.

Setting the sony as mentioned previously fixed the display

After changing the attributes with [PgcEdit]("http://download.videohelp.com/r0lz/pgcedit/")  to just 16:9 ;  automatic letterboxing and burning a new disk then the sony displayed properly, whether set to 4:3 automatic letterboxing or 4:3 automatic pan and scan

Why I'm not sure if this is useful to you....

I have newer, better dvd player that's only used Atm for pal, region 2 and region 4 disks. It doesn't have the somewhat worthless pan and scan setting and  displayed both discs properly.

Because i'm using dvd-rw disks, for curiosities sake I may see what happens if the stream attribute is set to just 16;9 or 16:9 pan and scan

---

### Post by onespeedbiker on 2009-09-22
> **mc4man said:**
> Probably not of much help, but info is info. 
Noting i used ffmpeg to convert and an app named Varsha to author (very basic authorer, may even use dvdauthor.

Anyway a quick rip and checking the domain stream attributes showed they had been set @ 16:9 ; automatic pan and scan : automatic letterboxing 

So with an older player (sony) being set at  automatic pan and scan the picture filled the screen.

Setting the sony as mentioned previously fixed the display

After changing the attributes with [PgcEdit]("http://download.videohelp.com/r0lz/pgcedit/")  to just 16:9 ;  automatic letterboxing and burning a new disk then the sony displayed properly, whether set to 4:3 automatic letterboxing or 4:3 automatic pan and scan

Why I'm not sure if this is useful to you....

I have newer, better dvd player that's only used Atm for pal, region 2 and region 4 disks. It doesn't have the somewhat worthless pan and scan setting and  displayed both discs properly.

Because i'm using dvd-rw disks, for curiosities sake I may see what happens if the stream attribute is set to just 16;9 or 16:9 pan and scan
I think you hit on a work around. I downloaded the program but I haven't figured out how to do what you did. Could you walk me through it?  Thanks

---

### Post by mc4man on 2009-09-22
It may be nothing or to no avail, but worth checking..

Do you have the linux or win version? (win versions runs ok in wine.
 
The only real diff is the interface, I use the win in wine cause I'm used to it. (win in wine has a few interface minor anoyances like some little windows get stuck, no big deal.

Anyway first you need your dvd in file format, A folder in home containing the VIDEO_TS would be fine.

 i'll need to to boot up to hardy to post a screen or 2, easy way to show

---

### Post by onespeedbiker on 2009-09-22
> **mc4man said:**
> It may be nothing or to no avail, but worth checking..

Do you have the linux or win version? (win versions runs ok in wine.
 
The only real diff is the interface, I use the win in wine cause I'm used to it. (win in wine has a few interface minor anoyances like some little windows get stuck, no big deal.

Anyway first you need your dvd in file format, A folder in home containing the VIDEO_TS would be fine.

 i'll need to to boot up to hardy to post a screen or 2, easy way to showGreat, I am indeed running in wine..

---

### Post by mc4man on 2009-09-22
I went ahead and used Varsha again, it does use dvdauthor. So this may not be your issue, (thinking that my player with no pan and scan setting could play both disks.

To show you anyway (be a little careful clicking around with the wine version, things do get stuck

Screen one is in 'trace mode', what you'll see will be a bit different, same idea though

Open pgcedit and click on the dvd icon or file -_ open dvd and browse to your VIDEO_TS folder (your home folder is found by expanding / and scroll down.
 
 Click on the video_ts and 'open', there will be a pop up about bov's, close.

Then highlight the first (or only..?) title in left side box (screen 1 ) -  Edit : the 'grey' in screen, not the yellow

Up in the taskbar will be a 'Domain'tab, click on and click on the attributes in dropdown. Disable the setting for pan and scan and click ok
screen2
Then close pgcedit and save at the prompt.

If you have more than 1 titleset (what's seen as yellow in screen one, ! only have 1 here) than check the title in that also, same method

( small note, pcgedit can do more than I'll ever know, 1 small thing I did is seen in screen 1.

Dvd author had used a post command of exit for title 1, so disk would stop there, Notice I changed it to jump to title 2 instead.

---

### Post by onespeedbiker on 2009-09-22
> **mc4man said:**
> I went ahead and used Varsha again, it does use dvdauthor. So this may not be your issue, (thinking that my player with no pan and scan setting could play both disks.

To show you anyway (be a little careful clicking around with the wine version, things do get stuck

Screen one is in 'trace mode', what you'll see will be a bit different, same idea though

Open pgcedit and click on the dvd icon or file -_ open dvd and browse to your VIDEO_TS folder (your home folder is found by expanding / and scroll down.
 
 Click on the video_ts and 'open', there will be a pop up about bov's, close.

Then highlight the first (or only..?) title in left side box (screen 1 ) -  Edit : the 'grey' in screen, not the yellow

Up in the taskbar will be a 'Domain'tab, click on and click on the attributes in dropdown. Disable the setting for pan and scan and click ok
screen2
Then close pgcedit and save at the prompt.

If you have more than 1 titleset (what's seen as yellow in screen one, ! only have 1 here) than check the title in that also, same method

( small note, pcgedit can do more than I'll ever know, 1 small thing I did is seen in screen 1.

Dvd author had used a post command of exit for title 1, so disk would stop there, Notice I changed it to jump to title 2 instead.
  That worked! thanks. Of course it does it seems a little work intensive. Do you know if pan and scan still works if requested on a player that has that option after this modification?

---

### Post by mc4man on 2009-09-22
I haven't had a chance to test those other 2 possibilities I mentioned, nor take a look at what a straight rip or what some win author's set as the default stream attributes on 16:9

 Though I've never had an issue before with correct display on the sony standalone even when it was set to p&s mode. (it wasn't set intentionally on my part to p&s

From what I see the p&s mode on a standlone, if implemented, is really a misnomer, doesn't amount to anything more than a zoom, ie. center  out
> 
Of course it does it seems a little work intensive

I think you'd find it would go very quickly in the future if needed, maybe worth checking future dvdauthor projects before burning.

( possibly there is a dvdauthor command  to not set automatic p&s as a stream  attribute ...?

---

### Post by onespeedbiker on 2009-09-22
> **mc4man said:**
> 

( possibly there is a dvdauthor command  to not set automatic p&s as a stream  attribute ...? This is what I am hoping for. As I said before DeVeDe uses dvdauthor to create it's file structure and I do not have the same issue.

---

### Post by onespeedbiker on 2009-09-22
**I found the answer**; it was something Andrew posted.

*-v video-opts*
--video=video-opts
      A plus (+) separated list of video options.  Dvdauthor will  try
      to  infer  any  unspecified  options.   pal,  ntsc,  4:3,  16:9,
      720xfull,  720x576,   720x480,   704xfull,   704x576,   704x480,
      352xfull,  352x576,  352x480, 352xhalf, 352x288, 352x240, nopan-
      scan, noletterbox, crop.  [B][COLOR=Red]Default is ntsc, 4:3, 720xfull

[/COLOR][/B]Andrew suggested I change the code from;

**dvdauthor -o dvd/ -t dvd.mpg** to **dvdauthor -t -o dvd/ --video=16.9 -f dvd.mpg**

That did not fix the problem put the solution was right there 3 commands back from the last; "**[COLOR=Red]nopanscan[/COLOR]"**. I'm guessing;

**dvdauthor -o dvd/ -v nopanscan -t dvd.mpg**

I'm away from my computer right now, but I'm sure it will work; I also noticed the default is 4:3 720xfull which is what I am seeing. If I made the change;

**dvdauthor -o dvd/ -v 720x480 -t dvd.mpg**

rather then 720xfull it may go to letterbox on it's own; I'm thinking "###xfull" and "letterbox" might be mutually exclusive, since "full" would mean always taking up the full screen.  

Anyway, we did it!   =D>

Here is the magic line command

**dvdauthor -t -o dvd/ -v nopanscan dvd.mpg**

---

### Post by mc4man on 2009-09-23
Glad you found the dvdauthor command, it's interesting that your player was using the auto p&s even though it didn't have a setting for it. (my better player ignores it, while the sony doesn't.

Small note;

While it's somewhat debated as to value, i think it's a good thing to do....

If you were to just open your authored VIDEO_TS  in PgcEdit right before burning and then  close and save at the prompt it will insert a min of 32kb gap(s) between your .ifo(s) and .bup(s)

The advantage here is this separates the .ifo and .bup so an inadvertent scratch or smudge won't damage both.
The .ifo is what tells your player how to playback the disk, the .bup is a backup in case the .ifo is unreadable.

( though some burning apps will ignore the spacing and put them back next to each other

---

