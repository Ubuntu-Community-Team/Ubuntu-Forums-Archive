---
title: "Recorded sound is noisy and cracking"
date: 2011-12-09
forum: Multimedia Software
---

### Post by marin123 on 2011-12-09
Hi guys :)

I have a problem with my sound. I am using Ubuntu 11.10. Just to state first that boot from LiveUSB works, this is just on my installation.

When I record audio (with Sound Recorder or Audacity) from Line In, I get cracking audio. I tried recording from ALSA and Pulse, both results with same audio, so I assume that it is ALSA problem.

I thought it was ALSA problem, so I reinstalled it, but no change. Then I tried sudo alsa reload and force-reload, but I get this error both ways:
```
 sudo alsa force-reload
[sudo] password for marin: 
Unloading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.

```So, it seems to be some kind of ALSA error, can someone help me fix this? ALSA version is 1.0.24.

EDIT: [http://adria.fesb.hr/~mbareta/2011-12-09-202439.wav]("http://adria.fesb.hr/%7Embareta/2011-12-09-202439.wav") here's a sample of what I'm getting.

---

### Post by marin123 on 2011-12-11
Just a bump, hope someone can help :)

---

### Post by chema7 on 2011-12-12
Hi,

I yesterday had the same problem on Ubuntu 11.10. I have solved it with "Pulse Audio Manager":

[LIST]
[*] Input devices tab, and decrease the intensity of both fronts to about 50% (internal microphone). This was too high for my particular case. Try it.
[/LIST]


Good luck
 Regards :)

---

### Post by marin123 on 2011-12-12
> **chema7 said:**
> Hi,

I yesterday had the same problem on Ubuntu 11.10. I have solved it with "Pulse Audio Manager":

[LIST]
[*] Input devices tab, and decrease the intensity of both fronts to about 50% (internal microphone). This was too high for my particular case. Try it.
[/LIST]


Good luck
 Regards :)

Thanks, but that's not it. I don't know if you have listened to the sample, but that on the recording isn't clipping, it is some kind of distorted echo.
Oh well, this will speed up my reinstall. Shame, I hoped it will last until 12.04 :)

---

### Post by chema7 on 2011-12-13
> **marin123 said:**
> Thanks, but that's not it. I don't know if you have listened to the sample, but that on the recording isn't clipping, it is some kind of distorted echo.
Oh well, this will speed up my reinstall. Shame, I hoped it will last until 12.04 :)

Sorry man ;), I had not heard the sample because the link did not work for me 2 days ago. It now works correctly. I now see that these are not exactly the same problem. According to the title, I thought it was like my problem.

Do you use an internal or external microphone? However, it is probably an Ubuntu kernel problem with HDA intel. It seems that this Ubuntu version is a rebel with these sound issues. Have you updated to the latest kernel?

I hope you can fix it soon.
Best Regards

---

### Post by marin123 on 2011-12-13
Thanks for your help anyway :)

I think this is following me since 11.04 (so I had to switch kernels, and now I have the latest updates). This is messing up my Skype too, sometimes it had some kind of distortion, but I can't tell for sure if it's the same problem.
I should have recorded better sample, because when I pause the player (I'm recording on Line In from Pioneer DJ Mixer), I get some kind of a tail, like echo, just distorted.

---

### Post by vangop on 2011-12-14
I have a similar noise issue on my dell laptop. It seems to be connected with snd_hda_intel module param. I haven't had time to resolve it yet, as simple steps from [here ]("https://help.ubuntu.com/community/HdaIntelSoundHowto")didn't work for me.

---

### Post by marin123 on 2012-01-18
GOT IT! :)

I stumbled upon this link [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)
and applied```
options snd-hda-intel position_fix=1
```
to file /etc/modprobe.d/alsa-base.conf (actually I already had that line just with fix=2) and now all of my audio works.
It also fixed Skype's cracking sounds.

---

### Post by birauser on 2012-01-30
thanks a lot, I've just added the fix=2 line and everything works flawlessly now! I can finally place calls on skype or google talk without having to reboot first, which is really something great.

However, finding this fix has been rather hard. I guess the issue has not been addressed until very recently. It would be appropriate to spread the word in someway, since the problem is not easy to explain in terms that are usable for a google search - that's also why I have added a couple of tags to the thread..

---

### Post by Schafir on 2012-01-31
Neither solution (options snd-hda-intel position_fix=1 or fix=2) solved this for me.

Acer TimelineX 5830TG 

Still looking for a fix.

---

### Post by simplygades on 2012-02-16
> **Schafir said:**
> Neither solution (options snd-hda-intel position_fix=1 or fix=2) solved this for me.

Acer TimelineX 5830TG 

Still looking for a fix.

Same here. I also tried uninstalling pulseaudio (I use Kubuntu) but the clipping is still there.

---

