---
title: "How do I capture sound streaming via a webpage ?"
date: 2009-12-08
forum: Multimedia Software
---

### Post by bobdobbs on 2009-12-08
Hi.

I'm trying to capture sound streaming from a webpage.

After searching the forums, I came across this thread:
[http://ubuntuforums.org/showthread.php?t=413313](http://ubuntuforums.org/showthread.php?t=413313)

The solution seems neat and easy.

However, even when I set sound recorder to capture at "CD Quality, Lossless" my captured file sounds distant and vague.

How can I capture, while retaining the sound quality?

---

### Post by amauk on 2009-12-08
```
#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/
#
#This script require sox
#sudo apt-get install sox

if [ -n "$1" ]; then
	OUTFILE="$1"
else
	TIME=$(date +%d-%b-%y_%H%M-%Z)
	OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"
```

---

### Post by bobdobbs on 2009-12-08
Thanks.

Unfortunately, the recording is silent.

Also, I tried capturing sound with audacity, and I had the same problem as I did initially: the sound quality was very poor.

---

### Post by VertexPusher on 2009-12-08
```
pcm.!default {
    type file
    slave.pcm {
        type pulse
    }
    file "/tmp/out.wav"
    format wav
}

ctl.!default {
    type pulse
}
```
Save this file as ".asoundrc" in your user home directory, then launch the browser. When you are done, quit the browser and delete the .asoundrc file. The file /tmp/out.wav should now contain a recording of the session.

---

### Post by bobdobbs on 2009-12-09
> **VertexPusher said:**
> ```
pcm.!default {
    type file
    slave.pcm {
        type pulse
    }
    file "/tmp/out.wav"
    format wav
}

ctl.!default {
    type pulse
}
```
Save this file as ".asoundrc" in your user home directory, then launch the browser. When you are done, quit the browser and delete the .asoundrc file. The file /tmp/out.wav should now contain a recording of the session.

Awesome!
This works!
Thank you!

The test files I've saved to out.wav that I've listened to so far have audio quality audible identical to what I hear playing initially through my browser. This is a vast improvement over my previous attempts.

How does this capture identical audio quality, when the other methods give me a much poorer quality recording?
Can you give me some advice and pointers on how and why this works?



Also, although this solution provides the best results so far, there are some limitations.
Like, it seems that I have to start a browser session for every track I want to download.
Ideally, I'd like to record every track as a seperate file.


Thank you.

---

