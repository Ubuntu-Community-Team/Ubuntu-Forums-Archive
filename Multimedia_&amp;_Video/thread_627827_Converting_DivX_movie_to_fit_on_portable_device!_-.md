---
title: "Converting DivX movie to fit on portable device! - How?"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by daller on 2007-11-30
Hi there,

I bought a nice Meizu Miniplayer, with OGG support, and several other cool features.

I would like to upload video to it, but I haven't found a way to convert it!

Most input files are "standard" DivX movies, and the output should be:

Video: 18 fps, <= 512kbps
Audio: MP3 56-256kbps, stereo

What can I do to convert these files?
I'm fine with some commandline tool, but a GUI would also be nice!

---

### Post by eye208 on 2007-11-30
Here's a command line you can use as a starting point. You'll probably have to tweak things a bit further to get optimal results.
```
mencoder <inputfile> -ofps 15 -vf expand=:::::4/3,scale=320:240 -ovc xvid -xvidencopts bitrate=150:profile=sp2 -oac mp3lame -lameopts cbr:br=96 -o <outputfile.avi>
```
The -vf option will reduce the video size to 320x240 without changing the aspect ratio.

The profile parameter in the -xvidencopts option will make sure the encoder does not use advanced MPEG-4 features unsupported by the output device. However I don't know the profile of the Meizu player, so you might get better results by choosing a more advanced profile for the encoding. See "man mencoder" for details about available profiles.

And of course you should tweak the bit rates of both video and audio. I've chosen conservative settings here, so again you have some headroom left to go higher and raise the level of quality (and increase file sizes of course).

If the Meizu supports container formats other than AVI (e.g. MP4), you can create these instead and save some space by doing so.

---

### Post by zenkaon on 2007-11-30
you could try acidrip, nice gui and all

---

### Post by daller on 2007-12-02
I ended up using this for my miniplayer:

```
mencoder INPUT.AVI -idx -noodml -ofps 18 -vf scale=320:-2,expand=:240:::1,crop=320:240,rotate=1 -ovc lavc -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256:vmax_b_frames=0:vhq -sws 9 -srate 44100 -oac mp3lame -lameopts cbr:br=128:mode=0 -o OUTPUT.AVI
```

I have a slight audio glitch, but it's not constant through the movie, it increases in timegap... any ideas?

---

### Post by gtr225 on 2008-02-25
Just got the same mp4 player and I'm interested in putting videos on it as well. Any luck on fixing the sound gap problem?

---

