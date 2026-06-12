---
title: "Restart a music dir with mplayer no shuffle after quitting."
date: 2015-11-11
forum: Multimedia Software
---

### Post by uh-huh on 2015-11-11
I'm going through a big directory with mplayer, trying to assemble a playlist of favo(u)rites. So, I want to go through the list with random off. My problem is having to start mplayer where it stopped without having to cycle through the tunes I've already played.

---

### Post by tgalati4 on 2015-11-11
What version of Ubuntu and what version of *mplayer*?

```
apt-cache policy mplayer2
```

Perhaps try *moc*.  It's terminal-based, but can go through directories pretty quickly.

```
sudo apt-get install moc
mocp
```

---

### Post by shantiq on 2015-11-12
hi uh huh   i cannot see this function in mplayer itself but in mpv which uses mplayer this exists

```
 mpv --save-position-on-quit *
```


so all you need to do is to go into your Music folder [if all your files are loose in there not in subfolders] and run command from terminal ... everytime you start again it will start off exactly where you stopped last



install mpv

```
sudo apt-get install mpv
``` or [here]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")

---

### Post by uh-huh on 2015-11-15
Thanks for the tip. Right now, however, everything is up in the air, my PC is struggling. I mistakenly up-graded to 16.04 and now lots of stuff is broke. But I just ordered a Zareason Zeto, qv, and when it gets here I will definitely be trying out mpv.

---

### Post by SeijiSensei on 2015-11-16
> cannot see this function in mplayer itself but in mpv which uses mplayer this exists
Just a hint that mpv and mplayer are two different media players. Mpv is a rewrite of the mplayer code by, I believe, the same team.  It also supercedes mplayer2, a fork of the original mplayer code. 

I suggest installing smplayer, a front end to mpv or mplayer, or an audio player like Rhythmbox or Clementine to build a playlist.

---

