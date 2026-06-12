---
title: "PVR150, MythTV and MPEG problems."
date: 2010-07-29
forum: Mythbuntu
---

### Post by Furry_Fighter_20x66 on 2010-07-29
I have a strange problem that crept in suddenly last week. The audio suddenly vanished when watching liveTV or new recordings.

After a lot of investigating I think that somewhere along the way last week there was some updates I finally got around to installing and things have quit working properly as a result. I have pulled the card from the server and put it in my desktop to test it. Just like the server it will make perfectly fine .mpg files up until the moment mythbackend seizes the reigns and begins to capture video for its own use. Then I have recordings that are badly damaged. Playing those files in vlc gets me error messages like this: 
> 
access_file debug: opening file `/home/user/Desktop/test.mpg'
main debug: using access module "access_file"
main debug: TIMER module_need() : 1.503 ms - Total 1.503 ms / 1 intvls (Avg 1.503 ms)
main debug: Using AStream*Stream
main debug: pre buffering
main debug: received first data after 0 ms
main debug: pre-buffering done 1024 bytes in 0s - 31250 kbytes/s
main debug: looking for stream_filter module: 5 candidates
main debug: TIMER module_need() : 0.153 ms - Total 0.153 ms / 1 intvls (Avg 0.153 ms)
main debug: looking for stream_filter module: 1 candidate
main debug: using stream_filter module "stream_filter_record"
main debug: TIMER module_need() : 0.151 ms - Total 0.151 ms / 1 intvls (Avg 0.151 ms)
main debug: creating demux: access='' demux='' path='/home/user/Desktop/test.mpg'
main debug: looking for demux module: 51 candidates
main debug: using demux module "ps"
main debug: TIMER module_need() : 0.469 ms - Total 0.469 ms / 1 intvls (Avg 0.469 ms)
main debug: looking for a subtitle file in /home/user/Desktop/
main debug: `/home/user/Desktop/test.mpg' successfully opened
ps warning: garbage at input, trying to resync...
ps warning: found sync code
ps debug: we found a length of: 14592000
ps debug: we found a length of: 14814800
main debug: selecting program id=0
main debug: looking for decoder module: 31 candidates
main debug: using decoder module "libmpeg2"
main debug: TIMER module_need() : 0.416 ms - Total 0.416 ms / 1 intvls (Avg 0.416 ms)
main debug: thread (decoder) created at priority 0 (input/decoder.c:315)
main debug: thread started
ps debug: es id=0xbd69 format unknown
main debug: Buffering 0%
main debug: looking for decoder module: 31 candidates
main debug: using decoder module "mpeg_audio"
main debug: TIMER module_need() : 0.567 ms - Total 0.567 ms / 1 intvls (Avg 0.567 ms)
main debug: thread (decoder) created at priority 5 (input/decoder.c:315)
main debug: thread started
libmpeg2 debug: 480x480 (display 480,480), aspect 576000, sar 4:3, 29.971 fps
main debug: Buffering -132%
mpeg_audio debug: MPGA channels:2 samplerate:48000 bitrate:384
main debug: Buffering -132%
main debug: Buffering -131%
main debug: Buffering -130%
main debug: Buffering -130%
main debug: Buffering -129%
main debug: Buffering -128%
main debug: Buffering -127%
main debug: Buffering -127%
main debug: Buffering -126%
main debug: reusing aout
main debug: Buffering -125%
main debug: Buffering -125%
main debug: Buffering -124%
main debug: Buffering -123%
main debug: Buffering -123%
main debug: Buffering -122%
main debug: Buffering -121%
main debug: Buffering 0%
main debug: Buffering -120%
main debug: looking for audio output module: 4 candidates
main debug: Buffering -120%
main debug: Buffering -119%
main debug: Buffering -118%
main debug: Buffering -118%
main debug: Buffering -117%
main debug: Buffering -116%
main debug: Buffering -116%
main debug: Buffering -115%
main debug: Buffering -114%
main debug: Buffering -114%
pulse info: No. of Audio Channels: 2
main debug: Buffering -113%
main debug: Buffering 0%
main debug: Buffering -112%
main debug: Buffering -111%
main debug: Buffering -111%
...
main debug: Buffering -28%
main debug: Buffering -27%
main debug: no usable vout present, spawning one
main debug: Buffering -26%
main debug: Buffering -25%
main debug: Buffering -25%
main debug: looking for text renderer module: 2 candidates
main debug: Buffering -24%
main debug: Buffering -23%
main debug: Buffering -23%
main debug: Buffering 0%
main debug: Buffering -22%
main debug: Buffering -21%
...
main debug: Buffering -16%
main debug: Buffering -16%
main debug: thread (fontlist builder) created at priority 0 (freetype.c:480)
main debug: Buffering -15%
freetype debug: using fontsize: 2
main debug: using text renderer module "freetype"
main debug: Buffering -14%
main debug: TIMER module_need() : 0.423 ms - Total 0.423 ms / 1 intvls (Avg 0.423 ms)
main debug: thread started
main debug: Buffering -14%
main debug: Buffering -13%
main debug: looking for video filter2 module: 20 candidates
main debug: Buffering -12%
main debug: Buffering -10%
main debug: Buffering -10%
main debug: Buffering -9%
main debug: Buffering -1%
main debug: Buffering 0%
main debug: Buffering 1%
main debug: Buffering 1%
main debug: Buffering 0%
main debug: Buffering 2%
...
main debug: Buffering 23%
swscale debug: 32x32 chroma: YUVA -> 16x16 chroma: YUVA with scaling using Bicubic (good quality)
main debug: using video filter2 module "swscale"
main debug: TIMER module_need() : 0.363 ms - Total 0.363 ms / 1 intvls (Avg 0.363 ms)
main debug: Buffering 24%
main debug: Buffering 27%
main debug: looking for video filter2 module: 20 candidates
main debug: Buffering 33%
yuvp debug: YUVP to YUVA converter
main debug: using video filter2 module "yuvp"
main debug: TIMER module_need() : 0.062 ms - Total 0.062 ms / 1 intvls (Avg 0.062 ms)
main debug: Buffering 0%
main debug: Buffering 34%
...
main debug: Buffering 97%
main debug: Stream buffering done (300 ms in 9 ms)
main debug: window size: 640x480
main debug: looking for video output module: 7 candidates
pulse debug: Pulse mainloop started
xvideo debug: adaptor 0, port 313, format 0x32315659 (YV12) planar
main debug: looking for xwindow module: 3 candidates
qt4 debug: requesting video...
pulse debug: Pulse stream connected
pulse debug: Pulse initialized successfully
pulse debug: Buffer metrics: maxlength=153600, tlength=46080, prebuf=38400, minreq=7680
pulse debug: Using sample spec 'float32le 2ch 48000Hz', channel map 'front-left,front-right'.
pulse debug: Connected to device alsa_output.pci-0000_03_06.0.analog-digital-stereo-out (0, not suspended).
main debug: using audio output module "pulse"
main debug: TIMER module_need() : 12.403 ms - Total 12.403 ms / 1 intvls (Avg 12.403 ms)
main debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
main debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
main debug: no need for any filter
main debug: looking for audio mixer module: 3 candidates
main debug: using audio mixer module "float32_mixer"
main debug: TIMER module_need() : 0.035 ms - Total 0.035 ms / 1 intvls (Avg 0.035 ms)
main debug: input 'mpga' 48000 Hz Stereo frame=1152 samples/1161 bytes
main debug: looking for audio filter module: 1 candidate
scaletempo warning: bad input or output format
main warning: no audio filter module matching "scaletempo" could be loaded
main debug: TIMER module_need() : 0.031 ms - Total 0.031 ms / 1 intvls (Avg 0.031 ms)
main debug: looking for audio filter module: 1 candidate
scaletempo debug: format: 48000 rate, 2 nch, 4 bps, fl32
scaletempo debug: params: 30 stride, 0.200 overlap, 14 search
scaletempo debug: 1.000 scale, 1440.000 stride_in, 1440 stride_out, 1152 standing, 288 overlap, 672 search, 2400 queue, fl32 mode
main debug: using audio filter module "scaletempo"
main debug: TIMER module_need() : 0.097 ms - Total 0.097 ms / 1 intvls (Avg 0.097 ms)
main debug: filter(s) 'mpga'->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "mpgatofixed32"
main debug: TIMER module_need() : 0.043 ms - Total 0.043 ms / 1 intvls (Avg 0.043 ms)
main debug: found a filter for the whole conversion
main debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
main debug: looking for audio filter module: 24 candidates
main debug: using audio filter module "bandlimited_resampler"
main debug: TIMER module_need() : 0.074 ms - Total 0.074 ms / 1 intvls (Avg 0.074 ms)
main debug: found a filter for the whole conversion
main debug: End of audio preroll
freetype debug: Building font database...
freetype debug: Finished building font database.
freetype debug: Took 250 microseconds
main debug: thread ended
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Video was requested -1, -1
qt4 debug: Video is resizing to: 640 480
qt4 debug: Updating the geometry
main debug: using xwindow module "qt4"
main debug: TIMER module_need() : 113.515 ms - Total 113.515 ms / 1 intvls (Avg 113.515 ms)
xvideo debug: XShm video extension v1.1 (without pixmaps, opcode: 142)
xvideo debug: Window manager supports NetWM
xvideo debug: Window manager supports _NET_WM_STATE_FULLSCREEN
xvideo debug: Window manager supports _NET_WM_STATE_ABOVE
xvideo debug: Window manager supports _NET_WM_STATE_BELOW
main debug: using video output module "xvideo"
main debug: TIMER module_need() : 120.178 ms - Total 120.178 ms / 1 intvls (Avg 120.178 ms)
main debug: Deinterlacing available
main debug: got 16 direct buffer(s)
main debug: pic render sz 480x480, of (0,0), vsz 480x480, 4cc I420, ar 4:3, sar 4:3, msk r0x0 g0x0 b0x0
main debug: pic in sz 480x480, of (0,0), vsz 480x480, 4cc I420, ar 4:3, sar 4:3, msk r0x0 g0x0 b0x0
main debug: pic out sz 480x480, of (0,0), vsz 480x480, 4cc I420, ar 4:3, sar 4:3, msk r0x0 g0x0 b0x0
main debug: direct render, mapping render pictures 0-14 to system pictures 1-15
main warning: dts != current_pts (-300332)
main warning: decoder synchro warning: pts != current_date (-33367)
main debug: End of video preroll
main debug: Received first picture
freetype debug: using fontsize: 30
main debug: looking for video blending module: 1 candidate
blend debug: chroma: YUVA -> I420
main debug: using video blending module "blend"
main debug: TIMER module_need() : 0.168 ms - Total 0.168 ms / 1 intvls (Avg 0.168 ms)
main debug: Decoder buffering done in 143 ms
main warning: PTS is out of range (201159), dropping buffer
main warning: PTS is out of range (177207), dropping buffer
main warning: PTS is out of range (153242), dropping buffer
main warning: PTS is out of range (129271), dropping buffer
main warning: PTS is out of range (105300), dropping buffer
main warning: PTS is out of range (81384), dropping buffer
main warning: PTS is out of range (57422), dropping buffer
main warning: PTS is out of range (33453), dropping buffer
main warning: PTS is out of range (9486), dropping buffer
main warning: PTS is out of range (-14484), dropping buffer
main warning: PTS is out of range (-38451), dropping buffer
pulse debug: Pulse stream started
qt4 debug: Qt: Entering Fullscreen
main error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 304 ms
main error: ES_OUT_RESET_PCR called
main warning: can't get output picture
main debug: Buffering 0%
main debug: Buffering 0%
...
main debug: Buffering 8%
main warning: decoder synchro warning: pts != current_date (-367034)
main debug: Buffering -139%
main debug: Buffering 8%
main debug: Buffering 9%
main debug: Buffering 11%
main debug: Buffering 15%
main debug: End of audio preroll
main debug: Buffering 15%
...
main debug: Buffering 40%
main warning: backward_pts != dts (400400)
main debug: Buffering 41%
main warning: backward_pts != current_pts (400399)
main debug: Buffering 41%
...
main debug: Buffering 97%
main debug: Buffering 98%
main debug: Buffering -139%
main debug: Buffering 99%
main debug: Buffering 99%
main debug: Stream buffering done (312 ms in 1 ms)
libmpeg2 error: DpbUnlinkPicture called on an invalid picture
main warning: decoder synchro warning: pts != current_date (-400401)
main debug: Decoder buffering done in 7 ms
main warning: the mixer got a packet in the past (321483)
main warning: the mixer got a packet in the past (297483)
main error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 425 ms
main error: ES_OUT_RESET_PCR called
main warning: the mixer got a packet in the past (273483)
main warning: the mixer got a packet in the past (249483)
main warning: the mixer got a packet in the past (225483)
main warning: the mixer got a packet in the past (201483)
main warning: the mixer got a packet in the past (177483)
main warning: the mixer got a packet in the past (153483)
main warning: the mixer got a packet in the past (129483)
main warning: the mixer got a packet in the past (105483)
main warning: the mixer got a packet in the past (81483)
main warning: the mixer got a packet in the past (57483)
main warning: the mixer got a packet in the past (33483)
main warning: output date isn't PTS date, requesting resampling (110347)
main warning: can't get output picture
main debug: Buffering 0%
main debug: Buffering 0%
....
main debug: Buffering 94%
main debug: Buffering 94%
main debug: Buffering -182%
main debug: Buffering 95%
main debug: Buffering 95%
main debug: Buffering 96%
main debug: Buffering 99%
main debug: Stream buffering done (426 ms in 2 ms)
main debug: Decoder buffering done in 8 ms
main error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 779 ms
main error: ES_OUT_RESET_PCR called
main warning: the mixer got a packet in the past (418493)
main warning: the mixer got a packet in the past (394493)
main warning: the mixer got a packet in the past (370493)
main warning: the mixer got a packet in the past (346493)
main warning: the mixer got a packet in the past (322493)
main warning: the mixer got a packet in the past (298493)
main warning: the mixer got a packet in the past (274493)
main warning: the mixer got a packet in the past (250493)
main warning: the mixer got a packet in the past (226493)
main warning: the mixer got a packet in the past (202493)
main warning: the mixer got a packet in the past (178493)
main warning: the mixer got a packet in the past (154493)
main warning: the mixer got a packet in the past (130493)
main warning: the mixer got a packet in the past (106493)
main warning: the mixer got a packet in the past (82493)
main warning: the mixer got a packet in the past (58493)
main warning: the mixer got a packet in the past (34493)
main warning: can't get output picture
main debug: Buffering 0%
...
main debug: Buffering 21%
main debug: Buffering 21%
main debug: Buffering 21%
main debug: Buffering 21%
main debug: Buffering 22%
main debug: Buffering -156%
libmpeg2 error: DpbUnlinkPicture called on an invalid picture
main warning: decoder synchro warning: pts != current_date (-100101)
main debug: Buffering 24%
main debug: Buffering 24%
...
main debug: Buffering -156%
main debug: Buffering 98%
main debug: Stream buffering done (786 ms in 4 ms)
main debug: Decoder buffering done in 6 ms
main error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 1221 ms
main error: ES_OUT_RESET_PCR called
main warning: the mixer got a packet in the past (394209)
main warning: the mixer got a packet in the past (370209)
main warning: the mixer got a packet in the past (346209)
main warning: the mixer got a packet in the past (322209)
main warning: the mixer got a packet in the past (298209)
main warning: the mixer got a packet in the past (274209)
main warning: the mixer got a packet in the past (250209)
main warning: the mixer got a packet in the past (226209)
main warning: the mixer got a packet in the past (202209)
main warning: the mixer got a packet in the past (178209)
main warning: the mixer got a packet in the past (154209)
main warning: the mixer got a packet in the past (130209)
main warning: the mixer got a packet in the past (106209)
main warning: the mixer got a packet in the past (82209)
main warning: the mixer got a packet in the past (58209)
main warning: the mixer got a packet in the past (34209)
main warning: the mixer got a packet in the past (10209)
main warning: mixer start isn't output start (3920)
main warning: can't get output picture
main warning: received buffer in the future
main debug: Buffering 0%
...
main debug: Buffering 6%
main debug: Buffering 6%
main debug: End of audio preroll
main debug: Buffering 6%
...
main debug: Buffering 10%
main debug: Buffering 10%
main warning: decoder synchro warning: pts != current_date (-400401)
main debug: Buffering 10%
main debug: Buffering 10%
...
main debug: Buffering 13%
main debug: Buffering -165%
main debug: Buffering 14%
main debug: Buffering 14%
main debug: Buffering 15%
main debug: Buffering 15%
main warning: backward_pts != dts (400400)
main debug: Buffering 15%
main warning: backward_pts != current_pts (400399)
main debug: Buffering 15%
main debug: Buffering 15%
...
main debug: Buffering 23%
main debug: Buffering 24%
libmpeg2 error: DpbUnlinkPicture called on an invalid picture
main debug: Buffering 24%
main debug: Buffering 24%
main warning: decoder synchro warning: pts != current_date (-400401)
main debug: Buffering 24%
main debug: Buffering 24%
...
main debug: Buffering 37%
libmpeg2 error: DpbUnlinkPicture called on an invalid picture
main debug: Buffering 37%
main debug: Buffering -165%
main debug: Buffering 37%
....
main debug: Buffering 99%
main debug: Buffering 99%
main debug: Stream buffering done (1221 ms in 12 ms)
main debug: End of video preroll
main debug: Received first picture
main debug: Decoder buffering done in 10 ms
main warning: the mixer got a packet in the past (338787)
main error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 2035 ms
main error: ES_OUT_RESET_PCR called
main warning: the mixer got a packet in the past (314787)
main warning: late picture skipped (934564310 > -802)
main warning: received buffer in the future
main warning: late picture skipped (934564310 > -802)
main warning: late picture skipped (934564310 > -802)
main warning: late picture skipped (934564310 > -802)
main warning: received buffer in the future
main warning: late picture skipped (934564310 > -802)
main warning: received buffer in the future
main warning: received buffer in the future
main debug: Buffering 0%
main debug: End of audio preroll
main debug: Buffering 0%
...


Fortunately the changes that MythTV does are not permanent. The second I turn off the computer for a while and then reboot the card goes back to normal. Anyone have some advice on what I need to fix in MythTV to get it working again? I went hunting through the setup options and there really isn't much in the way of configuring the ivtv setup.

---

### Post by ian dobson on 2010-07-30
Hi,

What version of mythtv are you using? Do you see anything interesting in the backend log file when recording?

When I used a PVR150 I added the following to the module configuration:-
options ivtv enc_mpg_buffers=16 ivtv_yuv_mode=2

just add that line to /etc/modprobe.d/ivtv.conf and reboot.

Regards
Ian Dobson

---

### Post by Furry_Fighter_20x66 on 2010-07-30
Hi Ian: 
I'm using mythtv 0.23.0+fixes24158-0ubuntu2

I tried the module configuration you suggested and it still didn't work. :( But it gives me some ideas I will try tomorrow.

I also remembered one of the updates recently was a kernel. So I booted up in the last kernel and tried recording both before mythtv and then using mythtv. Still behaved as before -- works great until mythtv reconfigures the card and then it stops working.

Mythbackend logs are mostly ho hum, even with the server set to log all messages. I didn't see anything in there that stuck me as abnormal anyway.

I remembered that Mythfrontend had some extra verbose settings so when I ran it with '-v playback' had some interesting things to say. I don't know if this is significant but I noticed this.
> 
2010-07-30 01:29:35.981 RingBuf(/media/MediaBay2/LiveTV/1514_20100730012934.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM analog
2010-07-30 01:29:35.997 AudioOutput Error: snd_pcm_open(analog): No such file or directory
2010-07-30 01:29:35.997 Opening audio device 'analog'. ch 2(2) sr 48000 (reenc 0)
2010-07-30 01:29:35.997 Opening ALSA audio device 'analog'.
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM analog
2010-07-30 01:29:35.997 AudioOutput Error: snd_pcm_open(analog): No such file or directory
2010-07-30 01:29:35.997 NVP(0): Disabling Audio, reason is: snd_pcm_open(analog): No such file or directory

also...
> 
'video_output' mean = '33358.48', std. dev. = '518.30', fps = '29.98'
'video_output' mean = '33366.95', std. dev. = '300.40', fps = '29.97'
'video_output' mean = '33364.64', std. dev. = '319.32', fps = '29.97'
2010-07-30 01:29:49.723 NVP(0): 400 interlaced frames seen.
'video_output' mean = '33361.42', std. dev. = '401.93', fps = '29.97'
'video_output' mean = '33375.32', std. dev. = '357.78', fps = '29.96'
'video_output' mean = '33357.18', std. dev. = '347.67', fps = '29.98'
'video_output' mean = '33372.11', std. dev. = '313.51', fps = '29.97'

Don't think standard deviations should be that high.

Thanks for your response Ian. I'll have to pick this up tomorrow and work on it now. It's getting late here and I have to be up early tomorrow.

I sure wish I had a spare one of these cards to try. Sadly I am very rural here and no one else I know has one within a few hours driving distance.

[ATTACH]164954[/ATTACH]

[ATTACH]164955[/ATTACH]

---

### Post by ian dobson on 2010-07-30
Hi,

What version of the ivtv drivers are you using?

I can remember that I had problems with the standard kernel supplied version of ivtv, sometime last sommer. In the end I used the bleeding edge version of the ivtv drivers which fixed all my problems. I've now gone over to 100% digital.

Regards
Ian Dobson

---

### Post by Furry_Fighter_20x66 on 2010-08-04
Sorry for the delay in getting back. I didn't have any time to work on this until now.

Okay.. I xxd' the /dev/video24 and noticed I was getting data from it, not just rows of 000s and FFFs. So I gave a try to "cat /dev/video24 | aplay -f dat" and I suddenly had sound even though the mythfrontend had reconfigured the card for its own purposes. Then I got noticing that the permissions for /dev/video24 and /dev/video32 were set to 660. I chmodded all them including /dev/vbi0 to 666 and now things are working again in mythbackend.

But I am still scratching my head on this. Why would this work? If I couldn't before capture audio from the pvr-150 after mythbackend soiled it like a cheap date, why would suddenly changing permissions work now? Maybe the card is failing... In any case I will have it do some recordings over the next few days and actively seek out a replacement in the meantime.

Thanks for your assistance Ian. This has definitely been a learning experience.

---

### Post by nickrout on 2010-08-04
Actually you shouldn't be capturing off /dev/video24 anyway, that is the raw audio, you want the compressed and muxed video and audio on  /dev/video0. I believe that's what myth uses,and dumps that output straight to disk.

What does mplayer /dev/video0 do?

what are the permissions on /dev/video0 ? The group should be video and group should have at least read permission.

what does mediainfo tell you about one of the files recorded? or ffmpeg -i

---

### Post by Furry_Fighter_20x66 on 2010-08-04
There was one clue I gleamed from your suggestion to use ffmpeg -i on two different files. The bit rate on a file that wouldn't play audio in mythfrontend or from VLC was 384 kb/s. Those recorded now are 320 kb/s. Otherwise information between the two files are identical. 

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from '1514_20100728013000.mpg':
  Duration: 00:06:48.61, start: 0.189278, bitrate: 5223 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s

I also installed mplayer and then tried it on on both recordings that didn't play properly and one that now does (I wonder why I never thought to try mplayer?). So at least I have been able to deduce it was recording audio the whole time, but VLC was not able to properly play it back. Does anyone else have trouble with VLC playing back a mpg file from their mythtv directory or from a stream directly from /dev/video0 after mythtv has reconfigured the card?

The other thing I have done is reboot a few times to see what happens. I reset the permissions back to 660 on video24, video32 and vbi0 (Video0 has always been 666 root/video) and things work fine now.

> Actually you shouldn't be capturing off /dev/video24 anyway, that is the raw audio, you want the compressed and muxed video and audio on /dev/video0. I believe that's what myth uses,and dumps that output straight to disk.
Yes, but at some point you do likely come around to test it when you are trying to determine why you have no audio or at least audio not working properly.

There is one outstanding question I do not have an answer to. If audio was working fine all along, why did both frontends on different machines both stop playing audio at the exact same time? Why did two entirely different installs of of the backend server and separate mysql databases and servers still yield the same problems? And why did it all suddenly start working again?

I see we had a long due solar flare explosion this week. Maybe it's all due to that? (shrugs). Whatever. I got my TV working again and that's all that matters. At least until it stops working again.

---

