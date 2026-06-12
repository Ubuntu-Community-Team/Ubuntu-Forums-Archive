---
title: "Video files playing in Negative colors?"
date: 2011-04-30
forum: Multimedia Software
---

### Post by louscookies on 2011-04-30
So, I upgraded to 11.04. Everything seems to running okay, but when I go to play a video file, the colors are all screwed up. It looks like they're almost negative in the way that they are displayed.

Does anyone know of any way to fix this?

---

### Post by louscookies on 2011-05-03
Nobody? :(

---

### Post by dnguyen1963 on 2011-05-03
> **louscookies said:**
> So, I upgraded to 11.04. Everything seems to running okay, but when I go to play a video file, the colors are all screwed up. It looks like they're almost negative in the way that they are displayed.

Does anyone know of any way to fix this?

I have the same problem and have been asking this forum multiple times without any response.  The only work-around solution so far is to open the video with another player such as smplayer then you can use Movie Player or VLC to watch the clip (You can stay with smplayer if you want.  In my case, I have no sound when I play a video with smplayer).  The other option is to clear out all the cookies and re-start your computer.

---

### Post by wittmaniac on 2011-05-04
I was having a similar problem. It's related to the proprietary Nvidia drivers (aka the worst driver in the history of drivers). Here is a link for some basic instructions on [fixing blue tinted videos in Ubuntu]("http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu"). Most notably, the following fix from the comments worked fine for me:

> For me the problem was in the &#8220;NVIDIA X-Server Settings&#8221; and the tab  called &#8220;X Server XVideo Settings&#8221;. The HUE was at the wrong setting (  all the way down ). Use &#8220;Reset hardware defaults&#8221; to bring it back to  its nominal value. Voilà!

---

### Post by dnguyen1963 on 2011-05-05
> **wittmaniac said:**
> I was having a similar problem. It's related to the proprietary Nvidia drivers (aka the worst driver in the history of drivers). Here is a link for some basic instructions on [fixing blue tinted videos in Ubuntu]("http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu"). Most notably, the following fix from the comments worked fine for me:

I have an Intel drivers, not Nvidia.  Not sure if this will work, but I'll give it a try tonight.

---

### Post by Romu on 2011-05-06
Hi,
I faced the same issue some months ago on my mother's PC, the fix was to go to the Totem preferences and move the "Hue" slider full left or full right.

Hope this helps.

---

### Post by dnguyen1963 on 2011-05-09
> **Romu said:**
> Hi,
I faced the same issue some months ago on my mother's PC, the fix was to go to the Totem preferences and move the "Hue" slider full left or full right.

Hope this helps.

This and the suggestion from above did not work for me...still the same old problem.

---

### Post by G_Dem on 2011-05-09
Does it look like this??? I think I might have the same problem too.

[http://ubuntuforums.org/showthread.php?t=1753944](http://ubuntuforums.org/showthread.php?t=1753944)

---

### Post by HeYzN on 2012-03-06
> **wittmaniac said:**
> I was having a similar problem. It's related to the proprietary Nvidia drivers (aka the worst driver in the history of drivers). Here is a link for some basic instructions on [fixing blue tinted videos in Ubuntu]("http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu"). Most notably, the following fix from the comments worked fine for me:


Thanks!
I had same problem and this solved it!

---

