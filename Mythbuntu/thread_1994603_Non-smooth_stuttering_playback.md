---
title: "Non-smooth stuttering playback"
date: 2012-06-03
forum: Mythbuntu
---

### Post by Ramrunner on 2012-06-03
Hey all,

This is actually an issue I've noticed since I've attached a 1920x1080 Samsung smart TV to my system (as opposed to my old NEC 1024x768). On the NEC, after seeking through ads, I used to occasionally get a little stutter after the seek, but it generally lasted a few seconds and playback was smooth directly after. The box was also loaded with other programs (transmission, active postfix etc.) Even when the box was approaching load avarage of 2.0 no problems.

So, after the TV upgrade, I noticed bad stutter on SOME shows. Bikie wars, NCIS, Revenge to name a few, mostly in panning shots or where there is a lot of background movement. I generally HARDLY notice it on MotoGP (HD), Formula 1 (HD), The Voice, Survivor to name a few of the good ones.

Funny thing is the 1080p content of the F1 would suggest the box is more than capable of playing the content properly.

So, what I've done to try and fix this:

1> Got a NAS and moved pretty much all background services. Load average now does not get above 0.3 pretty much.
2> Upgraded the video card from GT8500 to GT430.
3> Added the triplebuffer command to X configuration, as well as the composite thingy.
4> Although I haven't made it PERMANENT yet, turned off CPU throttling.
5> Tried every different profile on the planet (VDPAU, OpenGL, CPU in all flavours of slim, normal, and high).
6> Upgraded from 10.4 to 10.11, then to 11.04, 11.10, now 12.04. I'm now running myth 0.25 as a result obviously.
7> Turned off powermizer in the nvidia settings.

None of these seem to fix the problem. I've just run mythfrontend through a terminal and captured the log. There are a few errors, but I'm not sure how vital they are or what to do about them. Can someone please suggest other things to try and/or have a look at these logs and maybe see if there's anything I can do here?

Core 2 Duo 6600
WD15EARS Hard Disk
Asus GT430 Silent

Should be more than capable right? :(

Regards,
Ed.

---

### Post by Ramrunner on 2012-06-03
Oh, sorry to reply to my own post - I know it's bad form. This is a combined fe/be setup to all access is LOCAL.

---

### Post by nickrout on 2012-06-03
Turn off composite in your xorg config for a start!

What video drivers are you using? nvidia proprietary at a guess, what version?

you could try running mythfrontend -v playback and see if any informative errors come up

---

### Post by jeremycobert on 2012-06-03
does it happen with both interlaced or progressive video scan ?  for some reason I get stuttering on my local NBC HD channel unless I switch to progressive scan at which point it instantly fixes the issue.

---

### Post by Ramrunner on 2012-06-03
> **nickrout said:**
> Turn off composite in your xorg config for a start!

What video drivers are you using? nvidia proprietary at a guess, what version?

you could try running mythfrontend -v playback and see if any informative errors come up

Sorry - I wasn't clear. Composite is turned off. The option in xorg.conf is:


Section "Extensions"
        Option  "Composite"     "Disable"
EndSection

nvidia version:

edward@MEDIA-PC:/etc/X11$ dpkg -l | grep nvidia
ii  nvidia-current                         295.40-0ubuntu1                                NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                                Tool of configuring the NVIDIA graphics driver

Must mention that I've upgraded all the way up from 10.04 so I've used older versions also that exhibited the same behaviour.

As for the playback log, I already attached it in my original post. Could you have a look and see if anything obvious? There's something there about changing audio buffers failing but I'm not sure why that would fail.

Thanks for the reply so far mate.

Ed.

---

### Post by Ramrunner on 2012-06-03
> **jeremycobert said:**
> does it happen with both interlaced or progressive video scan ?  for some reason I get stuttering on my local NBC HD channel unless I switch to progressive scan at which point it instantly fixes the issue.

Interesting question. I thought all our broadcasts here in Australia were interlaced but maybe not. Where is that setting and is it a global setting or can we turn it on/off per channel or show? I've always had the de-interlacing on as far as I know, as when I initially set all this up, I had the combing effect, and I'm pretty sure when I transcode something for the kids I have to de-interlace on the transcode to avoid the combing, but I haven't played with it lately.

Thanks a lot for the reply so far. I'm sure I can nail this after all this time, it's just frustrating to make all these changes after reading things in forums but not get anywhere :)

Regards,
Ed.

---

### Post by nickrout on 2012-06-03
> **Ramrunner said:**
> Sorry - I wasn't clear. Composite is turned off. The option in xorg.conf is:


Section "Extensions"
        Option  "Composite"     "Disable"
EndSection

nvidia version:

edward@MEDIA-PC:/etc/X11$ dpkg -l | grep nvidia
ii  nvidia-current                         295.40-0ubuntu1                                NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                                Tool of configuring the NVIDIA graphics driver

Must mention that I've upgraded all the way up from 10.04 so I've used older versions also that exhibited the same behaviour.

As for the playback log, I already attached it in my original post. Could you have a look and see if anything obvious? There's something there about changing audio buffers failing but I'm not sure why that would fail.

Thanks for the reply so far mate.

Ed.

Tru vdpau slim profile.

Do these recordings play back OK in, eg, mplayer with vdpau enabled?

---

### Post by Ramrunner on 2012-06-03
> **nickrout said:**
> Tru vdpau slim profile.

Do these recordings play back OK in, eg, mplayer with vdpau enabled?

I've tried all combinations of profile as I mentioned before, however, your mplayer suggestion is a good one.

I'll try it over the next few days and report back.

---

### Post by Ramrunner on 2012-06-05
> **nickrout said:**
> Tru vdpau slim profile.

Do these recordings play back OK in, eg, mplayer with vdpau enabled?

OK, I MAY have nailed this. I made some changes according to this article:

[http://www.mythtv.org/wiki/User_Manual:JudderFree](http://www.mythtv.org/wiki/User_Manual:JudderFree)

In particular what I never really paid attention to was the refresh rate that showed on my LED, whenever I switched to the MythTV box.

It said 60Hz. Now, in Australia, if I understand correctly we use PAL 25fps on our digital TV channels. The Auto setting in MythTV setup may be wrong for Australia. The Samsung is 60Hz capable, but broadcasts are at the usual 25fps. 60 does not divide by 25 very nicely. 

I separated the GUI from the playback screen as described in the above link, made the GPU scaling change and FORCED the playback screen at 50Hz.

What has followed is a clean no stuttering version of me watching Bikie Wars (one of the shows I have most problems with). Change it back to Auto and the stutter comes back.

Now, this needs another week or so of watching shows and making sure nothing else is broken, but this is the first time I've ever had smooth playback of this show. I even turned VDPAU High back on with no problems.

Leave it with me for a week. I will report back. If the problem is solved I will mark this thread as such for other European/Australian PAL users.

---

### Post by Ramrunner on 2012-06-15
OK, playback on TV programs is now baby skin smooth even on VDPAU high, as long as the refresh rate is forced at 50fps.

WARNING!!!

Doing this will mess with some MythVideo movies you may have that are NOT in a refresh rate that matches the TV. You will get judders on those :(

Ideally, I would like MythTV to set the refresh rate on the TV automatically to the right frame rate to match the content, but the Auto setting does not work for me.

For me not a big problem, as I tend to stream my movies from the NAS directoy to my TV, and only watch TV from the MythTV box, but this may not be the ideal solution for you.

If anyone knows why MythTV and MythVideo playback is so juddery if the TV refresh rate does not match the frame rate of the content, and knows a great work around, I'm all ears. For now, this will have to do for me.

---

### Post by BicyclerBoy on 2012-06-16
MythTV can be configured to select the best video mode "ANY" & this is meant to find matching mode.
Does this not work for you?

AFAIK the video mode presets are based on video pixel size..which is not really the best approach when 1080 could be i50 i60 or 24p.

MythTV 0.25+fixes/0.26 are hyper-sensistive to mismatch of video frame rate & display refresh rate.

But the best solution (if you have a capable display) is to get mythtv to automatically use the best video mode.

Open a terminal & run
xrandr --prop
post the results..

---

