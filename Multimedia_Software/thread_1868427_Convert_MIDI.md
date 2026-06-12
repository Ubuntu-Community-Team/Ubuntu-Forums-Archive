---
title: "Convert MIDI"
date: 2011-10-24
forum: Multimedia Software
---

### Post by howlerbr on 2011-10-24
What program can I use to convert a MIDI format 1 to MIDI format 0.

I have an YAMAHA keyboard and it accepts only MIDI format 0 so I can use it for the lessons.

In Windows there are some converters but I'm looking a Linux solution for it.

Thanks!

---

### Post by shantiq on 2011-10-25
hi there   timidity is the program you want to convert to wav flac or aiff


install thus   ```
 sudo apt-get install timidity
```

full info

```
man timidity

```

```
NAME
       TiMidity++ - MIDI-to-WAVE converter and player

SYNOPSIS
       timidity [options] filename [...]

DESCRIPTION
       TiMidity++  is  a converter that converts some of MIDI files (supported formats:
       Standard MIDI files (*.mid), Recomposer files (*.rcp, *.r36, *.g18,  *.g36)  and
       Module  files  (*.mod)) into formatted audio files (e.g. RIFF WAVE).  TiMidity++
       uses Gravis Ultrasound-compatible patch files or Soundfonts  (*.sfx,  *.sf2)  to
       generate  digital  audio data from MIDI files.  The digital audio data generated
       by TiMidity++ can be stored in a file for processing, or  played  in  real  time
       through an audio device.
       In  real  time  playing,  TiMidity++ can show the lyrics contained in KAR or WRD
       files.
```


**examples**


```
timidity filename.mid -Ow -o filename.wav
```   basic midi to wave 16-bit


```
timidity filename.mid -OF -o filename.flac
```   basic 16-bit to flac


```
timidity --output-24bit -A120 filename.mid -Ow -o filename.wav

```       to wave 24-bit with sound hiked up one fifth

or same ```
 timidity  -A120 filename.mid -OF2 -o filename.flac  
```   to flac



**more options**

```
Available output modes (-O, --output-mode option):
  -Od          dsp device
  -Os          ALSA pcm device
  -Oe          Enlightened sound daemon
  -Oj          JACK device
  -On          Network Audio Server
  -Ow          RIFF WAVE file
  -Or          Raw waveform data
  -Ou          Sun audio file
  -Oa          AIFF file
  -Ov          Ogg Vorbis
  -OF          FLAC / OggFLAC
  -Ol          List MIDI event
  -OM          MOD -> MIDI file conversion

Output format options (append to -O? option):
  `S'          stereo
  `M'          monophonic
  `s'          signed output
  `u'          unsigned output
  `1'          16-bit sample width
  `2'          24-bit sample width
  `8'          8-bit sample width
  `l'          linear encoding
  `U'          U-Law encoding
  `A'          A-Law encoding
  `x'          byte-swapped output

Alternative output format long options:
  --output-stereo
  --output-mono
  --output-signed
  --output-unsigned
  --output-16bit
  --output-24bit
  --output-8bit
  --output-linear
  --output-ulaw
  --output-alaw
  --[no-]output-swab

```


================================================


**PS   **

 there is also a gui that will play your midi files in ubuntu


install  ```
 there is also a gui that will play your midi files in ubuntu
```    and start


```
timidity -ig
```   or create a launcher on desktop

right-click on desktop/create launcher etc...

---

### Post by shantiq on 2011-10-25
sorry than i reread your question and saw i had misunderstood your request



will leave info here anyway as may help someone else.  Sorry


========================

reading the timidity manual it says

```
Input File

TiMidity++ can handle the following file formats:

[B].mid, .rmi (Format 0, 1, 2)
[/B]Standard MIDI File
.rcp, .r36, .g18, .g36 (Recomposer formats)
Recomposer format which is product for COME ON MUSIC co.
.mfi (MFi Version 3 - Melody Format for i-Mode)
i-Mode is Japanese local mobile phone
.kar (Karaoke format)
Displays the lyrics as a Lyric Meta Event message.
.mod, mod.* (Module file)
.wrd (WRD format)
```



so you want to turn a mid into a rmi ?    looking around there does not seem to be a linux solution but hopefully i will be proved wrong

---

### Post by satanselbow on 2011-10-25
midi 0/1 converter: [http://midicomp.opensrc.org/](http://midicomp.opensrc.org/)

found here: [http://linux-sound.org/one-page.html#midi](http://linux-sound.org/one-page.html#midi)

---

