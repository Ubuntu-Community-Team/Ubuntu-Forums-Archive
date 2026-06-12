---
title: "kino dissappears after a few seconds"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by roberto.eiberle on 2008-01-20
I start Kino from the konsole " gksu kino " everything seems to work, camera present and movie visible, camera is canon XL1 minidv, afer a few seconds kino shuts down with following dump

> Kino Common being builtSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
/usr/share/kino/scripts/dvdauthor/none.sh
/usr/share/kino/scripts/dvdauthor/growisofs.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/ffmpeg_xvid_dual.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
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
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Image Filter: Superimpose
>>> Image Filter: Titler
>>> Image Filter: Colour Average
>>> Image Filter: Charcoal
>>> Image Filter: Jerky
>>> Image Filter: Levels
>>> Image Filter: Pan and Zoom
>>> Image Filter: Pixelate
>>> Image Transition: Composite
>>> Image Transition: Blue Chroma Key
>>> Image Transition: Green Chroma Key
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
>>> AVC enabled
>> Constructing File Capture tracker
>> Trying XVideo at 720x576
>>> XvQueryAdaptors count: 2
>>> Xv: NV17 Video Texture: ports 355 - 386
>>> formats supported: 4
>>>     0x32595559 (YUY2) packed
>>>     0x32315659 (YV12) planar
>>>     0x59565955 (UYVY) packed
>>>     0x30323449 (I420) planar
>>> 0: XV_IMAGE, 2046x2046 rate = 1/1
send oops
send oops

Kino experienced a segmentation fault.
Dumping stack from the offending thread

Obtained 8 stack frames.
kino [0x8078861]
[0xffffe420]
/usr/lib/libiec61883.so.0 [0xb7ed98f7]
/usr/lib/libraw1394.so.8(_raw1394_iso_iterate+0x36b) [0xb74827eb]
/usr/lib/libraw1394.so.8(raw1394_loop_iterate+0x132) [0xb7481562]
kino(_ZN14iec61883Reader6ThreadEv+0xa0) [0x80ae0b0]
/lib/tls/i686/cmov/libpthread.so.0 [0xb749246b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb72c46de]

Done dumping - exiting.
roberto@roberto-desktop:~$

I am not very technical and have no idea what is wrong, would very much appreciate some help

---

### Post by bwtranch on 2008-01-20
Might try a real terminal

---

