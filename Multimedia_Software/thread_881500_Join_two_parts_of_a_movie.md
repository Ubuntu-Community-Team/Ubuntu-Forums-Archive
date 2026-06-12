---
title: "Join two parts of a movie"
date: 2008-08-06
forum: Multimedia Software
---

### Post by GabrielWolff on 2008-08-06
I have two parts of a film, named Across.CD02.avi and Across.CD01.avi.

Both are around 700 MB.

I would like to join them to one big file.

When I opened a terminal and typed in: 
```
cat Across.CD01.avi Across.CD02.avi > Across.avi

```

I got one big file of around 1.4 GB, but when I opened it, it played only the content of the file Across.CD01.avi, and the time shown by VCL was that of Across.CD01.avi as well.

How could I make it work?

---

### Post by aeiah on 2008-08-06
off the top of my head (ie, you may want to check) do

```

mencoder -forceidx -aoc copy -ovc copy -o outputfilename.avi input1.avi input2.avi

```


the forceidx thing rebuilds the idx index, which can help with sync issues that can arise. the aoc and ovc copies are basically 'copy the audio and video and dont reencode either'

---

### Post by GabrielWolff on 2008-08-06
> **aeiah said:**
> off the top of my head (ie, you may want to check) do

```

mencoder -forceidx -aoc copy -ovc copy -o outputfilename.avi input1.avi input2.avi

```


the forceidx thing rebuilds the idx index, which can help with sync issues that can arise. the aoc and ovc copies are basically 'copy the audio and video and dont reencode either'

Uh...

```
gabriel@gabriel-laptop:~/Videos$ mencoder -forceidx -aoc copy -ovc copy -o Across.avi Across.CD01.avi Across.CD02.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-aoc is not an MEncoder option

Exiting... (error parsing command line)

```

Help?

---

### Post by aeiah on 2008-08-06
ooops :p

```
mencoder -forceidx -oac copy -ovc copy -o outputfilename.avi input1.avi input2.avi
```

sorry about that

---

### Post by GabrielWolff on 2008-08-07
> **aeiah said:**
> ooops :p

```
mencoder -forceidx -oac copy -ovc copy -o outputfilename.avi input1.avi input2.avi
```

sorry about that

Great, thanks :)

---

### Post by VortaX on 2008-08-20
ah great :) simple way of doing it:]

---

### Post by jmd9qs on 2009-01-05
i have used this to join 4 .avi's so that i can ffmpeg them into .mpg and author a DVD with it... however, it will go through the first video, then i get the error:

```
All video files must have identical fps, resolution, and codec for -ovc copy.
```

...? what do i do here? the code i originally used was:

```
avimerge -c -o PhysII_Lec05-08.avi -i PhysII_Lec05.avi PhysII_Lec06.avi PhysII_Lec07.avi PhysII_Lec08.avi
```

but the audio/video was WAY off, so then i:


```
 mencoder -forceidx -oac copy -ovc copy -o PhysII_Lec05-08.avi PhysII_Lec05.avi PhysII_Lec06.avi PhysII_Lec07.avi PhysII_Lec08.avi
```

this time the sync was great, but as stated above it only went through the first video and then stopped...

any suggestions???

---

### Post by netgrazer on 2009-12-02
I made an executable file called "vidmerge" in my ~/.gnome2/nautilus-scripts folder, and filled it with this:

```
#!/bin/bash
mencoder -forceidx -oac copy -ovc copy -o $NAUTILUS_SCRIPT_CURRENT_URI/merged.avi $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
exit
```

Now all I have to do is select the files to be merged in nautilus, right-click, and select "vidmerge" from the scripts menu. Merge in progress!

Todo:
- instead of "merged", use the string the source files have in common, minus things like "cd" " cd" "_cd" ".cd" "-cd" "part" " part" etc. Else, if they have nothing in common, use "merged"
- Also, check if it exists, first. Ask for overwrite.
- ignore non-avi files (if mencoder isn't already doing that)

That would make the ultimate script. Any suggestions on how to do that, particularly the file name manipulation, would be welcome :-k

---

### Post by gcbzzzz on 2010-01-02
netgrazer, feel free to adapt it for use in nautilus.

also to open a enhacement request to ship it :)
it's fully integrated with the gnome enviroment... only if notify-send was default in ubuntu....

[http://github.com/gcb/video-merger/blob/master/src/avi_merge.sh](http://github.com/gcb/video-merger/blob/master/src/avi_merge.sh)

---

### Post by gcbzzzz on 2010-01-02
see screenshot.


it also report on completion, errors from mencoder, and warnings about file overwrite and such.

---

### Post by Kale Good on 2010-07-21
I'm using this command:

mencoder -forceidx -ovc copy -oac copy part1.avi part2.avi -o file.avi

And, while it joins the videos, part1 is after part2. I've also tried the command without -forceidx (same thing) and with part1.avi and part2.avi in reverse order. All give me the same backwards result. 

Any ideas?

Thanks,
Kale

---

### Post by rubylaser on 2010-07-21
This is what avimerge was designed to do.  Try it like this...
```
avimerge -i part1.avi part2.avi -o mergedavifile.avi
```

---

### Post by Kale Good on 2010-07-21
This is giving me an .avi file that is 0 seconds in length. 

Here's the output from the command given above:
scanning file part1.avi for video/audio parameter
[avilib] V: 30.000 fps, codec=FMP4, frames=8702, width=640, height=480
[avilib] A: 44100 Hz, format=0x55, bits=0, channels=1, bitrate=64 kbps,
[avilib]    581 chunks, 2320016 bytes, CBR
merging multiple AVI-files (concatenating) ...
file 01 part1.avi
[part1.avi] (000000-008700) (290033.33 <-> 290002.00)
No audiodata left for track 0->0 (290002.00=290002.00) continuing ..
[part1.avi] (000000-008701) (290066.67 <-> 290002.00)
file 02 part2.avi
[part2.avi] (008702-017399) (580000.00 <-> 580002.00)
No audiodata left for track 0->0 (580002.00=580002.00) continuing ..
[part2.avi] (008702-017402) (580100.00 <-> 580002.00)
... done merging 2 file(s) in mergedavifile.avi
[avilib] V: 30.000 fps, codec=FMP4, frames=17403, width=640, height=480
[avilib] A: 44100 Hz, format=0x55, bits=0, channels=1, bitrate=64 kbps,
[avilib]    1161 chunks, 4640016 bytes, CBR


Thanks,
Kale

---

### Post by HarshReality on 2010-08-14
How do we join 2 video (avi) when the audio bitrates are different?

---

