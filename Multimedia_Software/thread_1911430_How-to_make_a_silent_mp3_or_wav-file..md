---
title: "How-to make a silent mp3 or wav-file."
date: 2012-01-18
forum: Multimedia Software
---

### Post by Azyx on 2012-01-18
Is there a simple way to make a silent sound-file for a sertain time? It should be an easy way to get silance pause in a playlist, for instanse över the night.

/Cheers

---

### Post by |{urse on 2012-01-18
Use audacity

> sudo apt-get install audacity

and make a blank one with whatever track length you want.

open audacity with the command 

> audacity

click the record button and wait 

click the stop button when its the length you want 

click file, click export

under the file browser window that pops up click the dropdown menu for filetype and select "Mp3 files"

name your file fooorwhatever.mp3 and click save 

all done :)

---

### Post by Azyx on 2012-01-18
Tanks! Cheers

---

### Post by shantiq on 2012-01-19
maybe easier even   with sox


enter    ```
rec  filename.wav
```   in terminal [without plugging in a microphone]

---

### Post by Azyx on 2012-01-19
> **shantiq said:**
> maybe easier even   with sox


enter    ```
rec  filename.wav
```   in terminal [without plugging in a microphone]

But i need to wait the time any way. sould be nice if just editing the lengt in the file ;)

Cheers

---

### Post by shantiq on 2012-01-19
ok really easy


```
rec  filename.wav  trim 0  30
```   

 will give thirty second recording   :KS

```
rec  filename.wav  trim 0  120
```   

will give you  a 2 minute recording


5 second mp3   with 320kbps

```
rec   -C 320  nameyouwant.mp3   trim  0 05
```


**[added options]("http://ubuntuforums.org/showpost.php?p=11056042&postcount=2")**

==========================

**PS**   those are the formats available

> AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb amr-nb amr-wb anb au avi avr awb cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 ffmpeg flac fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu m4a m4b maud mp2 mp3 mp4 mpg nist ogg prc raw s1 s16 s2 s24 s3 s32 s4 s8 sb sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox wav wavpcm wmv wv wve xa


---

### Post by Azyx on 2012-01-19
> **shantiq said:**
> ok really easy


Great. /Cheers

---

### Post by FakeOutdoorsman on 2012-01-19
Another method by using FFmpeg. 60 seconds of silent audio in WAV:
```
ffmpeg -ar 48000 -t 60 -f s16le -acodec pcm_s16le -ac 2 -i /dev/zero -acodec copy output.wav
```

60 seconds of silent audio in MP3:
```
ffmpeg -ar 48000 -t 60 -f s16le -acodec pcm_s16le -ac 2 -i /dev/zero -acodec libmp3lame -aq 4 output.mp3
```

Adjust the *-t* option for your desired length. Values can be in seconds as shown in the examples, or *hh:mm:ss.ms* as in 01:23:45.30. You probably don't need two channels for silent WAV audio, so consider dropping *-ac 2*.

---

### Post by Azyx on 2012-01-19
> **FakeOutdoorsman said:**
> Another method by using FFmpeg. 60 seconds of silent audio in WAV:
```
ffmpeg -ar 48000 -t 60 -f s16le -acodec pcm_s16le -ac 2 -i /dev/zero -acodec copy output.wav
```

60 seconds of silent audio in MP3:
```
ffmpeg -ar 48000 -t 60 -f s16le -acodec pcm_s16le -ac 2 -i /dev/zero -acodec libmp3lame -aq 4 output.mp3
```

Adjust the *-t* option for your desired length. Values can be in seconds as shown in the examples, or *hh:mm:ss.ms* as in 01:23:45.30. You probably don't need two channels for silent WAV audio, so consider dropping *-ac 2*.

Where do i find the file?

---

### Post by FakeOutdoorsman on 2012-01-19
The output file, *output.wav* or *output.mp3* in my examples, should appear in whatever directory you ran the command. For example, if I simply open Terminal and run the command the file will appear in my home directory.

---

### Post by Azyx on 2012-01-20
> **FakeOutdoorsman said:**
> The output file, *output.wav* or *output.mp3* in my examples, should appear in whatever directory you ran the command. For example, if I simply open Terminal and run the command the file will appear in my home directory.

Have a problem. It's unknown encoder 'libmp3lame' I seached in synaptic and find a libmp3lame0, but when I change your command from 'libmp3lame'->'libmp3lame0', I get the same error message, but that 'libmp3lame0' is uknown.

PS A hour silence .wav get 600MB big file ;)

---

### Post by FakeOutdoorsman on 2012-01-20
By default the version of ffmpeg from the repository requires installation of an additional package to enable more encoders, such as *libmp3lame*, the MP3 encoder. See **Option B** here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Azyx on 2012-01-20
> **FakeOutdoorsman said:**
> By default the version of ffmpeg from the repository requires installation of an additional package to enable more encoders, such as *libmp3lame*, the MP3 encoder. See **Option B** here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

It is f-up 
broken package and can't install libavcodec52... 
E: /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_i386.deb: trying to overwrite '/usr/share/ffmpeg/libx264-baseline.ffpreset', which is also in package ffmpeg 4

---

### Post by FakeOutdoorsman on 2012-01-20
Can you provide your command and the complete terminal output?

---

### Post by Azyx on 2012-01-20
> **FakeOutdoorsman said:**
> Can you provide your command and the complete terminal output?

I'm stupid. I read wrong instrutions on making support for 10.04LTS. I used the 10.10 way, but for 10.04 there should bee support from the beguinning, cos you only need to install ffmpeg.

I made a .ogg file from my 600MB file and it works fine. /Cheers

---

### Post by Azyx on 2012-01-20
> **FakeOutdoorsman said:**
> Can you provide your command and the complete terminal output?

The hole system are broken. when I try to install vlc to play movies it says:

E: /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_i386.deb: trying to overwrite '/usr/share/ffmpeg/libx264-baseline.ffpreset', which is also in package ffmpeg 4

---

### Post by FakeOutdoorsman on 2012-01-20
Can you provide your command that you used to attempt to install VLC and the complete terminal output that shows up when you attempt to install VLC?

---

### Post by Azyx on 2012-01-21
> **FakeOutdoorsman said:**
> Can you provide your command that you used to attempt to install VLC and the complete terminal output that shows up when you attempt to install VLC?

I'm really sorry. Everything is very strange I think the problem was what then I installed the newer ffmpeg-package 'libavcodec-extra-53 instead off 52 (for 10.04), that was in the way for everything with ffmpeg in the name. After that I get broken package in Synaptic. I Try to uninstall all with codecs 52 and 53 and VLC dissapear. I installed VLC again but when I ran VLC it says something that VLC could not play XVID!!!, and I could not do anything about it. I think Ubuntu did something radical between 8.04-->10.04 according propretarian codec. Look for example, the support about solution fore some propretarian drivers and Ubuntu cripplrd the ffmpeg package. I have upgraded before from 8.04LTS --> 10.04LTS. See for example under C in this link. [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283). Now I don't have any brokened packade anymore in synaptic. I have never since Windows had any problems with codecs, but the solutions was easier here, than in windows. This reply take much longer to whrigt than fix the problem that was totally remove everything with ffmpeg, and then install things after. By the way, after removing ffmpeg, 'The movie player' was not able to play XVID ether, but find plugin automagically, by I self.
Maybe, I'm not able to encode mp3, but I don't care. ogg worked fine for my purpuse (the silent 1 hours wav-file on 600MB get about 100kB as ogg with the sound converter.

/Cheers

---

