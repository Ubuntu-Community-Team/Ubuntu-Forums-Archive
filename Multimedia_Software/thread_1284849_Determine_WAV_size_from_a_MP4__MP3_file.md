---
title: "Determine WAV size from a MP4 / MP3 file"
date: 2009-10-07
forum: Multimedia Software
---

### Post by clausfod on 2009-10-07
Hi,

Is there anyway of determining the size of a wav file before converting it from mp3/mp4 ?

Claus

---

### Post by pmlxuser on 2009-10-07
from experience, the size of wav is approcmately 10x size of mp3/mp4 

so mathematically & & hypotheiticall

{
int size_wav //size of wav file
int size_mp //size of mp3 or mp4
size_mp=size_of_file()//somefunction of determining size of mp3/mp4
size_w=size_mp*10;
}

---

### Post by clausfod on 2009-10-07
Hi pmlxuser,

Thanks for your reply :-)

> from experience, the size of wav is approcmately 10x size of mp3/mp4 

I can see that K3b uses an algoritm for this which is close to 10x - but only close :-( Can anyone give me a more accurate solution for determine wav sizes ?

Regards
Claus

---

### Post by ron999 on 2009-10-07
> **clausfod said:**
> Can anyone give me a more accurate solution for determine wav sizes ?

The size of the wav file depends on the duration of the file.
It's approximately 10MB per minute.
So a 3 minute mp3 file will be approximately 30MB when converted to wav.

---

### Post by Chronon on 2009-10-07
WAV:
16 bit stereo PCM @ 44.1 kHz sampling rate gives
(16 bits)*2*(44100 /s) = 1411.2 kbps

Using mono or a different sampling rate will modify the calculation.

(note that the k here is 10^3 rather than 2^10 -- i.e. kilo rather than kibi)

---

### Post by Bachstelze on 2009-10-07
> **ron999 said:**
> The size of the wav file depends on the duration of the file.
It's approximately 10MB per minute.

It also depends on the bit-depth and sampling rate. For a standard two-channel, 16-bit PCM stream with 44.1kHz sampling rate, the resulting bitrate will be 2*16*44.1 = 1411.2kbps, which is exactly 1411.2*60/8 = 10.584 MB per minute.

---

