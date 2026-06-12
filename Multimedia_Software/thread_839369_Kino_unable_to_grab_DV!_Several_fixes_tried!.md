---
title: "Kino unable to grab DV! Several fixes tried!"
date: 2008-06-24
forum: Multimedia Software
---

### Post by diegogranziol@gmail.com on 2008-06-24
Hey, Im kinda new to Kubuntu and im using the new (I think its called "Hardy") version, with KDE 4, which is great in many aspects, but maybe in certain functionality things not the best idea, but after having my Sabayon unable to find my usb devices, then several failed installs and lost, data, can you blame me. Anyway, im not a noob to linux, so i got apt-get going fairly quickly and built a pretty insane system and i'd just like to say, that Kubuntu is completely awesome, probably the best Linux O.S i've tried so far, although Metisse integration and all-round better stability, would raise it a pedigree, but that will come.

Anyway, one thing i wanted to do, was take my family video's from my dad's camcorder onto DVD, all the software seems to be in-place, but for some weird reason, the Camcorder doesn't seem to be working properly.

I've read up on the issue, tried to solve it myself, all has seemed to fail, basically, this is what happens when I run gksudo kino

It says, AV Controls enabled, however when the camera is swithched on, on the capture mode, I get a mix of a few images (stops quickly and takes no more data), with beneath, some raw1394 error (shown in picture below), along with saying the camera isn't on and other error messages, any idea what it could be and what the solution may be?

Here is the code when gk sudo is typed in

```
Kino Common being builtSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
/usr/share/kino/scripts/dvdauthor/none.sh
/usr/share/kino/scripts/dvdauthor/growisofs.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid.sh
> Creating page trim
>>> Image Create: Colour Range
>>> Image Create: Fixed Colour
>>> Image Create: From File
>>> Image Create: Gradient
>>> Image Create: Random noise
>>> Image Filter: No Change
>>> Image Filter: Black & White
>>> Image Filter: Kaleidoscope
>>> Image Filter: Fade In
>>> Image Filter: Fade Out
>>> Image Filter: Flip
>>> Image Filter: Mirror
>>> Image Filter: Reverse Video
>>> Image Filter: Sepia
>>> Image Transition: Dissolve
>>> Image Transition: Barn Door Wipe
>>> Image Transition: Differences
>>> Image Transition: No Change
>>> Image Transition: Push Wipe
>>> Image Transition: Switch
>>> Audio Filter: No Change
>>> Audio Filter: Dub
>>> Audio Filter: Fade In
>>> Audio Filter: Fade Out
>>> Audio Filter: Gain
>>> Audio Filter: Mix
>>> Audio Filter: Silence
>>> Audio Transition: Cross Fade
>>> Audio Transition: No Change
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Image Filter: Colour Average
>>> Image Filter: Charcoal
>>> Image Filter: Jerky
>>> Image Filter: Levels
>>> Image Filter: Pan and Zoom
>>> Image Filter: Pixelate
>>> Image Transition: Composite
>>> Image Transition: Blue Chroma Key
>>> Image Transition: Green Chroma Key
>>> Image Filter: Superimpose
>>> Image Filter: Titler
>>> Image Filter: Blur
>>> Image Filter: Colour Hold
>>> Image Filter: Soft Focus
>>> Image Transition: Luma Wipe
>> Starting Editor
>>> iec61883Writer::iec61883Writer port 0 channel 63
>> Creating undo/redo buffer
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
>> Leaving Editor
>> Left Editor
>> Starting Capture
>> AV/C Enabled
>>> Using iec61883 capture
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>> Kino Common newFile
>> Leaving Capture
>> Constructing File Capture tracker
>> Starting Editor
>>> iec61883Writer::iec61883Writer port 0 channel 63
>>> Received playlist to store at position 0
>>>> Adding to end
Exiting Kino
```

Thnx!

---

### Post by quinnten83 on 2008-06-25
Check the Kino website, they might have some solution or instruction. Did you instal dvgrab?
I myself am having problems with kino. It's giving me hell when I want to import a file. It says importing, but then it never finishes importing.
I'm only having this issue now on Hardy. It worked reasonably okay-ish in gutsy.

---

### Post by diegogranziol@gmail.com on 2008-07-12
Had a look on the website, completely useless, didn't help, found this one post by one guy which was relatively helpfull

type this into the konsole

> sudo mknod /dev/raw1394 c 171 0


chmod it to 777, gksudo konqueror, etc.. and run kino as root, worked great till a few days when it went back to the same old problem, half work with a lot of /dev/raw1394 errors, anyone know of any permanent fixes?

---

