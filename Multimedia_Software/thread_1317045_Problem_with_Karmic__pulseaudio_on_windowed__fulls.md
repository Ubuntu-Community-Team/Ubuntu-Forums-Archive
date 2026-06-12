---
title: "Problem with Karmic / pulseaudio on windowed / fullscreen switch."
date: 2009-11-06
forum: Multimedia Software
---

### Post by isoToxin on 2009-11-06
Hi,

I'm having an odd issue in Karmic / GNOME whereby if I switch between windowed / fullscreen in certain apps (SCUMMVM for example), it can sometimes cause said app to start maxing the CPU at 100% utilisation.  I've been able to narrow it down a bit, and I've found that once this happens, the only way to get things to calm down back to normal is to kill pulseaudio process.  Then the system/application will continue to be ok for a while, but the problem always resurfaces after a few further fullscreen / windowed switches.  This behaviour occurs using compiz or metacity, and also happens even when no other apps are running other than the one in question.  Also, it is not the pulseaudio process which is consuming all the clock cycles according to top/system monitor, it's the app itself.

The apps I'm always able to reproduce this on are SCUMMVM and Oolite which were both installed from the ubuntu repositories.  When the cpu is running at 100%, the application becomes a lot more sluggish.  Exiting the app brings CPU back to normal, but if it's relaunched, it just shoots straight back up again.  As stated, the only way I can restore things is by killing the pulseaudio process.

Sequence of events to recreate:

Launch SCUMMVM
Do alt-enter to fullscreen / window.
Repeat a few times (usually only a couple before the problem occurs)
Eventually, the application's cpu usage ramps up to 100%, laptop fans speed up etc.  It will stay like this until the app is killed, and it's impossible to run the app normally again until pulseaudio has been killed.

I'm not sure how to troubleshoot this any further.  The SCUMMVM app is using the ALSA plug-in, which I can see in the sound control applet for pulse.  I can work around it (try to avoid alternating between fullscreen / window, kill pulseaudio frequently), but it would be nice to know what could be causing it, or if anyone else sees anything similar to this with Karmic.

The laptop is a fujitsu-siemens p7010 btw, and the SCUMMVM app normally only uses around 45% cpu on this machine.  The audio is realtek AC97 solution, and video is intel 855GME.  This issue only ever occurs after fullscreen / window switching, even when there has been no actual resolution change.  It will run for hours if left in one mode or the other, but can't survive more than a few switches between.  It's only really an issue because I tend to do this a lot so that I can go between firefox and fullscreen app etc.  Oh, and problem still occurs even if firefox is not running.

If anyone can shed any light on what could be happening to cause this, or even just suggest a few things which can cause these kind of symptoms in ubuntu, I'd be most grateful.

Thanks.  :)

---

### Post by isoToxin on 2009-11-06
I've managed to eliminate this problem by disabling pulseaudio.  I didn't actually uninstall it and switch to esound like a lot of people though, because ubuntu seems tightly integrated with pulse and other than the full screen switch problem, I haven't had any other issues.  I think the method I used is quite common, but will repost just in case anyone else wishes to know.

I just created a "client.conf" file in ~/.pulse folder, and added the line:

autospawn = no

Then did

killall pulseaudio

That causes it to stay killed.

Then I can fullscreen switch as much as I want without any of the cpu problems I described.  Seems there are lots of issues with pulse atm going by what I've seen on various linux forums this evening, but I can see the potential / features, so it just needs to mature a bit more probably.

---

