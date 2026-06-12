---
title: "VLC does not respect &quot;disable screensaver&quot; setting"
date: 2009-11-22
forum: Multimedia Software
---

### Post by negativ on 2009-11-22
When playing DVDs or videos through VLC, the screensaver kicks in even though "disable screensaver" is ticked in tools->prefs->advanced->video.  I have no idea why.

I have another machine with very similar hardware & software packages installed (nvidia accelerated driver 185 on both) and the setting works correctly on the other machine.  

Where would I start digging to figure this out?

edit:

Oops, I just thought of this; it might actually be a big deal. (/facepalm)

the biggest difference between the two machines is the one that works correctly is 32-bit and was first installed with the Karmic RC release, then upgraded to "official".  The one that does not work is 64-bit, installed from the "official" release.

---

### Post by undertakingyou on 2009-11-23
I am having this same issue on my machine and it is a fresh install 32 bit. I don't think it is the bit's that is the issue.

---

### Post by p_schott on 2009-11-24
The bug has been reported here :
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/428884]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/428884")

---

### Post by gobotsoup on 2010-04-30
So, there is still nothing for this issue? Any workaround or anything?

---

### Post by no2498 on 2010-04-30
totem turns the screen saver off in/on 910
you may find settings in it

---

### Post by Chronon on 2010-04-30
There's an app called "caffeine" whose purpose is to disable/prevent screen-savers, sleep, etc.

[http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html](http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html)

---

### Post by gobotsoup on 2010-05-01
> **Chronon said:**
> There's an app called "caffeine" whose purpose is to disable/prevent screen-savers, sleep, etc.

[http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html](http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html)
Thanks that looks like a cool little program. I tried installing using the PPA, but I got an error when it was requesting the key: 

gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

### Post by testora on 2013-03-30
[COLOR=#333333][FONT=Ubuntu Beta]SOLVED!!!

For easy understanding, the below instructions are shown in this video:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][http://www.youtube.com/watch?v=hmyPbhwjBn0](http://www.youtube.com/watch?v=hmyPbhwjBn0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
Since this problem is related to the operating system of any computer, this solution works for any other video player which has the same problem on screensavers.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
How to disable VLC player's Screensaver for good![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
While playing or after played a video on VLC, the Windows screensaver will come on (activate).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
The settings option within the VLC won't work to disable it. See the path:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]VLC -Tools - Preferences Go to left bottom column at Show settings and activate All button. Navigate down to Video section. Mark the option "Disable screensaver" All that won't disable the screensaver because VLC is related to your Windows settings for screensaver.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
Therefore, go to Desktop, right-click, and go to Screensaver options. In Windows Vista is: right-click on Desktop - Personalize - Screen Saver.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Look at "Wait" value. If it says 10 minutes, VLC will activate the screensaver after 10 minutes of idle, EVEN THOUGH your windows screensaver is deactivated. If it say 1 minute, VLC will do it after 1 minute, and so on.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
To fix all this problem, is to cheat: change the value to a very high one, like 480 minutes.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Change the value activating the screen saver and deactivating it just like i did before.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
From now on, VLC won't bother you at all. :)[/FONT][/COLOR]

---

### Post by QIII on 2013-03-30
Very old thread.  Closed.

---

