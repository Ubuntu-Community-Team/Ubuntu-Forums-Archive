---
title: "Software for screencasts"
date: 2017-11-06
forum: Multimedia Software
---

### Post by satimis on 2017-11-06
Hi all,

Which software shall I run to record the screen (screencast) as video on the steps in re package installation and/or configuration?

A brief search finds follows;

How To Record Your Screen In Ubuntu With SimpleScreenRecorder
[https://itsfoss.com/record-screen-ubuntu-simplescreenrecorder/](https://itsfoss.com/record-screen-ubuntu-simplescreenrecorder/)

Screenshots and screencasts
[https://help.ubuntu.com/stable/ubuntu-help/screen-shot-record.html](https://help.ubuntu.com/stable/ubuntu-help/screen-shot-record.html)

Top 4 screen recorders in Linux
[http://hackerspace.kinja.com/screen-recording-in-linux-1686055808](http://hackerspace.kinja.com/screen-recording-in-linux-1686055808)

Please advise.  Thanks

Regards
satimis

---

### Post by ajgreeny on 2017-11-06
It can also easily be done, as long as you need the video only, not sound, with the simple command ```
ffmpeg -f x11grab [COLOR="#FF0000"]-s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15[/COLOR] -qscale 0 Desktop/video.avi
```
The bit shown in red is the resolution of the input x11grab, the framerate, then the output file resolution and framerate again which you can set to what you need for your screen and video size.

Knowing how flexible ffmpeg is, I have no doubt that audio could be added to that ffmpeg command's output, but it is not something I've ever needed to do so I am not able to give you that info.  You may find a search or "ffmpeg screen recording" gives you a lot of info.

In spite of all this I do use SimpleScreenRecorder, which "does what it says on the tin" and very simply records video and sound for you.

---

### Post by satimis on 2017-11-06
> **ajgreeny said:**
> It can also easily be done, as long as you need the video only, not sound, with the simple command ```
ffmpeg -f x11grab [COLOR="#FF0000"]-s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15[/COLOR] -qscale 0 Desktop/video.avi
```
The bit shown in red is the resolution of the input x11grab, the framerate, then the output file resolution and framerate again which you can set to what you need for your screen and video size.

Knowing how flexible ffmpeg is, I have no doubt that audio could be added to that ffmpeg command's output, but it is not something I've ever needed to do so I am not able to give you that info.  You may find a search or "ffmpeg screen recording" gives you a lot of info.

In spite of all this I do use SimpleScreenRecorder, which "does what it says on the tin" and very simply records video and sound for you.
Hi,

Thanks for your advice.

What is 720x450 ?

I found;
FFmpeg
[https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop)

and also following thread;
Record screen when launching a program
[https://ubuntuforums.org/showthread.php?t=2365755&highlight=screen+recording](https://ubuntuforums.org/showthread.php?t=2365755&highlight=screen+recording)

I suppose that it will be more convenient to write a script which can be executed easily rather than running the command on Terminal each time?

Regards
satimis

---

### Post by vasa1 on 2017-11-06
> **satimis said:**
> ...I suppose that it will be more convenient to write a script which can be executed easily rather than running the command on Terminal each time?
...
Could you explain what you wish to record? Maybe you could clarify>  Which software shall I run to record the screen (screencast) as video on the steps in re package installation and/or configuration?from your first post?

---

### Post by satimis on 2017-11-06
> **vasa1 said:**
> Could you explain what you wish to record? Maybe you could clarifyfrom your first post?
I expect to record the complete steps on testing software, such as building/installing oVirt engine, oVirt node, Ansible Towers etc.  My purpose is only for recording software testing

satimis

---

### Post by vasa1 on 2017-11-06
From a look at *man ffmpeg*, 720x450 seems to be the area to be recorded: > The format is wxh (default - same as source).

---

### Post by satimis on 2017-11-06
> **vasa1 said:**
> From a look at *man ffmpeg*, 720x450 seems to be the area to be recorded:
Thanks

satimis

---

### Post by vasa1 on 2017-11-07
I just tried this:```
sleep 10s && ffmpeg -video_size 1000x500 -framerate 25 -f x11grab -i :0.0+100,100 -t 00:00:10 ~/"$(date +%H%M%S)".mp4
```to record a 10s screen record and it works for me on 16.04.

---

### Post by satimis on 2017-11-07
> **vasa1 said:**
> I just tried this:```
sleep 10s && ffmpeg -video_size 1000x500 -framerate 25 -f x11grab -i :0.0+100,100 -t 00:00:10 ~/"$(date +%H%M%S)".mp4
```to record a 10s screen record and it works for me on 16.04.
Hi,

Whether start the command line on Terminal first before performing the test, such as installing/configuring steps etc of software?

How to stop it temporarily?  How to restart recording to continue?

satimis

---

### Post by monkeybrain20122 on 2017-11-07
What is your DE? Many screencasters don't work well with desktop compositing but kazam is great and easy to use, it records both videos and audio with a press of a button, works perfectly in unity, but apparently doesn't work in gnome shell because the tray icon doesn't show up.  I think this is more of a gnome bug than Kazam's.  In case of GS you can try the gnome [easy screencast extension]("http://www.ubuntubuzz.com/2016/06/easyscreencast-gnome-shell-extension-video-audio-recording.html") I haven't used this so I can't vouch for it (another but:  but if you are using 17.10 this extension only work in X and moreover if you install it you won't be able to log into Wayland)

---

### Post by vasa1 on 2017-11-07
> **satimis said:**
> Hi,

Whether start the command line on Terminal first before performing the test, such as installing/configuring steps etc of software?

How to stop it temporarily?  How to restart recording to continue?

satimis
The sleep is there to allow you some time to move from the terminal to whatever else you want to do. I don't know how to pause or resume. Maybe something involving `bg` and `jobs`???

As monkeybrain20122 points out, GUI-based programs will offer a lot more features more conveniently. I have simple screen recorder but don't do much screen recording.

---

### Post by satimis on 2017-11-07
> **monkeybrain20122 said:**
> What is your DE? Many screencasters don't work well with desktop compositing but kazam is great and easy to use, it records both videos and audio with a press of a button, works perfectly in unity, but apparently doesn't work in gnome shell because the tray icon doesn't show up.  I think this is more of a gnome bug than Kazam's.  In case of GS you can try the gnome [easy screencast extension]("http://www.ubuntubuzz.com/2016/06/easyscreencast-gnome-shell-extension-video-audio-recording.html") I haven't used this so I can't vouch for it (another but:  but if you are using 17.10 this extension only work in X and moreover if you install it you won't be able to log into Wayland)
Ubuntu 16.04 Gnome desktop
Host of KVM

Can I install 
EasyScreenCast: GNOME Shell Extension for Recording Screen + Audio
on Guest of KVM ?

I expect keeping the Host clean only for running OS and KVM

I found following document to install it:
Install Simple Screen Recorder 0.3.8 in Ubuntu 16.04, 16.10
[http://ubuntuhandbook.org/index.php/2016/11/install-simple-screen-recorder-0-3-8-in-ubuntu-16-04-16-10/](http://ubuntuhandbook.org/index.php/2016/11/install-simple-screen-recorder-0-3-8-in-ubuntu-16-04-16-10/)

How about;
OBS-Studio
Open Broadcaster Software
[https://obsproject.com/](https://obsproject.com/)
?

Regards
satimis

---

### Post by monkeybrain20122 on 2017-11-07
> **satimis said:**
> Ubuntu 16.04 Gnome desktop
Host of KVM

Can I install 
EasyScreenCast: GNOME Shell Extension for Recording Screen + Audio
on Guest of KVM ?

I expect keeping the Host clean only for running OS and KVM

I found following document to install it:
Install Simple Screen Recorder 0.3.8 in Ubuntu 16.04, 16.10
[http://ubuntuhandbook.org/index.php/2016/11/install-simple-screen-recorder-0-3-8-in-ubuntu-16-04-16-10/](http://ubuntuhandbook.org/index.php/2016/11/install-simple-screen-recorder-0-3-8-in-ubuntu-16-04-16-10/)

How about;
OBS-Studio
Open Broadcaster Software
[https://obsproject.com/](https://obsproject.com/)
?

Regards
satimis

I don't know since I don't run linux in VM and like I said I have never used the Easy-Screencast extension . But it is easy to try it out and see for yourself, just go to the gnome extension webpage and install it like other gnome extensions and there you have it. [https://extensions.gnome.org/extension/690/easyscreencast/](https://extensions.gnome.org/extension/690/easyscreencast/)

**Edited:** you may also try kazam, it doesn't work with gnome in 17.10 since they apparently got rid of icon tray in gnome's tradition of removing  useful features because of their "vision" but in 16.04 it might work. I have very good experience using it on unity (not in VM thogh)

---

### Post by satimis on 2017-11-07
> **monkeybrain20122 said:**
> I don't know since I don't run linux in VM and like I said I have never used the Easy-Screencast extension . But it is easy to try it out and see for yourself, just go to the gnome extension webpage and install it like other gnome extensions and there you have it. [https://extensions.gnome.org/extension/690/easyscreencast/](https://extensions.gnome.org/extension/690/easyscreencast/)
I suppose the solution is simple after building up nested virtualization.  I'll create a new VM running Ubuntu 16.04 gnome desktop and KVM with its image stored on SSD.  Afterward I'll install oVirt engine and oVirt note on it.  All future tests will be performed on this new VM.  I'll create 150 G space for the new VM.  I suppose there is sufficient space on the 250G SSD.

(remark: I'm now testing oVirt engine and oVirt note on the Host.  If successful I will repeat the steps on the new VM)

> 
**Edited:** you may also try kazam, it doesn't work with gnome in 17.10 since they apparently got rid of icon tray in gnome's tradition of removing  useful features because of their "vision" but in 16.04 it might work. I have very good experience using it on unity (not in VM thogh)
Thanks

I found following threads
Kazam Screencaster
[https://apps.ubuntu.com/cat/applications/precise/kazam/](https://apps.ubuntu.com/cat/applications/precise/kazam/)

How to install Kazam 1.5.3 on 16.04?
[https://askubuntu.com/questions/766440/how-to-install-kazam-1-5-3-on-16-04](https://askubuntu.com/questions/766440/how-to-install-kazam-1-5-3-on-16-04)

Screen Recorders For Ubuntu 16.04 - Kazam
[https://www.youtube.com/watch?v=ADPPpY6ZEI8](https://www.youtube.com/watch?v=ADPPpY6ZEI8)

I'll take a look on it.

Regards
satimis

---

### Post by satimis on 2017-11-09
Hi all,

Finally I installed Kazam on Host.

Kazam is great suitable for my use, having start/pause/resume/finish functions and easy to use.  The output file is .mp4 format

I only need to record the steps on testing.  To edit the video recorded will be another story.  Maybe I can use OpenShot or OBS-Studio or anther software to be found later.

If installing Kazam on a VM I can't make it to capture the steps performed on other VMs.

Thanks again monkeybrain20122

Regards
satimis

---

