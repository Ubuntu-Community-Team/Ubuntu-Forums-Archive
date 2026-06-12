---
title: "For all you Audiophiles, need help making script to combine Stereo chans then export"
date: 2012-04-12
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-12
I've recently had an issue where some of my music will have split audio channels - eg: one part only comes through one part of the speaker - the other comes through the other, I want to make script that can merge both stereo channels and then export the file with the same settings that were used in the original rip - leaving it almost untouched.

Perhaps even a Normalize command too due to the loss of volume from combining the 2 channels.

I'm open for help.

---

### Post by shantiq on 2012-04-12
sox should do it easy and beautiful


```
sudo apt-get install sox
```



```
sox originalfile.flac -c1  monofile.flac
```


see here


> mediainfo rain.flac
General
Complete name                            : rain.flac
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
File size                                : 61.9 MiB
Duration                                 : 5mn 21s
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 614 Kbps
Track name                               : Chuva no Minha Janela  [rain on my window]
Performer                                : Chuva LLuvia
Recorded date                            : Timeless
Comment                                  : Processed by SoX

Audio
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
Duration                                 : 5mn 21s
Bit rate mode                            : Variable
Bit rate                                 : 1 614 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Bit depth                                : 24 bits
Stream size                              : 61.9 MiB (100%)
Writing library                          : libFLAC 1.2.1 (UTC 2007-09-17)


shantiq@shantiq-00000000000000000000000:~$ sox rain.flac -c1  monofile.flac
shantiq@shantiq-00000000000000000000000:~$ mediainfo monofile.flac
General
Complete name                            : monofile.flac
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
File size                                : 31.0 MiB
Duration                                 : 5mn 21s
Overall bit rate mode                    : Variable
Overall bit rate                         : 809 Kbps
Track name                               : Chuva no Minha Janela  [rain on my window]
Performer                                : Chuva LLuvia
Recorded date                            : Timeless
Comment                                  : Processed by SoX

Audio
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
Duration                                 : 5mn 21s
Bit rate mode                            : Variable
Bit rate                                 : 809 Kbps
Channel(s)                               : 1 channel
Sampling rate                            : 48.0 KHz
Bit depth                                : 24 bits
Stream size                              : 31.0 MiB (100%)
Writing library                          : libFLAC 1.2.1 (UTC 2007-09-17)



original 24-bit is kept  sampling rate remains the same  bit rate halved but fair enough since now mono
hope this helps  [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]


**PS**   if you want to pep up your volume on your new mono file you can use the gain function


```
sox monofile.flac monofilewithhikedvolume.flac gain +10
```



will pep it up


to check levels before doing so first play it to find your number of choice

```
play monofile gain +10
```  ```
play monofile gain +20
```   etc...

---

### Post by AlexOnVinyl on 2012-04-12
> **shantiq said:**
> sox should do it easy and beautiful


```
sudo apt-get install sox
```



```
sox originalfile.flac -c1  monofile.flac
```


see here





original 24-bit is kept  sampling rate remains the same  bit rate halved but fair enough since now mono
hope this helps  [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]


**PS**   if you want to pep up your volume on your new mono file you can use the gain function


```
sox monofile.flac monofilewithhikedvolume.flac gain +10
```



will pep it up


to check levels before doing so first play it to find your number of choice

```
play monofile gain +10
```  ```
play monofile gain +20
```   etc...

Wow, thanks man, but I just want to actually combine 2 Stereo channels - not necessarily make it Mono - check this out: [IMG]http://i.imgur.com/SfLAW.png[/IMG]

See, thats what I want to fix - put them together, and I have to do it for the whole album.  I just want to make a script that will go through and do that for all the songs.

---

### Post by AlexOnVinyl on 2012-04-12
> **shantiq said:**
> sox should do it easy and beautiful


```
sudo apt-get install sox
```



```
sox originalfile.flac -c1  monofile.flac
```


see here





original 24-bit is kept  sampling rate remains the same  bit rate halved but fair enough since now mono
hope this helps  [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]


**PS**   if you want to pep up your volume on your new mono file you can use the gain function


```
sox monofile.flac monofilewithhikedvolume.flac gain +10
```



will pep it up


to check levels before doing so first play it to find your number of choice

```
play monofile gain +10
```  ```
play monofile gain +20
```   etc...


ALSO - would using the '1$' or '$1' param work with sox? I want to make this into a script that I can right click and use

---

### Post by shantiq on 2012-04-12
ok you got me confused Alex :]  are they not always split AND different it shows 2 channels if it is stereo


see here mine  [ATTACH]215894[/ATTACH]


and then only 1   [if you want the same to come out of each speaker]


[ATTACH]215895[/ATTACH]


on your picture it is like my first one stereo


not sure if i understand what you mean then :KS:KS   someone else might

as regards scripting i have no extended knowledge there   sorry

with above command this works for bulk


```
for f in * ; do sox "$f" -c1  "${f%.*.flac}.flac"; done 

```

---

### Post by AlexOnVinyl on 2012-04-13
> **shantiq said:**
> ok you got me confused Alex :]  are they not always split AND different it shows 2 channels if it is stereo


see here mine  [ATTACH]215894[/ATTACH]


and then only 1   [if you want the same to come out of each speaker]


[ATTACH]215895[/ATTACH]


on your picture it is like my first one stereo


not sure if i understand what you mean then :KS:KS   someone else might

as regards scripting i have no extended knowledge there   sorry

with above command this works for bulk


```
for f in * ; do sox "$f" -c1  "${f%.*.flac}.flac"; done 

```

Thanks man, yeah I meant I wanted them in 1 single sound - mono - so that way I could hear it through both speakers equally. 

and also, what exactly does the "$f" stand for? can you explain the lettering in the command and what it does?

---

### Post by shantiq on 2012-04-14
hi there again Alex


> what exactly does the "$f" stand for? can you explain the lettering in the command and what it does?


sorry i cannot i just know that it works and have tested it.   I am no programmer  :KS:KS:KS:KS    I just collect bits of code i can use



av you tried this line on your files?   it will convert all of them [from stereo to mono and keep original files too] simply go to terminal cd to folder and paste   




regards   shan

---

