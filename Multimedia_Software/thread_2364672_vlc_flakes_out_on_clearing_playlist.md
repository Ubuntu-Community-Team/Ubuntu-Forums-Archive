---
title: "vlc flakes out on clearing playlist"
date: 2017-06-26
forum: Multimedia Software
---

### Post by OriTheEep on 2017-06-26
Here's a curiosity that, as far as I was able to research, doesn't appear to have affected anyone else but has been a nuisance for me since installing 16.04 originally and has survived not only a re-installation but a switch from using Samba to nfs. I've obviously done something stupid?

The vlc media player (2.2.2) has a habit of crashing pretty near every time I use the "Clear the playlist" option from a right click in the playlist. This problem does not happen on other machines still running 14.04 and vlc 2.1.6.

Clearing items from the playlist one by one (remove selected or delete key) seems to be OK but tedious. Remove selected or delete on several items at once also causes problems.

I use Classic GNOME Flashback

---

### Post by SeijiSensei on 2017-06-26
Might I suggest you give smplayer a try along with the mpv engine?

```
sudo apt-get install smplayer mpv
```

I've never had a problem with smplayer's handling of playlists.

---

### Post by ajgreeny on 2017-06-26
But I do not have a playlist management problem with VLC so I wonder if there is some user preference setting causing this for you.

Try renaming the **~/.config/vlc** folder as a backup to see if that solves it for you.

---

### Post by OriTheEep on 2017-06-26
> **SeijiSensei said:**
> Might I suggest you give smplayer a try along with the mpv engine?

```
sudo apt-get install smplayer mpv
```

I've never had a problem with smplayer's handling of playlists.


Thanks for the recommendation. Being an obstinate so and so, I will try to get to the bottom of **this** problem before pursuing alternatives but, be assured, the tip has been taken on board. :)

---

### Post by OriTheEep on 2017-06-26
> **ajgreeny said:**
> But I do not have a playlist management problem with VLC so I wonder if there is some user preference setting causing this for you.

Try renaming the **~/.config/vlc** folder as a backup to see if that solves it for you.

Good thinking! However...

I clicked the rest preferences button provided and tried again with the same result.

Would you think there is any point to purging the application and reinstalling it?

---

