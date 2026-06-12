---
title: "Can not download mmsh: stream"
date: 2009-03-20
forum: Multimedia Software
---

### Post by BioGeek on 2009-03-20
Hi all,

I'm trying to download the streaming news program from this page: [http://iwatch.be/2007/player.php?preview=1&category_id=hetnieuws&item_id=hetnieuws_3_19&dc=nieuws](http://iwatch.be/2007/player.php?preview=1&category_id=hetnieuws&item_id=hetnieuws_3_19&dc=nieuws)

It plays just fine on Jaunty (Yay!), but now I want to download that program for eternity because I have a small guest appearance in it.

Some poking around in the source code reveals the URL [http://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv](http://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv) but downloading that doesn't give me a .wmv file but a text file with 2 other URLs in. Trying to download from those URLs gives time-out errors.

```

$ wget http://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv
--2009-03-20 20:43:54--  http://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv
Resolving streaming.vtm.be... 194.0.174.8
Connecting to streaming.vtm.be|194.0.174.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 163 [video/x-ms-wvx]
Saving to: `20090318_hnlaat.wmv'

100%[======================================>] 163         --.-K/s   in 0s      

2009-03-20 20:43:55 (11.2 MB/s) - `20090318_hnlaat.wmv' saved [163/163]

$ file 20090318_hnlaat.wmv
20090318_hnlaat.wmv: ASCII text, with CRLF line terminators
$ cat 20090318_hnlaat.wmv
[Reference]
Ref1=http://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv?MSWMExt=.asf
Ref2=http://192.168.68.71:80/VTM/agility/20090318_hnlaat.wmv?MSWMExt=.asf
$ wget http://192.168.68.71:80/VTM/agility/20090318_hnlaat.wmv
--2009-03-20 20:46:20--  http://192.168.68.71/VTM/agility/20090318_hnlaat.wmv
Connecting to 192.168.68.71:80... failed: Connection timed out.



```

When I play the streaming file in Totem it gives as location [mmsh://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv]("mmsh://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv")

Trying [a trick found in another forum post]("ubuntuforums.org/showthread.php?t=201405") (after installing mplayer and mimms) doesn't work either:

```
$ mplayer -dumpstream mmsh://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv -dumpfile 2009_03_18_nieuws_vtm.wmv
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mmsh://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv.
No stream found to handle url mmsh://streaming.vtm.be/VTM/agility/20090318_hnlaat.wmv


Exiting... (End of file)
```


Any other things I can try?

---

### Post by jjpcexpert on 2010-12-19
You have to use a special rip program or a very long GStreamer pipeline.

---

### Post by markthekdeguy on 2010-12-21
this *may* help ..

in firefox i install an extension called
' media  player connectivity '
which enables me to decide which player to open a stream with.

then if you choose VLC and it works, you can simply press record !

you can show the red-dot record button in VLC
'view' - ' customise interface' then drag the red 'record ' button to the 
'line 1 bar' and it should now be easy to record.

hth
Mark

---

