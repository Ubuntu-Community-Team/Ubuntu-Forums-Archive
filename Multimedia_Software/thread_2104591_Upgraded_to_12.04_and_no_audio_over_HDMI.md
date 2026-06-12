---
title: "Upgraded to 12.04 and no audio over HDMI"
date: 2013-01-13
forum: Multimedia Software
---

### Post by TonyGould on 2013-01-13
Hi on 10.04 I had audio over HDMI working fine (don't remember exactly what I did but I think it was to switch from xfce to standard desktop, and simply choose the HDMI output in the sound settings at the top right, which took hours and hours to figure out and I was kicking myself afterwards).

Now I've upgraded to 12.04, and found HDMI audio doesn't work at all. After a while I remembered to switch from xfce (I have the default mythbuntu install) and install the gnome desktop so I could get the sound settings dialog. Sure enough, it was set to the default, non-HDMI option. But this time when I switched to HDMI audio out I got nothing.

I'm running with an nvidia Geforce 8200 (according to the nvidia settings dialog), with the latest driver, and I've used alsamixer to make sure that the main volume isn't muted. I've searched around a bunch of threads and done a speaker test on all the permutations given below from alist -l, but still nothing happens.
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I don't really understand the linux sound architecture at all well enough to know where to turn to next (apart from going back to 10.04 which is just giving up). Could someone maybe help me and point me out what I could try? I'm probably just missing something that's obvious to someone with a bit of knowledge -- given that it was all working fine under 10.04.

Thanks,

Tony

---

### Post by TonyGould on 2013-01-13
It turns out that I got it wrong above and I hadn't unmuted something significant in alsamixer. Thanks to a [really helpful post I found]("http://ubuntuforums.org/showthread.php?t=1967812"), I discovered that unmuting S/PDIF 1 in alsamixer meant that the following command gave white noise output: speaker-test -c 2 -r 48000 -D hw:0,3. Another bit of good news is that I can now get sound in the mythtv frontend (settings ALSA:hdmi:CARD=NVidia,DEV=0). However, the test speaker button in the sound settings applet at the top right of the screen still fails to produce any sound, as does, e.g., playing videos in a browser.

I've got a feeling this might be as far as I got in 10.04 -- so the question is, given that I have sound *almost* working, what do I have to do to get sound working on the main ubuntu desktop? I'd really like to be able to use iplayer, smplayer, google music and all the other good stuff available. I've spent almost 3 hours on this searching the internet and trying different stuff out, so would appreciate a pointer if anyone has one. 

thanks if anyone can help, sorry about all long posts,

Tony

---

### Post by BicyclerBoy on 2013-01-13
Try installing/running
pavucontrol

get the configuration tab  & set the right profile.
try: Digital stereo (iec958) output or similar.

I have a suspicion that 8200 IGP has incomplete HDMI capabilities & it does not report via ELD/EDID.

In MythTV you can set the amp/TV decode capabilities for iec958.

SMPlayer can point directly at the alsa device.

---

### Post by Yellow Pasque on 2013-01-14
So you have sound playing directly to the ALSA device, but no sound when trying to play through pulseaudio.
I would personally delete the user's pulse configuration files so fresh ones get generated.
```
rm -r ~/.pulse*
pulseaudio -k
```

---

### Post by TonyGould on 2013-01-14
Thanks both of you, it's awesome to get such prompt and good help. It's working now :), but I'm not 100% sure what got it to work, because I assumed that the gnome sound settings app test speakers function (on the hardware tab) gave accurate results. In fact, even though I now have sound from firefox, and from a terminal window, there is no sound coming from that test speakers function on the app. I'm tempted to report this as a bug -- I might have concluded that the help you guys gave me was in vain. It was only after I worked through both your posts using the sound settings app test speakers function, and was about to give up, that I thought I'd try an online video one more time, and it worked!

BicyclerBoy: thanks a lot, I did try this but I don't *think* it made any difference. It certainly made me realise that what you configure in pavucontrol (or in the sound settings app) is independent from what is used in speaker-test and mythtv. I think I thought that changing the profile to HDMI in pavucontrol / the sound settings app would affect mythtv, but mythtv just makes its own choice (i.e., you have to choose it separately).

Temüjin: thanks a lot also, I *think* this is what fixed the issue, but for the reason I gave above I can't be 100% sure. It was noticable that after removing the existing pulseaudio information, I got no profile options in the gnome sound settings app; it was only when I went into the pavucontrol that the profiles were restored. So although it looks like these two applications do the same thing (changing the profile in one changes it in the other), it seems that pavucontrol worked better for me.

For the record, I also tried adding the  /etc/asound.conf file as described at the bottom of [this post]("http://karuppuswamy.com/wordpress/2012/04/28/how-to-fix-nvidia-hdmi-audio-in-ubuntu-12-04/"), but it made no difference.

Thanks again both of you -- I'm pretty optimistic that I can now get on with the software-related issues (where I have a bit more expertise), so much happier.

best wishes,

Tony.

PS as I'm a software guy and enjoy playing with stuff, I thought I'd try logging out of gnome and going into mythbuntu and xfce (I believe mythbuntu is based on xfce). Neither worked -- mythtv wouldn't play and speakertest failed, in both cases. I can't say I'm that bothered, as I'm happy to stick with gnome, but I was curious as to whether I could have unmuted the S/PDIF 1 channel in alsamixer on mythbuntu and avoided the 3 or 4 hours, with your help, to get everything working under gnome. I'm really adding this PS in case there's anyone else in the future who has a similar problem to me and can benefit from the experience.

---

### Post by Yellow Pasque on 2013-01-14
Tony, posts like yours are what keep me going at this Ubuntu thing. I'm glad it's sorted out for you. Please mark the thread SOLVED by using the "Thread Tools" menu towards the top of the page.

---

