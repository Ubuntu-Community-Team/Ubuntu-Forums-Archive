---
title: "Command for converting large music file from mp3 to WAV"
date: 2012-10-17
forum: Multimedia Software
---

### Post by dmahoon on 2012-10-17
Hi People,

I've got about 50G of mp4 music files that I would like to convert to WAV.  I know this will take up a lot of space but I'm ok with that.  I know Linux is very powerful and that a single command would probably do the trick with the entire file.

I have found a few threads with commands to convert from WAV to mp4 but nothing to go the other way.....at least nothing recent.

Any tips would be most appreciated.

Patrick

Ubuntu 12.04 64bit
Mini itx homebuild
Asus P8H77-I motherboard
Intel Core i3 processor
2x4gb Gskill Ares RAM
Seagate 500gb Hard Drive

---

### Post by shantiq on 2012-10-18
well you can do this easily Patrick   but mp3/mp4 is a lossy format and therefore what you will end up with will be a "fake" wav   ie   a wav with a lossy file inside 


did you mean mp3 or mp4 ?    anyway works for both   just change accordingly


now the only reason i see to want to do that is that you want to burn cds


Anyway your decision    but if you explain what you are doing this for there might be other ways/formats


**anyway  ** answering your question

go into your Music Folder  > cd Music [if that is where your 50 Gb are]


enter all folders WITH THIS COMMAND turn mp3 to wav and delete mp3.... [copy as one block in terminal]

```

for i in */
do
  cd "$i"
for f in *.mp3; do ffmpeg -i "$f" "${f%.mp3}.wav"; done [COLOR="Red"]&& rm *.mp3[/COLOR]
  cd ..
done
```


the bit in red only use if you want to delete the original mp3 otherwise [COLOR="Red"]**DO NOT**[/COLOR]

---

### Post by dmahoon on 2012-10-18
Hi Shantiq,

Thanks for replying!  

Basically I've been reading a lot about the quality of compressed music files and found that the WAV format is the best for high quality listening on high quality equipment(which I am lucky enough to have).  The problem is that I have copied all of my music over the past few years onto my computer  (for my ipod) using itunes which has ok quality but not great quality.  Now I want to convert them all back with one command.  

But as you've mentioned this will create a 'fake' WAV format which may not be what I'm after.  I'll do some experimenting with some individual files and see what the difference in sound quality is.

I'm still very new using the command terminal so once again thanks for your guidance.

Patrick

---

### Post by Lars Noodén on 2012-10-18
The sound quality will be the same or worse.  You can't replace the information that was lost during the high compression that made the MP3s.  If you had ripped straight to FLAC or WAV, then you would have higher sound quality.  If the sound quality is very important to you, you will have to re-rip to FLAC or WAV but starting from MP3 is a lost cause.

---

### Post by Yellow Pasque on 2012-10-18
itunes is probably ripping to AAC (inside an mp4/m4a container). You should rip a few CD's to FLAC/WAV and give yourself a blind listening test to see if you can tell the difference. Depending on your ears and audio equipment, it may not be worth the time/effort to rip everything again (though I would recommend ripping to FLAC from now on).

---

### Post by TGamel on 2012-10-18
> **Lars Noodén said:**
> The sound quality will be the same or worse.  You can't replace the information that was lost during the high compression that made the MP3s.  If you had ripped straight to FLAC or WAV, then you would have higher sound quality.  If the sound quality is very important to you, you will have to re-rip to FLAC or WAV but starting from MP3 is a lost cause.

I agree, think of WAV format as a kind of like the RAW format when shooting pictures. You will get the most dynamic sound experience in the original WAV format. MP3 compresses the sound to make it smaller and you lose some sound quality in order to make the file smaller. 

Just as when you take a picture that is shot in RAW format vs JPEG. The RAW file is quite a bit larger but has a more dynamic range of attributes that can by manipulated. Once a RAW picture has been compressed it loses some of the bits during compression that cannot be recovered.

For the best sound or picture quality you should always RIP your files in the WAV format and shoot pictures in the RAW format. You can always compress them later, but once the compression is done you cannot get back those pieces that were lost due to compression. Yes you can convert an MP3 back to a WAV format, but the initial dynamic lose of sound cannot be recovered and the WAV conversion will never be as good as the original.

Of course, some of us old guys cannot tell the difference between a good MP3 and a good WAV....:P

Todd

---

### Post by shantiq on 2012-10-18
well if that is the situation Dmahoon


> Basically I've been reading a lot about the quality of compressed music files and found that the WAV format is the best for high quality listening on high quality equipment(which I am lucky enough to have)



you simply cannot do that as the other guys have explained


mp3   goes to 320 kbps     and wav   or cda when it is in a cd   is 1411kbps

so you are left with a fraction of the original info


to rerip to flac would be your best option here


failing that if you have 320kbps  mp3   it ain't that bad at all   soundwise


**my advice is keep what you have** as it is   and from now on rip to flac [which is lossless=ALL INFO FROM CD IS KEPT]   UNLESS you have the originals and the patience to rerip them


=====================================


as regards old guys not being able to tell the difference between mp3 and wav


my latest discovery [i am always late at the party] is  **[HE-AACv2]("http://ubuntuforums.org/showpost.php?p=12279533&postcount=2")**    and at 38k  [you read correctly**!!**]   i personally [and i have bat ears]  cannot distinguish it from a flac


have [**a test **]("http://ubuntuone.com/0qZoEnxTrJiMzDvcAS8Vvi")for yourself   from 22MB to 1.7 MB   [composed entirely on Linux Rosegarden]


flac file ```
mediainfo 'élucubrations.flac'
General
Complete name                            : élucubrations.flac
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
File size                                : 22.0 MiB
Duration                                 : 5mn 48s
Overall bit rate mode                    : Variable
Overall bit rate                         : 530 Kbps
Performer                                : shantiq
Recorded date                            : 2012
Writing application                      : Lavf54.25.105
Cover                                    : Yes
Cover description                        : Enter description
Cover type                               : Cover (front)
Cover MIME                               : image/png

Audio
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
Duration                                 : 5mn 48s
Bit rate mode                            : Variable
Bit rate                                 : 528 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 21.9 MiB (100%)
Writing library                          : Lavf54.25.105


```


he-aacv2  file  ```
mediainfo 'élucubrations.m4a'
General
Complete name                            : élucubrations.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 1.61 MiB
Duration                                 : 5mn 48s
Overall bit rate mode                    : Constant
Overall bit rate                         : 38.7 Kbps
Writing application                      : Lavf54.25.105

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : HE-AACv2 / HE-AAC / LC
Codec ID                                 : 40
Duration                                 : 5mn 48s
Bit rate mode                            : Constant
Bit rate                                 : 38.0 Kbps
Channel(s)                               : 2 channels / 1 channel / 1 channel
Channel positions                        : Front: L R / Front: C / Front: C
Sampling rate                            : 44.1 KHz / 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 1.58 MiB (98%)

```

hey wait that kind of invalidates all previous info   or maybe they have there a codec that is really good  [also means an album can be emailed as one file]

---

### Post by dmahoon on 2012-10-18
Thanks everyone,

I'm kinda old too and have listened to a lot of hard rock, prog rock, heavy metal and, well, pretty much everything at high volume both live, in the basement and through headphones.  I think I can tell the difference but for the amount of work involved I'll stick with what I've got and anything new will be saved in a better format.

Your feedback is most appreciated....

Patrick

---

