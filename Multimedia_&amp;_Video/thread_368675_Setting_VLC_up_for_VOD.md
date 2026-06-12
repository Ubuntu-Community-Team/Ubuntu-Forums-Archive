---
title: "Setting VLC up for VOD"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by elfranger on 2007-02-23
I have been looking in the forum for solution, but I am not really sure what to look for so here goes...

I have a DreamBox satellite tuner and running a VLC frontend plugin on it. I set VLC up on my windows computer and had it run as a backend... The procedure to do that is the following (for windows):
[i]> - File
- Open Network Stream

- Advanced options

- Select Stream/Save
- Select Settings
- Select  HTTP
- Set port 9090 for HTTP

- Select  MPEG TS
- Select Video Codec > mp2v
- Select Audio Codec > mpga
Store the settings by clicking Ok and Ok.

Then, activate WEBIF by selecting Settings - Add Interface - WEB Interface.[/i]

So, the question is, how do I set the VLC for linux up like that? I am running ubuntu 6.06.1, no gui...

The VLC frontend uses an XML file that contains the IP of the pc running VLC backend and the folder on the pc where the movie files are stored aswell as how to playback the various formats:

> [i]<server ip="192.168.1.10" webif-port="8080" stream-port="9090" user="admin" pass="admin" />
<config startdir="c:/movies" cddrive="d:" />
<codec mpeg1="mpgv" mpeg2="mp2v" audio="mpga" />
<setup name="SVCD" ext="NONE" Videorate="1000" fps="25" Videotranscode="0" Videocodec="mpeg2" Videosize="352x576" Audiorate="192" Audiotranscode="0" />[/i]

---

