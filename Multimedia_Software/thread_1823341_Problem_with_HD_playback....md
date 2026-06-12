---
title: "Problem with HD playback..."
date: 2011-08-11
forum: Multimedia Software
---

### Post by BuntuBurgundy on 2011-08-11
I am a total linux noob, this is my first install and am using natty 11.04 on a core duo @ 2 ghz and have an older nvidia 7950 gpu, now if i am posting this wrongly or in the incorrect section I apologize in advance. But as I search forums for answers I thought it wouldn't hurt to ask for help with my issue. Before switching to ubuntu I had played 720p video without a problem, as my hardware although the gpu doesnt support acceleration should be more than capable of 720p playback. Most of my media is mkv, and I have tried using vlc, the stock player, and umplayer. I also have tried using daily builds from this ppa:

 [https://launchpad.net/~motumedia/+archive/mplayer-daily]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily")

Whenever I try to watch any HD content, the video becomes laggy and oos . VLC was totally unbearable for me. umplayer although looks amazing ( the skin) cause lots of lag, and the best option so far has been the default mplayer packaged with ubuntu.

     It is extremely annoying. I love using and learning Ubuntu so far, and  this wont deter me, but its just a huge pita to not be able to watch any HD videos on this machine if i so choose to. Any help that this great community could offer would be greatly appreciated.

Thank you.

---

### Post by BicyclerBoy on 2011-08-12
Have you installed the proprietary driver from nVidia ?

gnome menu/System/Administration/Additional Drivers.
nVidia current.

It should make a big difference even without VDPAU..

---

### Post by aeiah on 2011-08-12
yea, it may be your lack of nvidia drivers. i can play 720p just fine with an Athlon 3800 X2, nvidia 7800 GT

but i do tend to use mplayer or xbmc

---

### Post by BuntuBurgundy on 2011-08-12
> **BicyclerBoy said:**
> Have you installed the proprietary driver from nVidia ?

gnome menu/System/Administration/Additional Drivers.
nVidia current.

It should make a big difference even without VDPAU..

I am not to sure which driver I have installed. When I first installed it prompted me to install a driver and listed 2 possible choices, one was labeled as (recommended) so me being new and cautious etc just opted for that one, I had no indication that anything was ever wrong until attempting playback of a 720p video file. Perhaps I will try to switch to that other nvidia driver listed or look at their website? I had not thought of that.

---

### Post by Duncan Williams on 2011-08-12
To get HD and 3D and openGL and stable (non-laggy) window manager (ie/compiz) sadly you pretty much have to install and make sure that
the proprietory nvidia drivers are working correctly. 
(as in nvidia xserver settings).

It will make a huge difference than if using the open-source drivers.
(believe me, I learnt the hard way)

You should be able to install from `additional drivers' as long as you have `nvidia current' installed (available from software manager)

[IMG]http://files.myopera.com/DuncanWilliams/usercss/drivers.png[/IMG]

---

### Post by BuntuBurgundy on 2011-08-12
[IMG]http://i.imgur.com/kXiZ5.png[/IMG]

I installed that from the get go, and afaik it was working ok. Was able to run unity and many other eye candy effects etc from compiz. Still unable to watch HD content without getting oos/jittery. What else could it be or should i try? Using that daily build for mplayer made no difference, there is still so much lag that it is unwatchable.

Also, what the hell does it mean that the driver is "activated" but not in use? I would imagine this would be bad? Doesn't the driver need to be in use?

---

### Post by beew on 2011-08-12
Op says he has a Nvidia 7950 card. I can be wrong but to my knowledge it doesn't support VDPAU (it is supported only for the 8 + series as far as i know, but I can be wrong about it)

@Op, try to install mplayer2 and use gnome-mplayer as your gui and see if it improves.

You can install mplayer2 and the latest version of gnome-mplayer by adding this ppa to your sources list and upgrade ( I think the mplayer2 package is still called mplayer in Synaptic)

[https://launchpad.net/~ed10vi86/+archive/tst]("https://launchpad.net/%7Eed10vi86/+archive/tst")

P.S. In my experience that mplayer daily build is actually not that great even though many people recommend it. I think mplayer2 is the best, otherwise mplayer-mt is ok too [https://launchpad.net/~longinus00/+archive/mplayer-mt](https://launchpad.net/~longinus00/+archive/mplayer-mt)

Also, VLC uses only one core so it would have problem with hd videos if the single cores are not powerful enough  individually.

---

### Post by Duncan Williams on 2011-08-13
miro is good for playback

couple of tweaks here.
[http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222](http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222)

---

### Post by BuntuBurgundy on 2011-08-13
> **beew said:**
> 

Also, VLC uses only one core so it would have problem with hd videos if the single cores are not powerful enough  individually.

I think that made a huge difference, VLC was so bad, will try those ppa's and see how it goes. Thanks for the replies.

---

### Post by BicyclerBoy on 2011-08-14
Maybe you should try other video output methods that VLC can support.
Try openGL or XVideo methods.
What post processing options do you have dialled in ?  yadifx2, post-processing like sharpening etc ?

I find core2duo can decode (& yadifx1) H264 encoded 1080 material (5GB/hr) on about ~60% CPU (& that is with another HD video playing in VDPAU).
Right now, in the really old VLC 1.0.6, the yadifx2 de-interlace is not working right.

Be aware that VLC currently has big problems with the time scheduler method of pulseaudio in natty.

Try adding *tsched=0* to the *load-module module-udev-detect* line in **/etc/pulse/default.pa**

---

### Post by Duncan Williams on 2011-08-14
also try disabling sync to vblank (in about 3 spots) and set your anti-aliasing, etc to `performance' in nvidia xserver settings.
If this resoves your lags you can try each setting, one at a time (and a reboot each time) and try to isolate which setting is causing your problem.

---

