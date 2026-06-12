---
title: "winff error"
date: 2011-09-16
forum: Multimedia Software
---

### Post by Mia1990 on 2011-09-16
I'M converting a avi to dvd format and i keep getting this error 

> [NULL @ 0x9351340] [Eval @ 0xbfd18b1c] Undefined constant or missing 
 '(' in 'mv0' 
 [NULL @ 0x9351340] Unable to parse option value "mv0" 
 [NULL @ 0x9351340] Error setting option trellis to value -mv0. 

Could someone tell me what this error is and what i need to do to fix it
I'M using winff and the the latest ffmpeg from git

Thanks

---

### Post by ron999 on 2011-09-16
> **Mia1990 said:**
> 
Could someone tell me what this error is and what i need to do to fix it
I'M using winff and the the latest ffmpeg from git

Hi
I have the same result with WinFF and FFmpeg from git too:-
"**Error setting option trellis to value -mv0**."

It seems the FFmpeg commands have changed so our WinFF DVD presets are out of date.
With **PAL** I can use these commands with FFmpeg:-
```
ffmpeg -i filename.avi -target pal-dvd -aspect 4:3 filename.mpg
```
or
```
ffmpeg -i filename.avi -target pal-dvd -aspect 16:9 filename.mpg
```

So try  similar commands for **NTSC**, and if it cures the fault then fix/replace your WinFF DVD presets.
```
ffmpeg -i filename.avi -target ntsc-dvd -aspect 4:3 filename.mpg
```
or
```
ffmpeg -i filename.avi -target ntsc-dvd -aspect 16:9 filename.mpg
```

---

### Post by FakeOutdoorsman on 2011-09-16
WinFF and FFmpeg from Git don't always work well together because the WinFF presets don't keep up with syntax changes. You'll need to modify your WinFF preset file. First copy the "new" preset file as andrew.46 displays: [updating your WinFF presets](http://ubuntuforums.org/showpost.php?p=11161810&postcount=8).

Then modify it:
```
sed -i 's/-trellis -mv0/-trellis 2 -flags +mv0/g' ~/.winff/presets.xml
```

I'm not sure if the WinFF presets for DVD actually work, and I'm also not totally sure if "2" is the best value for the trellis option in this case, but this should get things encoding for you at least.

**Edit:** I would trust ron999's examples more then the WinFF preset settings for DVD at least. The *-target* option has been around for a while, and I don't know why WinFF doesn't use that instead.

---

### Post by Mia1990 on 2011-09-17
Thank you FakeOutdoorsman and ron999.

I will try this first thing tomorrow morning.

---

