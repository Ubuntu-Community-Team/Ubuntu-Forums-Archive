---
title: "Solved: CC (and maybe Teletext) to DVD"
date: 2008-02-27
forum: Mythbuntu
---

### Post by faginbagin on 2008-02-27
OK, so I've got a solution for the one feature I wanted that MythTV didn't provide "out of the box." namely, the ability to burn recordings to DVDs with closed captions. If you're interested, you can learn about my package, called cc2subtitles, here:
[http://www.hbuus.com/cc2subtitles/](http://www.hbuus.com/cc2subtitles/)

Here are some details that should help you decide whether cc2subtitles might be useful to you: 

[LIST]
[*]It only works with recordings made with the IVTV driver, the one used by Hauppauge analog cards. FWIW, I have a PVR-150.
[COLOR="DarkRed"]**See following post for news about support for more media formats.**[/COLOR]
[*]It uses a library called libzvbi (also known as ZVBI - VBI Decoding Library). libzvbi is part of the Zapping project, a TV viewer for the Gnome desktop. libzvbi is available as a debian package in the debian and ubuntu repositories, and probably many other repositories, too. 
[*]libzvbi supports PAL/SECAM Teletext, probably better than NTSC CC, so there's a good chance my little utility will work with Teletext, too. I haven't tested it, but would be willing to, if I can get a hold of some PAL recordings that have VBI data. Or, perhaps someone else in PAL land would like to do the work? 
[*]It converts IVTV encoded VBI data into DVD subtitles. It takes advantage of the fact that libzvbi can produce .png (Portable Network Graphics) renderings of CC/Teletext. An included bash script then uses spumux (part of dvdauthor) to convert the .png images into DVD subtitles. I think the results are more appealing than other solutions that use spumux to encode text based subtitles. The results look like what you're used to seeing on your TV, including support for italics and special characters used in Spanish & French, as well as the musical note. Plus, it supports closed caption colors. 
Note: some special characters requires a patch for libzvbi. 
[*]I'm pretty sure it won't work if you like to cut commercials out of your recordings. That's because of the timestamp data I use to figure out where to add subtitles to recordings. I've worked around this problem by patching mytharchive's script, mythburn.py, to add chapter marks at the commercial marks found by mythcommflag.
[*]I'm using mythbuntu 8.04.2 with mythtv/mythplugins 0.21.0+fixes18207-0ubuntu4~hardy1.[/LIST]

---

### Post by faginbagin on 2009-06-22
The latest addition to the project is mythsubtitles, which can extract closed captions from a wider variety of media file formats. It is known to work with the following:
[LIST]
[*]ATSC/QAM recordings made with hardware DVB encoders supported by the cx18 and cx88 drivers and probably other dvb drivers. Tested with QAM recordings made with the cx18 and cx88 drivers using the digital inputs of a Hauppauge HVR-1600 and a pcHDTV HD-5500 connected to a US cable TV provider. 
[*]Recordings made with MPEG-2 hardware encoders supported by the ivtv and cx18 drivers. Tested with NTSC recordings made with the ivtv and cx18 drivers using the analog inputs of a Hauppauge PVR-150 and HVR-1600 connected to a US cable TV provider. 
[*]MythTV's NuppelVideo recordings, file extension .nuv. Tested with NTSC recordings made with the cx88 driver using the analog input of a pcHDTV HD-5500 connected to a US cable TV provider. 
[*]Individual titles ripped from DVDs, typical file extension .vob. Tested with titles ripped from NTSC DVDs using MythTV's MythVideo plug-in and the "Perfect" option.
[*]I'm using mythbuntu 9.04 with mythtv-0.21.0+fixes-20573-openglvdpau from avenard.org and mythplugins-0.21.0+fixes19556-0ubuntu8.
[/LIST]
For more information:
[http://www.hbuus.com/cc2subtitles/](http://www.hbuus.com/cc2subtitles/)

---

