---
title: "Using OSS instead of Alsa"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by k@zp3r on 2006-01-17
After struggeling to get Skype to work with Alsa, I finally decided to try to unload the alsa modules and try with Oss, which seems to work without any problems. (Alsa is not officially supported, yet, only Oss. Damn proprietary software :-))

Now, what is the "official Ubuntu way" to use Oss instead of alsa? I guess I could blacklist the alsa module in question (snd-cs46xx) and force the loading of cs46xx in /etc/modules, but I wanted to know if there's more I have to do to or a better way to make my system use oss.

Also, does anyone have any other ideas or options? I don't really need to use Skype as it's mainly for speaking to my girlfriend in another country (who runs Windows). If there are any alternatives that runs on both platforms I could use that instead, but so far I haven't found any. (I couldn't make Wengophone work and didn't really bother too much since it's still in a very early stage of development). Webcam support would be very cool too, but that isn't even supported by the linux version of skype yet.

Thanks a lot!

---

