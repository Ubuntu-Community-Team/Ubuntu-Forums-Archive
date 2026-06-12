---
title: "Myth TV Picture tearing - Unusual"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by jethro10 on 2007-03-02
Hi, 
nearly finished my myth tv box and have a strange visual problem.

When playing live tv, the picture looks like a comb effect on movement. BUT when I record, and play back the recording, its perfectly ok.

Playing DVD's or other mpeg, avi clips movies etc are all ok.

It looks like interlacing, or if live is PAL but its sent to the TV as NTSC. I have checked the menu in the live tv screen and changed all the options for interlaced, progressive etc.

Its with an ATI radeon card, proprietary binary drivers and a 1360x768 32" LCD tv via a proper PC input. PC runs at about 12% processing power, so its not that.
Is live TV and play back of recording using a different player? 
Sorry, i'm rather stuck.

J

---

### Post by newlinux on 2007-03-29
> **jethro10 said:**
> Hi, 
nearly finished my myth tv box and have a strange visual problem.

When playing live tv, the picture looks like a comb effect on movement. BUT when I record, and play back the recording, its perfectly ok.

Playing DVD's or other mpeg, avi clips movies etc are all ok.

It looks like interlacing, or if live is PAL but its sent to the TV as NTSC. I have checked the menu in the live tv screen and changed all the options for interlaced, progressive etc.

Its with an ATI radeon card, proprietary binary drivers and a 1360x768 32" LCD tv via a proper PC input. PC runs at about 12% processing power, so its not that.
Is live TV and play back of recording using a different player? 
Sorry, i'm rather stuck.

J

They shouldn't be using different players for playback unless you configured them to do so. Out of curiousity, do you do any transcoding of your recordings? When watching live tv when you rewind and watch a clip again do you still have the combing? What deinterlacing filter are you using (what do you have mythfrontend setup to do by default? I think the path to get there is Utilities/Setup->Setup->TV Settings->Playback but I'm not sure. You also might want to look at your recording profiles to see what is going on there...

Sorry I couldn't be more helpful at this point.

---

### Post by jethro10 on 2007-05-05
After a lot of heartache,
it was deinterlacing causing it.

Thanks
J

---

### Post by sikk on 2008-01-04
Thanks for posting the resolution, you saved me a bunch of heartache with 5min of search :)

---

