---
title: "how to determine DVD region codes"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by pytheas22 on 2008-01-22
I have a PAL DVD that I wanted to copy to NTSC so that I can play it in my American standalone DVD player.  I ripped the DVD to my hard drive, getting several .VOB files and corresponding IFOs and BUPs.  I then used the command "makedvd -burn" to write to disk, sort of assuming that it would create an NTSC DVD, because that's what I get every other time by default.  But the DVD I burned does not play on my DVD player, although it works fine on my computer.  I am not sure that the region code is the reason that it won't play in the DVD player (lots of other things could have gone wrong, I guess), so before I go further, I was hoping someone could tell me three things:

1. is there a way that I can check to see which region code is used by the DVD that I burned?

2. is there something I should have done with the .VOB files before burning them to make sure that they'd be written in NTSC?  I thought that the region code didn't have anything to do with the DVD contents themselves, but maybe I am missing something.

3. is there an argument I can use with makedvd to force the region code I want?  the man page doesn't mention anything like that

Thanks in advance for any help.

---

### Post by ron999 on 2008-01-22
Hi
Q1 The easiest way for me to find a DVD's region is to load the dvd then type into the monitor
**vlc dvd://**
(You need to have VLC media player installed)

I get a display like shown in the attachment.
One of the lines says:- "libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8".

Q2 There's a Windows prog called 'IfoEdit' which runs under wine. With that you can see the disc's region and set it to any permutation of regions or all of them, then save it (before you burn it). Look at line number [00000023] in the program's readout. It makes changes to the file video_ts.ifo.

You can also make it NTSC and change the resolution (720x480 for NTSC). Look at line number [00000100]. See the other attachment.
But I don't think it's that simple. Making these two changes only alters the information in the file video_ts.ifo. I don't think that it re-encodes the video. The ifo file contains instructions for your video player. So you'd just be fooling it into thinking that it's NTSC.

Q3 When you use makedvd -burn it will just burn the files, it's not possible to change things here.

If I was doing this job I'd use vobcopy (from the repo) to extract the main movie as one file on my hard drive.
Then I'd use tovid/makexml/makedvd to author and burn an all-region NTSC dvd.

This is the link for IfoEdit download:-[http://www.afterdawn.com/software/video_software/dvd-r_tools/ifoedit.cfm]("http://www.afterdawn.com/software/video_software/dvd-r_tools/ifoedit.cfm")

This is the link for tovid:- [http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")
:cool:

---

### Post by yabbies on 2008-01-22
I bought a PAL version of Flash Gordon and converted it to NTSC
essentially it comes down to after removing the region codes it still will not play because of PAL ratio
720x576 so you need to encode to NTSC 720x486/480
so what I did was use DVD::Rip to rip and transcode the main movie to avi.
then used tovid to transcode back to mpg with the correct NTSC
going to lose some quality with the compression

---

### Post by pytheas22 on 2008-01-22
Thanks for your responses; it makes sense now why it wouldn't work because of resolution issues.  I'm sure I'll figure it out eventually.

---

