---
title: "HELP!! I have problems encoding audio files!"
date: 2010-09-15
forum: Multimedia Software
---

### Post by Br1987 on 2010-09-15
[SIZE=2]Hi, mi name is Bruno and I'm from Peru...I'm new to Linux and Ubuntu so I'm facing a couple of troubles when trying some things... for example: When I use "Sound Converter" and try to encode to MP3 at 128Kbps te result is not what I expected... at the file's properties I found out that it is at 48Kbps and not at 128Kbps as I first wanted... but when listening to the converted MP3 file, it does not sound as if it were a 48Kbps sample... you know what I mean?? so I checked in my brother's PC (it has Windows XP Pro) and the converted file turned out to be 320Kbps!!... so I start trying with all the possible encoding options that "Sound Converter" has.... but I ended up having similar results ... there's something I'm doing wrong??[/SIZE]
P.S.: I also tried "SoundKonverter" but there's no result at all!! the MP3 encoded file does not sound!! :confused:

---

### Post by prshah on 2010-09-15
> **Br1987 said:**
> [SIZE=2]When I use "Sound Converter" and try to encode to MP3 at 128Kbps te result is not what I expected

48Kbps and not at 128Kbps

Windows XP Pro) and the converted file turned out to be 320Kbps


Sound Converter converts to vbr (variable bit rate) 320kbps by default. Are you looking for cbr (constant bit rate) 128kbps conversion? Try the following command to set this mode```
gconftool --type string --set /apps/SoundConverter/mp3-mode cbr
gconftool --type integer --set /apps/SoundConverter/mp3-cbr-quality 128
```

Note this will permanently change SoundConverter settings!

Please post back with your results.

---

### Post by ghostborg on 2010-09-15
Or you could just go to Sound Converters Edit menu and select Preferences and adjust the Format Bitrate and Quality settings.

Example:
Format: MP3(.mp3)
Bitrate mode: Constant(CBR)
Quality: Normal

On my system Normal gives me a Target bitrate of 128 kbps.

---

### Post by Br1987 on 2010-09-20
DAMN!! you guys are awesome!! :guitar: It worked like a charm!!
Hey sorry about the late reply... the thing is that I was not notify when you replied to my comment! (5 days ago!) so... how can I set the options on this forum to notify me anytime someones replies to my post??!! 
sprry... I'm really new =P

---

### Post by ron999 on 2010-09-20
> **Br1987 said:**
>  so... how can I set the options on this forum to notify me anytime someones replies to my post??!! 


Look near the top ...
It says in red [COLOR="Red"]_**Thread Tools**_[/COLOR]
Then
> Subscribe to this thread 
> Instant notification by email 
> Add subscription

:guitar:

---

### Post by Br1987 on 2010-09-22
thanks man... I did it already... and the problem with the audio files is fine now... I guess it is time to mark this thread as solved... right?? Thx again for your awesome support!! :KS

---

