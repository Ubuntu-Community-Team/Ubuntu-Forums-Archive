---
title: "Audio Recording Sampling Rate"
date: 2012-04-19
forum: Multimedia Software
---

### Post by ITPhoenix on 2012-04-19
[SIZE=2]I need to record a WAV sound file at 16 bit, 32kHz. My question is if my audio card does not support this combination, say the minumum sampling rate was 44.1kHz on the card specs, will any of the recorders available in Ubuntu somehow produce the desired results?[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]At any rate, is there a consensus as to what recorder is best? That is, the least problems.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Any pointers will be appreciated. Links to sites/pages would be welcomed.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Thanks.[/SIZE]

---

### Post by shantiq on 2012-04-20
i personally find command line SoX to cater to all microphone recordings


```
sudo apt-get install sox libsox-fmt-all

```



```
rec -c 6 -r 96000 -b 24  recording.wav

```

-r 96000    is where you tinker with sample rate   set it to what you want
-c   is for number of channels
-b   bit for bit as in  8-bit 16-bit 24-bit 32-bit 64-bit

```
rec  -C 320  nameyouwant.mp3

```



more info [here]("http://ubuntuforums.org/showpost.php?p=10565567&postcount=2")

---

### Post by ITPhoenix on 2012-04-20
Thanks.  The time has come to move away from GUI dependence as I need to write scripts and modify programs.  It reminds me of arecord which is an ALSA application.  I do not have Xubuntu installed yet, yet I recall fiddling with arecord on openSUSE.
 
I am not looking forward to audio since I had so much trouble in the past with the Creative drivers and buggy SUSE/KDE.  Moreover, Linux sound literature disjointed and confusing to me.
 
The reason I emphasized the recording rates is, in speech recognition, recording of adaptation files is so critical that if the files are not in the precise format and rates, the application will not work and I would have to go through the entire arduous procedure from scratch.  Moreover, I would be wasting my money on a card that will not serve my purposes.  
 
I worry that SOX may not complain about the disparity between my command line switches and the card's capabilites, and record at higher sampling rate.

---

### Post by shantiq on 2012-04-20
> I worry that SOX may not complain about the disparity between my command line switches and the card's capabilites, and record at higher sampling rate.


if you set your -r switch to what you know are your card's capabilities surely that has to be a perfect match:KS:KS if i understand your concerns

---

### Post by ITPhoenix on 2012-04-20
Thank you very much.  Now that were on this, here is something else that is cryptic to me.  Here is the full spec:
> Recordings must be 16khz 16bit mono files in MS WAV format with a single channel
What is a "channel" in this context?  I once considered one of the two sides of a stereo tape a "channel" or "track".
 
Mono is already indicated so we know it cannot be stereo.  Perhaps it refers to only one mono source, instead of, say, a stereo mic input blended into mono?  I do know the waveform output of two transducers (mics in this case) is very rarely in perfect syncronization given a single input.

---

### Post by shantiq on 2012-04-20
ok so

> Recordings must be 16khz 16bit mono files in MS WAV format with a single channel


let us translate into sox speak  :KS:KS   one channel[mono]two would be stereo sample rate 16000hz 16bit   MS stands for Microsoft who designed WAV

So  this here is your line


```
[SIZE="3"][FONT="Franklin Gothic Medium"]rec -c 1 -r 16000 -b 16  recording.wav  gain +10[/FONT][/SIZE]

```


you end up with a good quality voice recording in mono sound   you can add volume if you wish by adding gain +10 at the end  play with number to suit your needs or remove [depending on quality of your mike]


to play back    enter   > play recording.wav


you will then see the specs you have created


> rec -c 1 -r 16000 -b 16  recording.wav

Input File     : 'default' (alsa)
Channels       : 1
Sample Rate    : 16000
Precision      : 16-bit
Sample Encoding: 16-bit Signed Integer PCM

In:0.00% 00:01:00.93 [00:00:00.00] Out:967k  [      |      ]        Clip:0    ^Z
[5]+  Stopped                 rec -c 1 -r 16000 -b 16 recording.wav
shantiq@shantiq-00000000000000000000000:~$ play  recording.wav

recording.wav:

 File Size: 1.95M     
  Encoding: Signed PCM    
  Channels: 1 @ 16-bit   
Samplerate: 16000Hz      
Replaygain: off         
  Duration: unknown      

In:0.00% 00:01:00.93 [00:00:00.00] Out:975k  [      |      ]        Clip:0    
Done.


---

### Post by BicyclerBoy on 2012-04-20
AFAIUI the uncompressed PCM WAV file format supports channel number from 1 to 2^16-1.

A 2 channel WAV file is stereo.
Multi-channel (>2) WAV files have ambiguous channel mapping.

A mono recording can be stored as 2 channel WAV file..

An alsa utils cmd line to record mono little-endian wav from mic:
arecord -r 16000 -f S16_LE -c 1 -D plughw:0,0 -t wav dummy.wav

recording from plughw device enables automatic sample rate & format conversion..

---

### Post by ITPhoenix on 2012-04-20
I see.  I went to the ALSA programming page because I did not know what "plughw" was.  Their claim is the format will be converted with this spec.  I have read you cannot go up from the card's capabilities, e.g, a 96kHz recording from a 48khz max card.  I trust we can go down, which makes sense.  
 
As far as little-endian, I was under the belief WAV is little-endian and cannot be changed.  I need to make sure of all of these things because big-endian will not work with my app, for example.
 
Thank you very much everyone for input!

---

### Post by BicyclerBoy on 2012-04-20
The intel windows world is/was little-endian & WAV is a microsoft format.
The -f S16_LE setting might be redundant..
The WAV format was built on pre-existing formats developed for the Amiga etc. The Amiga & Mac were both Motorola 68000 family (big endian).

I would be surprised if plughw device did not allow up-sampling..
The quality might not be good.
My rubbish netbook can record at 192KHz on hw:0,0.

There is a re-sampling library for alsa & can be configured for very hiQ resampling, this can consume a lot of CPU cycles..

Pulse audio can be configured to re-sample at many different quality settings.

Install the program "mediainfo" if you want to be absolutely sure what you are creating..

---

### Post by ITPhoenix on 2012-04-20
Thanks.   I have to go down in quality so it should be alright. The ASUS Xonar DGX's minimum sampling rate at 16 bits is 44.1.  Low end card, but lousy onboard does not work with speech recognition.  I am looking forward to moving away from Creative, too.
 
Awesome pointer with the mediainfo.  Now I can be sure what was laid down.  Ubuntu specific download, too.

---

### Post by VanillaMozilla on 2012-04-20
Did you try Audacity?  A very good program, and there's a simple dropdown box on the lower left for sampling rate.  That might be a very simple solution.  Just select sampling rate and press the Record button.

---

### Post by ITPhoenix on 2012-04-21
I tried Audacity with SUSE and had trouble.  It conflicted with another program, and crashed the system.  Audacity was convenient and it did work, however.  I need to move away from GUIs and keep the system as simple as possible, by necessity.  Linux is not like Windows when it comes to audio. There we simply throw the card in and click away on say all the Creative bells and whistles, if we wish, and it always works.   It has its place, and Linux has its own place.  Windows is not a good platform for what I am doing.
 
Thank you for your input.

---

### Post by VanillaMozilla on 2012-04-23
Crashed the system?  Don't you hate it when it happens?

I can only suggest you try it on Ubuntu.  I haven't had any problems at all with recent versions.  Who knows, it might have been built on demented dependencies?  I really think it's worth another try.  You really might be surprised.

---

### Post by ITPhoenix on 2012-04-23
True indeed. SUSE was buggy. I was also installing/uninstalling other audio-related ware.

---

