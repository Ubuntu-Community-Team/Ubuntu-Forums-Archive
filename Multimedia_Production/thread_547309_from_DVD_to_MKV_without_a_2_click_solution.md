---
title: "from DVD to MKV without a 2 click solution"
date: 2007-09-09
forum: Multimedia Production
---

### Post by slavik on 2007-09-09
I used to encode anime for a group and my process went something like this:
- rip dvd (main feature as 1 VOB file)
- demux the ripped VOB
- encode audio using besweet
- create a d2v project for the video
- create decimate/telecide metrics for the decomb for avisynth (mencoder has the decomb plugin along with others that I used)
- edit the telecide/decimate metrics with YATTA (Yet Another Telecide Tool for Anime)
- encode the video with vdubmod (using avisynth for the filtering) using 2 passes
- mux the stuff (audio, video, SSA subtitles) into an MKV

I am trying to do something similar but on Linux. My problem so far is that I can't seem to find tools to rip the DVD in that way (I just want to select the chapters and tell it to just copy the files, or to select the chapters and it append them into a single file). Demuxing a VOB is also tedious, I know mplayer can extract a track, but I want it to just demux ALL channels.

Also, how can I encode audio and video separately through mencoder? I have asked in the mplayer/mencoder irc channel and wasn't able to get a response.

Another problem is how do I get decomb plugin in mencoder to take a file which tells it how to decimate and such ...

---

### Post by michael37 on 2007-09-09
> **slavik said:**
> I used to encode anime for a group and my process went something like this:
- rip dvd (main feature as 1 VOB file)
- demux the ripped VOB
- encode audio using besweet
- create a d2v project for the video
- create decimate/telecide metrics for the decomb for avisynth (mencoder has the decomb plugin along with others that I used)
- edit the telecide/decimate metrics with YATTA (Yet Another Telecide Tool for Anime)
- encode the video with vdubmod (using avisynth for the filtering) using 2 passes
- mux the stuff (audio, video, SSA subtitles) into an MKV

I am trying to do something similar but on Linux. My problem so far is that I can't seem to find tools to rip the DVD in that way (I just want to select the chapters and tell it to just copy the files, or to select the chapters and it append them into a single file). Demuxing a VOB is also tedious, I know mplayer can extract a track, but I want it to just demux ALL channels.

Also, how can I encode audio and video separately through mencoder? I have asked in the mplayer/mencoder irc channel and wasn't able to get a response.

Another problem is how do I get decomb plugin in mencoder to take a file which tells it how to decimate and such ...

Oddly enough, I found Ubuntu tools better than Windows tools.  Try them.

For ripping, use k9copy.
For recoding video and audio, use Avidemux.  It ships with many mplayer plugins.

---

### Post by slavik on 2007-09-10
I'll give k9copy a try, the thing with avidemux is that I couldn't get it to work on just audio ...

I am thinking of writing my own tools. (audio is simply link up the decoder, decode to raw, then send it to an encoder that handles raw).

the problem with avidemux (I have been using and for what I was able to get it to do, it is awesome), the problem came with not being able to tell the decomb plugin how to act.

with avidemux, I can tell the decomb filter to work on certain frame ranges and such, but the telecide file that is output automates this ...

On windows, I used the following tools (as a point of reference):
smart ripper for ripping
vobedit for demuxing
dgindex > yatta > avisynth (filters and decomb and such here) > vdubmod (for actual xvid encoding)
besweet for audio encoding
mkvtoolnix for muxing into an mkv file

---

### Post by eugenesan on 2008-01-20
One link will do the job :-)
[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

---

