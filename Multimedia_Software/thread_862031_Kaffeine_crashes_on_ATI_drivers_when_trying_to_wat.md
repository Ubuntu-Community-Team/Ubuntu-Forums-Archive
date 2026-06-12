---
title: "Kaffeine crashes on ATI drivers when trying to watch DVB TV"
date: 2008-07-17
forum: Multimedia Software
---

### Post by skrzyp on 2008-07-17
Howdy

After installing ATI Proprietary driver Kaffeine (and whole KDE) crashes every time i try to watch Satellite TV. It's always the same - i pick a channel, kaffeine plays it few milliseconds and then crashes whole KDE. However it can still play DVD's well. Xorg logs says it's caused by SEGV signal.

When i change /etc/X11/Xorg.conf Driver setting from fglrx back to vesa everyting works fine. So i guess it is not DVB card issue. It's SkyStar 2 rev 2.8a (Just in case).

I use Kubuntu 7.10 32bit, Kaffeine 0.8.5

Thanks for help

---

### Post by petegreenhorn on 2008-07-17
Hi don't know if this will help you but ,while iwas checking my card compatibility (skystar 2 tv ) i read that there were issues with versions after 2.6 . You could try googling the problem , as i can't remember the place i read it

---

### Post by markbuntu on 2008-07-17
I am not familiar wih Kaffeine but I know the flgrx driver has some issues with certain video playback modes, like XVideo and OpenGL, I can't really remember which ones made it crash but I know that certain modes in VLC would crash. Also, Miro would crash when using xine but not with gstreamer.

I hope that gives you some info to work with.

---

### Post by dajs on 2008-10-22
> **skrzyp said:**
> Howdy

After installing ATI Proprietary driver Kaffeine (and whole KDE) crashes every time i try to watch Satellite TV. It's always the same - i pick a channel, kaffeine plays it few milliseconds and then crashes whole KDE. However it can still play DVD's well. Xorg logs says it's caused by SEGV signal.

When i change /etc/X11/Xorg.conf Driver setting from fglrx back to vesa everyting works fine. So i guess it is not DVB card issue. It's SkyStar 2 rev 2.8a (Just in case).

I use Kubuntu 7.10 32bit, Kaffeine 0.8.5

Thanks for helpSame with me, except I use Ubuntu 8.04 32bit. And I have DVB-T(Hauppage WinTv Nova USB) not satellite. 

Any idea?

---

### Post by jmontelius on 2008-11-29
Same problems on one of my machines, a Kubuntu 8.10 with motherboard ATI 690G X1250 graphics. On another machine with NVIDIA GeForce 6150 motherboard graphics I have no problem. Both machines have Twinhan DVB-T Ter. 

The ATI drivers are otherwise ok but I had to turn all desktop extras off since all video and googleearth flickerd. Vide playback works fine but severe problems with DVB-T in Kaffeine.

I'm using the ATI drivers from the repository, could the once from ati.com improve the situation?

---

### Post by MonGol on 2008-12-15
nope^^

i am using a 64bit ubuntu 8.04.1 (under 8.10 my skystar 2 doesn't work) and the ati driver provided at ati.com and still the whole system is crashing when trying to watch dvb tv.

marcel

---

### Post by hresto on 2009-01-31
I have the same issue with Kaffeine crashing after a few seconds using the XV setting. I also found out that immediately before the crash, if you switch out of KDE to a console ctrl-F2 or ctrl-alt F2 (I forgot combination) and then switch back to KDE F7, then Kaffeine will play fine in XV mode (HighDef)and in fullscreen also. If you switch the channel, then the crash process starts again. It must be something with the Kaffeine not initializing the XV driver properly. Kaffeine 8.5 and ATI Catalyst&#8482; 8.11 Proprietary Linux x86_64 Display Driver. X11 setting in Kaffeine works fine, but choppy in fullscreen.

---

### Post by Philip Farrugia on 2009-03-28
Hi,

Just installed sapphire 4670 card an can't get kaffeine or me-tv to play dvb-t without crashing whole system. Using latest catalyst drivers and Ubuntu 9.04 beta 32bit.

All's well if I remove the ati catalyst drivers.

Be nice to have all playing nicely together.

Has anyone found a solution yet or is it a case of wait, wait, wait till ATI improve their drivers?

---

### Post by Bend3r on 2009-06-30
I can't believe this isn't solved yet.

---

### Post by talonsoalbi on 2009-07-08
After a lot of search I found no solution to this problem, but I have found a provisional 'fix'. In a system with an ATI card (HD3650 in my case) Kaffeine will inmediately crash the computer, but the behaviour of MythTV is quite better. I have two problems with MythTV, always when changing channels (never when entering TV watching for the first time from the main window):
1. Sometimes (once each 5 channel changes) the image appears corrupt, with random horizontal lines.
2. When in the first case, and again sometimes (after one or two hours watching TV) the system crashes, as when one uses Kaffeine.

Possible fixes from the user point of view:
1. Pressing Esc to go to the main window and entering TV watching solves the problem, or better going to the program guide and pressing Esc to go back to Live TV. It is not necessary to do this in a few milliseconds to avoid crashes.
2. It is (not always) possible to press Esc very (but very) quickly to go to the main window and then enter TV watching, but it is better to minimize MythTV window (configuring a key in KDE, F8 in my case) for two seconds or so. After the channel has been changed successfuly, it is possible to maximize it without any crash (but maybe with problem 1).

This fix is not close to be the ideal solution at all, but at least seems to be a provisional way to avoid system crashes until a decent ATI driver is released, if this is going to happen one day.

---

### Post by hannuko on 2009-08-30
> **talonsoalbi said:**
> After a lot of search I found no solution to this problem, but I have found a provisional 'fix'. In a system with an ATI card (HD3650 in my case) Kaffeine will inmediately crash the computer, but the behaviour of MythTV is quite better. I have two problems with MythTV, always when changing channels (never when entering TV watching for the first time from the main window):
1. Sometimes (once each 5 channel changes) the image appears corrupt, with random horizontal lines.
2. When in the first case, and again sometimes (after one or two hours watching TV) the system crashes, as when one uses Kaffeine.

Possible fixes from the user point of view:
1. Pressing Esc to go to the main window and entering TV watching solves the problem, or better going to the program guide and pressing Esc to go back to Live TV. It is not necessary to do this in a few milliseconds to avoid crashes.
2. It is (not always) possible to press Esc very (but very) quickly to go to the main window and then enter TV watching, but it is better to minimize MythTV window (configuring a key in KDE, F8 in my case) for two seconds or so. After the channel has been changed successfuly, it is possible to maximize it without any crash (but maybe with problem 1).

This fix is not close to be the ideal solution at all, but at least seems to be a provisional way to avoid system crashes until a decent ATI driver is released, if this is going to happen one day.

I have the same problem, System is AMD Phenom II X4, Asus motherboard with build in ATI HD HD3300. My Digi TV card is Cinergy Terratech T2.
When I open digitv with kaffeine, I can see a few seconds and then I just get kicked out and login screen appears. I'm using Ubuntu 9.04 and Catalyst version (hmm.. cannot see it from the about screen.. maybe it was 9.something, however, the leatest version.)
Also, MeTV seems to work better. I think the reason might be HW decode or some other HW related think that Kaffeine is using, but MeTV is not.

When the cras happens, I get several lines on the /var/log/messages:
[B]messages.0:Aug 25 20:53:35 cave kernel: [81514.750897] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
messages.0:Aug 25 20:53:35 cave kernel: [81514.752284] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
messages.0:Aug 25 20:53:35 cave kernel: [81514.753730] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
messages.0:Aug 25 20:53:35 cave kernel: [81514.755136] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
messages.0:Aug 25 20:53:35 cave kernel: [81514.756544] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
messages.0:Aug 25 20:53:35 cave kernel: [81514.757127] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53[/B]

Doesn't that tell where the problem is?! I think the actual problem is not with the Kaffeine, but some function it is using. The problem is most likely at the fglrx driver.. 

I think I'll ban all ATI video cards.. very bad linux support :-(

---

### Post by Devport on 2009-12-14
Its an old thread, but since I needed to cope with this crash now too I would like to tell you that I solved it by setting the video driver in the xine-engine settings to xshm.

---

### Post by super4sang on 2010-01-06
Hello,

Same issue here: "Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53". It was due to RAM failures (frequency too high). When issue was solved, not more such crash. Conclusion: run memtest86+ to be sure it does not come from a RAM issue.

Nicolas

---

