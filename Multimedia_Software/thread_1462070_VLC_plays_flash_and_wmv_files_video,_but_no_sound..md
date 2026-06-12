---
title: "VLC plays flash and wmv files video, but no sound."
date: 2010-04-25
forum: Multimedia Software
---

### Post by thegreatdestroyer on 2010-04-25
Ubuntu 8.04 Hardy Heron LTS
Kernel Linux 2.6.24-27
GNOME 2.22.3

Well fauzy and worked on this for a couple of hours and what I got out of it was a newer version of VLC media player that still does the same with those two file types. This wasn't happening until today. A day ago those were playing just fine. As a result of fauzy's help I now have Medibuntu and I believe Multiverse. I'll pastebin our conversation below as it perhaps someone will find something we missed.

[http://pastebin.com/73YFxHDY](http://pastebin.com/73YFxHDY)

The problem is occuring with flv and wmv files. They have video, but no sound in VLC. VLC plays mpg and mp3 just fine for now. I'll pastebin error messages from VLC for each file type below.

[http://pastebin.com/6iV72dGi](http://pastebin.com/6iV72dGi)

I'd really prefer to chat live with someone via instant messenger to solve this problem. I have handles for all popular protocols except Skype. I'm still pretty new to Ubuntu and Linux in general and can safely say I'll never be great with the command line. If you contact me please break things down. I'll list my messenger handles below. I'm on each day after lunch time EST. Messenger is up most days, just a drop me a line and I'll message you back as soon as I see it.

AOL theobserver711
Yahoo! sword_of_truth133
Windows Live [EMAIL="diversified_madness@live.com"]diversified_madness@live.com[/EMAIL]
GMail the.great.destroyer13
ICQ 353986119

Thanks in advance! :)

---

### Post by mc4man on 2010-04-25
Look for updates to libavcodec1d and libavformat1d this week - should resolve your issue

Otherwise you'd need to revert to last version (3:0.cvs20070307-5ubuntu7.3) or replace  with the current ones for hardy in medibuntu.

relevant links
[http://ubuntuforums.org/showthread.php?p=9161231#post9161231](http://ubuntuforums.org/showthread.php?p=9161231#post9161231)

(the odds of you building a current vlc git on hardy without some serious mods are zero - don't waste your time

---

