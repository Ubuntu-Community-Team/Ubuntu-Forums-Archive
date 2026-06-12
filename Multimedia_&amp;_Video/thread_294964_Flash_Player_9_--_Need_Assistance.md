---
title: "Flash Player 9 -- Need Assistance"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by thomasaaron on 2006-11-07
Hey, folks.

The other day, I installed flash player 9 and was able to watch this video ([www.newwesttv.com](www.newwesttv.com)). Now, it is not working. I tried reloading flash 9. Still no dice.

Can somebody with Flash9 please go to that site and see if the video works for you?

It is a writing sample for me (the copy in the video, that is) and I need to know if I can send the link out to some prospective clients.

Thanks,
Tom

---

### Post by taurus on 2006-11-07
Check to see if you still have flash 9 plugin for your firefox.  Type this in at the address field.

```
about:plugins
```

---

### Post by thomasaaron on 2006-11-07
It looks like it is saying that Flash 7 and 9 are both enabled?


Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 d55

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by thomasaaron on 2006-11-07
OK, I think I got it figured out -- hopefully permanently.

It appears that both flash 7 and flash 9 were enabled.

I put the new plugin in ~/.mozilla/plugins. 
But it appears that in /usr/lib/flashplugin-nonfree , it was still using the flash 7.

So, I manually swapped out that plugin and everything is working -- for now.

Thanks for pointing out  the about:plugins thing. Without that, I probably would have never figured out that both versions were enabled.

Best,
T

---

### Post by taurus on 2006-11-07
> **thomasaaron said:**
> OK, I think I got it figured out -- hopefully permanently.

It appears that both flash 7 and flash 9 were enabled.

I put the new plugin in ~/.mozilla/plugins. 
But it appears that in /usr/lib/flashplugin-nonfree , it was still using the flash 7.

So, I manually swapped out that plugin and everything is working -- for now.

Thanks for pointing out  the about:plugins thing. Without that, I probably would have never figured out that both versions were enabled.

Best,
T
Glad to hear you get flash 9 working, mate.

---

### Post by T'sora on 2006-11-12
Wow, I'm so glad I stumbled upon this thread. This was the exact same problem that my flash player 9 install was having. I'm fairly certain many others are having this problem without knowing it. Hope this helps get the word out.

Thanks for the help!

---

