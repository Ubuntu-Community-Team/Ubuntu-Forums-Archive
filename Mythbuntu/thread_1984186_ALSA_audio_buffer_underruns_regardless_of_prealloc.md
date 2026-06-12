---
title: "ALSA audio buffer underruns regardless of prealloc size"
date: 2012-05-21
forum: Mythbuntu
---

### Post by knnniggett on 2012-05-21
So I recently stepped into the modern world. I gave up my 32" CRT TV w/ scan converter for a 40” 1080p LED HDTV. Woo hoo! Unfortunately, it seems I have traded one set of problems for another.

I've got my Nvidia video card attached to my TV via hdmi cable and am attempting to play audio through the TV's two internal speakers (details below). What I am currently wrestling with are many audio buffer underruns. The issue manifests itself as audio “hiccups” when watching TV. 

The odd thing is that it is inconsistent. An OTA channel broadcasting at 1080 may seem fine, while a channel broadcasting an old episode of Stargate SG1 at 480 “hiccups” every other sentence. One might think the opposite should be true. It starts acting up right about the time I think I have solved the problem.

A quick check of my mythfrontend.log file reveals lots of these:
```
May 20 11:36:18 ubuntu-pvr mythfrontend[1714]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AC3 has 2 channels
May 20 11:36:18 ubuntu-pvr mythfrontend[1714]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x2310b90, id(AC3) type(Audio)
May 20 11:36:18 ubuntu-pvr mythfrontend[1714]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'dmix:CARD=NVidia,DEV=7' ch 2(2) sr 48000 sf signed 32 bit reenc 0
May 20 11:36:18 ubuntu-pvr mythfrontend[1714]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 24064
May 20 11:36:18 ubuntu-pvr mythfrontend[1714]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm7p/sub0/prealloc: Permission denied. 
May 20 11:36:18 ubuntu-pvr mythfrontend[1714]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 24064 | sudo tee /proc/asound/card0/pcm7p/sub0/prealloc
May 20 11:36:18 ubuntu-pvr mythfrontend[1714]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely

```

When Googling this error, most other issues out there seem to be resolved by simply increasing prealloc.   However, this is a moving target in my case. As soon as I increase prealloc to what it suggests, it immediately asks to raise it further.  After setting prealloc to the maximum of 32768, the errors now become:
```
May 20 20:19:17 ubuntu-pvr mythfrontend[1714]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x4429b90, id(MPEG2VIDEO) type(Video)
May 20 20:19:17 ubuntu-pvr mythfrontend[1714]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AC3 has 2 channels
May 20 20:19:17 ubuntu-pvr mythfrontend[1714]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x2b42f40, id(AC3) type(Audio)
May 20 20:19:17 ubuntu-pvr mythfrontend[1714]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'dmix:CARD=NVidia,DEV=7' ch 2(2) sr 48000 sf signed 32 bit reenc 0
May 20 20:19:17 ubuntu-pvr mythfrontend[1714]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely


```

True, I could likely increase prealloc_max and thus increase prealloc even further. However, I don't think that is the real issue. A 32MB audio buffer should be way more than I need. Something else is going here, and I'm looking for feedback regarding where to look.

Since prealloc is owned by root on my system, adding the mythtv user to the audio group does not have any effect.

My hardware & software should be sufficient:
Apex 40” 1080p, LED hdtv model# LE-40H88
Gigabyte GA-H67N-USB3-B3 (internal audio chipset is turned off)
Intel i3 2100
4GB RAM
128GB SSD boot drive + storage partition
two additional SATA II drives
All video data volumes are XFS
HDHomerun configured for OTA
Nvidia GeForce GTX 550 w/ 1G DDR5
Mythbuntu 12.04 LTS x86_64
Mythtv 0.25 + latest patches


TO DO:
Verify this problem occurs with the handful of unencrypted channels I get from Charter via a second hdhomerun.

Please let me know your suggestions.

---

### Post by singedwings on 2012-05-23
First off, I have been having the prealloc issue myself. How are you increasing the buffer size? I have been using```
sudo chmod 777 /proc/asound/card0/pcm0p/sub0/prealloc
```to solve this. It's not clean and tidy but it is easy, has to be redone after restarting the computer.

With your setup I cannot see any reason why the buffer would need to be maxed out and still not enough! Something else must be going on. What video display setting are you using? Is there anything different about the format that is causing problems?

---

### Post by knnniggett on 2012-05-23
It would seem that the best solution would be to have udev assign the audio group to all audio devices. As we both know, this is not happening. At the moment, I'm too focused on the stuttering issue itself to bother with filing a bug report or research if a report has already been filed.

But to answer your question, I have placed the following into my /etc/rc.local:
```
echo 32768 | sudo tee /proc/asound/card0/pcm7p/sub0/prealloc
```

When I had my CRT, I was forcing the desktop & video to 640x480. Following the upgrade to an HDTV, I have turned off that setting in Mythtv. I am letting Mythtv use whatever it thinks should be the best resolution. Ironically, that seems to be 640x480. For example, I could use randr to set my desktop to 1024x768, but when I start the frontend it puts it back to 640x480.

I tested my other hdhomerun (connected to the cable line) and it stutters as well so that eliminates antenna reception as the culprit.

I also use Hulu, and I don't recall any audio stuttering. I need to verify this tonight. 

One thing I have noticed is that Mythtv lists the same device multiple times under the audio devices. From memory I think it looks something like this:
```
hdw:CARD=NVidia,DEV=7
dmix:CARD=NVidia,DEV=7
hdmi:CARD=NVidia,DEV=7
```

I have chosen "dmix" on the assumption that, because I launch Hulu from within Mythtv, I need a mixer to allow audio from both to work. I'm basically guessing.

Something else on my to-do list will be to see if VDPAU is overtaxing the video card. I'll temporarily turn off VDPAU to see if there is a difference.

Any other ideas are welcome.

---

### Post by uncle hammy on 2012-05-24
I'd suggest taking this to the mythtv users list when JYA who manages the MythTV audio code will actually see it, and very likely be able to help you with this.

[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)

---

### Post by knnniggett on 2012-05-25
I wanted to spend a couple more days chewing on this before I took this issue to mythtv-user group. The feedback I got from this thread was enough to confirm that I wasn't doing anything obviously wrong. My hunch was I had some kind of configuration error so I went through every setting I could think of that could affect performance.

What I found was that the ringbuffer, of all things, was causing the issue. After I increased it from 32MB to the maximum ~90MB-ish the audio stuttering went away. 

Since most everything I've read about the ringbuffer plays down its role in recent versions of MythTV, I can't explain why it helped, but the most important thing is that the problem is solved.

---

### Post by nickrout on 2012-05-26
The comment on the setup page is "The HD ringbuffer allows the backend to weather moments of stress. The larger the ringbuffer ... the longer the moments of stress can be..."

Perhaps your system is stressed, probably specifically the Disk IO.

---

### Post by knnniggett on 2012-05-27
Yeah, I can see why you might say that. However, I did a lot of testing and one of the things I had done was prove to myself that the system wasn't stressed at all. CPU usage is a barely noticable 2-6%, disk I/O peaks at just ~3.5MBps, the nic and entire network runs at 1Gbps, commercial flagging was scheduled for after hours, memory usage is nowhere near the limit and nothing is getting swapped. The only thing I didn't measure directly was the load on the video card, but I ruled that out by simply turning off VDPAU and observing the same audio issue.

UPDATE: I confirmed that I am dealing with multiple issues. While initially I was dealing with audio underruns, once I increased prealloc sufficiently the underrun problem went away despite the warning in my logs that prealloc still wasn't large enough. I didn't realize until last night that there is a problem with the TV itself (a.k.a. problem #2). Throughout this ordeal, I thought to myself "Gee, some of these audio dropouts sure sounds like the TV's audio amp is clipping". Well, that is exactly what was happening. If I increase the volume on the TV just a tad higher than what I'll call a comfortable room level, loud noises start dropping out. If I increase the volume even further, the show becomes unlistenable. If I turn down the volume, the audio problem immediately goes away.

This of course throws into question my previous determination that the ring buffer had anything to do with the problem. At the time I was adjusting the ring buffer, I must have turned down the volume on the TV just enough so that every channel would play fine.

I guess that will teach me to buy a refurbished TV, huh?

---

