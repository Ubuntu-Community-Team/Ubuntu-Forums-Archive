---
title: "TiMidity does not work"
date: 2010-07-19
forum: Multimedia Software
---

### Post by Pitel on 2010-07-19
TiMidity, as daemon, does not work...

The daemon is running
```
$ ps ax | grep timidity
 7471 pts/3    S      0:00 /usr/bin/timidity -Os -iAD
```

It's MIDI ports are available
```
$ pmidi -l
 Port     Client name                       Port name
128:0     TiMidity                          TiMidity port 0
128:1     TiMidity                          TiMidity port 1
128:2     TiMidity                          TiMidity port 2
128:3     TiMidity                          TiMidity port 3
```

But I get no sound when playing MIDI through them using
```
$ pmidi -p128:0 be_sharp_bw_redfarn.mid
```

However, after stoping the daemon service and running it as MIDI server in another terminal makes it work.
```
$ sudo service timidity stop
$ timidity -Os -iA
$ pmidi -p128:0 be_sharp_bw_redfarn.mid #Bleep bloop
```

And when I want to start TiMidity daemon again, I got some strange message
```
$ sudo service timidity start
 * Starting TiMidity++ ALSA midi emulation... [ OK ] 
Home directory /etc/timidity not ours.
```

What might be wrong?

I'm using Ubuntu 10.04 64bit, PulseAudio, without any config edit in PulseAudio or TiMidity.

---

