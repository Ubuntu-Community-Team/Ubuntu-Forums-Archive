---
title: "Graphics conflict with ATI, compiz, and kdenlive"
date: 2010-03-01
forum: Multimedia Software
---

### Post by madscientist032 on 2010-03-01
I&#8217;m trying to edit a video with Kdenlive (0.7.7.1) in Ubuntu 9.04 (32-bit). Kdenlive works fine (read: playback of video in the preview box is of whole video) before I had enabled the restricted ATI drivers for Compiz. However, I have seen videos on YouTube where the user has Compiz running and Kdenlive running and there are no problems.  I have modified my ATI drivers to include the support from past releases because of a noticeable lag in minimizing / closing / maximizing windows. I used this fix in the forums (you have to scroll down to see the post I&#8217;m referring to: [http://ubuntuforums.org/showthread.php?t=1145967&page=3](http://ubuntuforums.org/showthread.php?t=1145967&page=3))

So after I&#8217;ve finished enabling ATI&#8217;s restricted drivers and after modifying the drivers (to remove the response lag), playback in Kdenlive will not work correctly. During playback, the video in the preview pane will zoom in to the middle of the video clip, thereby rendering the preview pane to be unusable.
Obviously, I would like to have the preview pane in kdenlive work properly when Compiz is enabled. 

Thanks in advance!

---

### Post by madscientist032 on 2010-03-02
So far the only workaround I have found was to disable Compiz by going to desktop, right-click -> change desktop background -> desktop effects -> none"

So when Compiz is running with desktop effects, video playback in the preview pane of kdenlive is zoomed in. When Compiz is turned off (read: Desktop effects are set to 'None') the video playback in the preview window of kdenlive is fine.

Disabling compiz / desktop effects is the only workaround I've seen that works.

---

### Post by acozzi on 2010-11-22
> **madscientist032 said:**
> I’m trying to edit a video with Kdenlive (0.7.7.1) in Ubuntu 9.04 (32-bit). Kdenlive works fine (read: playback of video in the preview box is of whole video) before I had enabled the restricted ATI drivers for Compiz. However, I have seen videos on YouTube where the user has Compiz running and Kdenlive running and there are no problems.  I have modified my ATI drivers to include the support from past releases because of a noticeable lag in minimizing / closing / maximizing windows. I used this fix in the forums (you have to scroll down to see the post I’m referring to: [http://ubuntuforums.org/showthread.php?t=1145967&page=3](http://ubuntuforums.org/showthread.php?t=1145967&page=3))

So after I’ve finished enabling ATI’s restricted drivers and after modifying the drivers (to remove the response lag), playback in Kdenlive will not work correctly. During playback, the video in the preview pane will zoom in to the middle of the video clip, thereby rendering the preview pane to be unusable.
Obviously, I would like to have the preview pane in kdenlive work properly when Compiz is enabled. 

Thanks in advance!




I got the same problem and find a solution adding this line in the KDEnlive launcher
env XLIB_SKIP_ARGB_VISUALS=1 kdenlive
just replace the launcher or execute this from a terminal, you don't need to disabled the desktop compiz
mi lap is an Dell with ATI and work fine!!

---

