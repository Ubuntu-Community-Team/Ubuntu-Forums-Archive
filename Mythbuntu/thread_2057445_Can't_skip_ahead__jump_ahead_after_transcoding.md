---
title: "Can't skip ahead / jump ahead after transcoding?"
date: 2012-09-13
forum: Mythbuntu
---

### Post by andrewc6l on 2012-09-13
I recently decided to try transcoding some of the shows I'm recording to save on disk space. It looks like the transcode works fine, but I'm running into a strange problem with the shows that have been transcoded.

When I try to skip ahead or jump ahead (cursor right or cursor down) while playing, the recording behaves as if I were recording live TV and was at the end. There's a slight jump, but I'm left at the same position I was before.

If I don't try to skip or jump, it appears to play fine (at least the first 10 minutes or so - haven't tested beyond that). I just can't go past what I don't want to watch.

I tried redoing the commercial flagging for that show - after doing that, I still can't skip. I also tried
```
mythcommflag --rebuild
```
after that I can skip for the first minute, but not beyond that.

Any ideas why this might be happening? I'm using 0.25.2.18 on the 2.6.32-42.96 kernel.

---

### Post by anonymousdog on 2012-09-13
I would tend to think that transcoding is breaking the seek table somehow and that, probably for the same reason, your seek table rebuild is also failing.  You'll probably have to look at your logs while it's happening and may need to ratchet up verbosity to get the answers you need.  You could also capture the logs from the seek table rebuild to ensure it's completing cleanly.

---

### Post by klc5555 on 2012-09-13
> **andrewc6l said:**
> I recently decided to try transcoding some of the shows I'm recording to save on disk space. It looks like the transcode works fine, but I'm running into a strange problem with the shows that have been transcoded.

When I try to skip ahead or jump ahead (cursor right or cursor down) while playing, the recording behaves as if I were recording live TV and was at the end. There's a slight jump, but I'm left at the same position I was before.

If I don't try to skip or jump, it appears to play fine (at least the first 10 minutes or so - haven't tested beyond that). I just can't go past what I don't want to watch.

I tried redoing the commercial flagging for that show - after doing that, I still can't skip. I also tried
```
mythcommflag --rebuild
```
after that I can skip for the first minute, but not beyond that.

Any ideas why this might be happening? I'm using 0.25.2.18 on the 2.6.32-42.96 kernel.
Mythcommflag is often unable to fix the seektable. Has been for years. Try the alternative```
mythtranscode --mpeg2 --buildindex --showprogress -c[myth's channel number] -s[complete start time]
```The process leaves one bit of detritus behind when it finishes --a zero byte .tmp file that can be deleted at some later time. But mythtranscode  always works.

---

### Post by andrewc6l on 2012-10-23
It's been a while, but I finally got around to testing this. Here's a progress report of sorts.

Doing a transcode with --buildindex didn't seem to work for me. I was able to run mythtranscode on the file:

```

~$ mythtranscode --verbose all --loglevel debug --showprogress --mpeg2 --buildindex --chanid 1051 --starttime 20121010233600

2012-10-23 00:55:20.468645 C  mythtranscode version: fixes/0.25 [v0.25.3] www.mythtv.org
2012-10-23 00:55:20.468740 C  Qt version: compile: 4.6.2, runtime: 4.6.2
2012-10-23 00:55:20.469773 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-10-23 00:55:20.470884 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-10-23 00:55:20.471000 E  (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file /usr/share/mythtv/mysql.txt
2012-10-23 00:55:20.471052 E  (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file /usr/etc/mythtv/mysql.txt
2012-10-23 00:55:20.471588 E  (old)Settings::ReadSettings(./mysql.txt) - No such file ./mysql.txt
2012-10-23 00:55:20.593686 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-10-23 00:55:50.790268 C  Disabling DB Logging: too many messages queued
2012-10-23 00:55:51.838310 C  Reenabling DB Logging
2012-10-23 00:55:52.140130 C  Disabling DB Logging: too many messages queued
2012-10-23 00:55:53.189951 C  Reenabling DB Logging
2012-10-23 00:55:53.391239 C  Disabling DB Logging: too many messages queued
2012-10-23 00:55:54.432875 C  Reenabling DB Logging
2012-10-23 00:55:54.634346 C  Disabling DB Logging: too many messages queued
2012-10-23 00:55:55.679826 C  Reenabling DB Logging
2012-10-23 00:55:55.981626 C  Disabling DB Logging: too many messages queued
2012-10-23 00:55:57.028753 C  Reenabling DB Logging
2012-10-23 00:55:57.330226 C  Disabling DB Logging: too many messages queued
2012-10-23 00:55:58.370826 C  Reenabling DB Logging
2012-10-23 00:55:58.772987 C  Disabling DB Logging: too many messages queued

```

This went by pretty quickly (under 30 seconds for a 3.2G file?) and at the end I still couldn't seek. I also tried tossing a "--profile autodetect" in there since the wiki says it's required - still no joy. I also don't see progress - so I'm guessing something's failing before then?

---

### Post by klc5555 on 2012-10-23
Hm. From the bugtracks, mythtranscode appears to have gotten a bit buggy in 0.25.x, and more so further on in 0.26, where lossless transcode appears to be broken completely for the moment.

Have you used lossless (--mpeg2) mythtranscode in your particular installation yet? Other than this? Did it work?

In your debug output, the expected next line after the "(old)Settings" lines should be something about "Using localhost value of mythbackend" followed by a couple of UPnP lines and/or a "Testing network connectivity to" line to the master backend. And finally a "Starting IO manager" when the job actually starts. Instead, your db logging gets swamped and disabled. So this must be the place that your installation of mythtranscode is breaking down. The recording never actually gets worked on. Does the mythbackend log show anything here?

One thing that's definitely broken already in 0.25.x is "--showprogress" So, as a first attempt, maybe try manually running the mythtranscode job again, while leaving off the "--showprogress" switch. A 3.2 Gig file should complete in (roughly) 2-4 minutes, depending on hardware. But only 30 seconds (with no extra 0-byte 1051_20121010233600.mpg.tmp file left behind), it clearly didn't run. Maybe removing the --showprogress switch will do the job all by itself (but frankly I doubt it). You could also try handling the recording as a pure video file (rather than a recording), whereupon the mythtranscode line would be (either with or without the "--video" switch):```
mythtranscode --mpeg2 --buildindex  -i 1051_20121010233600.mpg
```

Other potential tries that come to mind might involve a bit of surgery, which admittedly would be a long way to go just to build a frame index on a recording. Particularly if mythtranscode is working properly for non-lossless transcoding.

---

### Post by nickrout on 2012-10-23
Given the price of hard disk drives, transcoding to save space is a bit of a waste of time, cpu usage, and in your case a waste of functionality.

---

### Post by klc5555 on 2012-10-24
> **nickrout said:**
> Given the price of hard disk drives, transcoding to save space is a bit of a waste of time, cpu usage, and in your case a waste of functionality.

I agree. But if it turns out something is generally amiss with his lossless transcoding with mythtranscode, beyond just rebuilding the DVB seektables that mythcommflag can't handle, this will also likely prevent him from doing other useful lossless transcode tasks, like easily trimming commercials from recordings.

So I wonder if lossless transcode problems are generally to be found in any earlier versions of mythtranscode than 0.26? The OP is on 0.25.2.18

---

### Post by nickrout on 2012-10-24
> **klc5555 said:**
> I agree. But if it turns out something is generally amiss with his lossless transcoding with mythtranscode, beyond just rebuilding the DVB seektables that mythcommflag can't handle, this will also likely prevent him from doing other useful lossless transcode tasks, like easily trimming commercials from recordings.

So I wonder if lossless transcode problems are generally to be found in any earlier versions of mythtranscode than 0.26? The OP is on 0.25.2.18Sounds like a developer issue. OP should post a ticket to trak.

---

### Post by klc5555 on 2012-10-24
One supposedly exists already for 0.26. The current workaround consists of patching in an earlier version of mythtranscode cf. [http://www.gossamer-threads.com/lists/mythtv/users/529613](http://www.gossamer-threads.com/lists/mythtv/users/529613) 

But which version to patch with? Over at gossamer threads they're talking about some version from "0.25-fixes", compiled from source and copied over the version in 0.26. That's why it might be valuable to confirm whether the OP's mythtranscode problem was the same (or similar) problem with lossless transcoding as above, but already in 0.25.2.18. One would patch from what? 0.25-release? 0.24.3?

Of course, the OP's mythtranscode problem may be something else entirely, and unrelated. We just don't know yet.

---

