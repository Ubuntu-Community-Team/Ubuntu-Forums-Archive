---
title: "Playing flv video causes kernal panic"
date: 2012-03-01
forum: Multimedia Software
---

### Post by samuelsimon on 2012-03-01
I am running Ubuntu 11.10 with few changes from the standard installation and using get_iplayer  version 2.79-2. When watching downloaded flv files using Movie Player  after a few minutes the video freezes and the sound repeat a very short  loop or the screen switches to a text display with the bottom line  displaying "panic occurred, switching  back to text console". 

Any advice would be appreciated.

---

### Post by winh8r on 2012-03-01
Try going to the Ubuntu Software Centre and installing the following packages:


ffmpeg

x264


These are required by get i player in order to convert the flv to its preferred format.

Also, it might help you to click on the "Get Help With Flash" link in my sig below just to make sure you have the correct flash version installed and it is all configured correctly.

Hope this helps you.

---

### Post by samuelsimon on 2012-03-06
Thanks for the suggestions. I installed ffmpeg and x264. 

The versions I have are: 
ffmpeg: 4:0.7.3-0ubuntu0.11.10.1
x264: 2:0.116.2042+git178455c-1ubuntu1
get_iplayer: 2.79-2
totem moive player: 3.0.1-0ubuntu7.1

Unfortunately I still experience crashes when watching the flv files in Movie Player.

I have not tried FLASH-AID as this problem is not related to Firefox.

Any further advice would still be appreciated.

---

