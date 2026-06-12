---
title: "can't stream wma audio from VLC... but works with mplayer"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by retrovertigo on 2008-02-22
I have installed the w32codecs package, and I'm able to stream wma using mplayer, but when I try to do so in VLC, I don't get any audio.  Here's the output when I run VLC from the command line:

VLC media player 0.8.6c Janus
[00000300] access_mms access error: error while asking for file -1
[00000300] access_mms access error: error while asking for file -1
[00000300] access_mms access error: cannot connect to server
[00000300] access_mms access error: cannot read data
[00000309] main decoder error: no suitable decoder module for fourcc `wmal'.
VLC probably does not support this sound or video format.

I googled this and searched the forums but haven't found anything.  Is VLC just not capable of streaming this format, regardless of whether or not the codecs are installed?  Or, do I have to fiddle with VLC's configuration to get it to work?


I'm running Kubuntu 7.10, if that is of any consequence.

---

