---
title: "Planned HTPC Hardware"
date: 2011-09-13
forum: Mythbuntu
---

### Post by Koppschaechter on 2011-09-13
Mainboard/CPU: ZOTAC 479 IONITX-S-E (Atom D525; Next-Generation NVIDA 
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]ION)[COLOR=#969696][FONT=Arial][/FONT][/COLOR][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][INDENT][/INDENT]HDD: Western Digital 320GB Scorpio Blue SATAII

Memory: 2GB Kingston DDR-3 800

Tuner: TechnoTrend S2-3600 DVB-S2 USB


This is what I planned to buy for a HTPC. Not sure about the Case yet, but the above should give me a fully functional HTPC (right?).

I'd appreciate some comments or recommendation on whether this setup will work as both simultaniously, backend and frontend.

---

### Post by nickrout on 2011-09-13
Are you planning to commflag or transcode your recorded tv? If so then you want a more powerful CPU. If not then it should be fine.

I don't know about that particular DVB card, you will need to check on linuxtv.org.

Your hard drive is far too small, 2TB is quite economical at present.

If the video card uses system RAM you might want to go to 4GB.

---

### Post by Koppschaechter on 2011-09-14
I don't really need to commflag, so I wouldn't mind it not working.

About the transcoding... I don't really know what I need that for. I didn't have a decent look at the software yet. I just saw it a couple of times at a friend's place I liked it.

---

### Post by nickrout on 2011-09-14
> **Koppschaechter said:**
> I don't really need to commflag, so I wouldn't mind it not working.

About the transcoding... I don't really know what I need that for. I didn't have a decent look at the software yet. I just saw it a couple of times at a friend's place I liked it.

transcoding - only really necessary for (a) changing a file to a format capable of being used by different hardware, like a smartphone, or some retarded thing like a ps3 or xbox that is locked down. No, you probably don't need it. Point is that it is a CPU intensive operation, for which atom is ill-suited, or (b) saving disk space. But disk space is cheap these days, add another disk :)

One point i perhaps didn't mention before is playing files that are not encoded in a way that the ION graphics will process as VDPAU compatible. VDPAU is a video hardware acceleration feature of nVidia graphics cards, It supports mpeg2 and h264 video (with some limitations). Therefore is supports almost all broadcast digital TV. However if you download or otherwise obtain videos that are not compatible with VDPAU the system will fall back to decoding on the CPU, and there atom might fall down again. Having said that, I use an ION (first generation) box all the time and it is fine.

---

### Post by Koppschaechter on 2011-09-14
I forgot to mention, that the HDD I mentioned above is not planned to be the one for my media for long. I basically want to use it for the System and for the loop mythtv records permanently (dunno how it's actually called).

I am planning to buy two bigger USB Discs (later) to use them as a raid to have my media save and as an network storage. 

I don't see a need to transcode reading what it's good for. So no problem with that.

I think if I get some media that is not compatible to VDPAU I can transcode it to fit in. If necessary on another machine. I guess the Zotac board won't be good at that when its not good at playing it. 
Or is it possibly able to transcode uncompatible media while still showing me the current TV-Programm and therefor it takes longer to transcode? I could live with that.

---

### Post by nickrout on 2011-09-14
You would have to try transcoding and seeing. If it is SD material the CPU may play it anyway.

---

### Post by Koppschaechter on 2011-10-05
I bought the hardware mentioned above and it's working just fine, completely passively cooled.

The only problem I have atm is that I have some videos that won't play properly but stutter. Most of those videos are 720p but there are also some SD videos that stutter. I guess I need to transcode them to a format that suits my hardware better. Can someone help me with that?

---

### Post by ZedThou on 2011-10-05
I've been using an IONITX-A for a couple of years now and nothing that I've played stutters, once I got the configuration ironed down. I don't know much about your board, but on this one it was important to get a few xorg.conf options right to avoid any stuttering. Here's my xorg.conf, just in case the last three Options might be of any help.

```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
        Option "TripleBuffer" "True"
        Option "UseEvents" "0"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```

---

### Post by LowSky on 2011-10-07
> **Koppschaechter said:**
> I bought the hardware mentioned above and it's working just fine, completely passively cooled.

The only problem I have atm is that I have some videos that won't play properly but stutter. Most of those videos are 720p but there are also some SD videos that stutter. I guess I need to transcode them to a format that suits my hardware better. Can someone help me with that?

Just turn on VDPAU in the Mythtv frontend Tv settings. Stutter will go away.

---

### Post by Koppschaechter on 2011-10-11
I had VDPAU turned on from the beginning. I also added the options ZedThou posted. They seemed to help, but still some of those videos stutter.

---

### Post by nickrout on 2011-10-11
what does the frontend log say?

---

### Post by Koppschaechter on 2011-10-11
I couldn't find a File that stutters in mythtv atm, but I found one of those that wouldn't play at all in mythtv and stutter when played with VLC. Here's what the mythfrontend.log says:
```
011-10-11 09:19:40.818 TV: Attempting to change from None to WatchingVideo
2011-10-11 09:19:41.573 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2011-10-11 09:19:41.688 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:41.689 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:41.699 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2011-10-11 09:19:41.844 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2011-10-11 09:19:41.910 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2011-10-11 09:19:41.977 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2011-10-11 09:19:42.044 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2011-10-11 09:19:42.101 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning 0
2011-10-11 09:19:42.101 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.151 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.151 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.152 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.202 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.202 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.202 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.252 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.252 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.252 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.302 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.303 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.303 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.353 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.353 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.353 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.403 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.403 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.403 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.453 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.454 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.454 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.504 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.504 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.504 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.554 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.554 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.554 Player(3), Warning: OpenFile() waiting on data
2011-10-11 09:19:42.605 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Error: ReadPriv(..2048, peek): Attempt to read after commserror set
2011-10-11 09:19:42.605 RingBuf(myth://Videos@127.0.0.1:6543/test/test_720p.mkv) Warning: Peek() requested 2048 bytes, but only returning -1
2011-10-11 09:19:42.605 Player(3), Error: OpenFile(): Could not read first 2048 bytes of 'myth://Videos@127.0.0.1:6543/test/test_720p.mkv'
2011-10-11 09:19:42.605 Unable to open video file.
2011-10-11 09:20:02.641 playCtx, Error: StartPlaying() Failed to start player
```

---

### Post by Koppschaechter on 2011-10-11
Sorry, that was another problem. Solved that with google.

Somehow MythTV didn't have access to that files. The following fixed that:

```
sudo chown -R mythtv /var/lib/myhttv/video/
```

Does that mean I have to change the owner of each file I copy to the video folder?


This beeing a different problem means that I wasn't able to reproduce that problem. I probably deleted all affected files.

---

### Post by nickrout on 2011-10-11
Well if you can't tell us more about the files and the generated error messages you cannot expect any more help.

---

### Post by Koppschaechter on 2011-10-11
Sure, didn't expect any further help without beeing able to supply further information. I'll report back when I encounter this problem again.

---

