---
title: "Ubuntu will not decrypt DVD"
date: 2017-01-11
forum: Multimedia Software
---

### Post by curticegough on 2017-01-11
I am using Ubuntu 16.04 LTS.  I need to watch a dvd video for school, but when I open the DVD with VLC I get this error.
 [COLOR=#ff0000]
Playback failure:[/COLOR]

 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]

 [COLOR=#ff0000]Playback failure:[/COLOR]

 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]

 [COLOR=#ff0000]Your input can't be opened:[/COLOR]

 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///media/curtice/PHYSICAL_DVD_1/VIDEO_TS/'. Check the log for details.[/COLOR]

 [COLOR=#000000]
I already have libdvdcss2, ubuntu-restricted-extras, libdvdread4, and libdvdnav4, but none of them make any difference.  Any help would be appreciated.
[/COLOR]

---

### Post by TheFu on 2017-01-11
bad disk?

Try a different player. 

Can you play the individual .VOB files?  Try mpv, mplayer, gstreamer, etc ...

---

### Post by curticegough on 2017-01-11
The disk is not bad because is plays on my TV just fine.  I have already tried my internal disk drive and my external disk drive.  I don't think using a program other than vlc will do anything either.  If I try to open the disk in nautilus, it gives me this error

Sorry, could not display all the contents of &#8220;PHYSICAL_DVD_1&#8221;: Error when getting information for file '/media/curtice/PHYSICAL_DVD_1/VIDEO_TS.IFO': Input/output error

---

### Post by TheFu on 2017-01-11
Computer DVD drives are not the same as DVD players.  Some copy protection methods take advantage of this and are designed to break in computers, but DVD players ignore the same issues and continue.

Input/output error - means a bad sector on the disk.

You can try making a mirror of the disk using a tool like **ddrescue**.  That has worked for me - it pulls the DRM over, but ignores the physical disk errors they've added for another layer of anti-computer-DRM.

---

### Post by curticegough on 2017-01-11
I tried using ddrescue and this is what it gave me.

```
curtice@curtice-Satellite-L55-B:~$ ddrescue /media/curtice/PHYSICAL_DVD_1/VIDEO_TS.IFO /home/curtice/Desktop/Science-Labs /home/curtice/Desktop/ddrescue-log.txt
ddrescue: Can't open input file: Input/output error
curtice@curtice-Satellite-L55-B:~$ 


```

> Input/output error - means a bad sector on the disk.


Is there a way to make a bad sector a good sector?  (I really have no idea what that means I just want to watch this dvd on my laptop:confused:)

P.S. Windows played these just fine when I had it last year.  How does Windows get around the "bad sector"?

---

### Post by TheFu on 2017-01-11
Bad disk.

I'd try using **ddrescue** on the entire drive device, not 1 file.  That is usually /dev/sr0 (on all my recent systems). It won't complete, but after a few hrs, you should have most of the disk in a .iso file that vlc can mount and play.

---

### Post by curticegough on 2017-01-12
OK.  I'm trying **ddrescue** and it seems to be doing *something*.  As soon as its finished, I will post the logfile and anything else that looks important.  What exactly do you mean by "bad disk"?  And if it is a "bad disk" how does the DVD player on my TV read it?

---

### Post by curticegough on 2017-01-12
So far, I have been running **ddrescue** for two hours and this is what it says.

```
GNU ddrescue 1.19
Press Ctrl-C to interrupt
rescued:     34213 kB,      errsize:     1075 MB,        current rate:        0 B/S
ipos:        286763 kB,     errors:      1,              average rate:        4063 B/s
opos:        287933 kB,     run time:    2.34 h,         successful read:     2.24 h ago
Scraping failed blocks... (forwards)
```

You said:
> It won't complete, but after a few hrs, you should have most of the disk in a .iso file that vlc can mount and play.
Does this mean that I should interrupt it?

---

### Post by TheFu on 2017-01-12
Please re-read previous posts.  Google a little about DRM where they insert bad sectors on purpose to screw with computers, but HW DVD players handle fine.
 
I would have watched it on the TV, if it were this much trouble.
Goog luck.

---

### Post by curticegough on 2017-01-20
I would still like some more help with this if anyone else knows anything.:smile:

---

### Post by cariboo on 2017-01-20
You can check the vlc error log, by going to Tools->Messages, set the verbosity level to 2 (debug) and watch for error messages. The output should look something like the screenshot

---

### Post by curticegough on 2017-01-21
I tried to load the disc in VLC, and then went to the messages like you said.  Here is the screenshot.
[IMG]https://ubuntuforums.org/asset.php?fid=268655&uid=2055470&d=1485005158[/IMG]

---

