---
title: "FFMPEG -- DTS to flac mapping channels help"
date: 2010-09-13
forum: Multimedia Software
---

### Post by jimmah6786 on 2010-09-13
Hello, I am trying to DTS to flac(or even ac3)....however I know I can do it with FFMPEG and I have using basic parameters, however does anyone know if you need to supply FFMPEG with the audio channel layouts....

I found this 
5.1 WAV FL , FR , FC , LFE, SL , SR
5.1 AC3 FL , FC , FR , SL , SR , LFE
5.1 DTS FC , FL , FR , SL , SR , LFE
5.1 AAC FC , FL , FR , SL , SR , LFE
5.1 AIFF FL , SL , FC , FR , SR , LFE 

SO Clearly each codec is different in how it arranges the channels....

For example if I wanted to do DTS to AC3, it looks based on this chart that I would have to input the audio channel layout manually.

Anyone have any success with something similar?

---

### Post by jimmah6786 on 2010-09-13
> **jimmah6786 said:**
> Hello, I am trying to DTS to flac(or even ac3)....however I know I can do it with FFMPEG and I have using basic parameters, however does anyone know if you need to supply FFMPEG with the audio channel layouts....

I found this 
5.1 WAV FL , FR , FC , LFE, SL , SR
5.1 AC3 FL , FC , FR , SL , SR , LFE
5.1 DTS FC , FL , FR , SL , SR , LFE
5.1 AAC FC , FL , FR , SL , SR , LFE
5.1 AIFF FL , SL , FC , FR , SR , LFE 

SO Clearly each codec is different in how it arranges the channels....

For example if I wanted to do DTS to AC3, it looks based on this chart that I would have to input the audio channel layout manually.

Anyone have any success with something similar?

Found the mapping on flac documentation site.
LF, RF, FC, LFE, SL, SR

So the mappings are entirely different then DTS's...does anyone know how to manually pass the new mapping to ffmpeg

---

### Post by ron999 on 2010-09-13
Hi
I think that this mapping is OK:-
```
ffmpeg -i foo -map 0:1 -map 0:2 -map 0:0 -map 0:5 -map 0:3 -map 0:4 foo.flac
```
Though you may need to insert your 'basic parameters'.

---

### Post by jimmah6786 on 2010-09-13
> **ron999 said:**
> Hi
I think that this mapping is OK:-
```
ffmpeg -i foo -map 0:1 -map 0:2 -map 0:0 -map 0:5 -map 0:3 -map 0:4 foo.flac
```
Though you may need to insert your 'basic parameters'.

I thought that -map parameter was used for mapping multiple tracks inside the container, like 2 DTS tracks.

---

### Post by ron999 on 2010-09-13
> **jimmah6786 said:**
> I thought that -map parameter was used for mapping multiple tracks inside the container, like 2 DTS tracks.

Maybe you're right.
There's only one way to find out.:D

---

### Post by mc4man on 2010-09-13
> if you need to supply FFMPEG with the audio channel layouts....
It doesn't appear you'd need to (used several different 5.1 surround test files for ac3 and dts, all came out correct as flac and or wav

---

### Post by jimmah6786 on 2010-09-14
> **mc4man said:**
> It doesn't appear you'd need to (used several different 5.1 surround test files for ac3 and dts, all came out correct as flac and or wav

Cool I'll have to try it out. Thanks all!

---

### Post by cascade9 on 2010-09-14
Might as well leave DTS files as DTS files, not bother with conversions. Unless its DTS-HD, DTS is lossy......not much point converting a lossy codec to lossless in most situations.

---

