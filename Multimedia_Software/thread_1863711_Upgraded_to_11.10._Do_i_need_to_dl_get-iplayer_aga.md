---
title: "Upgraded to 11.10. Do i need to dl get-iplayer again?"
date: 2011-10-18
forum: Multimedia Software
---

### Post by Filthy Stockings on 2011-10-18
18 10 11 Upgraded to 11.10 y/day and tried out GET-IPLAYER as still on machine.

Found that for radio download the final file is listed as AAC not mp4 and slightly larger than download via 11.04.

Also noticed that in terminal, please bear with me as not very technical proficient so might use wrong language, at end of radio programme DL, instead of the usual speedy run of lines of PROGRESS, there were NONE and wondered if this was why the AAC form is now denoted instead of MP4.

Also since I obtained, in this forum, advice on how to remove static artwork on radio downloads, the post 11.10 upgrade radio DL didn't require me to operate that ATOMIC PARSLEY REMOVE ARTWORK effort; which is a plus for me.

This is what I received in downloading a radio prog with 11.10 installed:

                                  [COLOR=#000000][SIZE=3]ubuntu@PC-3:~$ get-iplayer -g 10678 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty. [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]This is free software, and you are welcome to redistribute it under certain [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]conditions; use --conditions for details. [/SIZE][/COLOR] 
  

  [COLOR=#000000][SIZE=3]Matches: [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]10678:    radio, Count Arthur Strong's Radio Show!: Series 2 - Episode 5, BBC Radio 4 Extra, Comedy,Radio,Spoof [/SIZE][/COLOR] 
  

  [COLOR=#000000][SIZE=3]INFO: 1 Matching Programmes [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]INFO: Checking existence of default version [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]INFO: flashaacstd1,flashaaclow1,wma1 modes will be tried for version default [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]INFO: Trying flashaacstd1 mode to record radio: Count Arthur Strong's Radio Show!: Series 2 - Episode 5 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Count_Arthur_Strongs_Radio_Show_Series_2_-_Episode_5_b00dbsqc_default                 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]FLVStreamer v2.1c1 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Starting download at: 0.000 kB [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Metadata: [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]duration              2160.06 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]moovPosition          36.00 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]audiocodecid          mp4a [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]aacaot                2.00 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]audiosamplerate       44100.00 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]audiochannels         2.00 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]tags: [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]©alb                 Count Arthur Strong's Radio Show! - Series 2 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]aART                  BBC Radio 4 Extra [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]©ART                 BBC Radio 4 Extra [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]©cmt                 The showbiz legend's got hospital tests, but says his goodbyes in case the worst happens. [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]cprt                  British Broadcasting Corporation Copyright 2011, all rights reserved. [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]©gen                 Podcast [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]©nam                 Count Arthur Strong's Radio Show! - Series 2 17 10 2011 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]©day                 2011 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]trackinfo: [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]length                95258624.00 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]timescale             44100.00 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]language              und [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]sampledescription: [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]sampletype            mp4a [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]35240.703 kB / 2156.62 sec (99.8%) [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Download complete [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]built on Oct  2 2011 15:13:26 with gcc 4.6.1 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]WARNING: library configuration mismatch [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]avutil      configuration: --extra-version='4:0.7.2.1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --enable-shared --disable-static [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]avcodec     configuration: --extra-version='4:0.7.2.1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --enable-shared --disable-static [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]libavutil    51.  7. 0 / 51.  7. 0 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]libavcodec   53.  5. 0 / 53.  5. 0 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]libavformat  53.  2. 0 / 53.  2. 0 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]libavdevice  53.  0. 0 / 53.  0. 0 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]libavfilter   2.  4. 0 /  2.  4. 0 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]libswscale    2.  0. 0 /  2.  0. 0 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]libpostproc  52.  0. 0 / 52.  0. 0 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3][flv @ 0x9a2560] max_analyze_duration reached [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3][flv @ 0x9a2560] Estimating duration from bitrate, this may be inaccurate [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Input #0, flv, from '/home/ubuntu/Count_Arthur_Strongs_Radio_Show_Series_2_-_Episode_5_b00dbsqc_default.partial.aac.flv': [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]Metadata: [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]duration        : 2160 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]moovPosition    : 36 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]audiocodecid    : mp4a [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]aacaot          : 2 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]audiosamplerate : 44100 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]audiochannels   : 2 [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]Duration: 00:36:00.06, start: 0.000000, bitrate: N/A [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]Stream #0.0: Audio: aac, 44100 Hz, stereo, s16 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Output #0, adts, to '/home/ubuntu/Count_Arthur_Strongs_Radio_Show_Series_2_-_Episode_5_b00dbsqc_default.partial.aac': [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]Metadata: [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]duration        : 2160 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]moovPosition    : 36 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]audiocodecid    : mp4a [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]aacaot          : 2 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]audiosamplerate : 44100 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]audiochannels   : 2 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]encoder         : Lavf53.2.0 [/SIZE][/COLOR] 
  [COLOR=#000000]    [SIZE=3]Stream #0.0: Audio: libvo_aacenc, 44100 Hz, stereo [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Stream mapping: [/SIZE][/COLOR] 
  [COLOR=#000000]  [SIZE=3]Stream #0.0 -> #0.0 [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]Press ctrl-c to stop encoding [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]size=   34387kB time=2160.06 bitrate= 130.4kbits/s    [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]video:0kB audio:33751kB global headers:0kB muxing overhead 1.884152% [/SIZE][/COLOR] 
  [COLOR=#000000][SIZE=3]INFO: Recorded /home/ubuntu/Count_Arthur_Strongs_Radio_Show_Series_2_-_Episode_5_b00dbsqc_default.aac [/SIZE][/COLOR] 
  

  [COLOR=#000000][SIZE=3]INFO: id3 tagging aac file [/SIZE][/COLOR] 
 
Also tried a tv programme DL and found there were artifacts which appeared as horizontal 'ripples' every few minutes and have never seen those sort of visual problems before.

So wondered if the UPGRADE to 11.10 has impaired the existing GET-IPLAYER programme and if I need or would benefit from downloading that utility again...and if so then any advice on where best to find it as many seem to be online.

Thanks in advance

SA

---

### Post by Catroaster on 2011-10-18
The best place to get get_iplayer from is [https://launchpad.net/~jon-hedgerows/+archive/get-iplayer](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer) . It (nearly) just works - all you will have to do is sudo apt-get install librtmp0 after installing the new get_iplayer and that works for me.

---

### Post by Filthy Stockings on 2011-10-18
Thanks for reply

Did you have to re-install after moving to 11.10 ie did you note problems with the new version of UBUNTU?

---

### Post by Catroaster on 2011-10-18
I'm afraid I did a complete wipe of the hard disk and reinstall, so I couldn't say whether the upgrade broke get_iplayer or not. However, I would upgrade get_iplayer if I were you - you appear to be using flvstreamer which has known problems with the iplayer's current output.

---

### Post by Filthy Stockings on 2011-10-18
Thanks for the reply. Do you know if I have to remove the old get-iplayer or will the re-install deal with that?

Am finding it very difficult to locate files/folders such as might hold get-iplayer with the very unfamilar 11.10 version.

Have been fine and happy with the currently used get-iplayer despite it always stating something about flvstreamer not supporting SWF verification...whatever that it. 

It gave me no visible / audible problems through months of use with 11.04 system.

Problems have only begun with the upgrade to 11.10 yesterday. 

Am reading that clean installs are advised over UPGRADES but didn't see any warnings in my UPDATE alert box so took up the offer that was made to me at that moment.

Could that have lead to the awful experiences I have had with 11.10 so far, do you think?

---

### Post by Catroaster on 2011-10-18
If you remove the get_iplayer 2.79 package from your system, then install the version from the PPA , that should work. The PPA version includes it's own versions of the required dependencies, and uses them. As I said, you will need to sudo apt-get install librtmp0 after installing get_iplayer 2.80.

There is a mailing list for this version of get_iplayer at [http://lists.infradead.org/pipermail/get_iplayer/](http://lists.infradead.org/pipermail/get_iplayer/) - let me know if you have any more problems, but they are the experts. I just know a bit from many months of fiddling around to get get_iplayer working.

---

### Post by Filthy Stockings on 2011-11-06
Belated thanks for response. Am still on old version as still bit fearful of messing up my current workable version BUT after last auto update for 11.10 now find that BANSHEE being associated with GIP audio files rather than preferred TOTEM MOVIEPLAYER.....but can work with this by just choosing OPEN WITH MOVIEPLAYER....

TV files open as before with just a double click.

Thanks again.

SA

---

### Post by Filthy Stockings on 2011-11-13
Solved this latest problem by disassociating BANSHEE.....think am learning 'how to fish' ...well tiddlers, anyway.

---

