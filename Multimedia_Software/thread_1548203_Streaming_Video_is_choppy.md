---
title: "Streaming Video is choppy"
date: 2010-08-08
forum: Multimedia Software
---

### Post by ryanwalex on 2010-08-08
I am stuck.

When I play streaming video on hulu or other sites it  is choppy. However, the sound is fine. Video files play fine when I  download them. 

I experience this problem in both Firefox and Chrome. I have a 10MB connection on other Linux desktops the streaming video is fine. 

I imagine it is a flash issue, but I have the latest flash v10.1

Specs:

[LIST]
[*]HP Pavilion 724c Desktop PC
[*]32-bit
[*]ubuntu 10.04, just installed
[*]1.5 GB RAM
[*][SIZE=2]Intel 82845G/GL/GE/PE/GV Graphics Controller [Display adapter][/SIZE]
[/LIST]
The other solution would be a video downloader for streaming video. I have not found one that works on Linux.

Thanks for any help.

---

### Post by JBAlaska on 2010-08-08
> **ryanwalex said:**
> I am stuck.

When I play streaming video on hulu or other sites it  is choppy. However, the sound is fine. Video files play fine when I  download them. 

I imagine it is a flash issue, but I have the latest flash v10.1

Specs:

[LIST]
[*]HP Pavilion 724c Desktop PC
[*]32-bit
[*]ubuntu 10.04, just installed
[*]1.5 GB RAM
[*][SIZE=2]Intel 82845G/GL/GE/PE/GV Graphics Controller [Display adapter][/SIZE]
[/LIST]
**The other solution would be a video downloader for streaming video. I have not found one that works on Linux.**

Thanks for any help.

I can't help with your flash, but you really don't need a video downloader. Just play the clip, do not close your browser and look in your tmp dir. your clip should be there ready to play, copy it to an other location to keep it.

---

### Post by ryanwalex on 2010-08-08
I should have maybe stated I am more of a novice. 

How do you get to the tmp directory? What is the file path?

---

### Post by oracle2b on 2010-08-08
Run your browser and right-click on any flash video or ad, go down to settings, and uncheck the box that says enable hardware acceleration. 

&#8220;Then open a terminal and type 
[COLOR="#ff0000"]sudo mkdir /etc/adobe 
sudo su
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg[/COLOR]



OR

play videos directly from your temp folder

open terminal

[COLOR="Red"]sh -c 'vlc /tmp/Flash*'[/COLOR]

---

### Post by linux18 on 2010-08-08
get the flash aid extention for firefox, it solved all of my problems

---

### Post by JBAlaska on 2010-08-08
> **ryanwalex said:**
> I should have maybe stated I am more of a novice. 

How do you get to the tmp directory? What is the file path?

/tmp

```
cd /tmp
```

---

### Post by roy913 on 2010-08-08
i am not sure about the solution for hulu but for youtube here is an option you can try.

isntall Flash Video Replacer (a.k.a. FlashVideoReplacer), which is an add-on for firefox. you'll then be able to use gnome-mplayer to play the video instead of flash player. You can choose the quality of video from low to high, which represents the resolution of the youtube video like 360, 480, 720, 1080

i am using a nvida 8XXX card and there is an option for vdpau.

once the above is done, my cpu usage is like 1x% at most even when playing 1080p movie.

HP Pavilion 724 nonetheless is an rather old machine so it may not be smooth with 720p or 1080p video.

you can suggest FlashVideoReplacer in their website to cover hulu.com.

---

### Post by lovinglinux on 2010-08-08
> **roy913 said:**
> i am not sure about the solution for hulu but for youtube here is an option you can try.

isntall Flash Video Replacer (a.k.a. FlashVideoReplacer), which is an add-on for firefox. you'll then be able to use gnome-mplayer to play the video instead of flash player. You can choose the quality of video from low to high, which represents the resolution of the youtube video like 360, 480, 720, 1080

i am using a nvida 8XXX card and there is an option for vdpau.

once the above is done, my cpu usage is like 1x% at most even when playing 1080p movie.

HP Pavilion 724 nonetheless is an rather old machine so it may not be smooth with 720p or 1080p video.

you can suggest FlashVideoReplacer in their website to cover hulu.com.

No need to suggest Hulu, since it is already on my to-do list. Nevertheless, due to geolocation constrains ( I don't have access to Hulu) I might not be able to implement Hulu support. 

Here are the links of the two extensions mentioned on the thread:

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Tarmalo on 2010-08-10
make sure to download the restricted extras from the Ubuntu software center. try to run the openjdk java or the ubuntu restricted extras. Download them all for safe measure. It worked for me. I'm running Ubuntu 10.04 lucid lynx.

---

### Post by freeediver on 2010-10-14
JBAlaska can you outline a step by step and what I should see?
When I open terminal and enter /tmp I get tmp$ as a result and that is all. I have 2 videos I need to copy.
Thanks
I have been pressing buttons and found "a" temp directory but when I cruze down to what I think is the proper video heading I do not have an option to copy the file to move it. when I click on it I get a full page of data but no positive indication that it is the correct video.

OOp's I goofed I can't use this legally for what I want, so I won't but I would still like to know what I did wrong.

---

### Post by Robsy1 on 2010-10-14
I have the same problem with video and radio/i-player.   I get 2 seconds of rushed and garbled sound and speeded up picture followed by 3 secs of silence and picture freeze.   This keeps on stop/start.  I have plenty of download speed (7000 kbps).   I replaced the latest Adobe Flash.  Anything else I should do, please?

---

### Post by markymark64 on 2011-05-08
I'm having a similar problem but only with hulu. When I watch streaming videos in full screen on my windows partition they play fine but when I watch them in full frame on hulu they're choppy. If I reduce the screen to the smaller size they play fine. Oh, and I have the restricted extras package and the latest version of adobe flash. Youtube plays fine. It's just hulu in full screen. Weird huh?

---

### Post by lovinglinux on 2011-05-09
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

