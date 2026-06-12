---
title: "AVI files running with Poor quality"
date: 2008-07-31
forum: Multimedia Software
---

### Post by virus2 on 2008-07-31
Hi All,

Iam facing problem with playing avi files on my Kubuntu 7.0.4 version.Whenever I play any avi file(which opens directly in kaffeine),the load on CPU increases and the video runs in frames and is not in sync with audio.Even the color of video shows green at some intervals.
Moving the mouse cursor from one position to other also takes time,which leads me to think that there is too much processing going at either CPU or HDD level.
I checked through settings that the engine used by kaffeine is xine.
Are there any codecs for playing avi files that needs to be installed in order to get it working.Or is this any other issue like motherboard drivers or something else????
Pls suggest........

Thanks...

---

### Post by pluviosity on 2008-07-31
While I'm not sure of what to suggest to get AVIs working with Kaffeine, you could try fixing the sync issues with individual files with VLC following the instructions here:  [http://lifehacker.com/367558/fix-desynchronized-video-and-audio-with-vlc](http://lifehacker.com/367558/fix-desynchronized-video-and-audio-with-vlc)

I wouldn't be surprised if mplayer or one of its frontends (SMPlayer, KMplayer, etc.) has similar functionality.

---

### Post by tuxxy on 2008-07-31
I suggest...GNOME  :)

---

### Post by virus2 on 2008-08-01
Ok,it now seems to be some DMA problem.I searched through net and found that CPU consumption going to 100% means that DMA is not enabled on your HD.
I tried enabling it by entering foll command:
sudo hdparm -d1 /dev/sda
,but got error as 'HDIO_SET_DMA failed: Inappropriate ioctl for device'.I know that hdparm is not for IDE drives,but fdisk -l shows my IDE drive as 'sda'.
Even if i do 'sudo hdparm -i /dev/sda',the output does not show anything about DMA setting(0 or 1)
Anyone can help me with this?????

---

