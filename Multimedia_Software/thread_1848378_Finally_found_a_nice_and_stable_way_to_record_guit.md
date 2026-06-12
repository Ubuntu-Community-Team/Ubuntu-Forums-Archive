---
title: "Finally found a nice and stable way to record guitar and voice..."
date: 2011-09-22
forum: Multimedia Software
---

### Post by shantiq on 2011-09-22
Been on ubuntu a couple of years now and as i write music on midi and also record live instruments and voice i have had a good look around


As regards midi Rosegarden ( with a fairly complex learning curve ) has really catered for that side of things


As regards live miked voice and electro-acoustic guitar i never had really found a nice and easy way    Ardour is good and as recording tool Audacity is a nightmare for me as regards external cards and such


So let me share this "happy" recipe


I use a Lexicon Alpha box to plug in mike and electroacoustic jack   ( but of course that is not the question here )



1.  using sox really works well here

i pick a high quality set up ( but can all be reduced to suit tastes )  6 channels because i might as well 96 kHz because if i go to 192 kHz it does not play back so well on my system
and 24-bit because it sounds so much better than 16-bit


```
 rec -c 6 -r 96000 -b 24  recording.wav 

```



2.  Then comes in Audacity; which as an **editing** tool is ace   

open the recording.wav here and pick view/collapse all tracks
then effect/ amplify to correct volume
maybe add filters if you like that   ( i personally usually do not )

3. export as flac 24-bit


I find this combination of SoX and Audacity to be fine this way.  Light easy to use programs.  Might be refreshing to you if you have struggled with more complex programs and leaves you with a high quality file.

---

### Post by perspectoff on 2011-09-22
> **shantiq said:**
> Been on ubuntu a couple of years now and as i write music on midi and also record live instruments and voice i have had a good look around


As regards midi Rosegarden ( with a fairly complex learning curve ) has really catered for that side of things


As regards live miked voice and electro-acoustic guitar i never had really found a nice and easy way    Ardour is good and as recording tool Audacity is a nightmare for me as regards external cards and such


So let me share this "happy" recipe


I use a Lexicon Alpha box to plug in mike and electroacoustic jack   ( but of course that is not the question here )



1.  using sox really works well here

i pick a high quality set up ( but can all be reduced to suit tastes )  6 channels because i might as well 96 kHz because if i go to 192 kHz it does not play back so well on my system
and 24-bit because it sounds so much better than 16-bit


```
 rec -c 6 -r 96000 -b 24  recording.wav 

```



2.  Then comes in Audacity; which as an **editing** tool is ace   

open the recording.wav here and pick view/collapse all tracks
then effect/ amplify to correct volume
maybe add filters if you like that   ( i personally usually do not )

3. export as flac 24-bit


I find this combination of SoX and Audacity to be fine this way.  Light easy to use programs.  Might be refreshing to you if you have struggled with more complex programs and leaves you with a high quality file.

Isn't flac for AAC, the proprietary Apple format? I could be wrong...

---

### Post by shantiq on 2011-09-22
hi there Perspectoff


flac is different it is a lossless format so you can return to the full original wav file

[**aac**]("http://en.wikipedia.org/wiki/Advanced_Audio_Coding") is apple also goes under m4a extension and is lossy
with aac you cannot go back to full file with all original data


therefore i suggest [**flac**]("http://en.wikipedia.org/wiki/Free_Lossless_Audio_Codec") as a good way to store music.  


==================================================


 [** Alac**]("http://en.wikipedia.org/wiki/Alac") might be the one you mean it is lossless AND Apple


lossy formats are fine for a portable music player   but these days with external drives lossless makes a lot of sense for music on a computer even with many albums



=======================================


Just found out alac is now available in ffmpeg for decoding which it was before but **[also]("http://ubuntuforums.org/showthread.php?p=11276181#post11276181")** for encoding

---

### Post by shantiq on 2011-10-04
> **shantiq said:**
> Been on ubuntu a couple of years now and as i write music on midi and also record live instruments and voice i have had a good look around





1.  using sox really works well here

i pick a high quality set up ( but can all be reduced to suit tastes )  6 channels because i might as well 96 kHz because if i go to 192 kHz it does not play back so well on my system
and 24-bit because it sounds so much better than 16-bit


```
 rec -c 6 -r 96000 -b 24  recording.wav 

```



2.  Then comes in Audacity


**Actually a nice refinement** might be to use sox INSTEAD to up the sound and maybe add reverb onto a freshly recorded piece

this will do it

```
sox  filename.wav  -C 10 -V6 filename.ogg  gain  +28   reverb +20
```      

Convert your file from wav to ogg [as it can handle/retain six channels 24-bit and high kHz] at 499kbps
with a lot of increase in the volume and added reverb    [change numbers to suit]

---

### Post by Clito on 2012-12-03
Shantiq

I can see it's been a while since you opened this thread (thank you for sharing this info), but I've been looking around and you seem to be one of the few that could help me out.  

I use a Lexicon Alpha for recording as well, but I can't make it play midi files (no sound :confused:). It all works OK but that one thing, and I don't really know what to look for to make it work. I think the system is not using the Lexicon sound card as a midi device, but I can't really tell, and I don't see where to change that in the sound settings screen or in Jack. Just to make it clear, I get no sound from media players, tablature editors or any other application using midi.

I'm not asking you to write me a tutorial on how to fix it, but I would really appreciate it if you could at least tell me what I need to look for. I'll sure be able to fix it sooner or later.


Thank you in advance!

---

### Post by shantiq on 2012-12-03
with midi you may need to run    ```
timidity -iA
```   first



> timidity 
TiMidity++ version 2.13.2 -- MIDI to WAVE converter and player



you get this


> timidity -iA
Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3




then link to one of the ports

see if that helps


[i use this with Rosegarden for midi composition and the sound is out through Alpha Lexicon]

---

### Post by silverhaze06 on 2012-12-07
What I do is interface Ardour with a Zoom H4n recorder. Works fine, and with an interface you can use real quality mics with quality preamps.

---

