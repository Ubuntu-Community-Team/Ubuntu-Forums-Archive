---
title: "Sloppy video playback in Browser"
date: 2014-03-02
forum: Multimedia Software
---

### Post by theterminalrocks on 2014-03-02
hi there,

first of all -being a former windows user- i have to say i'm quite impressed: Installation of Kubuntu (13.10.) was hasslefree and various devices were recognized right out of the box.....
BUT the sloppy playback of videos in any browser is driving me nuts (720p or higher results in slowmotion playback on youtube and alike).
 
At first i thought it was a drivers issue with the Radeon 6570 so i tried different drivers with no better results, in contrary other drivers seem to put more strain on Xorg Cpu usage so i went back to the initially installed driver (lib/modules/3.11.0-12-generic/kernel/drivers/gpu/drm/radeon/radeon.ko)
 Weird thing: the same video downloaded plays just fine in for instance Kaffeine which I guess rules out a driver issue as well.
 

 After some reading thought the culprit here was flash: tried out like gnash, lightspark with no luck; I then installed viewtube, playback was still sloppy but again the downloaded file played fine in Kaffeine.
 

 Needless to say that whilst trying to play such a video in Firefox (or Chromium, Chrome) the CPU usage rockets up to like 60%; strangely enough it works in Firefox under XP :O

 

 Any thoughts?
 Thx

---

### Post by raccoonstrait on 2014-03-02
I have a similar issue, and I find this very interesting. If I install flashplugin and go to YouTube in Firefox the videos are squashed to half size and are at an extremely low resolution. In short; not only un-viewable, but are often not stoppable because the controls are not visible. 

If I then uninstall the flashplugin and go back to the same video, it works beautifully. Now I understand that it is HTML5 taking over there. 

My issue is there are some websites still that stupidly (always has been stupid) use flash on their homepage, and maybe further, but without flash you cannot find out. 

I tried one of the Firefox add-ons, and read about several others. The one I tried did nothing, and the others say they will block all flash. 

So what's the difference with having no flash at all, or having flash and a blocking plugin? 

Second, how can I (oh I know, stop laughing) use flash sites but opt for HTML5 on video?

Some computer info below, let me know what else might be needed.

Racconstrait

Think-pad R50e, 756 MB RAM, Intel GSM graphics, Saucy up to date latest generic kernel, Xfce and KDE both installed and work, Ubuntu desktop does not.

---

