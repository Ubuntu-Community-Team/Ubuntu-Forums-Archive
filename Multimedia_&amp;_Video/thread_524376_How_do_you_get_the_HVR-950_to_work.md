---
title: "How do you get the HVR-950 to work?"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by nunayabiznis on 2007-08-13
I am trying to get my HVR-950 TV tuner to work in Xubuntu. I did everything in this guide ([http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html)), but MythTV says it cant find the card and it seems like way to bloated a program for my needs anyways. The program TVtime works but only for normal analog OTA stations. 

What I am looking for is a prgram that will let me watch Over-the-Air ATSC stations with my HVR-950, and any steps I need to go through to get said program to work.

Thanks in advance.

---

### Post by winterequinox on 2007-10-08
You can view dvb content with xine by selecting dvb from the menu at the bottom
of the main screen.  However, you have to have a channels.conf file in .xine.

You can try to find a channels.conf file for your area on the internet or create one
using a program called dtvscan.

If you want to record dvb content, you can use mencoder from the mplayer
suite for that, but you need 2 windows, one running a program called azap
(which requires a channels.conf file in a .azap directory), and mencoder
in another window.  I posed instructions about this in the talkback to a thread
on the PVR-950, which I'll cut and paste here:
o record dvb, you might try pchdtvr (for me it’s been
problematic, currently not working too well). Another,
much clunkier solution is to use atscscan, (get
dvb-atsc-tools-1.0.7 (or whatever latest revision is).
To use it, first get a list of
channels for your area (or maybe use dtvscan to scan for them),
create a list and put it in .azap/channels.conf, then, in
one window run azap -r .
for example, my channels.conf has the line:
KCSMMHz:647000000:8VSB:65:68:4

so to record it I can run the command:
azap -r KCSMMHz

Then in another window I run the command:
mencoder /dev/dvb/adapter0/dvr0 -ovc lavc -oac \
mp3lame -lameopts cbr:br=64 -vop pp=lb -o test.avi

And that records to test.avi

---

### Post by winterequinox on 2007-10-26
I upgraded my 64 bit AMD system to gutsy gibbon, and using the DVB button on xine no
longer works.  xine says it can't find the channels.conf file.  OK, I did a little googling and
other people said the same thing, but they COULD use xine to watch ATSC dvb broadcasts
using a command like "xine dvb://.XXX " where XXX is the tag of a station in the
channels.conf file, and that works for me.  (for example, my .xine/channels.conf file has
the line 'KQEDDT3:569000000:8VSB:81:83:3', I can watch that dvb channel with sound
using the command: xine dvb://KQEDDT3

As for recording, hey I got pchdtvr to work!  I compiled it from source (version 1.0), xtscut
didn't compile, but everything else seems to have.  I used the command:
      pchdtvr -s10 -p /home/cpw -o hdtv.out 30

and it recordied 10 seconds to a file called hdtv.out.  What is channel 30?  Well, I ran a
program called dtvscan and discerned that 30 was a valid channel, but I'm still a little
confused about demarcating channels in the ATSC dvb world myself.

---

### Post by dkscudder on 2007-11-03
nunayabiznis,

Perhaps you have figured this out by now, but this card worked perfectly for me after:

```
sudo modprobe dvb_core
sudo modprobe dst
```

I don't know that they are both necessary, but it is what I did.  Now it works beautifully in MythTV, but like you said, it is a huge program.  I would love to get it to work with kaffeine, but nothing has worked so far.  I don't have anything in the "Sources:" pick list, and I can't scan for channels.  I have tried using various "scan . . ." commands, but nothing has made it work.  If you, or any one else, know of a solution . . .

---

### Post by inkling on 2007-11-07
Hi All,

I wanted to let you know my old pchdtvr codebase is now called atscap and that you may find my 'new and improved' codebase at [http://atscap.sourceforge.net](http://atscap.sourceforge.net) along with an atscap-users forum and a bug-tracker.

Biggest improvements for atscap vs pchdtvr are man pages, better channel detection during setup, a web server with HTML3 and HTML4+CSS, less memory used when idle and some bug-fixes in the stream handling. Xtscut and atscut have also been improved.

Perhaps the latest version of Xtscut will compile for winterequinox. If not, let me know and I'll try to figure out why it doesn't work.

I have been working hard on the new atscap codebase for the past 18 months and I hope you like all of the new features.

Cheers!

-ink

---

### Post by winterequinox on 2007-11-09
Hello Inkling,

I downloaded /atscap-1.1rc9t.  Can't get it to compile on 64 bit gutsy-gibbon,
no imlib.h, no mpeg2dec/mpeg2.h, or mpeg2convert.h

I googled and apt got things like kde-devel, still no dice.  I suppose this is more an
ubuntu problem than anything else.  Maybe when I go back to slackware (I've
always ended up going back to slackware, the first distro I ever tried, back in 1994)
I'll be able to get it to work.

---

### Post by inkling on 2007-11-11
Try apt get imlib-1.9.14 and libmpeg2-0.4.1.  That should fix the missing header compile errors.

You might have to do similar for any distro, because the reports I read indicate that none of the distros have these installed by the usual "multi-media" package defaults.

There may be "-devel" packages required for the headers, in addition to the libraries themselves, depending upon how the distro handles the packaging. Gentoo fetches the original sources, so the libraries and headers are usually installed in one step.

From what I can tell, Xine and mplayer both use an embedded version of libmpeg2. That probably explains why the distros don't install libmpeg2 by default, even though the media player is there.

The old version of imlib that Xtscut is using is not usually installed by any package defaults, since most newer projects have switched to the newer imlib2. The older imlib should be OK for 64-bit.

Let me know if it gives you any further trouble.

---

### Post by winterequinox on 2007-11-15
I get "E: Invalid operation imlib-1.9.14"  when I try to get it.

I thought about trying to get the source tar ball, but I'm afraid I'll end
up getting a confused system as far as include files and libraries
if I try to build something like that from source.  I suppose I could
try to compartmentalize everything in /usr/local/ this and that, but
ubuntu is supposed to be a turnkey system, and, while I'm willing
to build a standalone executable like pchdtvr or atscap, I don't want
to have to customize the whole system for it.

One weird thing, I'm able to watch at least some High Definition
broadcasts (like PBS), with xine, but I can't record them with
the azap -r and mencoder tricks.  But everything is fine with
standard definition DVB broadcasts.  But of course, even when
I can record, it's inconvenient to set up things in two windows,
and using 'at' doesn't seem to work as a timer, though I had gotten
cron jobs to work with mencoder for analog TV in the past.

I suppose I could try to get myth TV to work but it's so elaborate, and
you're supposed to subscribe to services to give you channel info,
even if I got it to work I suspect it would be overkill for somebody who
just wants to record the occasional Nature or Wired Science documentary.

---

### Post by ZychoFlow on 2007-11-16
Hi I've also been having problems with the HVR-950. Some problems have been resolved,
but I'm going to detail them because I've seen many people with similar problems.

My problem is that I get video in both tvtime and mytht, but no audio.

_Resolved_
The first problem the I got was that I have usb speakers (a companion 5).
Linux configures usb audio devices as actual sound cards themselves, 
so at booting time you get this conflict over which drivers are loaded first 
the sound or the usb. After much trial and error I got my players to work by 
using the alsa:device=hw=<sound card index> (in my case  alsa:device=hw=3.0).
Note = The index is found by doing the "aplay -l" command.

Output
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Audio [Bose USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


That got my players to work.

_Resolved_
Problem number 2  My overall system sound wasn't working.
Like firefox, flash, youtube  etc.

so y used: "asoundconf list"

Names of available sound cards:
CA0106
CX8801
ICH5
Audio (my usb sound card).

Now to set the default sound card I used the command:
"asoundconf set-default-card Audio"

Now overall system sound works.

_Unresolved_
Now MythTv and TVTime still don't work. After some trial and error I got the video to work.

Some specs: My sistem has 3 sound card:
-MB integrated soundcard
-Audigy Live
-Use audio (Bose)

Two TV Tuners:
HDTV Wonder (/dev/video0)
HVR-950 (/dev/video1)

TVTime won't work for me

Configuration:
<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="DefaultBrightness" value="-1"/>
  <option name="DefaultContrast" value="-1"/>
  <option name="DefaultSaturation" value="-1"/>
  <option name="DefaultHue" value="-1"/>
  <option name="PrevChannel" value="46"/>
  <option name="Channel" value="45"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="3.5"/>
  <option name="CheckForSignal" value="0"/>
  <option name="AudioBoost" value="100"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="-1"/>
  <option name="Muted" value="0"/>
  <option name="V4LDevice" value="/dev/video1"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="stereo"/>
  <option name="PalDKMode" value="0"/>
  <option name="ShowCC" value="1"/>
  <option name="FullScreen" value="0"/>
  <option name="NTSCCableMode" value="Nominal"/>
  <option name="Frequencies" value="us-cable"/>
  <option name="DeinterlaceMethod" value="TelevisionFull"/>
  <option name="WideScreen" value="0"/>
  <option name="InputWidth" value="768"/>
  <option name="Norm" value="NTSC"/>
</tvtime>

Maybe I'm missing something?
Any help will me much appreciated.

---

### Post by inkling on 2007-11-20
Nothing much uses old imlib anymore, except Xtscut. Eventually I'll switch over to imlib2 because it claims to be faster.

It should be OK to configure the source to use PREFIX /usr/local. 

Most distros don't check that when compiling or installing new apps, and most new apps are using imlib2, so old imlib should be ignored.


MythTV and most other DVR software are overkill for ATSC broadcast. 

The EPG is usually included in ATSC broadcast.

atscap has no need for any subscriptions to any extra EPG services because it gets it from the broadcast.

It's really pathetic when the broadcasters want to charge me a fee to know what is going to come on the television.

If they can't bother to tell me what's coming on, in a standardized ATSC EPG format, then I won't bother to watch their shows.

---

### Post by methane on 2007-12-16
> **dkscudder said:**
> nunayabiznis,

Perhaps you have figured this out by now, but this card worked perfectly for me after:

```
sudo modprobe dvb_core
sudo modprobe dst
```

I don't know that they are both necessary, but it is what I did.  Now it works beautifully in MythTV, but like you said, it is a huge program.  I would love to get it to work with kaffeine, but nothing has worked so far.  I don't have anything in the "Sources:" pick list, and I can't scan for channels.  I have tried using various "scan . . ." commands, but nothing has made it work.  If you, or any one else, know of a solution . . .

I just got a HVR-950 as well, and I'm having the exact same problem in kaffeine with no "sources" pick list.  Were you ever able to solve this?
I've also tried to get xine to work with my HVR-950.  I've used 'scan' to generate a channels.conf list as shown here: [http://wiki.archlinux.org/index.php/DVB-S](http://wiki.archlinux.org/index.php/DVB-S)
but when I copy it into ~/.xine/  xine still complains that it can't find the file when I try to use DVB.  It doesn't, however, tell me what path it's looking in and I don't know if ~/.xine/ is the correct place for channels.conf.  
tvtime works with the HVR-950 but there is no sound for the analog channels (the only ones it can use).  'scan' found my local HD and DT channels when I used it, but I haven't been able to get anything to view these channels.

Any help would be greatly appreciated.  Thanks.

---

### Post by methane on 2007-12-16
Well, having once more searched around, I found that Kaffeine does, in fact, support ATSC.
There is a tool available to convert channels.conf from xine into a format which Kaffeine will happily read.  So, run the 'scan' tool to generate channels.conf, run the convert on that file, then drop it into the kaffeine .kde directory as per these instructions:
[http://sourceforge.net/mailarchive/message.php?msg_id=E1HGuNx-0003qI-4F%40sc8-sf-web9.sourceforge.net](http://sourceforge.net/mailarchive/message.php?msg_id=E1HGuNx-0003qI-4F%40sc8-sf-web9.sourceforge.net)

Anyway, this is what worked for me! :)

---

