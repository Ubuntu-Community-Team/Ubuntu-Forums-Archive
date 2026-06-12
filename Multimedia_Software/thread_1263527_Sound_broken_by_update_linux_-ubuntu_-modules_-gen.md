---
title: "Sound broken by update: linux -ubuntu -modules -generic  version 2.6.24-24.40"
date: 2009-09-11
forum: Multimedia Software
---

### Post by bw44 on 2009-09-11
I've been running Ubuntu 8.04 since it came out and have never had sound problems -- until Sept 9 when I applied  the following update:
```
Commit Log for Wed Sep  9 08:06:03 2009

Upgraded the following packages:
linux-ubuntu-modules-2.6.24-24-generic (2.6.24-24.39) to 2.6.24-24.40

```
Since then I've had no sound on my right audio channel (either on the built-in laptop speaker or an external one.) This is true for all audio applications I use or could test (Skype, VLC, Flash Video, Mplayer, Rhythmbox, etc.) 

My machine dual-boots to Windows XP and sound continues to work fine on that system.

I would like to back out the Ubuntu update, but don't know how to do it, or if it's even possible.  I thought I might uninstall  it with the Synaptic Package Manager, since there is an earlier version, linux-ubuntu-modules-2.6.24-24-generic 2.6.24-24.37 (but not .39, which the log led me to expect).  But when I marked linux-ubuntu-modules-2.6.24-24-generic 2.6.24-24.40 for removal, it said two other major components would have to be removed, linux-generic and linux-image-generic.  I got cold feet since I don't really know what I'm doing.

I'm 99% sure the problem resulted from this update, as I had not installed any other software updates or installed new software for over a week.

Has anyone else had this problem, and can anyone help?

Thanks in advance.

---

### Post by tmurph on 2009-09-11
I have the same problem... Help would be appreciated!

---

### Post by bw44 on 2009-09-11
> **tmurph said:**
> I have the same problem... Help would be appreciated!

Happy to hear it! (Sorry, just kidding, but misery loves company!)

Since no one has lept forward with a solution, I posted a different description of the problem.  You might want to follow that thread too, in case anyone replies to it:

[http://ubuntuforums.org/showthread.php?t=1263906](http://ubuntuforums.org/showthread.php?t=1263906)

Do you know what audio chip your system uses?

Cheers,
bw44

PS. Having restored my system to a month ago, which did not correct the problem, I'm probably wrong about it being caused by the linux-ubuntu upgrade.

---

### Post by bw44 on 2009-09-12
I have no idea why this problem occurred, but I "fixed" it by muting and then un-muting the PCM channel fader on the Gnome Volume Control panel (something I had never done before, so don't know how the right channel came to be muted on my system). 

I stumbled on a blog post which pointed me to the solution.  The author said: >  Ubuntu Linux has a master volume control in the screen-top control bar. Left-click on it to control your volume. Right-click on it, and a menu appears, including the option to "open" the volume control. This gives you a larger volume control panel with ... mute-buttons. When Ubuntu Gutsy and Hardy were configured for shipping, someone correctly decided that the master volume should be on and the PC speaker too. But the "PCM", line-in, CD and microphone were apparently best muted by default in this person's opinion.

PCM means "pulse-code modulation", which really leaves me no wiser. And apparently, it's important stuff. So, Dear Reader, if your Ubuntu machine is inexplicably silent, try unmuting the PCM. It worked for me!

Here's the URL if you want to read the whole article:

[http://scienceblogs.com/aardvarchaeology/2008/04/tech_note_ubuntu_linux_804_har.php](http://scienceblogs.com/aardvarchaeology/2008/04/tech_note_ubuntu_linux_804_har.php)

Is it possible something in a software update reset the PCM channels to the muted state?   I'd still like to know, but in the meantime I have to admit to finding an easy solution.    Hope it helps someone else.

---

