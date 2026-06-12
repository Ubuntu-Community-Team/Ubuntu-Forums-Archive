---
title: "[SOLVED] smplayer and subtitles"
date: 2008-11-07
forum: Multimedia Software
---

### Post by lovinglinux on 2008-11-07
Why I can't make the subtitles align at the top of the screen using smplayer preferences? I have changed the slider position, but it doesn't have any effect on the subtitle position.

> **rvm4000 said:**
> That option in preferences specifies the position of the subtitles by *default* and only works if the SSA/*** library is disabled. It's used when you open a video which you never played before. For videos you already played, the position they had before is kept, but it can be changed with the options **Up** and **Down** in the Subtitles menu.

Remember this only works with the SSA/*** library disabled and with subtitles in srt or sub formats. 

If you want subtitles on the top of the screen with the SSA/*** library enabled, it's possible, but you need to get the latest version of smplayer from svn (you can get packages [here](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)), it allows further customization of SSA/*** subtitles, including the possibility to display them on the top of the screen.

Thanks, but it still doesn't work without SAA library. The up and down options in the subtitles menu also doesn't work. Just to let you know, it doesn't work with gnome-mplayer either.

---

### Post by shirilover on 2008-11-08
Are the subtitles actually a separate stream, or are they encoded onto the video?

---

### Post by lovinglinux on 2008-11-08
> **shirilover said:**
> Are the subtitles actually a separate stream, or are they encoded onto the video?

They are on a separate srt file. But I don't have issues displaying or formatting them. The only issue I have is that I can't change subtitle position/alignment.

---

### Post by rvm4000 on 2008-11-08
Are you sure you have the SSA library disabled? Subtitles don't move with that library on.

What version of mplayer are you using?

I've just tested with mplayer 1.0rc2 and it works ok.

---

### Post by lovinglinux on 2008-11-08
> **rvm4000 said:**
> Are you sure you have the SSA library disabled? Subtitles don't move with that library on.

What version of mplayer are you using?

I've just tested with mplayer 1.0rc2 and it works ok.

I disabled SSA in the smplayer preferences, but forgot to remove the SSA entry form /.mplayer/config

Now it works. Thanks.

---

### Post by rvm4000 on 2008-11-09
Oops, that's smplayer's fault. It should use -noass if the SSA library is not used.

I've just fixed it in svn r2220.

---

