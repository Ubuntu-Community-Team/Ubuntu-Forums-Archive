---
title: "Can't get streaming working in Chromium/Firefox in Karmic"
date: 2010-06-17
forum: Multimedia Software
---

### Post by olafurg on 2010-06-17
Hi

I've been going through the [Comprehensive multimedia and video howto]("http://ubuntuforums.org/showthread.php?t=766683") a couple of times and never get streaming going. When testing on the [Apple trailers]("http://trailers.apple.com/") site and [this here]("http://dagskra.ruv.is/frsjonvarp/") I don't get it to work.

I tried both streaming options set in the thread, (a) Gecko Media Player and (b) MPlayer Plug-in (removing the other one in between) and am getting very annoyed. Currently have option (a) installed.

Please if you are able to help me I'd be really grateful. What do you need to know?

---

### Post by olafurg on 2010-06-17
Update:

I had tried to remove totem and see if that made any difference (didn't) and now that I've added totem again then I'm offered to search for a suitable plugin when viewing [this here]("http://dagskra.ruv.is/frsjonvarp/") but get the result that no packages were found (reqested plugins are: text/html decoder). Re-adding totem has no effect on the [Apple Trailers site]("http://trailers.apple.com/"), still get asked to download QuickTime.

---

### Post by lovinglinux on 2010-06-27
> **olafurg said:**
> Update:

I had tried to remove totem and see if that made any difference (didn't) and now that I've added totem again then I'm offered to search for a suitable plugin when viewing [this here]("http://dagskra.ruv.is/frsjonvarp/") but get the result that no packages were found (reqested plugins are: text/html decoder). Re-adding totem has no effect on the [Apple Trailers site]("http://trailers.apple.com/"), still get asked to download QuickTime.

Having multiple plugins installed for the same type of content will most likely to cause trouble. Make sure you have only gecko-mediaplayer and all the necessary codecs installed. The Comprehensive multimedia and video howto works for me. I have gecko-mediaplayer and I'm able to play Apple trailers. Nevertheless, I was able to play only on a new FF profile, without NoScript, which is preventing the video from playing even when I allow scripts globally.

---

