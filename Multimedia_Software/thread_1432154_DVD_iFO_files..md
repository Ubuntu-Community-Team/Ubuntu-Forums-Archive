---
title: "DVD iFO files."
date: 2010-03-17
forum: Multimedia Software
---

### Post by NiGhtMarEs0nWax on 2010-03-17
I'm trying to create a DVD with K3b, I encoded a DIVx MP4 file to vob, but i need to create the iFO and BUP files if that is correct?

is it possible in any way to create iFO & BUP files?


Thanks.

---

### Post by ron999 on 2010-03-17
Hi
Look at using '_**tovid**_'. I think that it's in Ubuntu's repo.

You've done the first part, you should have an MPEG2 file with a name such as **movie.mpg**.

The next step is to use '**makexml**' to create an xml file, a type of 'cue' file.
The command to use is:-
```
makexml movie.mpg -out MyDisc.xml
```
This results in a file named [B]MyDisc.xml
[/B]
Then you use '**makedvd**' to create the file structure. That's a directory named **video_ts** that contains vob, ifo and bup files.
The command is:-
```
makedvd -author MyDisc.xml

```
Then use k3b to create an iso file (if you like).
Then burn it with k3b

There's information here about tovid:-[http://tovid.wikia.com/wiki/Tovid_Wiki]("http://tovid.wikia.com/wiki/Tovid_Wiki")

---

### Post by NiGhtMarEs0nWax on 2010-03-17
Thanks, to what mpg file are you referring to? teh source file is mpg format but the encoded video files i created with ffmpeg are in vob format.

Thanks.

---

### Post by ron999 on 2010-03-17
Hi
The file that you converted from DIVx MP4, rename it **movie.mpg** for convenience. Then you can follow my instructions if you like.

---

### Post by NiGhtMarEs0nWax on 2010-03-17
Thanks, sorry i think i am misunderstanding, can I not just use the vob files directly?

---

### Post by ron999 on 2010-03-17
> **NiGhtMarEs0nWax said:**
> Thanks, sorry i think i am misunderstanding, can I not just use the vob files directly?
Yes you can, but the command will be:- 
```
makexml <name of vob file> -out MyDisc.xml
```

---

### Post by NiGhtMarEs0nWax on 2010-03-17
Thanks, I thought as much, I managed to create an iso image which i burnt, it has the vob, ifo and bup files in the VIDEO_TS directory. the only problem is that my dvd player wont read the disc.  
I read somewhere that *some* dvd players wont play dvds unless they have something in the AUDIO_TS directory, is this true? what will I put in there?

it was encoded into pal-dvd initially using ffmpeg, i live in the uk.

Thanks again man, much appreciated.

---

### Post by NiGhtMarEs0nWax on 2010-03-17
bump.

---

### Post by ron999 on 2010-03-17
audio_ts folder is usually empty.
Check out what's in the audio_ts folder on some of your other DVDs.

---

### Post by datacrusher on 2010-10-21
i couldnt use this command right way since makexml and makedvd are not in /usr/bin, i had to call hem from /usr/share/tovid/

---

