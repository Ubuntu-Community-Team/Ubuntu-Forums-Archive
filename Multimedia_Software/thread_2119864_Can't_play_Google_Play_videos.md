---
title: "Can't play Google Play videos"
date: 2013-02-25
forum: Multimedia Software
---

### Post by tornadoes28 on 2013-02-25
I am not able to play movies or TV shows from Google play. I contacted Google play and was told this:

In order to watch on Google Play with computers running Linux OS you must install a HAL module. Please follow the instructions provided in the link below to install the necessary module: 

[http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html](http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html)

Here are the instructions:

For Ubuntu 10.04 or later, ensure that the Hardware Abstraction Layer module is first installed using apt-get.
(Watch carefully for “hal” install errors, as a damaged package install can continue to affect video playback.)

sudo apt-get install hal

After the "libhal" (HAL) library install completes, close the browser and clear the Adobe Access directories by executing the following shell commands:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

Note:
If the Hardware Abstraction Layer module is missing, Flash Player still functions. However, it cannot play protected content that requires the Adobe Flash Access DRM (Digital Rights Management) module.



I followed the instructions however I am still not able to play the videos. I contacted Google again but I wanted to find out if anyone here had a solution.

---

### Post by carl4926 on 2013-02-25
Try rebooting

---

### Post by tornadoes28 on 2013-02-25
I did but no go. 

But I received another reply from Google stating that reports of similar issues on Chrome browsers on Linux and they are working on it. So maybe the next browser version will fix it.

---

### Post by carl4926 on 2013-02-25
I can't test it for you as the movies are Pay for.

I can tell you it's all connected to DRM.

---

