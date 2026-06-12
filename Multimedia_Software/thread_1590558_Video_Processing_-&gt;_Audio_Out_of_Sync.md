---
title: "Video Processing -&gt; Audio Out of Sync"
date: 2010-10-08
forum: Multimedia Software
---

### Post by curioususer on 2010-10-08
Whether I am ripping a dvd with k3b, or converting a .wmv file to .avi with mencoder, or messing with a file in kdenlive, the resulting video always has audio out of sync with the video!  The original plays just fine (in mplayer, vlc, or in flash once I've uploaded it).  The converted file is out of sync whether its in mplayer, vlc, or flash once uploaded.  The only common thread is:

Original (Source: DVD, Windows Laptop, Camcorder) -> Process on Linux -> Out of Sync.

I'm running Ubuntu 10.04.  What can I do?  Thanks for your help!

(Bonus!  Also kdenlive won't let me convert to h264 for some reason, it did fine when I was running 9.x, what changed?)

---

### Post by ricardisimo on 2010-10-26
I've had quite a problem making DVDs either with all of my home videos, or compiling various TV shows onto one disc. Audio slides in and out of sync on almost every video or episode.

Anyhow, I'm looking at tovid right now to see if it indeed does a better job encoding. I just have one question: Which engine should I use, ffmpeg or mpeg2enc? Thanks.

---

### Post by ricardisimo on 2010-10-27
bumpalicious.

---

### Post by ricardisimo on 2010-11-27
I think I've discovered a curious little detail about the sync issue: The audio will be in perfect sync until a fade-to-black comes up (like a commercial for a TV show) and then the problem starts, and it takes a few minutes for the audio to slowly correct itself.

What would black scenes have to do with the audio and video lining up properly? Bizarre, no?

---

### Post by ricardisimo on 2010-11-30
No ideas?

---

### Post by ricardisimo on 2010-12-04
I keep checking discs I've made with devede, QDVDAuthor and DVD Styler, and the same issue is always there: a loss of sync right after black scenes. No one has experienced this? No one can tell me why it's happening or what to do about it? Thanks in advance.

---

### Post by ricardisimo on 2010-12-07
I'm going to try re-encoding all of my vids to DVD-suitable mpeg files with WinFF before making my DVDs with (probably) devede. I'll post back to say if this worked. Seems like a lot of extra work, but if the results are good...

---

### Post by amsterdamharu on 2010-12-07
I had a big problem trying to burn DVD/SVCD but got it working now.
[http://ubuntuforums.org/showthread.php?t=1620426](http://ubuntuforums.org/showthread.php?t=1620426)

> use devede but make sure when adding the files you check "This is  already a DVD/xCD suitable MPEG-PS file" under the file properties  "advanced options" -> misc tab

Now I re-encode most of my stuff as XVID because most DVD players can play that anyway and it's a lot smaller:

Use this for the preset in winff:

```
-f avi -r 25 -vcodec libxvid -vtag DX50 -s 352x288 -aspect 4:3 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2
```
or for 16:9
```
-f avi -r 25 -vcodec libxvid -vtag DX50 -s 352x288 -aspect 16:9  -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2  -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar  48000 -ab 128k -ac 2
```

---

### Post by ricardisimo on 2010-12-08
Wow. I cannot tell you the difference that using WinFF ahead of time makes. Amazing. Now, if only there were some way to automate the process...

The defaults on WinFF seem pretty good. Is there any particular reason I would want to use the settings you have posted here, amsterdamharu?

---

### Post by amsterdamharu on 2010-12-09
> Is there any particular reason I would want to use the settings you have posted here, amsterdamharu?I use 352x288 because I can't see the difference on my TV or small laptop screen anyway, the file size is smaller. The rest is the same.

As for automation; in winff you can select options -> check display cmd line. When choosing convert it will show you the script, copy and paste that in a textfile called convert.sh. Comment out all the echo statements (replace echo with # echo). Then I convert the lot before going to bed or something where the last statement in the file is:
```
sudo shutdown now
```It will not ask me for a password because the last line in sudoers is:
```
myuser ALL=NOPASSWD: /sbin/shutdown
```You can only edit sudoers with the command:
```
sudo visudo
```Then exit with
control + o
enter
control + x

To start the script I log out of the gui, press control + alt + F1, stop gdm and start the script:
```
sudo service gdm stop
bash convert.sh
```

The next morning I can use devede to create a VCD or like I do now just leave it because my DVD player will play the AVI files from usb.

---

### Post by ricardisimo on 2010-12-14
OK. So I'm noticing a limitation with - evidently - devede. When I make a single-layer, 4.7 GB DVD (using re-encoded video files via Winff) everything seems to go hunky dory; audio's in sync, and no pixelization. However, when I try to do the same at the double-layer size, I get problems.

Using avis, mkvs or other files directly with devede, the primary issue was audio sync, as the thread's title and early posts suggest. Using WinFF-created, DVD-suitable mpegs, the problems are breaks in audio - complete silence for short stretches - and some pretty significant pixelization.

Any clues as to how to get around this? Should I not be using devede? I like the simple interface, and I am definitely a GUI person, so...

---

### Post by amsterdamharu on 2010-12-14
Did you save the project in devede? You can open it and make sure you checked all the boxes "This is already a DVD/xCD MPEG-..." Make sure it was checked for every file or devede will re encode it and maybe messed it up.

I assume the original mpg files play without the missing audio so devede did something wrong.

---

### Post by ricardisimo on 2010-12-15
Yeah, I selected it across the board, and the simplest way to confirm that is to note that it takes just a minute or two to render the image when there is no encoding to be done. I'm going to go back and really pay attention to the mpgs and make sure there is no issue with them. I'm confident that the issue is something else, though.

---

