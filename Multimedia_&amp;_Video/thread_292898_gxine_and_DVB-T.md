---
title: "gxine and DVB-T"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by MikeMcKay on 2006-11-04
Hi,

I'm trying to get my DVB-T card working with either MPlayer or gxine in preparation for installing mythTV in accordance with the advice in [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php).  

I think I've got the TV card outputting a sensible data stream to stdout but I get problems with both MPlayer and gxine when I try to get them to read from stdin. They appear to be different problems and I've taken the liberty of starting a separate thread for each. This thread concerns gxine.

The tzap command seems to work and reports the following about every second:[INDENT]     status 1f | signal c9c9 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
[/INDENT]The command I'm using to pipe the mpeg stream to gxine is:[INDENT]mike@polaris:~$ sudo -s -H
Password:
root@polaris:/home/mike# dvbstream -o -ps 201 202 -qam 16 -cr 3_4 | gxine -v stdin://mpeg2
[/INDENT]The gxine UI comes up but I immediately get a GUI error box with:[INDENT]The xine engine failed to start.
No demuxer found - stream format not recognised.
[/INDENT]The terminal output of dvbstream and gxine is attached.

I note that about two thirds of the way down the log messages, gxine appears to report sensibly formatted video and audio streams.

I'm also confused by the seemingly contradictory messages:[INDENT]"couldn't find demux for >stdin://mpeg2<", and
"found demuxer plug-in: Elementary MPEG stream demux plugin".
[/INDENT]I've tried a few different stream designators in the command line, e.g. "stdin://", "stdin:/" and "stdin:", with no difference in the results.  There were virtually identical log messages.

I'm now completely stuck.  I don't want to proceed with the mythTV installation because I've seen various comments that If you haven't got the basic TV functions working first you won't get far with mythTV.  Also, I have heard that mythTV uses MPlayer or gxine for tv display.

So all in all, any suggestions or pointers would be most welcome.

---

### Post by MikeMcKay on 2006-11-04
Hi,

Some additional information since my last post.

The gxine UI -> xine engine log -> messages, contains the following:[INDENT]xine: found demuxer plug-in: Elementary MPEG stream demux plugin
xine: found input plug-in  : file input plug-in
xine: couldn't find demux for >stdin://mpeg2<
xine: found input plug-in  : stdin streaming input plug-in
[/INDENT]and the gxine UI -> Stream Info, contains:[INDENT]Video codec:  MPEG (libmpeg2)
Video format: 320x240, 25fps, 1.98:1, 0bps
System layer: MPEG_ELEM
[/INDENT]Which all looks almost right ? ? ?

---

### Post by MikeMcKay on 2006-11-06
Hi,

Some further information.  The problem seems very specific to the use of the MRL, stdin:/

The following works OK:
```
cat file.mpg > test.mpg
gxine file:///home/mike/test.mpg
```but the following does not:

```
 cat file.mpg | gxine stdin:/

```Anyone have any thoughts ?

---

