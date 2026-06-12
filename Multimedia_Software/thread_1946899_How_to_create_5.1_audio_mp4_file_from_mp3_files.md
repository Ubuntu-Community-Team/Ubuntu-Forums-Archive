---
title: "How to create 5.1 audio mp4 file from mp3 files"
date: 2012-03-25
forum: Multimedia Software
---

### Post by Kissell on 2012-03-25
I have five CDs (from The Flaming Lips) that are meant to be played simultaneously in five different CD players...  obviously that is a hassle...  I have ripped them to mp3 format.  

How can I combine them into a single mp4 file (or whatever container is capable of surround sound, like mkv) that is encoded with 5.0 surround sound?  This way I can just play that one file and it'll play the correct CD out the correct speaker.  Similar to when I play an mp4 movie file that has 5.1 surround sound, but without a video track.

---

### Post by nothingspecial on 2012-03-27
*Thread moved to **Multimedia & Video**.*

---

### Post by Kissell on 2012-03-27
I tried using Audacity to create a multi-channel FLAC file from a bunch of mp3 files used as channels sources, but in the various things I've tried the channels weren't isolated...  or some weren't mapped to any speakers.

---

### Post by BicyclerBoy on 2012-03-27
Great idea..

These below methods require recent ffmpeg that has lavfi filters..

I've tried this with 3 stereo mp2 audio only files..
If you have 3x stereo sound files called funky[1-3].mp2 you can:
make a 4 ch audio file:
ffmpeg -f lavfi -i "amovie=funky1.mp2:si=0 [a1]; amovie=funky2.mp2:si=0 [a2]; [a1][a2] amerge" -c:a pcm_s16le output-4.mkv

then add another stereo funky3.mp2:
ffmpeg -f lavfi -i "amovie=output-4.mkv:si=0 [a1]; amovie=funky3.mp2:si=0 [a2]; [a1][a2] amerge" -c:a pcm_s16le output-6.mkv
This channel order should be a1 a2 b1 b2 c1 c2..

If the channel order is wrong (& who knows??):
This (is meant to) swaps front left & right:

ffmpeg -f lavfi -i amovie=output-6.mkv,pan="5.1: c0=c1:c1=c0:c2=c2:c3=c3:c4=c4:c5=c5" -c:a pcm_s16le output-6-RL.mkv

Using 6 mono mp3 files is :
ffmpeg -f lavfi -i "
amovie=input1.mp3:si=0 [a0];
amovie=input2.mp3:si=0 [a1];
amovie=input3.mp3:si=0 [a2];
amovie=input4.mp3:si=0 [a3];
amovie=input5.mp3:si=0 [a4];
amovie=input6.mp3:si=0 [a5];
[a0][a1][a2][a3][a4][a5] amerge" -c:a pcm_s16le output.mkv

would pay to set the bitrate to something audio like -b:a 320K.
You can change the channel order by changing the input file order or by changing orderof the amerge input streams [an]..
Then you need to be able to output direct by HDMI 5.1 LPCM or encode into AC3 or use alsa a52 encoder..

---

