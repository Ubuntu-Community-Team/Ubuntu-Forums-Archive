---
title: "Firefox + Flash = no sound (will pay)"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by ChrisC on 2006-12-01
First, please note my sig.  I'm serious.  I will pay for fixes.

Sound has always been flaky on my Ubuntu 6.06 install, but this time it really won't work.  More specifically:
 - CD playback works
 - mp3 playback in XMMS works
 - Flash sound does NOT work

I tried the latter in Google Video, Youtube and Pandora -- no sound in any of them, although the content loads and is playing (e.g. moving pictures).

It does this even with no other apps running, and after a clean reboot.  In the past a Firefox restart would usually fix it (ugh, gotta close all my browser sessions) or if not then a reboot definitely would.  All that's changed recently is that I applied the latest round of security fixes provided by Ubuntu.

I read [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) , but that has to do with getting the drivers to work, and my drivers seem to work fine, as evidenced by the successful XMMS playback of mp3 files.

Any ideas?  I'd even be happy with a solution that involves my running a "reset the sound" script every time it craps out like this.  I already have to do that every time I KVM away and back to this machine :)

---

### Post by divague on 2006-12-01
You could try this fix

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

Restart Firefox

---

### Post by ChrisC on 2006-12-01
Kick ***.  That worked!

Private message forthcoming ...

---

### Post by DX 00 on 2006-12-07
I had the same problem with firefox 1.5 and this solution fixed the problem. I upgraded to Firefox 2 and now I have the same problem. (I installed using this instructions [http://www.ubuntuforums.org/showthread.php?t=283965&highlight=install+firefox2](http://www.ubuntuforums.org/showthread.php?t=283965&highlight=install+firefox2) which means I have firefox 1.5 and 2.0 running). Now this solution won't work because in firefox2, i couldn't find a firefoxrc file. Any idea on what to do?

---

### Post by DX 00 on 2006-12-07
I found out that by deleting the flash player 7.X plugin and installing the flashplayer 9, everything seamed to work fine. The videos are a little choppy but other than that it works.

---

### Post by Old Pink on 2006-12-07
My guide: [http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

---

### Post by ChrisC on 2006-12-28
Just a followup ... divague's fix worked for me in that I now always have audio, but now I also frequently have Firefox crashes.  Nothing sucks quite as much as having your entire browser crash when you have a dozen windows open :(  It seems to be triggered when I navigate back away from a page that has flash in it, or reload the page.

Just now when I'd had enough of this crashing B.S. and was going to revert the firefox_dsp change, some googling led me to

[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)

which suggests adding

export XLIB_SKIP_ARGB_VISUALS=1

to the /usr/bin/firefox startup script; I added it at the bottom just before the program binary itself gets launched.   I'll keep the FIREFOX_DSP="aoss" for now and see if things go better with the ARGB fix.

---

