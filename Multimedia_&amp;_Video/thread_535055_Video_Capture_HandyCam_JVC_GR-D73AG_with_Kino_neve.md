---
title: "Video Capture HandyCam JVC GR-D73AG with Kino never success!!!"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by ramadhian on 2007-08-26
at my first time installation of Feisty 7.04 from CD, kino can capture video from my JVC GR-D73AG

after I add so many repo at my source list kino not work anymore

Today, I've just update kernel version to Gutsy kernel Linux 2.6.22-10-generic i686

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

and also I already update my Kino version to 1.1.1
but it still can not help me to make video capture work out-of-the-box

kenzo@ramadhian:~$ dmesg | grep 1394
[] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feafe000-feafe7ff]  Max   
   Packet=[65536]  IR/IT contexts=[4/4]
[] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size 
    to 512 bytes
[] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[ffffffffffffffff]
[] ieee1394: raw1394: /dev/raw1394 device initialized
[] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. 
   Use raw1394 instead.
[] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] video1394: Installed video1394 module

kenzo@ramadhian:~$ kino
> help language code en
> Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/none.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
/usr/share/kino/scripts/dvdauthor/growisofs.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid.sh
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
> setting video preview size to 768x576
>> Starting Editor
>> Creating undo/redo buffer
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end


then I click on Edit -> Preferences .. My AV/C Device still not showing at IEEEE 1394 Subsystem

If I click on Capture Button .. it said "No AV/C Complience detected or not switch on"

My HandyCam is already in Switch On Mode  ,, sometime Kino get Freeze when I click on Preferences to see AV/C Device detection if I switch on my handycam before I start kino, 

starting kino before HandyCam Switch On make no different too..

I am so confuse what is the Issue exaclty ,,

- Is it a kernel problem ?
- or I have a bad Firewire Card
- or the problem is Kino itself ?

in my windows xp ,. everything run so perfectly with Pinnacle Studio

please dont tell me to switch to windows for capturing video

---

### Post by ramadhian on 2007-08-26
kenzo@ramadhian:~$ dmesg | grep 1394

[] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feafe000-feafe7ff]  
   Max Packet=[65536]  IR/IT contexts=[4/4]
[] ohci1394: fw-host0: Serial EEPROM has suspicious values, 
   attempting to set max_packet_size to 512 bytes
[] ieeee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0080880304f88088]
[] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[ffffffffffffffff]
[] ieee1394: raw1394: /dev/raw1394 device initialized
[] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release.
  Use raw1394 instead.

with GSCANBUS, I can see JVC Device

---

### Post by jmiter on 2007-09-02
I have a quick fix that worked for my JCV GR-DF550u camcorder using Kino 0.9.2 on Fiesty (amd64)

I started Kino using sudo from the command line.  No problems - device was recognized and everything captures correctly with device controlled from Kino.  Previously was starting Kino as my regular user.  No luck with kino finding the device.  /dev/dv1394/0 existed, but chmod that device to 666 did not work.  neither did chown to my regular user.

I do not know if this is optimal, but it works and I'll probably change my kde menu icon to start Kino as root.

---

