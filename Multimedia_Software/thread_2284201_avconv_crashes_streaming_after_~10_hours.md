---
title: "avconv crashes streaming after ~10 hours"
date: 2015-06-27
forum: Multimedia Software
---

### Post by 317070 on 2015-06-27
Hi,

I am running a 24/7 stream online ( [http://www.twitch.tv/317070](http://www.twitch.tv/317070) ) using avconv. Avconv however crashes after ~10 hours with the exception: 

```
*** Error in `avconv': free(): invalid pointer: 0x0000000203ea68e8 ***
```

The commando I use for parsing my rawvideo to a stream is this:

```
command = [ 'avconv',                        '-y', # overwrite
                '-f', 'rawvideo',
                '-r', '30',
                '-vcodec','rawvideo',
                '-s', '%dx%d'%(self.width, self.height), # size of one frame
                '-pix_fmt', 'rgb24',
                '-i', '-', # The input comes from a pipe


                '-ar', '48000', '-ac', '2', '-f', 's16le', '-i', '/dev/zero',
                '-vcodec', 'libx264', '-r', '%d'%self.fps, '-b:v', '3000k', '-s', '%dx%d'%(self.width, self.height),
                                '-preset', 'veryfast',
                                '-crf','23',
                                '-pix_fmt', 'yuv420p'
                                '-minrate', '3000k', '-maxrate', '3000k', '-bufsize', '12000k',
                                '-g','60',
                                '-keyint_min','1',
                '-vsync','passthrough',
                '-acodec', 'libmp3lame', '-ar', '44100', '-b', '160k',
                               '-bufsize', '8192k', '-ac', '2',
                '-map', '0:v', '-map', '1:a', #use only video from first input and only audio from second
                '-threads', '1',
                '-f', 'flv', 'rtmp://live-fra.twitch.tv/app/%s'%twitch_stream_key
                ]
```

My version is: 
```
avconv version 9.11-6:9.11-2ubuntu2, Copyright (c) 2000-2013 the Libav developers
  built on Mar 24 2014 06:12:33 with gcc 4.8 (Ubuntu 4.8.2-17ubuntu1)
```

I also notice that avconv has a really high memory use, up to 17 Gigabyte of memory right now, for instance. The machine has 32GB of RAM, but it has other processes who need this memory as well.
```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
15040 jdgrave   20   0 25.518g 0.017t   2268 R 104.5 56.6   1221:43 avconv
```

So, am I doing something wrong? Can the crashes and/or high memory use be fixed? Is is possible to use avconv to stream 24/7?

---

