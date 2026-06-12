---
title: "No sound with ATI SB 450 (Intel HDA)"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Lavaeolus on 2007-11-04
Hello,
I got a new laptop (Medion MD 96431) and installed ubuntu 7.10. I finally got everything working...except sound. From reading the wiki and forums, it seems that hda-intel is causing the problems, though none of the proposed solutions worked for me so far.

I have an ATI SB450, Codec is SigmaTel STAC9200. (These are the infos i got following [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28HdaIntelSoundHowto%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28HdaIntelSoundHowto%29) ). I added "options snd-hda-intel model=ref" to /etc/modprobe.d/alsa-base. I also followed the instructions on [http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is) and [http://ubuntuforums.org/showthread.php?t=424400](http://ubuntuforums.org/showthread.php?t=424400) , but sound still doesn't work.

So, I have no idea what to do next. Any help is greatly appreciated.

---

### Post by Lavaeolus on 2008-03-26
Yay, after months without sound and after even my local linux gurus broke their teeth at this, it finally works! :) Sound came back, when I switched to OSS v4.0. For anyone else having this problem, I recommend this guide:

[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

---

