---
title: "Garbled video with vlc and capture card"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by aprete on 2007-12-20
I have a Canopus video capture card, which takes a composite analog video signal and converts it to Firewire.  Under Window$ I was able to connect a VCR to the card and watch TV on my computer, using the software that came bundled with my DVD burner.  This software, Ulead DVD Player, has an option to play video direct from the capture card.  I want to do the same thing under Ubuntu Gutsy.

I like the vlc video player, because it supports full screen and DVD menus work under it.  It has an option to play from capture devices (File/Open Capture Device) but I can't get it to work.  When I click File/Open Capture Device/OK I see a timer ticking in the lower left-hand corner of the vlc window, but no video or audio.

I poked around the forum and tried the following two commands:

sudo chmod 666 /dev/raw1394
vlc dv/rawdv:///dev/raw1394

When I do this, I get garbled audio and video.  The video looks like it is divided into squares then scrambled (almost like one of those puzzles with sliding tiles).  The audio sounds like the scrambled audio on one of those Sony CDs that they tried to sell to the public about a year ago.  The terminal shows repeated "AC EOB marker is absent pos=xx" messages with varying values for xx.

There is nothing wrong with my hardware, because I can use Kino to capture video and audio.  But I don't want to use Kino because it's not full screen, and I don't want to capture, just watch.

I have been a Window$ user for many years.  I have dabbled in various flavors of Linux (SuSE, Knoppix) from time to time, but have always gone back to M$ because of one difficulty or another.  But now it seems that while Window$ is getting buggier, slower, more bloated, and more expensive (read: Vista), Linux is getting easier and easier to use, and it's free!  So I just got back into Linux recently by downloading and installing Gutsy.

Thanks for any help.

---

### Post by ddennedy on 2007-12-23
I don't know how to do it in VLC.  I'm not certain it should be possible. reading /dev/raw1394 does not provide raw DV. Firewire is not a DV specific technology, and raw1394 is just a generic way to access firewire on the system. It sounds like it is reading garbage. 

Here is one other way:
dvgrab - | ffplay -f dv -
press 'f' while playing to go fullscreen.

Maybe for VLC you can do:
dvgrab - | vlc dv/rawdv:///dev/stdin
or some other way to tell VLC to read from a pipe.

---

### Post by aprete on 2007-12-23
ddennedy:

I installed dvgrab and tried your method 1.  I saw the following messages

Found AV/C device with GUID 0x002011010200117e
Capture Started

but saw no video.

I tried your method 2 and got the same garbled video/audio that I saw/heard when I tried to play directly from /dev/raw1394.

Just for grins I installed vlc on Window$ and it works fine, playing from a URL called dshow://

---

### Post by aprete on 2008-02-07
I solved it.  The way that works is to pipe the output of dvgrab into vlc with the following command:

dvgrab - | vlc - --no-sub-autodetect-file :demux=rawdv

The problem was a bug in dvgrab 3.0 that was preventing the video stream from being written to stdout.  I downloaded dvgrab 3.1 and installed it and it works now.  As of this writing there's no package available for the latest dvgrab, so I had to compile it.

I still need to sudo chmod 666 /dev/raw1394 before I enter the above command, once every time I boot.

---

