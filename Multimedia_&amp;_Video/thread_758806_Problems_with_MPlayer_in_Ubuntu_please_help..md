---
title: "Problems with MPlayer in Ubuntu please help."
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by csh on 2008-04-18
My Mplayer can play realmedia and other types of file.

I had installed the graphic driver from my ATI video card. The driver is downloaded from AMD website. The screen resolution of my monitor is 1440x900.

I install MPlayer through Synaptic Package Manager.

Mplayer play my video files, it does not play the video according to the resolution (width and height) of my video file. It play my video file according to the resolution of my monitor.

When playing non-wide screen video, video with 640x480 resolution, the width of the video are enlarged and the characters in the video become "fat". And, in full screen mode, there is no 'black border' on the left and right side of the video (640x480 video file).

I had tried to set the aspect ratio to 4:3 but does not work.

I only want to use MPlayer and don't want to use the others.

How to solve this problem, without changing the screen resolution?

---

### Post by fs3rp4 on 2008-04-18
> **csh said:**
> My Mplayer can play realmedia and other types of file.

I had installed the graphic driver from my ATI video card. The driver is downloaded from AMD website. The screen resolution of my monitor is 1440x900.

I install MPlayer through Synaptic Package Manager.

Mplayer play my video files, it does not play the video according to the resolution (width and height) of my video file. It play my video file according to the resolution of my monitor.

When playing non-wide screen video, video with 640x480 resolution, the width of the video are enlarged and the characters in the video become "fat". And, in full screen mode, there is no 'black border' on the left and right side of the video (640x480 video file).

I had tried to set the aspect ratio to 4:3 but does not work.

I only want to use MPlayer and don't want to use the others.

How to solve this problem, without changing the screen resolution?

Hi!

Probably this happens because the 3D it's not activated. The driver is really OK? 

In Mplayer the correct codec to play video is 

preferences/video/ XV

---

### Post by csh on 2008-04-18
> **fs3rp4 said:**
> Hi!

Probably this happens because the 3D it's not activated. The driver is really OK? 

In Mplayer the correct codec to play video is 

preferences/video/ XV

Before I post this question, I had set the preferences/video to XV but it does not work. And the 3D you means is 3D effects?

Any replies will be appreciated.

---

### Post by Jose Catre-Vandis on 2008-04-18
Check you have the overlay settings correct in your xorg.conf

In my Screen section, it says```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Monitor         "PLE431"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1152x864"      "1024x768"      "832x624"       "800x600"       "720x400"     $
        EndSubSection
```

---

### Post by csh on 2008-04-19
> **Jose Catre-Vandis said:**
> Check you have the overlay settings correct in your xorg.conf

In my Screen section, it says```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Monitor         "PLE431"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1152x864"      "1024x768"      "832x624"       "800x600"       "720x400"     $
        EndSubSection
```

Thanks for your reply. But your solution does not solve my problem. My problem does not occur in Totem movie player. But, I only want to use Mplayer.

Any other solution?

---

### Post by shirilover on 2008-04-19
You could try adding the following to ~/.mplayer/config

monitoraspect=16:10

---

### Post by csh on 2008-04-20
> **shirilover said:**
> You could try adding the following to ~/.mplayer/config

monitoraspect=16:10

I followed what you said. But, still cannot solve my problem.

---

### Post by IanW on 2008-04-20
OK. Instead of monitoraspect=16:10 try monitoraspect=1.6

I recently had a similar problem with my HTPC, and found that a decimal figure worked when the actual ratio didn't.

---

### Post by bijeeshvs on 2008-04-20
I know you love Mplayer a lot but i would suggest you should try VLC Media player it can play almost any format its worth a try

---

### Post by Gaki-san2001 on 2008-04-22
Try installing SMplayer. Your mplayer will get a lot more option and all of them will work. :) I am beginner with linux and it works for me. Keep VLC and gxine for safety.

Of course I also like to use mplayer gui. I had the same problem with 4:3 in mplayer but monitoraspect=16:10 solved it. Thanks very much! Zoom or panscan does not work but I might have to live with it. When I press the w or e buttons the scale appers on the screen but nothing moves.

---

### Post by csh on 2008-04-23
Thanks for all your replies. Now, I tried to re-edit the mplayer configuration files. There is some spelling mistake inside. I had corrected it. Now my problem had been solved.

Anyway, thanks for all of you. I really appreciate it.

And, I want to know that how to mark this thread as SOLVED?

---

