---
title: "Poor video quality after installing Feisty"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by shane_on_u on 2007-04-30
I recently did a clean install of my system from Edgy to Feisty. The only problem I'm having in Feisty is with video playback quality. Video playback (xvid, divx, dvd) is horribly pixelated with occasional tearing. These same files used to run perfectly under Edgy.

I've tried Totem/xine, VLC, Mplayer and all with the same results. Does anyone have any suggestions? My computer is currently useless for video.

---

### Post by disturbed1 on 2007-04-30
What type of video card are you using?

I'd check that the correct drivers are installed. Depending on the type of card, there are some options you might want to try in xorg.conf to get better video playback.

---

### Post by shane_on_u on 2007-05-01
> **disturbed1 said:**
> What type of video card are you using?

I'd check that the correct drivers are installed. Depending on the type of card, there are some options you might want to try in xorg.conf to get better video playback.



I have an ATI x850xt. I just disabled the restricted driver and my video is pretty decent again. Don't remember if it's as good as it was under Edgy but I suppose that means it's close enough. Any idea what settings might need configuring to get decent video quality from the restricted driver?

Thanks,

Shane

---

### Post by disturbed1 on 2007-05-01
With fglrx make sure you have
Option      "VideoOverlay" "on"
in your xorg.conf under the device section.

---

### Post by kircher on 2007-05-01
I have the same problem since I upgraded to feisty. I tried totem-xine, mplayer and VLC and it was still poor quality. I changed my Nvidia drivers to the proprietary ones in the repository, but there was no change. I installed the latest Nvidia driver from the nvidia download website, and there was also no change. I guess it's called "pixellating" and "tearing" as described by the shane_on_u. As it was not an issue with edgy, I imagine this is a configuration problem. Can anyone help me with what to change in xorg.conf? I have attached a screen shot of what is happening. This is totem-xine, but vlc and mplayer are no different. I am using an NVidia 6600GT card, with the latest proprietary drivers. As far as I know, this only occurs with DVDs. I have been watching other videos with no problems.

---

### Post by disturbed1 on 2007-05-01
> **kircher said:**
> I have the same problem since I upgraded to feisty. I tried totem-xine, mplayer and VLC and it was still poor quality. I changed my Nvidia drivers to the proprietary ones in the repository, but there was no change. I installed the latest Nvidia driver from the nvidia download website, and there was also no change. I guess it's called "pixellating" and "tearing" as described by the shane_on_u. As it was not an issue with edgy, I imagine this is a configuration problem. Can anyone help me with what to change in xorg.conf? I have attached a screen shot of what is happening. This is totem-xine, but vlc and mplayer are no different. I am using an NVidia 6600GT card, with the latest proprietary drivers. As far as I know, this only occurs with DVDs. I have been watching other videos with no problems.

That's called interlacing ;) Just turn on the deinterlacing filter in which ever app you are playing back with.

---

### Post by kircher on 2007-05-02
> **disturbed1 said:**
> That's called interlacing ;) Just turn on the deinterlacing filter in which ever app you are playing back with.

Ok, thankyou. I failed to mention in my last post that I had tried deinterlacing, but then everything looked rough. Fast moving scenes flowed much better without the "interlacing", but it still didn't look as good as it did when using edgy. I didn't use the "deinterlace" filter in edgy, or dapper for that matter because I remember turning it on by accident and noticing how rough everything looked. These two screenshots show what I mean. "smooth.png" is with the deinterlace filter off, and "rough.png" is with it on. If no one knows how to solve this, I guess I can deal with watching dvds with the deinterlace filter on for now. Thank you.

---

### Post by disturbed1 on 2007-05-02
Try using VLC, it has a few different deinterlacing filters. I find myself sometimes using the "X" filter, and sometimes using the "linear" filter. Just depends on how the studio mastered the footage.

---

### Post by KonoKanji on 2007-05-03
[center]For anyone using the new ATI Fglrx Driver [8.36.5], the problem is stated in the release notes:

> - Video tearing during playback. Further details can be found in topic number 737-26984.

I'm not sure why they would release it with this much video tearing, but it only seems to be bother some users.

The rest of the information can be found here:
[http://wiki.cchtml.com/index.php/8.36.5]("http://wiki.cchtml.com/index.php/8.36.5")[/center]

---

### Post by WorLord on 2007-07-18
I'll be darned.  All this time, I've been using other players because i thought Totem-Xine just flat didn't work right in Feisty.  The "Deinterlace" option was checked, making everything look like "rough.png" in this thread.  

Yay!  Have my favorite media player back.  You guys rock.

---

