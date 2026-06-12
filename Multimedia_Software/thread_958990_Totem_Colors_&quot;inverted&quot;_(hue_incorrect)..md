---
title: "Totem Colors &quot;inverted&quot; (hue incorrect). looking for a real solution."
date: 2008-10-26
forum: Multimedia Software
---

### Post by mobrien118 on 2008-10-26
Hello,

I have the most recent RC of Intrepid. I upgraded when Intrepid was mid-beta. When I did, I also changed hardware to an Nvidia 8500 card. I am using the most current and highest version of the NVidia drivers packaged in the restricted Ubuntu packages. (177 I think). Ever since I did this, the colors in videos I watch open in Totem (the default and I like it) have blue people and all kinds of crazy colors.

If I open the Nvidia control panel, it immediately fixes the colors until I close the movie and open another (or the same one again). The first time I actually clicked the "restore defaults" button in the Nvidia control panel.

I have found a number of threads talking about solutions to the problem. My temporary fix is to mis-adjust the "Hue" in Totem to reverse the effects of the improper Hue as suggested in this thread: [http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white](http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white)

I also see a solution that involves changing a symlink, which I really don't want to do because it blatantly corrupts the "cleanness" of my system and from what i have read, can lead to other problems or loss of functionality and will be reverted if the package is upgraded or re-installed anyway.

So what I'm looking for is a solution where I change a config file somewhere, or for a more permanent solution, like that the bug actually gets fixed.

Any help anyone can offer would be awesome!

Thanks!

--mobrien118

---

### Post by cor2y on 2008-10-26
Sorry theres no final/real solution.
This rests solely on the shoulders of Nvidia.
The Open Source nv drivers do not have this problem, its all a Nvidia thing they reversed the hue settings in their drivers and now refuse to fix it.

---

### Post by sonicb00m on 2008-10-26
Yes it's really annoying. Any fix seems very temporary and after a few open/closes the hue problem returns.

---

### Post by Sandworm on 2008-10-26
Similar problems here, Started with this morning's update, all video players are affected, except my video editing software.  

I found a somewhat easier trick.  For some reason if I play the same file simultaneously in two windows, the second to open seems to be fine.  Damb strange bug.
-Sandworm

---

### Post by sonicb00m on 2008-10-28
I've put the nv driver  back on until this is fixed. No idea how to find that out though.

---

### Post by mobrien118 on 2008-10-28
The nv drivers don't work well enough for me (using a 1360x768 LCD-TV as my monitor, which isn't auto-detected in nv and trying to run PS3Grid on the graphics card, not to mention inferior GLX etc.)

Does anyone know how to successfully file a formal bug report? I have done it through the integrated tool in Ubuntu, but not directly. I have seen this bug listed for Hardy, etc., but I think we should file a new one for the new driver and OS. The previous one was mostly directed at the "Pink border" issue, which is related to this one, but I think this should be a separate issue. Also, I think the pink border issue is already solved independently.

Anyone have the knowledge/time to do this for this issue?

Thanks,

--mobrien118

---

### Post by yuribroze on 2011-10-22
[http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)

Solution is there.  Essentially,

```
$ gstreamer-properties
```

Now click on the Video tab. From the Plugin dropdown box select Custom. Finally add the following line to the Pipeline box.

```
videobalance hue=-1 ! autovideosink
```

---

