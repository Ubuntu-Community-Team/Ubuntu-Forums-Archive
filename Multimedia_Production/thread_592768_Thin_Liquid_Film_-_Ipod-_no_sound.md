---
title: "Thin Liquid Film - Ipod- no sound"
date: 2007-10-26
forum: Multimedia Production
---

### Post by aconley1 on 2007-10-26
If anyone out there uses thin liquid film, maybe you can help me out.  I am able to convert my video files to .mp4 using TLF.  When I play the converted files on my laptop, everything is great.  I have perfect video and audio.  However, when I add the files to the ipod using TLF, the audio doesn't play.  
Has anyone else encountered this, and do you know how to fix it?
Thanks

---

### Post by aconley1 on 2007-10-26
Any ideas? anybody?

---

### Post by FRuMMaGe on 2008-01-11
Same problem here. It seems to be a problem with how Ubuntu puts the videos onto the iPod

---

### Post by Creative2 on 2008-01-12
mmm i don't know what is TLF

 but have your tried ffmpeg ? 

 i know ffmpeg can encode mp4 for ipod as well as mencoder. and that rocks
as you can see here 

[http://ffmpeg.mplayerhq.hu/faq.html#SEC18](http://ffmpeg.mplayerhq.hu/faq.html#SEC18)
it can encode 
```
ffmpeg -i INPUT -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X OUTPUT
```

Or this

```
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 OUTPUT 
```

i used these for my interface. they  should work fine 

[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

### Post by FRuMMaGe on 2008-01-12
> **Creative2 said:**
> mmm i don't know what is TLF

 but have your tried ffmpeg ? 

 i know ffmpeg can encode mp4 for ipod as well as mencoder. and that rocks
as you can see here 

[http://ffmpeg.mplayerhq.hu/faq.html#SEC18](http://ffmpeg.mplayerhq.hu/faq.html#SEC18)
it can encode 
```
ffmpeg -i INPUT -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X OUTPUT
```

Or this

```
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 OUTPUT 
```

i used these for my interface. they  should work fine 

[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

TLF is just a frontend for ffmpeg.

---

