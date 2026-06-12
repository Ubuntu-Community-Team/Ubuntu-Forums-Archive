---
title: "ERRO: &quot;[h264 @ 0xb73fe764]number of ...&quot;"
date: 2008-11-11
forum: Mythbuntu
---

### Post by ajut on 2008-11-11
Hello,

I have tons of messages like those in  /var/log/mythtv/mythbackend.log

```
2008-11-11 13:50:01.448 [h264 @ 0xb73fe764]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-11 13:50:01.455 [h264 @ 0xb73fe764]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-11 13:50:01.472 [h264 @ 0xb73fe764]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-11 13:50:01.473 [h264 @ 0xb73fe764]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-11 13:50:01.481 [h264 @ 0xb73fe764]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-11 13:50:01.486 [h264 @ 0xb73fe764]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-11 13:50:01.494 [h264 @ 0xb73fe764]number of reference frames exceeds max (probably corrupt input), discarding one
....

2008-11-11 11:45:07.778 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.783 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.791 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.798 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.807 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.815 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.822 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.830 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.839 KeyframeSequencer::decode_Header: SPS has not been parsed!
2008-11-11 11:45:07.846 KeyframeSequencer::decode_Header: SPS has not been parsed!

```


MythBuntu 8.10
I386
2.6.27-7-generic
Hauppauge NOVA-T PCI
MPEG4-AVC SD


Questions:

1. What can I do, to get ride of those messages?

2. Can I force mythbackend to not log those messages? Not helping to solve original problem but reduces hard disk activity.


BR,
Ajut

---

### Post by majoridiot on 2008-11-11
> **ajut said:**
> Questions:

1. What can I do, to get ride of those messages?

my guess is not much, at least for the h264 errors.  either the files are encoded using a
level that the internal player does not like (too many b frames) or the codec itself has issues.
if the files play ok, i would not worry about it for now.

> **ajut said:**
> 2. Can I force mythbackend to not log those messages? Not helping to solve original problem but reduces hard disk activity.

you can change the logging methods mythbackend uses and pick and choose what you want logged.

```
$ mythbackend -v help
```

will list the logging options (you can run this command with the backend running)

the levels are both additive and subtractive (by adding "no" in front of what you want to 
prevent logging of... e.g.:

```
$ mythtvbackend -d -v important,general
```

runs it as a daemon with default logging...

```
$ mythbackend -d -v important,general,noplayback
```

would default log but should omit all playback-related logging.

you may need to play with it a bit to sort out the options you do and do not want.

---

### Post by ajut on 2008-11-11
> 
you can change the logging methods mythbackend uses and pick and choose what you want logged.

```
$ mythbackend -v help
```

will list the logging options (you can run this command with the backend running)

the levels are both additive and subtractive (by adding "no" in front of what you want to 
prevent logging of... e.g.:

```
$ mythtvbackend -d -v important,general
```

runs it as a daemon with default logging...

```
$ mythbackend -d -v important,general,noplayback
```

would default log but should omit all playback-related logging.

you may need to play with it a bit to sort out the options you do and do not want.


I'ts strange, that some thumbnails in "http://127.0.0.1/mythweb/tv/recordeds are good looking, some are scrambled and the other are empty at all.

I have heard, that provider using long pauses between "full frames" in DVB-T stream to keep bandwidth low (long pauses between channel changes in setup boxes etc) and quite new encoding - MPEG4-AVC PAFF interlacing.

I have theory, that maybe mythtv don't recognize "full frame" and starts recording somewhere between "full frames", so the beginning of recorded stream is corrupted and "Grabbing preview" can't get nice "full frame". And every time I watch such recording, I get errors described before.

How can I check that theory and how can I force mythtv to begin recording with "full frame"?

BTW: Play with log options is good idea, thanks :)

Br,
Ajut

---

### Post by ajut on 2008-11-14
> 
BTW: Play with log options is good idea, thanks :)



Even "-v none" option for mythtv-backend, didn't helped to get ride of " [h264 @ 0xb73a7764]number of reference frame  exceeds max ..." errors :(

---

### Post by Neon Dusk on 2008-11-14
> **ajut said:**
> Hello,

I have tons of messages like those in  /var/log/mythtv/mythbackend.log

...
Ajut

That looks like the problem I was having with BBC HD see [here](http://svn.mythtv.org/trac/ticket/5730)

---

### Post by Eldis on 2009-12-23
My logs are full of this also. I'm not even watching HD content but using VDPAU normal profile and dvb-c card x 2.

---

### Post by Eldis on 2009-12-23
Also I get these messages every few milliseconds even when I'm not watching a channel or recording so there is something going on. I also my rig seems sluggish and watching tv from a remote frontend will crash the backend. The backend process won't segfault or anything the backend will just become even more unresponsive.

```
2009-12-23 21:21:34.273 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.306 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.340 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.373 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.406 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.440 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.474 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.523 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.556 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.598 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.633 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.665 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.698 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.732 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.766 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.799 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.833 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.866 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.900 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.933 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:34.967 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:35.000 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one
2009-12-23 21:21:35.034 [h264 @ 0x7ff9baf18820]number of reference frames exceeds max (probably corrupt input), discarding one

```

---

