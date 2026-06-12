---
title: "make iso image from Video_ts folder"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by joriad on 2007-07-05
I downloaded a Video_ts folder from a torrent site but am unsure of how to make an iso image from the folder contents. It has all the .bup, .ifo, and .vob files. Also is an audio folder required to beincluded in the iso image. I have tried devede and avidemux but came up with errors. If someone could walk me through this process that would be great.


thanks

---

### Post by RomeReactor on 2007-07-06
Hi. The easiest way I've found to make a video DVD from a Video_ts folder is through K3B (you can find it through Synaptic or Add/Remove, or from the command line:
```
sudo apt-get install k3b
```
once it's installed, open it and look for an option (I think it's in the  **tools** menu) to make a video DVD; once selected, you'll see in the window that there are two folders: **audio_ts** and **video_ts**. Copy the contents of the video_ts file you want to burn and paste them inside the video_ts folder in K3B. After that, all that's left is Burn.

---

### Post by joriad on 2007-07-07
That worked great, Thanks.

---

### Post by PurplePenguin on 2007-07-21
Here's another way:

> mkisofs -dvd-video -o /path/to/output/output.iso /path/to/input/(with VIDEO_TS in here)

From what I understand, the -dvd-video switch improves compatibility with some set-top players.

---

### Post by everdred on 2008-03-09
> **PurplePenguin said:**
> Here's another way:



From what I understand, the -dvd-video switch improves compatibility with some set-top players.

Actually, it seems you shouldn't include the VIDEO_TS folder in the path when using mkisofs. At least, it only worked when I left it out.

---

### Post by Mud.Knee.Havoc on 2008-03-09
You are absolutely correct.  I now realize that my description wasn't clear enough.  You just include the path to where the VIDEO_TS is located, you don't actually include VIDEO_TS in the path.

So if you have /media/harddrive/movie_to_burn/VIDEO_TS
you would consider /media/harddrive/movie_to_burn your input path

Thanks for the clarification... I'd hate for somebody to try it unsuccessfully and get frustrated! :D

---

