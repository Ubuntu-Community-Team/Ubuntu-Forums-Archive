---
title: "Smplayer Woes (again)"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by yochaigal on 2008-02-23
Hi. I recently upgrade to SMPlayer 0.6.0rc2 to fix some pause/unpause problems.
So here's the problem: from time to time when i open a video (my default player is SMPlayer). The audio plays, and the video is clearly going, but I get no video (and no controls either).  
I can play the video in any other player.

What gives?

thanks

---

### Post by Bubba64 on 2008-02-23
Here is a post on plugins and programs and players needed to make everything work better togother.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by rvm4000 on 2008-02-23
Is the video blank?

Have you tried to enable (or disable) the option "Don't repaint the background of the video window" in Preferences->Advanced?

---

### Post by yochaigal on 2008-02-23
Hi guys.

I tried to disable/enable that options "don't repaint the background window" and it made no difference.  
I don't see how checking those plugins will help; I can play everything in every other player.

thanks!

---

### Post by rvm4000 on 2008-02-23
Could you explain a little better what the problem is?

Instead of video there's a black window?

The video widget is hidden and only the control and menus appear?

No main window at all?

Didn't this problem happen in a previous version? Which one were you using before?

---

### Post by yochaigal on 2008-02-23
Here is a screen shot of it playing.

---

### Post by yochaigal on 2008-02-23
And no, this problem has never happened before. The problem I had before was that I couldn't pause and unpause video playback with the same key.

---

### Post by rvm4000 on 2008-02-23
You were using before smplayer 0.5.62, weren't you?

I think the only change made since that version which could produce a problem like this is a fix in the colorkey.

What video driver are you using? (you can see it in Preferences->General)

If it's xv then try to change the colorkey in Preferences->Advanced.

If that doesn't fix it, try other video drivers, like x11 or gl, and see if the problem still happens or not.

---

### Post by yochaigal on 2008-03-02
Ok a little discovery:
The problem still exists, but if I run SMPlayer in its own window it works---

Any Ideas?

---

### Post by rvm4000 on 2008-03-02
Indeed it seems a problem when embedding the mplayer window in smplayer.

Does this problem happens too with the other video drivers (gl, x11...)?

---

### Post by yochaigal on 2008-03-02
Yes, this problem persists regardless of whether I'm using xv, x11, gl or whatever.

---

### Post by rvm4000 on 2008-03-02
And can you confirm that the previous version 0.5.62 worked ok?

Did you update something else? (like Qt)

Have you tried to delete (or move) your ~/.smplayer/smplayer.ini?

---

### Post by yochaigal on 2008-03-02
This problem didn't happen in the previous version, no.  To my knowledge i haven't updated qt (or any "cute" related software).  

but maybe you're onto something.

thanks

---

### Post by rvm4000 on 2008-03-03
I think the only thing I changed which maybe is related to this problem is a fix in the way to pass the colorkey to mplayer. But it works for me in my suse and in ubuntu feisty.

Could you test this binary?
[ftp://ftp.berlios.de/pub/smplayer/ubuntu/smplayer_nohexcolorkey.tar.bz2](ftp://ftp.berlios.de/pub/smplayer/ubuntu/smplayer_nohexcolorkey.tar.bz2)

Just uncompress the binary in /tmp for instance and run it. Does it fix the problem?

---

### Post by yochaigal on 2008-03-03
I changed the colorkey--- it made no difference.
II will extract that tarball later and try running an avi through it--- but remember, this problem is off and on (I would say about half the time I play videos the problem occurs).

thanks

---

### Post by yochaigal on 2008-03-04
Using that version of smplayer did not fix the problem; in fact it's now worse! I can no longer play any files in smplayer; I am currently using mplayer-totem.

---

### Post by yochaigal on 2008-03-04
okay nevermind,  when I enabled the "change volume just before playing" the debug gave an error.  I disabled it and now it runs.... i'll test it to see if it stays working.

---

### Post by yochaigal on 2008-03-04
So the problem returned with my normal player, then i tried the download and it seemed to fix it.  What do I need to do to make my default player work like the one I downloaded?

thanks

---

### Post by rvm4000 on 2008-03-05
Now that you confirm that the modified version doesn't have this problem, I'll try to find out what's wrong in the code in version 0.6.0rc2, as I thought that code was right.

Could you answer the following?

What version of mplayer do you have installed?
What version of Qt?
What version of Ubuntu?
Are you using a 64bit distro?

---

### Post by yochaigal on 2008-03-05
MPlayer 1.0rc2-4.1.3
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Ubuntu Gutsy Gibbon, 32-bit Version.
I can't figure out which version of qt I'm using, I assume it's qt4.

thanks!

---

### Post by rvm4000 on 2008-03-05
> **yochaigal said:**
> I can't figure out which version of qt I'm using, I assume it's qt4.

In smplayer, Help->About Qt.

---

### Post by yochaigal on 2008-03-05
QT Open Source Version 4.3.2.
god bless trolltech..  even if their phone didn't work out

---

### Post by rvm4000 on 2008-03-05
I have installed a Ubuntu Feisty in a virtual machine. I suppose I'll have to update it to Gutsy to see if I can reproduce the problem.

Does anyone else with Gutsy have this problem?

But this is very strange. The problem seems to be in the value passed to the -colorkey option, but the colorkey is used by xv only I think, but you say it happens too with x11 and gl/gl2. Strange.

I've only seen a similar problem some time ago. It only affected xv. The video went blank after closing a dialog. Opening a menu or moving the window made the video to come back. The problem seemed to be a repaint of the window by Qt where mplayer displayed the image. I fixed it avoiding that repaint (if the option "Don't repaint the background of the video window" was checked).

---

### Post by rvm4000 on 2008-03-06
Could you test this other binary and tell me if it works?
[smplayer_nocolorkey.tar.bz2](ftp://ftp.berlios.de/pub/smplayer/ubuntu/smplayer_nocolorkey.tar.bz2)

---

### Post by Tiftof on 2008-07-15
I think I'm having the exact same problem. But I do get video when disabling compiz. Any solution yet?

---

