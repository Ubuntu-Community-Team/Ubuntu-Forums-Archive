---
title: "mplayer - possible to watch and save simultaneously?"
date: 2011-11-24
forum: Multimedia Software
---

### Post by terryeden on 2011-11-24
I have a remote video stream of my security cam that I want to be able to save **while** watching.

To save, I use mplayer to dump the stream.
```
mplayer http://example.com/stream.asf  -dumpstream -dumpfile ycam.asf
```

To watch, I use mplayer as normal.
```
mplayer http://example.com/stream.asf
```

What I want is a command which will save the video as I'm watching it.

Any ideas?

---

### Post by wolfen69 on 2011-11-24
I know you can do this with vlc. In vlc, go to view>advanced controls to get a record button on the interface. All vids are saved to your /home.

---

### Post by adbot asdakjsfhs on 2012-03-05
See this thread [1]. Basically:
mplayer [http://user:password@example.com/stream.asf](http://user:password@example.com/stream.asf) -dumpstream -dumpfile ./mystream.asf

and in another terminal:
mplayer – < ./mystream.asf

Or there is a description to use pipes to see the current stream without seeking.

[1] [http://shkspr.mobi/blog/index.php/2011/11/watching-and-simultaneously-saving-video-in-mplayer/](http://shkspr.mobi/blog/index.php/2011/11/watching-and-simultaneously-saving-video-in-mplayer/)

---

