---
title: "Audio loopback not present!"
date: 2010-09-04
forum: Multimedia Software
---

### Post by .Michael on 2010-09-04
I have the same problem in Windows 7 and Ubuntu 10.04 where I can't record "what I hear" or "Stereo Mix" or "loopback", etc...

I did not have this problem in previous versions of Windows (XP) and Ubuntu (9.04)...

I hope this isn't because of MPAA/RIAA/DMCA/ACTA crap!

Audio Card as reported by alsamixer: SigmaTel STAC9200

---

### Post by cchhrriiss121212 on 2010-09-04
What is it you are recording from and what program are you using to do it?

---

### Post by amauk on 2010-09-04
Bash script
will record all sound produced by your system, and save it as a wav file

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

### Post by .Michael on 2010-09-04
Pretty handy shell script.
Thanks.

---

### Post by nikkool on 2010-09-20
awesome script, did the job perfectly.
Thanks

---

### Post by benow on 2010-12-10
Thx for the juicy script, sox rox.

---

