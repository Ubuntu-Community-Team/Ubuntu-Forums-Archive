---
title: "Media players crashing &quot;Bus Error (core dumped)&quot;"
date: 2013-10-20
forum: Multimedia Software
---

### Post by Anuovis on 2013-10-20
I have been using Ubuntu for years and the current 12.04 since it was released, never had a problem like this. 
Not sure when it started but I can't play any video files at the moment, my media players just crash.

**VLC**
Doesn't start at all. If I run it from terminal I get:

```
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
Bus error (core dumped)
```

**Totem**
Starts fine, can play mp3 files. Whenever I try to open a video file, it crashes. 

When ran from terminal:
```
(totem:22112): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'
```

During crashes (opening the video file):
```
Bus error (core dumped)
```
[B]
SMPlayer[/B]
Starts fine, crashes when I try to play either an mp3 file or a video file. Terminal doesn't give any output, just
```
This is SMPlayer v. 0.7.0 (SVN r3809) running on Linux
```

All crashes usually pop some "Ubuntu experienced internal error", "System experienced internal error" screens, sometimes a few at a time, with the option of reporting the problem. SMPlayer has a crash log of its own, it seems. I could post that if it would be helpful.

The video files I tried were .flv and .mp4
Youtube videos in the browser play just fine, a game that I have in Wine plays the video intro just fine. But I can't view any video files on my hardrive.

Things that haven't worked so far:
-restarting/updating the system
-reinstalling VLC and Ubuntu Restricted Extras
-adding my username in Audio and Pulse groups, as suggested in the answer[ here]("http://askubuntu.com/questions/165895/no-media-player-working-except-vlc-by-an-ordinary-user").

Is there any way to fix this?

---

### Post by sanderj on 2013-10-20
> **Anuovis said:**
> with the option of reporting the problem.

... and did you do that? Because that reporting also does "comparison" against existing bug reports. In other words: is it a known bug.

---

### Post by Anuovis on 2013-10-20
I did that a few times, but it did not show me any comparisons to other bugs. Is it supposed to? Did I miss it?

 I tried googling this problem but there seem to be lots of variations to this. There are also hits from as far as 2008, I have no idea how to filter them out. The Ubuntu crash reports are very long and I am not sure which parts are relevant to this problem.

If I should just wait for an update, I am more or less fine with that. What else could I do?

---

### Post by sanderj on 2013-10-20
The website should do the analysis based on Ubuntu's own one-liner, not you.

My guess in order of likelyhood:
1) local installation / configuration problem on your system. Easy to test: live-boot a fresh Ubuntu from USB-stick/CD and try VLC
2) memory problem. Test with "memtest86" in the GRUB boot menu
3) a bug in Ubuntu.

---

### Post by Anuovis on 2013-10-26
I haven't tested these yet, had a crazy busy week. But now my system pops a system error message/report after each boot into the desktop. So there is probably something corrupted within the system and a few updates I had in the meanwhile didn't fix it. I will do the memtest and most likely just reinstall the whole thing instead of hunting this down, seems like an easier solution right now.

Thank you for the help.

---

