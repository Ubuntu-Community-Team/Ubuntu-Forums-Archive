---
title: "pvr-150 video quality very poor in mythtv..."
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by railso on 2006-12-03
after 5 hours I finally got mythtv set up with ubuntu edgy. and the video quality sucks. it's grainy and looks like an overcompressed jpeg. the tv right next to me is fine.

what could it be? I googled a bit and found nothing relevant to the PVR-150...I followed the exact instructions on the [here]("https://help.ubuntu.com/community/Install_IVTV_Edgy"), and got whichever version of ivtv it got (0.72 I believe)

the first hour was nice and smooth, and since then nothing but frustration. couldn't get TV out to work, getting dumped to a blank screen multiple times, and finally everything is set up and it's fairly disappointing...I hate to say it, but I'm considering just installing windows - know how to use it, never had a problem, no driver issues...but I'm willing to give ubuntu another chance (it's quite pretty), but not if it'll take up every evening to figure out. I know many people have edgy+mythtv+pvr-150 and say it's great, so there's got to be a fix.

anyone know what I can do?

---

### Post by railso on 2006-12-03
one more thing: I'm viewing this on an LCD screen, so it's possible that it looks low quality because the higher resolution is magnifying the regular-def tv broadcast...is it?

---

### Post by FluffyElmo on 2006-12-03
Sorry, I don't have access to my Myth box at the moment so this will be a little vague and rambling...

First, LCD will make it look poorer. If you have a fast machine you can enable various post-processing filters to improve playback quality. I think it involves entering a command line in the set-up, it's not intuitive but the Myth documentation has some examples I think.

Second, somewhere in the setup you can change the LiveTV Profile settings. If you increase the bitrate and card recording profile (I think DVD gives the best quality) you will get better quality. The default is pretty low I think.

It's a question of disk-space vs quality really. If you go with a high LiveTV bitrate be sure to increase your TV buffer size. You can also change your recording profiles, or set up more than one for different programs.

Recordings are trickier because you have to choose between high quality and fewer hours of recording or lots of recording time with some blockiness. Most people I know (myself included) started high and end up reducing quality to record more.

As a general rule, I think the maximum bitrate of the PVR150 is ~11MBPS, if you ever plan to burn recordings to DVD the max allowable bitrate for DVDs is ~9MBPS (9.6?). There are charts online which compare recording quality vs bitrate and it may save you some experimentation.

Hope this helps a little, the bad news is that recording settings are a little bit of a black-art and very subjective. You can get very good results with the PVR-150 but it will take experimentation to find a balance you can live with.

To start though, increasing your LiveTV bitrate and card profile will get you a better idea of what the card is capable of.

---

### Post by railso on 2006-12-03
thanks for the tips. increasing the bitrate didn't seem to do much. I'm currently recording something, I'll check it out after and hopefully get the TV out to work. if it looks bad on a TV screen as well, there has to be something else wrong. interestingly, even when the video is played back at a smaller size it looks grainy and the colors are poor, I would have thought it would look better scaled down since TV resolution doesn't compare to an LCD.

---

### Post by railso on 2006-12-03
well, the recording looks pretty awful. grainy, washed out colors, looks like an overcompressed jpeg. this is with a higher bitrate. it's basically unwatchable, so I'm not sure where to go next.

I found some screenshots at mythtv's site [here]("http://www.mythtv.org/modules.php?name=MythFeatures"), and interestingly my picture looks a bit like those. but those screenshots are also grainy, noisy, and fuzzy...is this just how it looks?

---

### Post by railso on 2006-12-04
ok, I tried resizing my mythtv from fullscreen to 720x480 which seems to have helped. I also think it could be partially a signal issue, I tried hooking it up directly to the cable line instead of via a splitter as I had it, and I think it helped a bit.

video still seems a bit "soft" (not sure how to describe it), like a compressed PC video and not actual TV. but it's better, so maybe some more tweaking and I won't have to go back to windows after all :)

---

### Post by superm1 on 2006-12-04
Here are some samples of content that I have recorded that you can reference.  If yours is significantly worse then mine, then we have some problems.

[http://people.atrpms.net/~mlimonciello/test_content/](http://people.atrpms.net/~mlimonciello/test_content/)

---

### Post by FluffyElmo on 2006-12-04
Also note that Myth records at 480x480 by default. It looks much better when you set it to 720x480 in the Profiles.

---

### Post by superm1 on 2006-12-04
The two clips from the PVR-500 that are included there were set to record at 720x480 btw.

---

