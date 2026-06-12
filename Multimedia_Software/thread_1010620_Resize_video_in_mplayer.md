---
title: "Resize video in mplayer"
date: 2008-12-13
forum: Multimedia Software
---

### Post by jeenuv on 2008-12-13
I've mplayer package installed. What I'm looking for is a way to resize video at launch time so that it shows up in a scaled-down window. I looked at mpmlayer manpage but couldn't figure out how to do this. Gmplayer seem to have a menu option for this and it does work. Since it uses mplayer as the backend, there should be something that mplayer offers to let gmplayer to have such an menu option.

Thanks
Jeenu

---

### Post by andrew.46 on 2008-12-14
Hi jeenuv,

Try the following:

```
mplayer -vf scale -zoom -xy 600 my_file.avi
```

Simply alter the '-xy 600' number to change the size of the movie, this is the x axis only and the y axis will be calculated by MPlayer with correct aspect ratio. This works with the current svn MPlayer so hopefully with the Ubuntu version as well :-)

All the best,

  Andrew

---

### Post by jeenuv on 2008-12-14
:D That seem to work. I had tried the same, but didn't bother varying values enough to notice difference; and hence I thought it was not working.

By the way it seems to work without the -vf scale option too.

And a big thanks to you!!!

---

### Post by laceration on 2008-12-14
you could also put in your ~/.mplayer/config file
there are various ways to do it
```
screenw=600
screenh=400
xy=.5
xy=600
```
and for fullscreen
```
fs=1
```

---

### Post by jeenuv on 2008-12-14
Thank you, laceration, for the info.

---

