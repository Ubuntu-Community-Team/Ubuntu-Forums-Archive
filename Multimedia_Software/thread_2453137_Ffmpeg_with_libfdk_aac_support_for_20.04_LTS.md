---
title: "Ffmpeg with libfdk_aac support for 20.04 LTS"
date: 2020-11-03
forum: Multimedia Software
---

### Post by plazman30 on 2020-11-03
Is there a repository that offers ffmpeg compiled to use libfdk_aac for 20.04 LTS?  I’m getting ready to upgrade from 18.04 to 20.04 and this is the only thing holding me back right now.

I know I can compile it myself, but compiling ffmpeg takes FOREVER to do.  It would be nice of there was a PPA for Focal that offered it.

---

### Post by CelticWarrior on 2020-11-03
Check your the PPA you're using now. Maybe it has support already.

---

### Post by plazman30 on 2020-11-03
The PPA I am using only support Bionic.  Hence why I posted this.

---

### Post by Yellow Pasque on 2020-11-04
Is there a reason you need fdkaac and can't use ffmpeg's built-in aac support?

---

### Post by plazman30 on 2020-11-04
fdk_aac sounds much better.

---

### Post by Yellow Pasque on 2020-11-04
> **plazman30 said:**
> fdk_aac sounds much better.

Ah, I see. I thought their implementation had gotten better in that regard since ffmpeg 4.x
I'll see if I can whip one up in my PPA. It might take a little while to build. I'll let you know.

---

### Post by Yellow Pasque on 2020-11-04
Well, you can try it out here: [https://launchpad.net/~dtl131/+archive/ubuntu/ffmpegcustom/+packages](https://launchpad.net/~dtl131/+archive/ubuntu/ffmpegcustom/+packages)

---

### Post by Yellow Pasque on 2020-11-04
Also note that ffmpeg says "as of 2017 libfdk_aac may not always be better than aac for AAC-LC. The built in aac encoder is quite good." - [https://trac.ffmpeg.org/wiki/Encode/HighQualityAudio](https://trac.ffmpeg.org/wiki/Encode/HighQualityAudio)

---

### Post by andrew.46 on 2020-11-14
> **Yellow Pasque said:**
> Also note that ffmpeg says "as of 2017 libfdk_aac may not always be better than aac for AAC-LC. The built in aac encoder is quite good." - [https://trac.ffmpeg.org/wiki/Encode/HighQualityAudio](https://trac.ffmpeg.org/wiki/Encode/HighQualityAudio)

Interestingly enough hydrogenaudio still [ranks fdkaac above FFmpeg's AAC encoder]("https://wiki.hydrogenaud.io/index.php?title=AAC_encoders"). Mind you the hydrogenaudio rankings have not been updated for some time. For best AAC under Linux however I believe Apple AAC is still undisputed leader and for Linux that means [qaac...]("https://www.andrews-corner.org/qaac.html")

---

### Post by Yellow Pasque on 2020-11-14
> **andrew.46 said:**
> Interestingly enough hydrogenaudio still [ranks fdkaac above FFmpeg's AAC encoder]("https://wiki.hydrogenaud.io/index.php?title=AAC_encoders"). Mind you the hydrogenaudio rankings have not been updated for some time.

Yeah, it appears this page was last updated in 2016. I'd be interested to know if the ffmpeg encoder got better in 4.x

My ears do not particularly care for AAC. I'd rather use vorbis, opus or mp3.

---

### Post by plazman30 on 2020-11-28
Thanks for finding this.

---

