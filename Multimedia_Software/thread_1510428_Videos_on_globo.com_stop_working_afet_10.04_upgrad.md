---
title: "Videos on globo.com stop working afet 10.04 upgrade"
date: 2010-06-15
forum: Multimedia Software
---

### Post by nat on 2010-06-15
Hi,

I upgraded my wife's ubuntu to 10.04 and after that all videos on [http://video.globo.com](http://video.globo.com) stopped to work. The video player loads and it looks like it start loading but it loads forever.

I think adobe flash works properly since youtube works.

Any ideas?

---

### Post by lovinglinux on 2010-06-16
Make sure you have the latest version of flash and don't have any conflicting plugins.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

I'm a globo.com subscriber and the author of that extension. Globo is working really nice with flash 10.1 r53, including fullscreen. So feel free to ask any additional questions.

---

### Post by nat on 2010-06-21
Thanks alot for the answer, I tried the plugin but same thing happened.

In fact, I had the same issue on my arch linux (64bit) and it even happened on windows firefox in wine (running on my alpine linux laptop).

I tried the midori browser and there the video just worked, so I figured there must be something with firefox that blocked the video. I disabled the adblock plugin and it started to work.

So I ended up adding an exception for ads.globo.com in the adblock whitelist. Now things works.

Thanks!

---

### Post by lovinglinux on 2010-06-21
> **nat said:**
> Thanks alot for the answer, I tried the plugin but same thing happened.

In fact, I had the same issue on my arch linux (64bit) and it even happened on windows firefox in wine (running on my alpine linux laptop).

I tried the midori browser and there the video just worked, so I figured there must be something with firefox that blocked the video. I disabled the adblock plugin and it started to work.

So I ended up adding an exception for ads.globo.com in the adblock whitelist. Now things works.

Thanks!

I forgot about that. Globo videos doesn't work if you block the ads. This started to happen about a month ago.

---

### Post by boobsbr on 2010-11-23
Great tip, just turned Adblock Plus off and it worked!

---

