---
title: "Problem with streaming"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by linux-beginner on 2007-03-03
Hi everyone,

I can't listen to bbc ([http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.asx)](http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.asx))!
Could you guide me how I can play this streaming, please?

Thanks,

---

### Post by joselin on 2007-03-03
This page was not available.

---

### Post by yabbadabbadont on 2007-03-03
That's because his link ends with ")".  Remove it and the asx file will be available for download.

By the way, it plays fine with:

xine [http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.asx](http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.asx)

---

### Post by joselin on 2007-03-03
You are right. And works fine here too.

---

### Post by linux-beginner on 2007-03-03
If I click on the link I get this message:
> Totem could not play 'mms://a1149.l1305038288.c13050.g.lm.akamaistream.net/D/1149/13050/v0001/reflector:38288'.
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

---

### Post by yabbadabbadont on 2007-03-03
> **linux-beginner said:**
> If I click on the link I get this message:

That's because you don't have the Microsoft codecs installed.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by linux-beginner on 2007-03-03
I've installed all packages which are needed to play Microsoft codes (I think)!
I don't have any idea why It doesn't run??:confused:

---

### Post by yabbadabbadont on 2007-03-03
Do you have the w32codecs installed?

You might also try replacing totem-gstreamer with totem-xine and making sure that you have libxine-extracodecs, libxine-main1, and libxine1 installed.  You will need to have the universe and multiverse repositories enabled.  I think that was covered by the link I gave you.

---

### Post by linux-beginner on 2007-03-03
Yes I've also installed w32codes. What I don't understand is since I reinstalled my ubuntu this problem exists. Before that I could run every streaming with my totem. I don't think it depends to totem or Xine!

---

### Post by bwallum on 2007-03-08
This works for me, follow it carefully, I had to re run through it because I rushed.

[https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

---

