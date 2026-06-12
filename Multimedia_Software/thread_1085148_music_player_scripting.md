---
title: "music player scripting"
date: 2009-03-02
forum: Multimedia Software
---

### Post by monguin61 on 2009-03-02
I am in the process of migrating from XP to Ubuntu, and I have gotten pretty comfortable with Ubuntu but there are a few things that still bug me. In XP I use winamp media player for music and video. The biggest features I miss from that is support for random album shuffling and global hotkeys. I know global hotkeys are pretty easy to setup in linux, so I'm not too worried about that. As for the album shuffle, I have not been able to find a music player that does what I want, which breaks down to two things:
1. upon completion of one album, randomly select another album from a given library/directory, and play/queue that entire album.
2. randomly select and (immediately) play an album in response to a global hotkey shortcut.

I am a programmer, not a ton of experience with bash or python but I'm sure I can figure out whatever I need to get my own scripts working.

Does anyone have any advice on what music player might be best for doing something like this, and some resources I can look at to figure out how to do it myself?

Thanks

---

### Post by mobilediesel on 2009-03-02
> **monguin61 said:**
> I am in the process of migrating from XP to Ubuntu, and I have gotten pretty comfortable with Ubuntu but there are a few things that still bug me. In XP I use winamp media player for music and video. The biggest features I miss from that is support for random album shuffling and global hotkeys. I know global hotkeys are pretty easy to setup in linux, so I'm not too worried about that. As for the album shuffle, I have not been able to find a music player that does what I want, which breaks down to two things:
1. upon completion of one album, randomly select another album from a given library/directory, and play/queue that entire album.
2. randomly select and (immediately) play an album in response to a global hotkey shortcut.

I am a programmer, not a ton of experience with bash or python but I'm sure I can figure out whatever I need to get my own scripts working.

Does anyone have any advice on what music player might be best for doing something like this, and some resources I can look at to figure out how to do it myself?

Thanks

You could probably use [MPD]("http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki") with [MPC]("http://linux.die.net/man/1/mpc").

I use those along with [Sonata]("http://linux.die.net/man/1/sonata"). MPD is a music player server, MPC and Sonata are clients to send commands to the server. I never thought about scripting the music player but since MPC runs from the commandline, I'll have to try that out.

---

