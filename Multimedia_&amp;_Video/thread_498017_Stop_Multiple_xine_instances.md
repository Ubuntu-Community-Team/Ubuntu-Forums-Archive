---
title: "Stop Multiple xine instances"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Norst on 2007-07-10
Ok here is what I have set up:

I have a monitor and a TV.

I have setup the tv as a separate X screen (:0.1)

Altered .xine/config to read:

```
# Name of video display
# string, default: 
gui.video_display::0.1
```

I've made a script like so (called it tv.sh):

```
$ vi tv
xine -f $1
```

I then made a launcher on my desktop with the command:

```
tv.sh
```

So now all I have to do is drag and drop a file or URL to a video on to the icon and xine will launch with the ui controls on my monitor and the video in full screen on my tv. It works great but here is where I run in to an issue.
Once a file is playing, if I drag and drop another video on to the icon it will start a new instance of xine doing the same thing. This is obviously what I have told it to do but I would rather it replace the current video in the running instance of xine rather than start a new instance.
Anyone know how I could make this happen?

Thank you for any help offered.

-------EDIT----------

I hate when I post a Q: after hours of looking and then solving the issue lol.

I changed the script to read as follows:

$ vi tv
killall xine
xine -f $1

:)

---

