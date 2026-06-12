---
title: "upside problem webcam in skype only in ubuntu 10.10"
date: 2011-03-19
forum: Multimedia Software
---

### Post by clp32r on 2011-03-19
Hi,
I know there have been a million posts about this, but I followed as many as i could find of them and still no success.
I have a ASUS K52J.

I tried cheese. It was initially upside down. Then I tried Video for linux device preferences. When I checked vertival flip, that fixed cheese. But it was still upside down in skype.

I tried downloading skype from the webpage, and from synaptic.

I tried running skype in sudo.

I tried:
 export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
but i get: ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored

and I tried: 
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored

I tried this:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
When skype loads up, i go to the options>video>test. The green light comes on by the built in webcam, then i get a segmentation fault and skype crashes:
/usr/local/bin/skype: line 2:  4055 Segmentation fault      LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

Then I tried:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
then running skype and i got the segmentation fault again.

I may have missed some threads on this but everyone else seemed to be thanking someone for fixing their problem by now.

Finally I tried threating my computer with a Windows installation. But I think both me and the computer knew it was a hollow threat,

I'd really appreciate if someone could point me in the right direction on this one,
Thankyou!

---

### Post by clp32r on 2011-03-20
OK, a temporary solution for anyone with similar issues:
The new version of skype allows screen sharing, so just load up cheese first, flip the image vertically using video4linux device preferences, then share your screen with the person you are talking to. You can just show the cheese screen if you want.

---

### Post by Victormd on 2011-03-21
Yeah, I noticed this... went the cheese route as well...

---

### Post by Vi3tHoneyX on 2011-05-12
*bump* I've got the same laptop running 10.10 and have the same problem, except it's not upside in only Skype. Even on tinychat or gmail my webcam is upside down. For some reason Cheese always works though. Have you figured anything out, yet?

---

### Post by no2498 on 2011-05-13
[http://www.google.com/search?client=opera&rls=en&q=webcam+is+upside+down&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=webcam+is+upside+down&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

---

