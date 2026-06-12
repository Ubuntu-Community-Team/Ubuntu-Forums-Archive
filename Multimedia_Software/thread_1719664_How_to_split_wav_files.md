---
title: "How to split wav files"
date: 2011-04-02
forum: Multimedia Software
---

### Post by bill-lancaster on 2011-04-02
Can anyone show me how to split wav files from the command line?

---

### Post by andrew.46 on 2011-04-02
sox will do this for you using the *trim* option. For example I use sox below to extract the first minute of my test wav file:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]sox test.wav 60secs.wav --show-progress trim 0 01:00[/COLOR]**

Input File     : 'test.wav'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:02:01.28 = 5348352 samples = 9095.84 CDDA sectors
File Size      : 21.4M
Bit Rate       : 1.41M
Sample Encoding: 16-bit Signed Integer PCM

In:49.5% 00:01:00.00 [00:01:01.28] Out:2.65M [!=====|=====!]        Clip:0    
Done.

```

Andrew

---

### Post by bill-lancaster on 2011-04-02
Andrew - works a treat, thank you.

---

### Post by andrew.46 on 2011-04-02
> **bill-lancaster said:**
> Andrew - works a treat, thank you.

Excellent :). FFmpeg will do the same but I have always found that sox is a better tool for smaller tasks such as this...

---

### Post by shantiq on 2011-04-02
> **andrew.46 said:**
> Excellent :). FFmpeg will do the same but I have always found that sox is a better tool for smaller tasks such as this...



I had never thought of using ffmpeg just for that Andrew but yes really good too:KS


```
ffmpeg -i 101Morning-Glory.wav -ss 00:00:00 -t 00:05:00  -acodec copy 101Morning-Glory_5_minutes.wav
```

-ss is for start time   -t is for duration

---

### Post by danieleverywhere on 2012-05-17
I discovered the tool "wavbreaker" as very convenient

---

