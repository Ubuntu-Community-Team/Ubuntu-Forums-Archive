---
title: "VHS to DVD converting"
date: 2011-11-05
forum: Mythbuntu
---

### Post by AlecJ on 2011-11-05
I have a friend who wants to convert a training VHS to DVD, I have given it some thought and,

I have an old analog UHF TV PCI card, so install Myth on my Desktop Ubuntu with the card assuming Myth recognizes the card, tune the card with one channel, the UHF output of the VHS then play the video and record manually.

Then with myth archive make the DVD.

Unless anybody has a better way or idea?

---

### Post by ian dobson on 2011-11-05
Hi,

Installing mythtv just to grab a VHS tape sounds like alot of work.

I had a PVR-150 some time ago and it included a windows tool to grab from a s-video source. Under linux I just copied from the video device (/dev/video) to a file (cp /dev/video /home/id/video.mpg)

I don't know what "UHF TV PCI card" you have, but try installing it, looking in /dev what devices are created and try copying from the video device to a file.

Regards
Ian Dobson

---

### Post by klc5555 on 2011-11-05
AlecJ:

Ian's right of course.

But if you were to happen to already have Mythtv installed at some point, your method for converting should work perfectly well. A local high school which still has a collection of VHS tapes from the '80s and '90s asks me from time to time to convert one over to DVD and/or file, and that's essentially the method I use. I have a separate Video Source set up with the one channel for VCR input. An overly long manual recording time is set for the VCR output, the VHS tape is played and recorded, and the resulting Myth recording is trimmed to suit prior to being made into a DVD .iso by setting up a cutlist and then discarding the unwanted portions with mythtranscode the same as is done for any other Mythtv recording.

---

### Post by AlecJ on 2011-11-06
The card has a BT878 chip and a Philips tuner 3139 147 13901L  FM1246/PH   SV22 9914.

I think BT878 is supported?

Will try Ians suggestion first, but it's going on my friends computer who shall we say is not into computers so Myth may be better understood. hopefully fit and forget on my part.

---

### Post by ian dobson on 2011-11-06
Hi,

Mythtv could be abit too much for just recording from a s-video source.

Have a look here [http://forums.whirlpool.net.au/archive/1137787](http://forums.whirlpool.net.au/archive/1137787), maybe a different program might be easier to use/setup.

Regards
Ian Dobson

---

### Post by AlecJ on 2011-11-06
> **ian dobson said:**
> Hi,

Mythtv could be abit too much for just recording from a s-video source.

Have a look here [http://forums.whirlpool.net.au/archive/1137787](http://forums.whirlpool.net.au/archive/1137787), maybe a different program might be easier to use/setup.

Regards
Ian Dobson


Thanks had a look at that, there not too happy with xawtv.
I was planning to use the UHF from the VCR. Not sure what the VCR has in the way of outputs. May have a scart socket but then I have the audio problem?
S-Video from memory shows in black and white only on the British Pal system, was a long time ago mind.
But the Card does have an s-video in socket and a yellow phono video in with audio in jack.
Would it be possible using mplayer, to make a video file?

---

### Post by ian dobson on 2011-11-06
Hi,

SCART has audio and video signal (In several different versions) on different pins:-


PIN USE LEVEL / IMPEDANCE 
1 Audio Output (R) 0.5V / 1K-ohm 
2 Audio Input (R) 0.5V / 10K-ohm 
3 Audio Output (L) 0.5V / 1K-ohm 
4 Audio Ground -------------------- 
5 Blue Ground -------------------- 
6 Audio Input (L) 0.5V / 10K-ohm 
7 Blue 0.7Vp-p / 75ohm 
8 Status (CVBS) L:0-2V H:10 - 12V / 10K-ohm 
9 Green Ground -------------------- 
10 Data D2B (Inverted) -------------------- 
11 Green 0.7Vp-p / 75 ohm 
12 Data D2B -------------------- 
13 Red Ground -------------------- 
14 D2B Ground -------------------- 
15 Red 0.7Vp-p / 75 ohm 
16 RGB Status/Fast Blanking L:0-0.4V H:1-3V / 75 ohm 
17 CVBS Video Ground -------------------- 
18 RGB Status Ground -------------------- 
19 Composite Video Output 1V / 75 ohm 
20 Composite Video Input 1V / 75 ohm 
21 Case Shield --------------------- 

For recording with mplayer have a look here:- [http://ubuntuforums.org/showthread.php?t=759287](http://ubuntuforums.org/showthread.php?t=759287)

Regards
Ian Dobson

---

### Post by AlecJ on 2011-11-06
Thanks Ian

I'm going over to his house to "play" next week

Will let you know how it worked out.

---

### Post by thatguruguy on 2011-11-06
I've been trying to figure out how to convert a movie on vhs to another  format myself.  I eventually decided to use mencoder.  Here's the  command line I used:```

mencoder -tv  driver=v4l2:device=/dev/video0:fps=30000/1001:audiorate=32000:alsa:adevice=hw.1:input=1:amode=1:normid=4:width=576:height=432  -ovc x264 -x264encopts  threads=2:bitrate=500:bframes=2:subq=1:frameref=4:8x8dct -oac mp3lame  -lameopts cbr:br=64 -endpos 01:02:20.000 -o converted.avi tv:// >  /dev/null
```

A few things to note:

[LIST]
[*]In my particular case, the tv card I have accepts composite input; that's why "input=1" in the above code.
[*]My tv card shows up as /dev/video0 in my computer; it's possible that yours is different.
[*]The audio part of my tv card is detected as an alsa device at hw:1,0. The proper way to get mencoder to recognize it is "alsa:adevice=hw.1".  Again, YMMV.
[*]I set the recording a few seconds longer than the actual tape I was using, in order to account for any lag in the tape starting to run and mencoder actually recording/converting the signal.  ("-endpos 01:02:20.000" in the above code).
[/LIST]
I hope that helps.

---

### Post by AlecJ on 2011-11-09
> **thatguruguy said:**
> I've been trying to figure out how to convert a movie on vhs to another  format myself.  I eventually decided to use mencoder.  Here's the  command line I used:```

mencoder -tv  driver=v4l2:device=/dev/video0:fps=30000/1001:audiorate=32000:alsa:adevice=hw.1:input=1:amode=1:normid=4:width=576:height=432  -ovc x264 -x264encopts  threads=2:bitrate=500:bframes=2:subq=1:frameref=4:8x8dct -oac mp3lame  -lameopts cbr:br=64 -endpos 01:02:20.000 -o converted.avi tv:// >  /dev/null
```A few things to note:

[LIST]
[*]In my particular case, the tv card I have accepts composite input; that's why "input=1" in the above code.
[*]My tv card shows up as /dev/video0 in my computer; it's possible that yours is different.
[*]The audio part of my tv card is detected as an alsa device at hw:1,0. The proper way to get mencoder to recognize it is "alsa:adevice=hw.1".  Again, YMMV.
[*]I set the recording a few seconds longer than the actual tape I was using, in order to account for any lag in the tape starting to run and mencoder actually recording/converting the signal.  ("-endpos 01:02:20.000" in the above code).
[/LIST]
I hope that helps.

Thanks
I have problems with my card's audio part, it's not in alsa:-

```
desktop:~$ lspci -v | grep -A7 -i "audio"
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 8217
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fce78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

--
01:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
    Subsystem: Askey Computer Corp. Device 3002
    Flags: bus master, medium devsel, latency 32, IRQ 10
    Memory at dfffe000 (32-bit, prefetchable) [size=4K]

02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Biostar Microtech Int'l Corp Device 1408
    Flags: bus master, fast devsel, latency 0, IRQ 20

desktop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfce78000 irq 21


```
And dmesg gives
```
[   11.891744] bttv: driver version 0.9.18 loaded
[   11.891748] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.892083] bttv: Bt8xx card found (0).
[   11.892108] bttv 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[   11.892120] bttv0: Bt878 (rev 2) at 0000:01:08.0, irq: 19, latency: 32, mmio: 0xdffff000
[   11.892145] bttv0: detected: (Askey Magic/others) TView99 CPH05x [card=24], PCI subsystem ID is 144f:3002
[   11.892148] bttv0: using: Askey CPH05X/06X (bt878) [many vendors] [card=24,autodetected]
[   11.892180] bttv0: gpio: en=00000000, out=00000000 in=00feffff [init]
[   11.892256] bttv0: radio detected by subsystem id (CPH05x)
[   11.892258] bttv0: tuner type unset
[   11.892340] bttv0: registered device video0
[   11.892366] bttv0: registered device vbi0
[   11.892388] bttv0: registered device radio0
[   11.892408] bttv0: PLL: 28636363 => 35468950 .. ok

```

I get the video with your mencorder line but not sound, after I changed to hw.0 as hw.1 caused an error.

I like the mencorder idea, what would the command be to get the sound from the "line in" on the sound card, and make a Pal DVD quality .mpeg file?
I have been given 25 Video8 camcorder tapes that I have to put on DVD.

Thanks

---

### Post by thatguruguy on 2011-11-09
> **AlecJ said:**
> Thanks
I have problems with my card's audio part, it's not in alsa:-
*[snip]*
I get the video with your mencorder line but not sound, after I changed to hw.0 as hw.1 caused an error.
I like the mencorder idea, what would the command be to get the sound  from the "line in" on the sound card, and make a Pal DVD quality .mpeg  file?
I have been given 25 Video8 camcorder tapes that I have to put on DVD.
Thanks

That's why I mentioned that your mileage may vary on the sound issue.  It's highly dependant on what your system is using.  Here's what I did:

[LIST=1]
[*]First, I wanted to make sure that my tuner was able to stream the  signal from the vcr.  In order to do that, I installed the program  "tvtime." tvtime is available in the repositories, and is set up  specifically to handle analog signals. The developer maintains a website  at [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/) which will answer any questions you may have on getting it set up.
[*]Next, I turned on the vcr so I'd have a stream, and then played  with the settings on tvtime until I had both a picture and audio.  It's a  LOT easier to do that with the on-screen menus on tvtime than it is to  try to figure out settings on the command line.
[*]By testing on tvtime, it was clear that what worked for my  particular setup was composite video and alsa audio, set to hw:1,0.   Again, that may be different on your system, but you can easily change  settings in tvtime until you find ones that work.
[*]Once I had my settings, I had to refer to the manual for mencoder  (type "man mencoder" [without the quotes] in a terminal) to find out how  to apply the settings to mencoder.
[/LIST]
I looked through several guides on the internet until I found information that was useful.  Unfortunately, I didn't bookmark them all, or I'd pass on the links.  However, you may want to try the following pages for more information:

[LIST]
[*][http://www.mplayerhq.hu/DOCS/HTML/en/tv-input.html](http://www.mplayerhq.hu/DOCS/HTML/en/tv-input.html) [NOTE: some of the information here is out-of-date (eg, they use v4l instead of v4l2), but it's still worth reading to get a basic understanding of the usage of the mencoder options)
[*][http://linuxtv.org/wiki/index.php/MEncoder](http://linuxtv.org/wiki/index.php/MEncoder) [Another good overview, plus several scripts for different setups].
[/LIST]

---

### Post by AlecJ on 2011-11-10
Finally after 13 hrs of searching and being frustrated I have put together the MEncorder line that works! for me anyway.

```
mencoder -tv driver=v4l2:device=/dev/video0:audiorate=32000:alsa:adevice=hw.0,2:forceaudio:input=1:fps=25:normid=4 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1830:vrc_maxrate=9800:vbitrate=5000:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=4/3 -ofps 25 -o capture.mpg
```

This takes the sound from the Line In on the sound card and the video from the TV card analog Yellow phono and makes a mpg file ready for DVD.

I have to force the audio to get round the pulseaudio lack of /dev/dsp? and this only works in the natty latest MEncorder from Medibuntu.

Thanks for everybody's help

---

