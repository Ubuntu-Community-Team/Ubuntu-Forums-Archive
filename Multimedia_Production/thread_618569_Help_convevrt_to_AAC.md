---
title: "Help convevrt to AAC"
date: 2007-11-20
forum: Multimedia Production
---

### Post by Tethylis on 2007-11-20
Hey, what can I use to convert my mp3's to aac format so I can put them on my ipod. I already have amarok setup, but all I need to do is convert them. Any ideas?

---

### Post by qamelian on 2007-11-20
Why do you need to convert them to put them on your iPod? The iPod will play them as is and there is really no benefit to converting them. In fact, conversion has a very real chance of degrading the sound quality.

---

### Post by rsambuca on 2007-11-20
Why convert from one lossy format to another?  iPods can use mp3 anyways.

---

### Post by Tethylis on 2007-11-20
Well, I just thought that was the problem I was having. Because I formatted my ipod and then tried putting the songs on it again using amarok. But for some reason the ipod doesn't see the music or anything. Im pretty sure the files are on there too.

---

### Post by Trini45 on 2007-11-23
have the same problem....

---

### Post by timcredible on 2007-11-23
.

---

### Post by Creative2 on 2007-11-24
convert to aac

ffmpeg -i INPUT -ab 128k  -acodec aac OUTPUT

if you want a nice interface to convert lots files see here [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by lvleph on 2007-11-29
The reason why someone might want to convert from MP3 to AAC is simple. For the same quality one gets a smaller file. Smaller files give you the ability to have more music on you iPod. It was a simple choice for me. I have 13k+ songs and a 60GB iPod. When I first started using an iPod I had 11K songs and a 40GB iPod. If I tried to use MP3 I would have only been able to fit 85-90% of my songs.

---

### Post by rsambuca on 2007-11-29
> **lvleph said:**
> The reason why someone might want to convert from MP3 to AAC is simple. For the same quality one gets a smaller file. Smaller files give you the ability to have more music on you iPod. It was a simple choice for me. I have 13k+ songs and a 60GB iPod. When I first started using an iPod I had 11K songs and a 40GB iPod. If I tried to use MP3 I would have only been able to fit 85-90% of my songs.

You clearly don't understand the point of my question.  Definitely AAC is a superior compression format, however, it is still a lossy format, meaning data is lost.  When an mp3 is created (also a lossy format), data is thrown out during the compression.  This data is gone.  Lost forever.  If you now use the mp3 to create an AAC file, more data is lost during the compression, and you have an imperfect source on top of it.  If you are going to go to AAC, fine, but go back to the original uncompromised source.  Otherwise, despite the fact that the AAC is a better format, you are still making the audio quality worse than the mp3.

---

### Post by lvleph on 2007-12-03
My CDs are scratched, so I would have to buy them again.

---

### Post by rsambuca on 2007-12-03
> **lvleph said:**
> My CDs are scratched, so I would have to buy them again.

Then leave them as is.  Don't destroy the fidelity of the music any further.  Surely 11,000 songs is sufficient at any one time.  You can always change some out after the 4 years it would take you to listen to those!

---

### Post by raulih on 2008-02-18
> **Creative2 said:**
> convert to aac

ffmpeg -i INPUT -ab 128 -acodec aac OUTPUT

Unfortunately it's not as simple as that. I will get "Unknown codec 'aac'" error when trying. Here's some information: [http://ubuntuforums.org/showthread.php?t=90424](http://ubuntuforums.org/showthread.php?t=90424) but I don't understand much of it.

---

### Post by Creative2 on 2008-02-18
plz post this:

ffmpeg -formats |grep aac

-if you get libfaac replace aac with libaac

---

### Post by andrew.46 on 2008-02-22
Hi,

Could be a simple terminology problem:

> **raulih said:**
> Unfortunately it's not as simple as that. I will get "Unknown codec 'aac'" error when trying. Here's some information: [http://ubuntuforums.org/showthread.php?t=90424](http://ubuntuforums.org/showthread.php?t=90424) but I don't understand much of it.

Instead of  '-acodec aac' try '-acodec libfaac' without the inverted commas of course!

     Andrew

---

### Post by raulih on 2008-02-22
> **Creative2 said:**
> plz post this:

ffmpeg -formats |grep aac

-if you get libfaac replace aac with libaac

$ ffmpeg -formats |grep aac
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
 D  aac             ADTS AAC

> **andrew.46 said:**
> Instead of '-acodec aac' try '-acodec libfaac'

This didn't work either.

Actually I don't need the convert anymore, but I send this information in case the discussion is useful to someone. Thanks for your help anyway!

---

### Post by andrew.46 on 2008-02-22
Hi,

 Well I downloaded and installed today and my own results are:

```
andrew@ilium~$ ffmpeg -formats |grep aac
FFmpeg version SVN-r12176, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug \
--enable-shared --disable-static --enable-pthreads --enable-libtheora \
--enable-libvorbis --enable-gpl --enable-pp --enable-swscaler \
--enable-x11grab --enable-libmp3lame --enable-libfaac \
--enable-libfaad --enable-libxvid --enable-liba52 --enable-libx264 \
--enable-libamr-nb --enable-libamr-wb --enable-nonfree
  libavutil version: 49.6.0
  libavcodec version: 51.50.1
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb 22 2008 15:49:22, gcc: 4.1.2
 D  aac             ADTS AAC
  EA    libfaac
 D A    mpeg4aac
```

I am a little new to ffmpeg although I have a little more experience with mencode / mplayer but -acodec libfaac works for me. (Just tidied the --enables to fit on the screen!)

           Andrew

---

### Post by Creative2 on 2008-02-22
**how to check you version of ffmpeg and so understand if you CAN encode and HOW encode **

execute in a terminal this :  ```
ffmpeg -formats |grep aac:
```

-IF YOU HAVE  FFMPEG WITH NO SUPPORT FOR AAC : you will get


```

D aac ADTS AAC
```

here you** can't** see  E= encoder  so untill you have not ffmpeg with all supports you will not able to encode because you HAVE NOT Encoder 

easy solutions 

READ THIS [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29)
if you turn on medibuntu repo and update ffmpeg and mencodder will be updated and will support every formats 
[https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29)





-IF YOU HAVE   FFMPEG COMPILED  FROM SOURCE you will get

as you can see  here  it has D= decoder (aac) and it has  E= encoder ,name of the codec for compiled ffmpeg is libfaac 

```
 D  aac             ADTS AAC
  EA    libfaac
 D A    mpeg4aac
```

so you need to use

ffmpeg -i INPUT -ab 128k -acodec libfaac OUTPUT


 

- IF YOU HAVE   FFMPEG FROM MEDIBUNTU REPO you will get  

```

D  aac             ADTS AAC
 DEA    aac
 D A    mpeg4aac

```

so you need  to use

 ffmpeg -i INPUT -ab 128k  -acodec aac OUTPUT

 instead for ffmpeg from medibuntu repo it has E = aac so the name you must use is aac

---

### Post by raulih on 2008-02-22
**medibuntu** and its **ffmpeg**-update made it, and possibly **w32codecs** - i already had **ubuntu-restricted-extras**. Thanks!

---

### Post by andrew.46 on 2008-02-22
Hi,

Thanks for clearing up all the confusion:

> **Creative2 said:**
> how to check you version of ffmpeg and so understand if you CAN encode and HOW encode 
[...]
output of this command  ```
ffmpeg -formats |grep aac:
```
  FFMPEG COMPILED  FROM SOURCE

as you can see  here  it has D= decoder (aac) and it has  E= encoder ,name of the codec for compiled ffmpeg is libfaac 
```
 D  aac             ADTS AAC
  EA    libfaac
 D A    mpeg4aac
```
so you need to use
ffmpeg -i INPUT -ab 128k -acodec libfaac OUTPUT


In fact my own copy, which fits the picture above, was compiled from source, both svn ffmpeg and faac. I was very puzzled as to why people had such different results :-)

    Andrew

---

