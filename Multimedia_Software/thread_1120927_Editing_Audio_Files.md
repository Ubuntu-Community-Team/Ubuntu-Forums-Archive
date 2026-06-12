---
title: "Editing Audio Files"
date: 2009-04-09
forum: Multimedia Software
---

### Post by Geffers on 2009-04-09
I've got a 3 hour 160MB mp3 audio file, I would like to extract about 3 minutes of this as a seperate file.

Can ffmpeg do this or is there a preferable method.

Geffers

---

### Post by dnguyen1963 on 2009-04-09
Use Audacity for this purpose.  A simple search on the net will give you the link.

---

### Post by logos34 on 2009-04-09
If you know exactly where you want the cuts, you can do one command (mp3splt) from the CLI:

> NAME
       mp3splt &#8212; Utility for mp3/ogg splitting without decoding

SYNOPSIS
[COLOR="Red"]       mp3splt [OPTIONS] FILE... [BEGIN_TIME] [END_TIME...][/COLOR]



man mp3splt

---

### Post by Geffers on 2009-04-09
> **dnguyen1963 said:**
> Use Audacity for this purpose.  A simple search on the net will give you the link.

Tried it, for some reason it was taking absolutely ages to load the sound file.

Geffers

---

### Post by Geffers on 2009-04-09
> **logos34 said:**
> If you know exactly where you want the cuts, you can do one command (mp3splt) from the CLI:

man mp3splt

That worked brilliantly, and so quick.

Thanks.

Geffers

---

### Post by andrew.46 on 2009-04-09
Hi Geffers,

> **Geffers said:**
> I've got a 3 hour 160MB mp3 audio file, I would like to extract about 3 minutes of this as a seperate file.

Can ffmpeg do this or is there a preferable method.

FFmpeg has 2 options that will allow this. The first is the '-t' option:

> 
       -t duration
           Restrict the transcoded/captured video sequence to the duration
           specified in seconds.  "hh:mm:ss[.xxx]" syntax is also supported.


and the second is the '-ss' option:

> 
       -ss position
           Seek to given time position in seconds.  "hh:mm:ss[.xxx]" syntax is
           also supported.



So if you wished to extract 3 minutes of your mp3 file, starting at 6 minutes and 30 seconds in, copying to a new file you could run:

```
ffmpeg -i input.mp3 -ss 06:30 -t 03:00 -acodec copy output.mp3
```

It depends how you want to do it, mp3split *does* sound interesting :-).

Andrew

---

### Post by Geffers on 2009-04-09
> **andrew.46 said:**
> Hi Geffers,



FFmpeg has 2 options that will allow this. The first is the '-t' option:



and the second is the '-ss' option:



So if you wished to extract 3 minutes of your mp3 file, starting at 6 minutes and 30 seconds in, copying to a new file you could run:

```
ffmpeg input.mp3 -ss 06:30 -t 03:00 -acodec copy output.mp3
```

It depends how you want to do it, mp3split *does* sound interesting :-).

Andrew

mp3splt was easy and worked well but I like ffmpeg after FakeOutdoorsman assisted with my conversion to mpeg2 problem.

Geffers

---

### Post by andrew.46 on 2009-04-09
Hi Geffers,

> **Geffers said:**
> mp3splt was easy and worked well but I like ffmpeg after FakeOutdoorsman assisted with my conversion to mpeg2 problem.

It was the Fakeoutdoorsman's guide that swung me towards FFmpeg as well :-).

Andrew

---

### Post by FakeOutdoorsman on 2009-04-09
> **andrew.46 said:**
> ...
So if you wished to extract 3 minutes of your mp3 file, starting at 6 minutes and 30 seconds in, copying to a new file you could run:

```
ffmpeg input.mp3 -ss 06:30 -t 03:00 -acodec copy output.mp3
```

It depends how you want to do it, mp3split *does* sound interesting :-).

Andrew
If you declare *-ss* and *-t* as input file options FFmpeg will seek before decoding the input, otherwise it will seek after decoding the input file and would be slower...probably.
```
ffmpeg -ss 06:30 -t 03:00 input.mp3 -acodec copy output.mp3
```

> **Geffers said:**
> mp3splt was easy and worked well but I like ffmpeg after FakeOutdoorsman assisted with my conversion to mpeg2 problem.

Geffers
Glad I could help, but I can't take all the credit since Andrew helped too.

---

### Post by andrew.46 on 2009-04-09
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> If you declare *-ss* and *-t* as input file options FFmpeg will seek before decoding the input, otherwise it will seek after decoding the input file and would be slower...probably.
```
ffmpeg -ss 06:30 -t 03:00 input.mp3 -acodec copy output.mp3
```


Oops :-).

Andrew

---

### Post by FakeOutdoorsman on 2009-04-10
> **andrew.46 said:**
> Hi FakeOutdoorsman,



Oops :-).

Andrew

I just found this out myself not to long ago.

---

### Post by Geffers on 2009-04-11
> **andrew.46 said:**
> Hi Geffers,



FFmpeg has 2 options that will allow this. The first is the '-t' option:



and the second is the '-ss' option:



So if you wished to extract 3 minutes of your mp3 file, starting at 6 minutes and 30 seconds in, copying to a new file you could run:

```
ffmpeg -i input.mp3 -ss 06:30 -t 03:00 -acodec copy output.mp3
```

It depends how you want to do it, mp3split *does* sound interesting :-).

Andrew

I'm obviously doing something wrong with ffmpeg here, if I issue the following;

```
geoff@Columbia:~/Desktop$ ffmpeg -i today.mp3 -ss 1:14:53 -t 00:04:32 -acodec copy test1.mp3
```

I keep getting an mp3 file of zero bytes and no duration.

The today.mp3 was a 2h 57m radio 4 broadcast and I wanted to extract about 5 minutes of an interview from it.

Done it fine with mp3splt so ffmpeg in now curiosity.

Geffers

---

