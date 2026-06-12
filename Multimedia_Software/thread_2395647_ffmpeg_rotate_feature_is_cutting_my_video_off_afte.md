---
title: "ffmpeg rotate feature is cutting my video off after 1 minute"
date: 2018-07-04
forum: Multimedia Software
---

### Post by edcompsci on 2018-07-04
Every time  I try to rotate my video with ffmpeg that is 2 min 10 sec long the outputted file only captures the first half of the video.   

Why is this and can this be made not to do this?
```

ffmpeg -i "VIDEO0016.mp4" -vf "transpose=1" "VIDEO0016-out.mp4"

ffmpeg -i "VIDEO0016.mp4" -vf "rotate=PI/2" "VIDEO0016-rot.mp4"

```

---

### Post by kazakore on 2018-07-07
What version of Ubuntu?

Where have you got ffmpeg from? Ubuntu removed the real one at least for 16.04 and a few other versions and replaced it with the avconv package using the ffmpeg name. Personally I make sure to have the real ffmpeg installed by using an external ppa. I think they have gone back to the proper package with 18.04 though....

Posting your full output would help maybe. Also checking your man pages. ffmpeg renames -vfilters to just -vf not so long ago so you need to make sure your ffmpeg version matches with the instructions you are trying to use.

man ffmpeg
man ffmpeg-filters

Will both help you.

---

### Post by edcompsci on 2018-07-11
> **kazakore said:**
> What version of Ubuntu?

Where have you got ffmpeg from? Ubuntu removed the real one at least for 16.04 and a few other versions and replaced it with the avconv package using the ffmpeg name. Personally I make sure to have the real ffmpeg installed by using an external ppa. I think they have gone back to the proper package with 18.04 though....

Posting your full output would help maybe. Also checking your man pages. ffmpeg renames -vfilters to just -vf not so long ago so you need to make sure your ffmpeg version matches with the instructions you are trying to use.

man ffmpeg
man ffmpeg-filters

Will both help you.

Thank you for your help.


> 
lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    LinuxMint
Description:    Linux Mint 18 Sarah
Release:    18
Codename:    sarah

uname -r
4.4.0-21-generic


ffmpeg version is 7.2.8.14-0ubuntu0.16.04.1

Sorry, this is my Linux Mint computer and I know Mint has its own forums but I was on my other computer Ubuntu Studio when I ran int to the error and first posted it.

I see in Synaptic Package Manager by searching for avconv that there is a gui called winff.  I'm going to install and check it out to see what it looks like.

---

