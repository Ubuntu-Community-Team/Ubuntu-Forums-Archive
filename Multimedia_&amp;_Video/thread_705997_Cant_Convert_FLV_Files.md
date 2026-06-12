---
title: "Cant Convert FLV Files"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by dontgetshocked on 2008-02-24
I tried using WinFF,DownTube,GCStar and none of them work even though I get no errors.
I am missing something that is not installed , just dont know what!

Suggestions?


Thanks,

Dave

---

### Post by vishzilla on 2008-02-24
> **dontgetshocked said:**
> I tried using WinFF,DownTube,GCStar and none of them work even though I get no errors.
I am missing something that is not installed , just dont know what!

Suggestions?


Thanks,

Dave

I sometimes use media-convert.com or zamzar.com to convert FLV files, have you tried it?

---

### Post by benny bronx on 2008-02-24
You can try the firefox add on  "Video DownloadHelper"  It works well for me.

---

### Post by dontgetshocked on 2008-02-24
But that's just for getting them downloaded off the net. I have some files downloaded already, I need to convert them to avi or whatever format I choose?

Thanks,

---

### Post by mc4man on 2008-02-24
you could try FLV Extract  - needs mono (for linux) installed

---

### Post by kostkon on 2008-02-24
> **dontgetshocked said:**
> I tried using WinFF,DownTube,GCStar and none of them work even though I get no errors.
I am missing something that is not installed , just dont know what!

Suggestions?


Thanks,

Dave

Have you installed the version of *FFmpeg* from the [*Medibuntu* repository]("http://medibuntu.org/")?

---

### Post by harold4 on 2008-02-24
In the terminal, try the following and see what output you get
```
ffmpeg -i 1.flv 2.avi
```

---

### Post by dontgetshocked on 2008-02-24
OK, that worked, so how come the gui version's don't work?
Also, is there a wildcard to use with this so I can convert as a batch?

---

### Post by ron999 on 2008-02-24
Hi
If WinFF isn't working you could ask BiggMatt the question on his forum.

---

### Post by harold4 on 2008-02-24
> **dontgetshocked said:**
> OK, that worked, so how come the gui version's don't work?
Also, is there a wildcard to use with this so I can convert as a batch?

Toss this in a file, chmod +x fileName and run like ./fileName /path/to/dir

DISCLAIMER: Did not test as I'm not on a nix machine.
```

#!/bin/bash
inF=`ls $1/*.flv`

for x in $inF
do
	ffmpeg -i $x.flv $x.avi
done

```

---

