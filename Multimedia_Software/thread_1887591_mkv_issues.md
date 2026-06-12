---
title: "mkv issues"
date: 2011-11-27
forum: Multimedia Software
---

### Post by fisheye11 on 2011-11-27
I've downloaded the packages for the media player and grabbed VLC for some MKV files.  The video on both players is a little choppy, but the audio is fine.  How can I fix this?

I have 11.10 Unity

---

### Post by papibe on 2011-11-27
Hi fisheye11. Welcome to the forums.

Could you give us more information on the video? Is it an HD video?

While playing it in VLC, could you post what it says in Tool -> Codec Information?

Regards.

---

### Post by fisheye11 on 2011-11-27
H264-MPEG-4 AVC (part10) (avc1)

rez: 1920x1080
rate: 23.976216

---

### Post by papibe on 2011-11-27
Thanks.

That's a full HD video. In order to play it smoothly you need video hardware acceleration. That require some minimum hardware and/or to install some libraries.

What is your graphic card?

Could you post the result of this command?
```
 lspci | grep -i vga
```
Regards.

---

### Post by fisheye11 on 2011-11-27
ATI Technologies Inc RS880 [Radeon HD 4200]

---

### Post by papibe on 2011-11-27
Unfortunately, I don't enough experience with ATI cards. But here's a few links that can help you. In general, you need to install the proprietary driver, then the vaapi library, and finally enable the acceleration on the player.

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

[http://ubuntuforums.org/showthread.php?t=1588465&highlight=ati+vaapi](http://ubuntuforums.org/showthread.php?t=1588465&highlight=ati+vaapi)

[https://wiki.archlinux.org/index.php/Ati](https://wiki.archlinux.org/index.php/Ati)

Hopefully someone else pith in, and give you more detail instructions.

Regards.

---

### Post by inobe on 2011-11-27
[http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric](http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric)

have a look there.

side note, if you have an nvidia card, i would use that instead.

---

