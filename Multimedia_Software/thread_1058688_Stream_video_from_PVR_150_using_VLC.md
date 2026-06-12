---
title: "Stream video from PVR 150 using VLC"
date: 2009-02-03
forum: Multimedia Software
---

### Post by steenbras on 2009-02-03
I'm having a fair bit of trouble trying to get this to work, and I'm sure I'm missing something basic (I'm not really trying to do anything too advanced here, so it must be relatively simple.

I have a Hauppauge PVR 150 MCE card in an old Dell Optiplex. I'm running Hardy and VLC 0.94 (packaged).

All I want to do is stream via UDP or RTP (with SAP announcements) the video (with audio) coming directly into the card's composite connector (input 1). My signal is PAL-I (South Africa) and the input is a DSTV decoder - our local digital satellite broadcaster.

As the PVR 150 already outputs MPEG-2, I'm unsure of the need for full transcoding. With transcoding, I get very bad results - jumpy pictures or massive pixelation.

At no stage have I been able to broadcast any audio.

This has been my most successful attempt yet:

```
vlc -vvv v4l2:///dev/video0:input=2:standard=8:audio-input=1:audio-method=3 --sout udp:239.255.1.1 --ttl 12
```

Although I'm not sure the standard setting is working - I get this extract from the message log:

```
[00000420] v4l2 access debug: video input 0 (Tuner 1) has type: Tuner adapter  
[00000420] v4l2 access debug: video input 1 (S-Video 1) has type: External analog input  
[00000420] v4l2 access debug: video input 2 (Composite 1) has type: External analog input *
[00000420] v4l2 access debug: video input 3 (S-Video 2) has type: External analog input  
[00000420] v4l2 access debug: video input 4 (Composite 2) has type: External analog input  
[00000420] v4l2 access debug: video standard 0 is: NTSC  
[00000420] v4l2 access debug: video standard 1 is: NTSC-M *
[00000420] v4l2 access debug: video standard 2 is: NTSC-M-JP  
[00000420] v4l2 access debug: video standard 3 is: NTSC-M-KR  
[00000420] v4l2 access debug: video standard 4 is: NTSC-443  
[00000420] v4l2 access debug: video standard 5 is: PAL  
[00000420] v4l2 access debug: video standard 6 is: PAL-BG  
[00000420] v4l2 access debug: video standard 7 is: PAL-H  
[00000420] v4l2 access debug: video standard 8 is: PAL-I  
[00000420] v4l2 access debug: video standard 9 is: PAL-DK  
[00000420] v4l2 access debug: video standard 10 is: PAL-M  
[00000420] v4l2 access debug: video standard 11 is: PAL-N  
[00000420] v4l2 access debug: video standard 12 is: PAL-Nc  
[00000420] v4l2 access debug: video standard 13 is: PAL-60  
[00000420] v4l2 access debug: video standard 14 is: SECAM  
[00000420] v4l2 access debug: video standard 15 is: SECAM-B  
[00000420] v4l2 access debug: video standard 16 is: SECAM-G  
[00000420] v4l2 access debug: video standard 17 is: SECAM-H  
[00000420] v4l2 access debug: video standard 18 is: SECAM-DK  
[00000420] v4l2 access debug: video standard 19 is: SECAM-L  
[00000420] v4l2 access debug: video standard 20 is: SECAM-Lc  
[00000420] v4l2 access debug: audio input 0 (Tuner 1) is Stereo   
[00000420] v4l2 access debug: audio input 1 (Line In 1) is Stereo  *
[00000420] v4l2 access debug: audio input 2 (Line In 2) is Stereo   

```

I presume the asterisks indicate selections - this looks like NTSC-M is being selected, and this accounts for the picture quality I'm seeing.

I'd really appreciate any help - I'm just going around in circles now.

---

### Post by steenbras on 2009-02-03
Just to re-iterate - the problems I am having are:

1. Video standard not being set properly, leading to venetian blind effect when there is movement in the videostream (largely static pictures not affected)

2. Cannot pick up audio.

After starting vlc with that command line in my post above, running a v4l2-ctl gives the following:

```
Video input : 2 (Composite 1)
Audio input : 1 (Line In 1)
Frequency: 704 (44.000000 MHz)
Video Standard = 0x00000001
	PAL-B

```

Slightly confused by that last entry there, since the output from vlc shows 
```
v4l2 access debug: video standard 1 is: NTSC-M *
```

Same value (1) but different standard.

---

### Post by steenbras on 2009-02-04
Quiet thread!

I've found a solution to both issues... but the solution to the interlacing is not ideal, so any thoughts you can share would be welcome.

The reason for the lack of audio was a simple one. VLC was streaming with quiet audio! I opened the GUI on the streaming server, chose the extended settings and in the V4L options I upped the volume. Voila - sound!

I've added the volume to the command line for launching, so that's now:

```
vlc -vvv v4l2:///dev/video0:input=2:audio-input=1:standard=8:volume=54272 --sout udp:239.255.1.1 --ttl 12
```

Regarding the interlacing issue - I can set deinterlacing on a vlc client, but I'd rather have it deinterlaced on broadcast. I'm presuming that setting the standard to PAL-I would do this, so any help on getting the set standard to take effect would still be greatly appreciated.

At the end of this all, I hope to have a HOWTO for other people trying to do this - it certainly ain't as easy as it should be.

---

### Post by steenbras on 2009-02-06
I still haven't worked out how to broadcast deinterlaced video, but as that can be rectified in the client, I'm not all that worried. I assume that to stream without interlacing, I would need to transcode - and as the card already does mpeg-2 conversion that's probably an overhead that I can do without.

So following is the command line I use to stream video from the PVR-150. This takes a composite video input, with audio in composite (Line 1). This stream is setup with a SAP announcement that can be detected by clients on the LAN. 

Further discoveries I made here - the packaged version of vlc (0.9.4) will NOT announce the stream successfully to clients on Windows or OS/X. I assume this is because the SAP announcement standard is not strictly followed on the broadcast in the earlier version. However, there are .deb files [here]("http://archive.getdeb.net/dump/intrepid/vlc/") which will allow you to install 0.9.8a, and streaming from this version I have picked up the announcements on all 3 OSs - XP, OS/X Leopard, and Intrepid. You will need the vlc-nox and vlc packages from that page.

Here goes:
```
vlc -vvv v4l2:///dev/video0:input=2:audio-input=1:standard=8:volume=54272 --sout '#rtp{mux=,dst=239.255.1.1,sap,name="DSTV"}' --ttl 1
```

I hope this helps others trying to do this (what should be) simple task.

---

### Post by Swiwer on 2009-06-26
Hi steenbras.
A very interesting thread, but, as basically all others, written for Linux. I have WinTV-PVR-150 on Windows XP Pro SP3 machine and I cannot get VLC to open the video from it. I select "Open Capture Device", select Hauppauge PVR-150, but it won't play. You have mentioned XP in your post. Did you actually get your card to work with VLC on a Windows XP machine ? I have Googled everywhere but I just didn't find any other  way to stream the already encoded MPEG-2 stream from PVR-150 over my LAN. Transcoding is not an option due to a weak CPU. Let me know if you have any ideas which could help me. Thanks.

---

