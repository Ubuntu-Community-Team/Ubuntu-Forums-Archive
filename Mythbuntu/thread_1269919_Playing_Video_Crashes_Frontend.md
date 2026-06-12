---
title: "Playing Video Crashes Frontend"
date: 2009-09-18
forum: Mythbuntu
---

### Post by slamhound on 2009-09-18
I have been using Mythbuntu for about a year (first on 8.10 and then 9.04) and decided to upgrade my 9.04 box to Avenard's .22 trunk repository ([http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html](http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html)).  The upgrade went smoothly and most things that I want to do work well.  I can watch, record, and playback TV and the graphite theme looks great.  However, if I try to play a video or watch a dvd, the frontend crashes with a segfault.  I am now looking for advice as to how to troubleshoot this problem.  

Here are some additional pieces of info:

The video files that I want to play work fine in vlc, and they play in mplayer (though I get an error box that pops up saying "unsupported pixelformat -1" in mplayer).  

I have tried setting the video player to mplayer (which it was set to as default when I installed) or internal.  Same problem with both.

I'm not sure if this matters, but I've tried different TV playback profiles, along with a vdpau profile that Avenard recommended.  

My system is 64-bit with nvidia 8300 graphics (and the 180 drivers).

Again, the only thing that looked unusual in the logs was the segfault message (I can provide it if it is informative; I'm still not sure what information is useful to people) in the syslog that occurs right when I try to play the file.

---

### Post by slamhound on 2009-09-26
A bump and an update . . . 

It turns out that the problem was a bit more limited than I thought.  First, I can now get DVDs to play (my stupid error of not reinstalling libdvdcss when I reinstalled the system).  In addition, the crash seems to be limited to when I play .vob files.  If I try to play an mpg file, it plays fine using the internal player.  Also, I can get mplayer to play the vob file from within Myth, but (I think) this only works when I do not use storage groups (which only support the internal player).  When I tried it from a machine that uses storage groups it wouldn't play (which I think is to be expected).

So my question is whether anyone can think of a reason why the Myth Internal player will crash when trying to play a vob file.  Again, I'm using .22, and I've tried both Avenard's repository and the 9.10 Mythbuntu alpha with the same results. And do you have any ideas about how to troubleshoot if you don't have an idea about a solution? I've looked at the logs but can't find any errors other than what was reported in my previous post.

---

### Post by slamhound on 2009-09-27
Okay, after a little more investigating, this appears to be a bug in MythTV .22:

[http://svn.mythtv.org/trac/ticket/6808](http://svn.mythtv.org/trac/ticket/6808)

This is from that bug report:  

"This appears to be an ffmpeg bug in Closed Caption decoding. You can work around it by disabling the parsing (comment out line 2303 of libs/libavcodec/mpeg12.c) but that's not an acceptable long term solution. "

I'm not exactly sure how to find "libs/libavcodec/mpeg12.c". Anyone know where this is (or whether it is even a file on my system that I can edit)?

And on a side note, is there anyway to search for files in Mythbuntu?  Thunar doesn't seem to have the same search functions that Nautilus does (or am I missing something obvious).

---

### Post by slamhound on 2009-09-29
Well it looks like the only way to solve this is to recompile myth, which is a bit beyond what I'm used to doing.  So I think I'll stick with using mplayer for vob files for now.

Should I assume that if a bug is filed for this with MythTV that no bug needs to be filed with Mythbuntu?  Or is alerting Mythbuntu developers helpful too?

---

