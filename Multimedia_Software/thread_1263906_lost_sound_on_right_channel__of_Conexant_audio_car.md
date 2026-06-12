---
title: "lost sound on right channel  of Conexant audio card"
date: 2009-09-11
forum: Multimedia Software
---

### Post by bw44 on 2009-09-11
Running Ubuntu 8.04, all updates applied, on an HP/Compaq Presario laptop.  The audio chip is a Conexant CX20551 (Waikiki). Sound has been working fine for two years on both Ubuntu and Windows XP (dual-boot).  Sound still works fine under XP.

Since sound is OK under XP I suspect a software/driver problem under Ubuntu.  I tried restoring my system to one month ago when sound was working fine, but this didn't correct the problem.

Can anyone tell me how to reset the audio chip/driver? 

I tried the following commands (which someone posted elsewhere about a similar problem) but it didn't help. ```
$ sudo killall pulseaudio
$ sudo alsa force-reload
```:(

---

### Post by bw44 on 2009-09-12
I have no idea why this problem occurred, but I "fixed" it by muting and then un-muting the PCM channel fader on the Gnome Volume Control panel (something I had never done before, so don't know how the right channel came to be muted on my system). 

I stumbled on a blog post which pointed me to the solution.  The author said: >  Ubuntu Linux has a master volume control in the screen-top control bar. Left-click on it to control your volume. Right-click on it, and a menu appears, including the option to "open" the volume control. This gives you a larger volume control panel with ... mute-buttons. When Ubuntu Gutsy and Hardy were configured for shipping, someone correctly decided that the master volume should be on and the PC speaker too. But the "PCM", line-in, CD and microphone were apparently best muted by default in this person's opinion.

PCM means "pulse-code modulation", which really leaves me no wiser. And apparently, it's important stuff. So, Dear Reader, if your Ubuntu machine is inexplicably silent, try unmuting the PCM. It worked for me!

Here's the URL if you want to read the whole article:

[http://scienceblogs.com/aardvarchaeology/2008/04/tech_note_ubuntu_linux_804_har.php](http://scienceblogs.com/aardvarchaeology/2008/04/tech_note_ubuntu_linux_804_har.php)

Is it possible something in a software update reset the PCM channels to the muted state?   I'd still like to know, but in the meantime I have to admit to finding an easy solution.    Hope it helps someone else.

---

### Post by lisati on 2009-09-12
Is this related to your [other thread]("http://ubuntuforums.org/showthread.php?t=1263527")?

---

### Post by bw44 on 2009-09-12
> **lisati said:**
> Is this related to your [other thread]("http://ubuntuforums.org/showthread.php?t=1263527")?

Yes, I confess to having posted the same problem with two different descriptions, hoping that one might attract a response the other didn't.
Mea culpa.

I also posted the "solution" I came up with to both threads, so maybe it will help someone else resolve a similar problem.

I wish I knew how/why it occurred in the first place.

---

