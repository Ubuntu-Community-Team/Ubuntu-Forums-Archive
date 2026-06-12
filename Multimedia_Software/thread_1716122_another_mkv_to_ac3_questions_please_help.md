---
title: "another mkv to ac3 questions please help"
date: 2011-03-28
forum: Multimedia Software
---

### Post by adduds on 2011-03-28
hi there i'm trying to take a mkv file The Tourist which has that cinavia audio track watermarking

i'm trying to convert the DTS audio track to AC3 to avoid it muting my movie on my ps3 while streaming it

I downloaded avidemux GTK+ copied the video and changed the audio to AC3 now when i browse the it says folders on my ps3 the new video file doesn't come up

i also downloaded the mkvdts2ac3.sh when i try to run it it says do you have dcadec installed?

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

