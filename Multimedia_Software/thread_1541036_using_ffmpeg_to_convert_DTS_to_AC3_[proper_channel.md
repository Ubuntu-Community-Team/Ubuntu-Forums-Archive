---
title: "using ffmpeg to convert DTS to AC3 [proper channels reordering]"
date: 2010-07-28
forum: Multimedia Software
---

### Post by Ko$ on 2010-07-28
I have a .mkv container with proper video (h264/~6000kbps) and audio (DTS/1500kbps). For some reason I want to have similar quality but with another video and audio codecs. For video it goes well and ffmpeg is very helpful here, no problems. Also, I want DTS to become AC3/320-448kbps/5-6 channels. Commands like this:

> ffmpeg -i in.dts/mkv -acodec ac3 -ac 5 -ab 448k out.ac3

gives me not proper reordered sound in channels, so I hear center on the right, music on the left, etc. 

Is there a way to make that properly with ffmpeg? 

Also, I have a question about multi core encoding cause I have a quad processor. Ffmpeg seems not using them in all the way, I get something like 25% of CPU usage while encoding. Command -threads, even using the h264, does not make any extra load of cpu.

---

### Post by Ko$ on 2010-07-28
This one does it:

[http://github.com/JakeWharton/mkvdts2ac3/tree/8131e77772ef20250d2b304ba6f12a3813cd6664](http://github.com/JakeWharton/mkvdts2ac3/tree/8131e77772ef20250d2b304ba6f12a3813cd6664)

---

### Post by jimmah6786 on 2010-09-13
Can anyone confirm that ffmpeg will not reorder the channels correctly when going from dts to ac3??

---

### Post by ian.ward on 2011-01-04
I confirm this problem with ffmpeg in Ubuntu 10.04

Using dcadec + aften instead of ffmpeg (the way the script linked above does) works properly though.

---

### Post by MarceloCulotta on 2011-09-01
For converting MKV DTS to MKV ac3, I use two applications: 
WinFF and MKVmerge (it shows as MKV files creator in the Applications menu)


[LIST=1]
[*]WinFF:For creating the AC3  audio track, I open WinFF, then I Add the MKV file that contains the DTS  track. In Output details,  I select
[/LIST]
           
           Convet to           **Audio**
            Device Preset      **Ac3 - 384kbps Stereo **
           Output Folder      **Any folder you like** (I use the one containing the MKV file)
           
           This will create an audio file with the same name as the MKV file, but with the   ac3 extension

            2. MKV files creator (mkvmerge)
    
    Input Files: **add the MKV** file for which you created the ac3 audio track.
    In the Tracks, chapters and tags, **UNSELECT the DTS audio file**
    Input files again: **add the ac3** file that you created with WinFF
    **Start muxing**

This creates a file with the same name as the MKV file, except it has a  (1) added to it that will have the ac3 audio track for playing as 2  channel stereo.
   
I hope this helps!

---

