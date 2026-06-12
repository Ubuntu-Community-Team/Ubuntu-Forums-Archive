---
title: "No sound from Chrome....."
date: 2013-12-12
forum: Multimedia Software
---

### Post by diyhouse on 2013-12-12
Hi am running the latest myth-ubuntu build/install,... and although basic Myth install is fine,.. ( sound and video work great from within Myth). I cannot use the chrome ( or other ) browser,..

I have found many articles on setting sound setup,.. all seem to point to the /etc/asound.conf file as the key,.. I have edited this file.
and have generally been following the URL:- [http://ubuntuforums.org/archive/inde...t-2144668.html](http://ubuntuforums.org/archive/inde...t-2144668.html)

I have used the speaker-test -Dhw:0,3 -c2,.. to output test tones to the TV speakers,.. so I know the card and device refs are good.

I am trying to output via the HDMI lead to the TV for stereo only sound

DO any folks know what I have done/doing wrong and what I need to do in order to restore sound to my broswer environment as well ( I hope to VLC ).

Many thanks

---

### Post by diyhouse on 2014-02-10
As a close out to this post,.. I have abandoned base mythbuntu distro in favour of ubuntu 12.04 LTS and 0.27mythtv,.. as I tried many other distros and they all worked fine for browser  sound,.. after a little tweak to the sound setting,.. ie to tell system where to squirt the sound to eg HDMI....
Rgds all

---

### Post by Bucky Ball on 2014-02-10
Please mark the thread as solved. Thanks.

---

### Post by diyhouse on 2014-08-30
As An ongoing updates to my old posts,.. I now run mythbuntu 14.04 and yes the base install still does not deliver sound from chrome,...
However,.. loading the **pavucontrol **( pulse audio Volume control ), and then use this tool to direct the audio output allows media playing with the sound outputing via the HDMI lead.

---

