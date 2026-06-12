---
title: "KaudioCreator, Amarok and KsCD won't detect Audio CDs"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by MalachiConstant on 2006-11-28
Hi there,

I just switched from Xp to Kubuntu 6.10 a few weeks ago. Having a blast so far, though I a few strange issues...

One of them is KaudioCreator, KsCD and Amarok not detecting my Audio CDs. Last week, I wanted to rip a CD. At first Kaudio didn't detect it, then after a while, for no apparent reason, it suddenly did. Now I wanted to rip some more CDs, but none is detected. The CDs appear as audio CDs on my Desktop, though. And I can play them with caffeine.

Any suggestions? Thanks!
 janus

---

### Post by MalachiConstant on 2006-11-30
I hope bumping is not against the forum rules. I still have the same problem and absolutely no clue how to solve it. You think a fresh install of Kubuntu would do the trick? Maybe I removed a necessary package. Though I really can't imagine which one that could have been. Is there a list of the packages needed for KAudioCreator? I already checked the dependencies in Adept and they seem to be fine...

---

### Post by MalachiConstant on 2006-12-05
Ok, the issue is solved. There appears to be a rather stupid bug in recognizing audio CDs. When you insert a CD, a dialog box opens asking what to do with it. I chose "do nothing". And that caused some programs not to recognize audio CDs at all. Now I activated "extract and encode audio files" and KAudioCreator detects the CDs just fine. But every time I insert a new CD, a new instance of KAudioCreator starts. And funnily all open instances will start ripping the CD, causing massive chaos. So I have to close one instance every time I insert a CD. Not a very comfortable way of ripping...

---

