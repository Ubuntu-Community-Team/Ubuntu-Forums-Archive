---
title: "Extracing the sound track from an AVI file"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by elreteipos on 2007-03-19
Is it possible to extract the audio track from an AVI file and save it as an MP3?

---

### Post by qamelian on 2007-03-19
It is possible and there are several ways to do it. Most video editing software will allow you to export the audio track.

---

### Post by elreteipos on 2007-03-19
Is there a simple command line tool to do this? I'm not planning to do any video editing.

---

### Post by lha on 2007-03-20
> **elreteipos said:**
> Is there a simple command line tool to do this? I'm not planning to do any video editing.

```

mplayer -dumpaudio -dumpfile FILE_OUT FILE_IN

```

Mplayer can dump audio from video files. If the audio in your video file is encoded as mp3, FILE_OUT will be a mp3. Otherwise you have to re-encode it.

---

### Post by elreteipos on 2007-03-22
How can I determine whether the audio was encoded as MP3 or not?

---

### Post by lha on 2007-03-22
> **elreteipos said:**
> How can I determine whether the audio was encoded as MP3 or not?
```
mplayer FILE_IN
```
It shows a lot more than just the codec. Try
```
mplayer -msglevel all=-1:decaudio=4 FILE_IN
```
if you want mplayer to show less uncalled-for information.

---

### Post by elreteipos on 2007-03-23
Here's what it says:> Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 32000 Hz, 2 ch, s16le, 1024.0 kbit/100.00% (ratio: 128000->128000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)Does that mean I have to use a different program to rip the sound?

---

### Post by lha on 2007-03-25
> **elreteipos said:**
> Here's what it says: Does that mean I have to use a different program to rip the sound?

No, but you need another program to re-encode the resulting audio file. Lame is a popular choice. The audio in your video file seems to be in a suitable format for lame. You can try if lame accepts audio file given by "mplayer -dumpaudio...". If not, use
```

mplayer -vc null -vo null -ao pcm FILE_IN

```
It will create a file "audiodump.wav", which you can then encode to mp3. The latter command should work with any video file that mplayer supports.

---

### Post by elreteipos on 2007-03-29
Doesn't work for some reason...> [AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 32000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
[AO PCM] Failed to open audiodump.wav for writing!
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...[Update] If I cd to $HOME/Desktop, it works. Thanks for your help.

---

