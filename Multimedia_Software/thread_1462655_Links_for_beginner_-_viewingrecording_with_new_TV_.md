---
title: "Links for beginner - viewing/recording with new TV Tuner?"
date: 2010-04-26
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-04-26
No progress viewing input yet in Linux. I installed MythTV, VLC, and no luck yet with vids or sound.

I had video input with Windows Movie Maker, and Media Player Classic (3rd party), but no sound in either.

Help?

---

### Post by WinterRain on 2010-04-26
Open a terminal and do:
```
lspci
```
and post the output here.

---

### Post by Moozillaaa on 2010-04-26
04:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
04:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
chucknb@chucknb-desktop:~$ 

Dual tuner card, shows up by chip/style/model in a few different places so far, just not the right one yet...

---

### Post by WinterRain on 2010-04-26
I wrote a tutorial on my blog for that chipset. It should work even if it is not a Hauppauge PVR 150. [http://thelinuxcurmudgeon.blogspot.com/2010/04/using-hauppauge-pvr-150250350500-tv.html](http://thelinuxcurmudgeon.blogspot.com/2010/04/using-hauppauge-pvr-150250350500-tv.html)

---

### Post by Moozillaaa on 2010-04-26
> **WinterRain said:**
> I wrote a tutorial on my blog for that chipset. It should work even if it is not a Hauppauge PVR 150. [http://thelinuxcurmudgeon.blogspot.com/2010/04/using-hauppauge-pvr-150250350500-tv.html](http://thelinuxcurmudgeon.blogspot.com/2010/04/using-hauppauge-pvr-150250350500-tv.html)

I'm there, thanks!

---

### Post by Moozillaaa on 2010-04-26
> **Moozillaaa said:**
> I'm there, thanks!

I WAS there... :confused:

I think they changed the lock on the door...
> 
**We're sorry, but we were unable to complete your request.**

   When reporting this error to Blogger Support or on the Blogger Help Group, please:
 
[LIST]
[*]**Describe what you were doing** when you got this error.
[*]Provide the following **error code** and **additional information**.
[/LIST]
 bX-2co2mz
 **Additional information**

 **host:** thelinuxcurmudgeon.blogspot.com
 **uri:** /2010/04/using-hauppauge-pvr-150250350500-tv.html

 This information will help us to track down your specific problem and fix it! We apologize for the inconvenience.
 **Find help**

 See if anyone else is having the same problem: [Search the Blogger Help Group for bX-2co2mz]("http://help.blogger.com/bin/search.py?hl=en&forum=1&query=bX-2co2mz")
If you don't get any results for that search, you can start a new topic. Please make sure to mention **bX-2co2mz** in your message.





---

### Post by WinterRain on 2010-04-26
I just tried the link, and it works for me. The link in my sig contains the article also, it's the second blog down on the main page.

---

### Post by Moozillaaa on 2010-04-26
Thanks - I got back on here...

Any special software repo's to enable?

---

### Post by Moozillaaa on 2010-04-26
Looks like stream stats is piling up, but no display or volume?

---

### Post by WinterRain on 2010-04-26
You don't really need to do
```
ivtv-tune -h
```
for *anything*.
I don't know if you changed any settings or not, but all you needed to do was:
```
sudo apt-get install ivtv-utils vlc
```

then open vlc as I wrote, and change channels.

---

### Post by Moozillaaa on 2010-04-26
> **WinterRain said:**
> You don't really need to do
```
ivtv-tune -h
```for *anything*.
I don't know if you changed any settings or not, but all you needed to do was:
```
sudo apt-get install ivtv-utils vlc
```then open vlc as I wrote, and change channels.

Change channels one at a time, till I find one?

I have my VCR/DVD player incoming on a coax input...


So I started over - and cannot open pvr
> Unable to open 'pvr://'

---

### Post by WinterRain on 2010-04-27
Is there a cable box involved too?

---

### Post by Moozillaaa on 2010-04-27
No - signal is coming straight from VCR/DVD player on coax. 3 year old player, practically new tho'. Signal confirmed on line...

Not sure if it's RG-6 or RG-59 line; does it make a difference?


edit:
This PC is new build, new Hardy x64, and I just installed x64 Flash player. That's not what the problem was?

---

### Post by WinterRain on 2010-04-27
> **Moozillaaa said:**
> No - signal is coming straight from VCR/DVD player on coax. 3 year old player, practically new tho'. Signal confirmed on line...

Not sure if it's RG-6 or RG-59 line; does it make a difference?


edit:
This PC is new build, new Hardy x64, and I just installed x64 Flash player. That's not what the problem was?

Can you change channels on the vcr? If so, start vlc, then do:
```
ivtv-tune -c3
```
and try changing channels on the vcr.

If nothing, diconnect the vcr and go directly to the tuner card and see what happens.

---

### Post by Moozillaaa on 2010-04-27
The VCR/DVD player doesn't have a channel selector like the old 3-4 select switch. I think it's defaulted at 3.

So I started VLC, entered the line in CLI, and returned 

/dev/video0: 61.250 MHz

Nothing (someone in VLC forums posted** vlc pvr:///dev/video0 **). Sooo... what?
> 
If nothing, diconnect the vcr and go directly to the tuner card and see what happens. 	
You mean VCR/DVD player line out directly to tuner card? I have that already.
> No - signal is coming straight from VCR/DVD player on coax.

Thanks for ideas tho'...

---

### Post by Moozillaaa on 2010-04-27
Alright here - possibly a clue...

I opened Totem, and 'Opened'  /dev/video1 , and got prompted to load Gstreamer tools. I loaded 3 tools, and the input started, video static, no audio.

Mean anything?




from CLI return:
[00000444] main video output warning: late picture skipped (113950)
[00000444] main video output warning: late picture skipped (47259)
[00000372] main audio output warning: output date isn't PTS date, requesting resampling (45050)
[00000372] main audio output warning: audio drift is too big (143782), dropping buffer
[00000372] main audio output warning: output date isn't PTS date, requesting resampling (67475)
[00000372] main audio output warning: audio drift is too big (182507), dropping buffer
[00000372] main audio output warning: audio drift is too big (158507), dropping buffer
[00000372] main audio output warning: audio drift is too big (134507), dropping buffer
[00000372] main audio output warning: output date isn't PTS date, requesting resampling (44317)
[00000372] main audio output warning: audio drift is too big (150553), dropping buffer
[00000372] main audio output warning: audio drift is too big (126553), dropping buffer
[00000444] main video output warning: late picture skipped (23344)
[00000444] main video output warning: late picture skipped (95871)
[00000444] main video output warning: late picture skipped (64304)
[00000444] main video output warning: late picture skipped (30943)
[00000447] main private debug: decoded 102/105 pictures

---

### Post by Moozillaaa on 2010-04-28
This is the end of the program that was coming in.

Any clues?


[00000372] main audio output warning: output date isn't PTS date, requesting resampling (69566)
[00000372] main audio output warning: output date isn't PTS date, requesting resampling (90226)
[00000372] main audio output warning: audio drift is too big (185530), dropping buffer
[00000372] main audio output warning: audio drift is too big (161530), dropping buffer
[00000372] main audio output warning: audio drift is too big (137530), dropping buffer
[00000489] main video output warning: late picture skipped (60354)
[00000489] main video output warning: late picture skipped (27405)
[00000489] main video output warning: late picture skipped (10682)
[00000372] main audio output warning: resampling stopped after 16020169 usec (drift: -80093)
[00000372] main audio output warning: buffer is 80260 late, triggering upsampling
[00000489] main video output warning: late picture skipped (48818)
[00000489] main video output warning: late picture skipped (14839)
[00000496] main input debug: control type=0
[00000496] main input debug: control: stopping input
[00000496] main input debug: closing input
[00000502] main decoder debug: removing module "mpeg_audio"
[00000502] main decoder debug: thread 1150372176 joined (input/decoder.c:191)
[00000502] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO
[00000505] main private debug: removing module "mpgatofixed32"
[00000506] main private debug: removing module "bandlimited_resampler"
[00000372] pulse audio output debug: Pulse Close
[00000372] main audio output debug: removing module "pulse"
[00000504] main private debug: removing module "float32tos16"
[00000372] main audio output debug: removing module "trivial_mixer"
[00000501] main decoder debug: removing module "libmpeg2"
[00000501] main decoder debug: thread 1167157584 joined (input/decoder.c:191)
[00000501] main decoder debug: killing decoder fourcc `mpgv', 68 PES in FIFO
[00000496] main input debug: Program doesn't contain anymore ES
[00000500] main demuxer debug: removing module "ps"
[00000498] pvr access error: Called Close()
[00000498] main access debug: removing module "pvr"
[00000496] main input debug: thread 1133586768 joined (input/input.c:412)
[00000289] main playlist debug: garbage collector destroys 1 vout
[00000489] main video output debug: removing module "i420_rgb_mmx"
[00000489] main video output debug: removing module "x11"
[00000489] main video output debug: thread 1141979472 joined (video_output/video_output.c:461)
[00000289] main playlist debug: adding playlist item `/home/chucknb/Desktop/v4l-cx2341x-init.mpg' ( /home/chucknb/Desktop/v4l-cx2341x-init.mpg )
[00000289] main playlist debug: creating new input thread
[00000507] main input debug: waiting for thread completion
[00000507] main input debug: `/home/chucknb/Desktop/v4l-cx2341x-init.mpg' gives access `' demux `' path `/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000507] main input debug: creating demux: access='' demux='' path='/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000508] main demuxer debug: looking for access_demux module: 2 candidates
[00000507] main input debug: creating access '' path='/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000510] main access debug: looking for access2 module: 5 candidates
[00000510] vcd access debug: trying .cue file: /home/chucknb/Desktop/v4l-cx2341x-init.cue
[00000510] vcd access debug: could not find .cue file
[00000510] access_file access debug: opening file `/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000510] main access debug: using access2 module "access_file"
[00000511] main private debug: pre-buffering...
[00000511] main private debug: received first data for our buffer
[00000507] main input debug: creating demux: access='' demux='' path='/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000512] main demuxer debug: looking for demux2 module: 45 candidates
[00000507] main input debug: thread 1141979472 (input) created at priority 0 (input/input.c:265)
[00000512] ffmpeg demuxer debug: couldn't guess format
[00000512] vobsub demuxer debug: this doesn't seem to be a vobsub file
[00000512] ps demuxer warning: this does not look like an MPEG PS stream, continuing anyway
[00000512] main demuxer debug: using demux2 module "ps"
[00000507] main input debug: looking for a subtitle file in /home/chucknb/Desktop/
[00000507] main input debug: `/home/chucknb/Desktop/v4l-cx2341x-init.mpg' successfully opened
[00000512] ps demuxer warning: garbage at input, trying to resync...
[00000507] main input debug: EOF reached
[00000507] main input debug: closing input
[00000512] main demuxer debug: removing module "ps"
[00000510] main access debug: removing module "access_file"
[00000507] main input debug: thread 1141979472 joined (input/input.c:412)
[00000289] main playlist warning: unable to find parent!
[00000289] main playlist: nothing to play
[00000289] main playlist debug: adding playlist item `/home/chucknb/Desktop/v4l-cx2341x-init.mpg' ( /home/chucknb/Desktop/v4l-cx2341x-init.mpg )
[00000289] main playlist debug: creating new input thread
[00000529] main input debug: waiting for thread completion
[00000529] main input debug: `/home/chucknb/Desktop/v4l-cx2341x-init.mpg' gives access `' demux `' path `/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000529] main input debug: creating demux: access='' demux='' path='/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000530] main demuxer debug: looking for access_demux module: 2 candidates
[00000529] main input debug: creating access '' path='/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000531] main access debug: looking for access2 module: 5 candidates
[00000531] vcd access debug: trying .cue file: /home/chucknb/Desktop/v4l-cx2341x-init.cue
[00000531] vcd access debug: could not find .cue file
[00000531] access_file access debug: opening file `/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000531] main access debug: using access2 module "access_file"
[00000532] main private debug: pre-buffering...
[00000532] main private debug: received first data for our buffer
[00000529] main input debug: creating demux: access='' demux='' path='/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000533] main demuxer debug: looking for demux2 module: 45 candidates
[00000533] ffmpeg demuxer debug: couldn't guess format
[00000533] vobsub demuxer debug: this doesn't seem to be a vobsub file
[00000533] ps demuxer warning: this does not look like an MPEG PS stream, continuing anyway
[00000533] main demuxer debug: using demux2 module "ps"
[00000529] main input debug: looking for a subtitle file in /home/chucknb/Desktop/
[00000529] main input debug: `/home/chucknb/Desktop/v4l-cx2341x-init.mpg' successfully opened
[00000533] ps demuxer warning: garbage at input, trying to resync...
[00000529] main input debug: EOF reached
[00000529] main input debug: thread 1133586768 (input) created at priority 0 (input/input.c:265)
[00000529] main input debug: closing input
[00000533] main demuxer debug: removing module "ps"
[00000531] main access debug: removing module "access_file"
[00000529] main input debug: thread 1133586768 joined (input/input.c:412)
[00000289] main playlist: nothing to play
[00000001] main private debug: removing all interfaces
[00000295] main interface debug: thread 1125194064 joined (interface/interface.c:258)
[00000295] main interface debug: removing module "wxwidgets"
[00000293] main interface debug: thread 1116801360 joined (interface/interface.c:258)
[00000293] main interface debug: removing module "screensaver"
[00000291] main interface debug: thread 1108408656 joined (interface/interface.c:258)
[00000291] main interface debug: removing module "hotkeys"
[00000001] main private debug: removing playlist handler
[00000290] main private debug: thread 1100015952 joined (playlist/playlist.c:247)
[00000289] main playlist debug: thread 1091602768 joined (playlist/playlist.c:248)
[00000289] main playlist debug: deleting playlist item `pvr:///dev/video0'
[00000289] main playlist debug: deleting playlist item `v4l://'
[00000289] main playlist debug: deleting playlist item `v4l://'
[00000289] main playlist debug: deleting playlist item `v4l://'
[00000289] main playlist debug: deleting playlist item `pvr://'
[00000289] main playlist debug: deleting playlist item `Streaming/Transcoding Wizard'
[00000289] main playlist debug: deleting playlist item `pvr://'
[00000289] main playlist debug: deleting playlist item `v4l://'
[00000289] main playlist debug: deleting playlist item `pvr://'
[00000289] main playlist debug: deleting playlist item `pvr://'
[00000289] main playlist debug: deleting playlist item `/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000289] main playlist: stopping playback
[00000289] main playlist debug: deleting playlist item `/home/chucknb/Desktop/v4l-cx2341x-init.mpg'
[00000289] main playlist warning: refcount is 1, delaying before deletion (id=289,type=-5)
[00000289] main playlist error: refcount is 1, delaying again (id=289,type=-5)
[00000289] main playlist error: waited too long, cancelling destruction (id=289,type=-5)
[00000001] main private debug: removing all video outputs
[00000001] main private debug: removing all audio outputs
[00000001] main private debug: removing module "memcpymmxext"
[00000001] main private debug: opening config file /home/chucknb/.vlc/vlcrc
[00000001] main private debug: saving plugins cache file /home/chucknb/.vlc/cache/plugins-04081e.dat
chucknb@chucknb-desktop:~$

---

### Post by WinterRain on 2010-04-28
I'm not sure what to tell you. I have the same chipset in my card and never had a problem in 3 years using *any* distro. Good luck.

---

### Post by Moozillaaa on 2010-04-29
> **WinterRain said:**
> I'm not sure what to tell you. I have the same chipset in my card and never had a problem in 3 years using *any* distro. Good luck.

I KNEW there was no problem; it was a configuration setting. I still don't know which one it was either.

This guy got me in with these 4 commands in post 2. 
[http://ubuntuforums.org/showthread.php?t=1464858](http://ubuntuforums.org/showthread.php?t=1464858)
I WOULD like to know HOW it's working; not just that it IS working... If something breaks, I could get jammed again, but if I figure how it's working, I can fix, and improve...

You see anything in his command entries?

---

### Post by saedelaere on 2010-05-12
In case you want to try a nice frontend for ivtv devices have a look at [this thread ]("http://ubuntuforums.org/showthread.php?t=763698") or on [the homepage of TV-Viewer]("http://tv-viewer.sourceforge.net/")


Regards

---

### Post by Moozillaaa on 2010-05-13
Thanks - I'm there.

I got audio + vids, but now, the config and fine tuning is yet to come UGH!

---

