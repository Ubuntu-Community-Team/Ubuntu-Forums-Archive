---
title: "Flash plugin skips on fully loaded youtube videos, won't display imeem."
date: 2009-08-14
forum: Multimedia Software
---

### Post by murderslastcrow on 2009-08-14
Well, after the video card on my perfectly fine lappy went out, my friend lent me the laptop I fixed for him. Direct rendering is on, compiz has amazing performance, so basically the video performance in everything else is amazing.

However, when it comes to flash, online, everything used to have a grey box with a play button (I guess to prevent huge ads from sucking up memory), and whenever I would play a youtube video, even if it were fully loaded, it would skip about 2 seconds every 30 seconds or so. Also, imeem flash boxes just wouldn't display at all. Just completely white.

So, I went to the flash website and installed the deb package. No more grey boxes with play buttons before I can view the content, but I still have the same jumping problems and the non-display issues on some websites.

I'm using firefox as updated through the update manager, no extra repositories.

Since the performance is perfect in every other aspect with this laptop, this is kind of a thorn in my side at the moment. I hope, if we're not switching over to HTML5 too soon, that flash releases a fool-proof flash plugin for linux.

Any helpful comments or observations are welcome.

---

### Post by murderslastcrow on 2009-08-14
Alright, I fixed it, but it took a while. Here's why...

I went to about:plugins and discovered the it said I was using Flash 9. So, I removed the nonfree flash plugin with synaptic, and the flash plugin installer package, and installed the version 10 deb from the flash website.

So I go back and lo and behold, it still says it's version 9. I repeat the steps to no avail. Then I look and find out the plugin name is libswfmozenc.so, or something like that. So basically, it's a mozilla specific package I didn't need that was overlapping the flash plugin I needed!

So, I just removed it from synaptic, no everything's working perfectly. :P I think we should stop trying to integrate firefox too closely, some days. I mean, not everyone uses it. @,@

Thanks for anyone reading this- I hope it helps people with a similar issue.

---

