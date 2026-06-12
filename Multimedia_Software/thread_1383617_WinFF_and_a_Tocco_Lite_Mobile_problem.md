---
title: "WinFF and a Tocco Lite Mobile problem"
date: 2010-01-17
forum: Multimedia Software
---

### Post by Naiki Muliaina on 2010-01-17
Okis, i have a Tocco Lite mobile that can play back MP4's and 3GP's i have downloaded from the net. It can play all the 512kb films from archive.org. What it cant seem to play is anything i convert into 3gp or mp4. 

I am using Ubuntu Karmic with WinFF. I use the following template :

```
    <label>3GPP H.264 320x240 4:3 AAC stereo</label>
    <params>-r 15 -b 128kb -s 320x240 -ar 22050 -ab 64kb -acodec libfaac -vcodec libx264 -coder 1 -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me_method hex -subq 6 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -b_strategy 1 -threads 0</params>
    <extension>3gp</extension>
    <category>Mobile Phones</category>
```

When i try to play them on the Tocco Lite it gives me the following error message :

```
Unsupported media or bit rate over
```

Can anyone tell me what im doing wrong? Thankies in advance! :)

---

### Post by SuperSonic4 on 2010-01-17
I don't have a Tocco Lite but the Tocco doesn't like h264 encoded videos so I always use mpeg4 and aac audio

What happens if you run (from the CLI) ```
ffmpeg -i *input.avi* -vcodec mpeg4 -b 128kb -s 320x240 -ar 22050 -ab 64kb -acodec libfaac output.3gp
```

I guessed yours was avi but it's largely irrelevant on the input type, just use it's actual extension

I use something similar (but better audio) on my phone

---

### Post by Naiki Muliaina on 2010-01-17
Brilliant, thankies it worked. :)

For anyone using WinFF GUI the preset is below. 

```
<?xml version="1.0"?>
<presets>
  <MP3GP320x240stereo43>
    <label>3GPP Tocco</label>
    <params>-vcodec mpeg4 -b 128kb -s 320x240 -ar 22050 -ab 64kb -acodec libfaac</params>
    <extension>3gp</extension>
    <category>Mobile Phones</category>
  </MP3GP320x240stereo43>
</presets>
```

---

### Post by tonyuk123 on 2010-01-23
i'm having exactly the same problem
i have done what is said here
but i get the error saying mpeg4 is unknown format
any ideas?

---

### Post by paul.gevers on 2010-01-25
> **tonyuk123 said:**
> i'm having exactly the same problem
i have done what is said here
but i get the error saying mpeg4 is unknown format
any ideas?

ffmpeg error? Then you probably need to install libavcodec-unstripped-51 or libavcodec-unstripped-52 or libavcodec-extra-52 depending on which version of Ubuntu you are running.

---

### Post by Dai777 on 2010-03-05
Have you got Tocco lite to work in karmic if so how?
IT does not even recocnise my phone. zilch, nada, absolutely nothing.

any info on how to get teh Tocco lite working with karmic would be appreciated.

---

### Post by Naiki Muliaina on 2010-03-10
If your talking about how to put stuff onto your phones memory, on you phone got to Settings > Phone Settings > PC Connections > Select Mass Storage and save. Connect it to a PC and the PC will assume your phone is just a memory card. On ubuntu when you plug your phone into your PC it should just pop up a nautilus window for you.

---

### Post by Dai777 on 2010-03-10
> **Naiki Muliaina said:**
> If your talking about how to put stuff onto your phones memory, on you phone got to Settings > Phone Settings > PC Connections > Select Mass Storage and save. Connect it to a PC and the PC will assume your phone is just a memory card. On ubuntu when you plug your phone into your PC it should just pop up a nautilus window for you.

cheers woks great

---

### Post by webdevelopment on 2010-10-01
looking for a mpeg4 full HD preset

---

