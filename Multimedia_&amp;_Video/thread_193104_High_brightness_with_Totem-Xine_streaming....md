---
title: "High brightness with Totem-Xine streaming..."
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2006-06-09
Whenever I stream a video using Totem-Xine, the colors are washed out by really high brightness.  The program has the proper settings in and of itself, and it is fine when watching downloaded video.  

I secondary-clicked and chose 'Preferences,' but the dialog does not come up that would allow me to modify any settings.

Is this a known bug?  Can it be fixed?

Thanks, everyone!

---

### Post by aniceyoungman on 2006-06-09
I had this problem too with my old install of breezy (never could figure out a fix), but since I installed dapper the problem remains no more.  Sorry...

---

### Post by Donshyoku on 2006-06-11
I am getting it now with MPlayer streaming too.  Is there something wrong with my setup?  Are they using some borked files in tandem?  

I am off to try VLC now... that is the last media player I know of having a FF plug-in...

---

### Post by muhkayoh on 2006-06-12
I'm having the same problem.  In my case, all video playback from all video players is suddenly bright and washed out.  It seemed to happen after I applied a fix to get sound from a swf file.  Not sure the two are related, but the one did follow the other.  I've searche dfor a fix for the video problem, but I haven't seen aything that seemed definitive enough to try.

Matt Jordan

---

### Post by Jeff250 on 2006-06-13
Do you have an Intel video card?
See this bug:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/32963/+index](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/32963/+index)
If this is the case, comment in the above link that you also have this problem to make sure this bug has enough momentum.  There are two other things you can do for now:  Switch to a renderer other than Xv (such as xshm or gl), but this is a really bad option since high-quality video like DVD's will be choppy using non-Xv renderers.  Best thing you can do for now is in Totem, go to the preferences menu, display tab, and then turn the contrast from 50% to about 30%.  This restores video to normal.

If you're using a non-Intel video card, I'm afraid I can't help, but search launchpad.net for perhaps a similar bug with your graphics card.

---

### Post by muhkayoh on 2006-06-13
[QUOTE=Jeff250]Do you have an Intel video card?
[/QUOTE]

Forgive the rookie question, but how do I tell?  I've been poking around for a while trying to figure it out here and over at LinuxTopia's Ubuntu guide, but I can't find the command to tell me what video card I have.

Thanks,

Matt Jordan

---

### Post by Jeff250 on 2006-06-13
Probably the easiest way is to copy and paste this into a terminal:
```
lspci | grep VGA
```
For example, when I run that command, I get:
> 0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

### Post by muhkayoh on 2006-06-13
Thanks!

Here's what I have:

> 0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by Donshyoku on 2006-06-14
I can't change the Contrast in Totem as it crashes when I open the program itself.  It opens and immediately closes the window.  It has been doing this since Dapper Flight 2, and I haven't found a fix yet.

If I play a video, it will load and play without crashing.  I will go DL something and then change the contrast there, and report back on my streaming issue.

---

### Post by Donshyoku on 2006-06-14
Hmm... lowered the contrast and brightness in the player and now my streaming is better.  A little odd considering I thought they were playing normal videos fine, just not streams.  Guess I was wrong.

Donshyoku = owned

Problem = solved

Thanks again!

---

### Post by Jeff250 on 2006-06-15
[QUOTE=muhkayoh]Thanks!

Here's what I have:[/QUOTE]

Yep, you also have an Intel video card.

---

### Post by muhkayoh on 2006-06-15
[QUOTE=Donshyoku]I can't change the Contrast in Totem as it crashes when I open the program itself.  It opens and immediately closes the window.  It has been doing this since Dapper Flight 2, and I haven't found a fix yet.[/QUOTE]

I also have this Totem/crashing problem.

And thanks again, Jeff250.

Matt Jordan

---

### Post by aleska on 2006-09-13
> **Jeff250 said:**
> Best thing you can do for now is in Totem, go to the preferences menu, display tab, and then turn the contrast from 50% to about 30%.  This restores video to normal.


Thanks very much Jeff.  Changing the contrast works like a charm for me.  You da man!

---

