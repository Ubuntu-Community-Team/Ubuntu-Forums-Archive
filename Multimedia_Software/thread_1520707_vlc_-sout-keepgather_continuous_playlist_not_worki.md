---
title: "vlc -sout-keep/gather continuous playlist not working"
date: 2010-06-29
forum: Multimedia Software
---

### Post by frankjohn on 2010-06-29
Been trying for days but still nothing:

> vlc --playlist-tree "/home/john/movies/" --loop -vvv **-[COLOR=Red]-sout-keep[/COLOR]**  --sout='[COLOR=Red]**#gather**[/COLOR]:duplicate{dst="transcode{venc=x264{keyint=60,idrint=2},vcodec=h264,vb=600,acodec=mp4a,ab=64,channels=2,samplerate=44100, width=320,  height=240}:rtp{dst=127.0.0.1,port=1234,sdp=file:///home/john/vlcstream/vlc.sdp}"}' Works fine for the first stream loaded but when it changes to the next in the list the output is blank. 

Here's a snipet from vlcs wiki:

> 
**--sout-keep**, --no-sout-keep
                                 Keep stream output open (default disabled)
          This allows you to keep an unique stream output instance across
          multiple playlist item (**automatically insert the gather stream output**
          if not specified) (default disabled)Any ideas?

LOGS:

> $ vlc -l|grep stream
VLC media player 1.2.0-git Twoflower (revision 1.1.0-pre1-1073-g85fadc9)
  mp4                    MP4 stream demuxer
  mkv                    Matroska stream demuxer
  stream_out_raop        Remote Audio Output Protocol stream output
  stream_out_record      Record stream output
  **stream_out_gather**      Gathering stream output
  stream_out_rtp         RTP stream output
  stream_out_es          Elementary stream output
..........................................................................> **main debug: stream=`gather'**
main debug: looking for sout stream module: 1 candidate
**main debug: using sout stream module "stream_out_gather"**
main debug: TIMER module_need() : 0.399 ms - Total 0.399 ms / 1 intvls (Avg 0.399 ms)
main debug: using timeshift granularity of 50 MiB
main debug: using timeshift path '/tmp'

---

### Post by frankjohn on 2010-07-02
Anyone?

---

### Post by rogerdpack on 2010-11-16
Maybe the two streams don't match encoding? If not then you'll want to transcode them...
See [http://wiki.videolan.org/Documentation:Modules/gather](http://wiki.videolan.org/Documentation:Modules/gather)

---

### Post by bliffle on 2011-01-20
This has been fixed, I believe, over here:

[http://ubuntuforums.org/showthread.php?t=1551771&highlight=vlc+playlist](http://ubuntuforums.org/showthread.php?t=1551771&highlight=vlc+playlist)

---

