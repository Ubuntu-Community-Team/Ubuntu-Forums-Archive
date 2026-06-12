---
title: "Flash 10.2 with no vdpau acceleration"
date: 2011-02-11
forum: Multimedia Software
---

### Post by onemanclapping on 2011-02-11
Hello,

Basically, the title says it all: I installed the new Flash 10.2 (with flash-aid) and I have no acceleration on Youtube.

I thought that maybe I had something wrong with my system, so I reinstalled Ubuntu 10.10. Then installed Flash and the vdpau-va-driver. Still nothing.

I have a ION card, so I should have full flash acceleration on video, like I have in windows.

Any advice on how to debug this?

Thanks in advance.

---

### Post by JOHNNYG713 on 2011-02-11
When you installed 10.10 did you also install the third party applications in the ubiquity installer, (this option is on one of the first pages of the installation) If so then there is no need to install flash player manually, as it gets installed from the start, You may have conflicting installations of flash !

---

### Post by beew on 2011-02-11
I have the same issue. I have tried disabling Comoiz but it makes no difference.


> **JOHNNYG713 said:**
> When you installed 10.10 did you also install the third party applications in the ubiquity installer, (this option is on one of the first pages of the installation) If so then there is no need to install flash player manually, as it gets installed from the start, You may have conflicting installations of flash !

Lovinglinux's flashaid plugin is supposed to get the latest flash while removing conflicting versions. Normally it works better than anything in the Ubuntu repositories.

---

### Post by onemanclapping on 2011-02-11
> **beew said:**
> I have the same issue. I have tried disabling Comoiz but it makes no difference.

Do you also have an ION? Maybe this is an ION issue...

---

### Post by gradinaruvasile on 2011-02-11
Flash player does support vdpau. Tried and works (nvidia 8200 integrated, 270.18 drivers, should work with any vdau driver in theory). I just downloaded the tar.gz, unpacked it in $HOME/.mozilla/plugins/ (i have no flash installed from the repos).

Here is what i did to enable hardware decoding:
Created

/etc/adobe/mms.cfg and put this in it:

EnableLinuxHWVideoDecode=1

Restarted the browser and it worked (well on some sites anyway).

Working site: youtube, 1080p content works either at ~40% cpu or ~10-20% - i dont know why is this big difference, i tested it wth the same clip (big buck bunny) a few times.
I turned on the video details from the right click menu and it showed that it was accelerated (software rendering is at ~100% on my Athlon II x2 250 @3 GHz)
Vimeo said that stage video is available but for whatever reason it did not use it.

Problems: some sites wont play streaming video if hardware acceleration is enabled. Additionally, if flash is loaded once, i get tearing vdpau playback (with mplayer). Regardless if the browser is stopped, the tearing remains until i restart x or sometimes it goes away after a few suspend/resume cycles.
So Adobe had good reason to disable it by default.

---

### Post by onemanclapping on 2011-02-11
> **gradinaruvasile said:**
> 
Here is what i did to enable hardware decoding:
Created

/etc/adobe/mms.cfg and put this in it:

EnableLinuxHWVideoDecode=1

Restarted the browser and it worked (well on some sites anyway).


PERFECT, worked like a charm! Thank you!

---

### Post by WannabeFantasma on 2011-02-14
Gonna have to try this solution... Just installed new flash + new nvidia drivers, and 1080P is worse than the old nvidia drivers(185....) and the older flash(10.1)....

My cpu usage of my ion is going at like 80%...
Screenshot :
[http://img11.imageshack.us/f/huhhn.png/](http://img11.imageshack.us/f/huhhn.png/)

Yay working here!  
Youtube never played 1080p as smooth!
Bumped into this glitch/bug though...
[http://ubuntuforums.org/showthread.php?t=1688323](http://ubuntuforums.org/showthread.php?t=1688323)

---

### Post by thecapsaicinkid on 2011-02-19
The test videos on Adobe's site confirm acceleration is working but I'm not getting any acceleration on YouTube (video info shows undefined rendering and cpu is high).

This is in Chromium btw.

---

### Post by onemanclapping on 2011-02-25
> **thecapsaicinkid said:**
> This is in Chromium btw.

Firefox is fine. But Youtube only. Most websites are not accelerated...

---

