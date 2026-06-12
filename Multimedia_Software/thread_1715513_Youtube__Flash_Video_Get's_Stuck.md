---
title: "Youtube / Flash Video Get's Stuck"
date: 2011-03-27
forum: Multimedia Software
---

### Post by SneakPeak on 2011-03-27
Hi,

(Problem Solved using Flash replacement described by LovingLinux)

I am having strange behavior from some youtube videos. The video starts to play normally but then gets stuck. Sometimes if one moves the slider on a second or two it resumes playing but sometimes not. This is not a buffering issue as the whole video appears to have been downloaded but it just won't play past a particular point.

For example.  "National Geographic World's Most Typical Person" gets stuck at around 35 seconds.  One can bump it along and it continues but then it gets stuck again at about 1:24 and nothing makes it work.  

Strangely I have virtual box running with a Windows XP virtual machine.  The behavior is exactly the same on the XP machine.  I have tried Chrome and Firefox and both have the same problem.  I can't get any youtube videos to play in Totem.  

I have searched the web and it seems other people have had the same problem but I can't find a solution anywhere that works.

Any help would be appreciated.

Thanks

Sneaks.

---

### Post by lovinglinux on 2011-03-27
Get [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") and [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer") extensions.

---

### Post by SneakPeak on 2011-03-27
Hey LovingLinux,

Thanks for the response. FlashVideoReplacer seems to do the job.   Only problem is I now have many, many pauses while the video is buffering.  (I live in South Africa, connections are slow).  What I normally do is pause the video and leave it to download for a few minutes and then I press play and normally I can watch all the way through before the play catches up to the download if you know what I mean.  With FlashVideoReplacer this doesn't seem to be the case.  It looks, as far as I can tell that there is no buffering during playback or pause?  I looked at the preferences but couldn't find any settings to change.  

Any ideas?

Thanks

Sneaks

---

### Post by lovinglinux on 2011-03-27
> **SneakPeak said:**
> Hey LovingLinux,

Thanks for the response. FlashVideoReplacer seems to do the job.   Only problem is I now have many, many pauses while the video is buffering.  (I live in South Africa, connections are slow).  What I normally do is pause the video and leave it to download for a few minutes and then I press play and normally I can watch all the way through before the play catches up to the download if you know what I mean.  With FlashVideoReplacer this doesn't seem to be the case.  It looks, as far as I can tell that there is no buffering during playback or pause?  I looked at the preferences but couldn't find any settings to change.  

Any ideas?

Thanks

Sneaks

The buffering option needs to be modified in the plugin config, not my extension. For instance, if you are using gecko-mediaplayer, then the config file is locates at ~/.mplayer/config

For example, add the following to the [default] section:

```
[default]
cache=8192
cache-min=20.0
cache-seek-min=50
```

Change the values to your linking.

---

### Post by SneakPeak on 2011-03-27
Ok, thanks,

I know this is a really stupid question but how do I know what plugin I am using?  I thought FlashVideoPlayer was it.  I am a bit confused because I couldn't get Totem to play youtube.  Is my plugin Totem?

Sneaks

---

### Post by lovinglinux on 2011-03-27
> **SneakPeak said:**
> Ok, thanks,

I know this is a really stupid question but how do I know what plugin I am using?  I thought FlashVideoPlayer was it.  I am a bit confused because I couldn't get Totem to play youtube.  Is my plugin Totem?

Sneaks

Type **about[noparse]:[/noparse]plugins** in the address bar. Is probably totem.

I recommend removing totem and installing gecko-mediaplayer:

```
sudo apt-get remove totem-mozilla
sudo apt-get install gecko-mediaplayer
```

BTW, FlashVideoReplacer is not a plugin, is an extension. What it does is to replace the video content, so you can play it with a different plugin other than flash.

---

### Post by SneakPeak on 2011-03-27
Hi LovingLinux,

Problem solved.  I was using Totem.  I have replaced with gecko and all seems to be working well.

Thanks for your help.  Much appreciated.

(Of course problem persists in Chrome! Oh well I will use two browsers.)

Sneaks

---

### Post by lovinglinux on 2011-03-27
> **SneakPeak said:**
> Hi LovingLinux,

Problem solved.  I was using Totem.  I have replaced with gecko and all seems to be working well.

Thanks for your help.  Much appreciated.

(Of course problem persists in Chrome! Oh well I will use two browsers.)

Sneaks

You are welcome. A new version of FVR is coming soon, full of improvements.

---

