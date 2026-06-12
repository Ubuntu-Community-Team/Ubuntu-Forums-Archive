---
title: "Sound only when trying to play .MOV"
date: 2011-04-17
forum: Multimedia Software
---

### Post by DShad on 2011-04-17
Got into something weird here...  I only get the AUDIO when trying to play my .MOV files.

I have "ubuntu-restricted" extras and "w64codecs" installed but no luck.

I'm running on Ubuntu 10.10 AMD64.

Tried to play those same files on Linux Mint 64bits with success...

Please help.

---

### Post by K_45 on 2011-04-17
Try

```
sudo apt-get install vlc
```

That should play them.

---

### Post by DShad on 2011-04-17
> **K_45 said:**
> Try

```
sudo apt-get install vlc
```

That should play them.

That's the player I'm using.  Also tried totem, mplayer and all with the same result... :(

---

### Post by K_45 on 2011-04-17
OK. CD to the directory the .mov file is in. Then run

```
vlc *name of file*
```

Post a screenshot of the output of the terminal.

---

### Post by technmom on 2011-05-11
Did you ever get this working? I'm having problems too.

---

### Post by DShad on 2011-05-11
> **technmom said:**
> Did you ever get this working? I'm having problems too.

I managed to make it play with mplayer.  So I installed smplayer (GUI) and am using it for all my videos.

Good luck!

---

