---
title: "Upgrade from 9.10 to 10.04 broke video playback"
date: 2010-10-14
forum: Mythbuntu
---

### Post by Meph1st0 on 2010-10-14
After upgrading from 9.10 to 10.04 my video playback has gone nuts.  It appears that the RED and BLUE video channels are there but GREEN is not.  The picture is very dark and all I can see are red and blue colors.  Is there some sort of new RGB color adjustment setting in 10.04 that I'm not aware of?

Under settings-tv settings-playback-playback profiles I have the High Quality built in profile selected.  This is the same playback profile I used before with no problems.

I should clarify that this is only when watching video (whether it be live tv or a recording).  Everything else is just fine.

---

### Post by klc5555 on 2010-10-15
This may or may not be your issue, but I had apparently the same initial trouble ("smurfing") in Mythtv playback (and only in Mythtv) on a (non-Ubuntu) machine I moved from the Nvidia 177. series drivers to the 253. series. When I reverted back to 177. (and the earlier Xorg that didn't break 177.), the smurfing was gone. It took a while to figure out that all that was required with the 253. driver was to adjust the onscreen picture controls (particularly "hue", but also brightness and contrast) one time during a Mythtv playback to more reasonable values, and everything was permanently back to normal.

Hope this helps.

---

### Post by Meph1st0 on 2010-10-15
I love how spurious and seemingly unrelated my problems seem to be.  klc5555, thank you for your response.  It was very helpful.  I don't quite understand what you mean when you said you needed to adjust the on screen picture controls during a mythtv playback.  Did you mean that when something was playing you needed to press the M key to bring up the onscreen menu and then adjust it there?  The problem with this is that when I press the M key I can't see the menu due to the picture being so messed up.  Or were you talking about adjusting it in NVIDIA X Server Settings? Also, if I play the very same video in VLC I get the same weird picture colors.

I tried the other thing you suggested.  Going back to an older version of the NVIDIA drivers.  I don't see a version 177 in the Hardware Drivers window but I do see a version 173.  So I selected that one and activated it and then rebooted.  The cool thing is that after doing that the picture colors were back to normal....except, I lost my audio.  This is what I meant by saying that my problems seem spurious and unrelated.  I went back to the recommended (current) NVIDIA drivers (it doesn't say which version they are) and my audio came back but my picture colors are back to being messed up.

---

### Post by klc5555 on 2010-10-15
Sorry. From your initial post it sounded as though the problem was mythtv specific. Since vlc also suffers from this issue, then your Mythbuntu problem is not in the Myth, but rather in the 'buntu. So my particular issue and solution are not relevant to your case.

My personal choice would be to revert the Nvidia driver to the earlier level and try debugging the sound, which is likely easier than attempting to do it the other way around. I wonder if the first driver that loads is preventing the other from loading correctly, some sort of vmalloc issue, but I suppose lsmod, aplay -l, and a look at the syslog will begin to give you some debugging information.

Good luck.

---

### Post by Meph1st0 on 2010-10-16
Alright, well some degree of good news.  Last night I went ahead and took another leap and upgraded all the way to 10.10.  I still had the video issue so then I tried reverting back to the 173 version of the nvidia drivers which fixed the video issue AND I still have sound.  Now that's pretty cool.  So I'm going to go ahead and mark this thread as solved.  Thanks again for your help klc5555.  Now all I gotta do is get my remote to work again.  But that problem is in another thread.

---

### Post by klc5555 on 2010-10-17
Glad everything works! (Well, except for lirc, of course. I'd be tempted to backlevel that also to your earlier version --0.8.4a I suppose, since you were coming from 9.04. The change from 0.8.4a to 0.8.6 was a serious breakage point.) 

All the best.

---

