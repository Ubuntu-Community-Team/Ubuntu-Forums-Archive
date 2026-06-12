---
title: "LMMS produces no sound output"
date: 2010-01-01
forum: Multimedia Software
---

### Post by northrup on 2010-01-01
I can hear crickets chirping in the Multimedia Production forum... might as well try here instead...


I installed LMMS 0.4.5 on my computer (Ubuntu 9.10), but I'm getting no sound output from the program on ALSA, and whenever I try one of the other options (PulseAudio, OSS, etc.) it reverts to dummy audio. I tried installing JACK to correct the problem, but JACK seems to be giving errors and quitting, and in the past I've always used ALSA for LMMS and it's worked just fine.

The problem is local to LMMS, even after a reinstall. My audio output is fine for all other programs I've tested the problem for so far.

What could be causing this issue?

Also, I just noticed that my instances of LMMS are not being terminated after the windows are being closed...

Notable system info:

Ubuntu 9.10 x86 (kernel 2.6.31-16-generic) installed via Wubi
LMMS 0.4.5 (installed via Ubuntu Software Centre)
3.06 GHz Pentium IV (it looks like dual core)
432 MiB RAM
ATI IXP 584x0 High Definition Audio Controller (according to the lshw command

---

### Post by maxadocious on 2010-01-02
Let me preface this with the fact that I'm a huge newb.

I switched about 4 mo. ago from Mac OS (14-15 yrs.)  so I'm vry GUI oriented.

anyways, I was beating my head on the wall trying to get Hydrogen to work, and I installed Jack and qjackctl, and I expected to find a nice faq about how to get jack working. I ended up just having to go to the website for jack. they said that if you modify the limit.conf file (sudo gedit /etc/security/limit.conf, i think) to include a couple of lines, that it would work. And indeed it did. I did this to give my username access to jack, and upon restart, (and opening the jack app & pressing start) hydrogen works fine. Thinking it would all be the same, I tried opening LMMS which i was having similar problems with, but it said I needed to give the program access to jack, so i modified the limit.conf file again, but i haven't tried yet.

granted if you've already been through all of this rigomoroll then i'm sry, but if you're in the same boat, maybe this will help. good luck

---

### Post by kozmad on 2010-01-03
Hi,
try this link it worked for me:
[http://lmms.sourceforge.net/wiki/index.php?title=Installation](http://lmms.sourceforge.net/wiki/index.php?title=Installation)
Unfortunately I couldn't solve using another music program and LMMS in the same time.

I think using LMMS with JACK is not the best way, i've tried it but it was much more slower, the sound wasn't continous.
Maybe your JACK settings is not correct. I think you should check if the realtime box is checked, because you need realtime (rt) kernel for using realtime function in JACK.

---

### Post by a2z on 2010-01-04
> **northrup said:**
> I can hear crickets chirping in the Multimedia Production forum... might as well try here instead...


I installed LMMS 0.4.5 on my computer (Ubuntu 9.10), but I'm getting no sound output from the program on ALSA, and whenever I try one of the other options (PulseAudio, OSS, etc.) it reverts to dummy audio. I tried installing JACK to correct the problem, but JACK seems to be giving errors and quitting, and in the past I've always used ALSA for LMMS and it's worked just fine.

The problem is local to LMMS, even after a reinstall. My audio output is fine for all other programs I've tested the problem for so far.

What could be causing this issue?

Also, I just noticed that my instances of LMMS are not being terminated after the windows are being closed...

Notable system info:

Ubuntu 9.10 x86 (kernel 2.6.31-16-generic) installed via Wubi
LMMS 0.4.5 (installed via Ubuntu Software Centre)
3.06 GHz Pentium IV (it looks like dual core)
432 MiB RAM
ATI IXP 584x0 High Definition Audio Controller (according to the lshw command

Oh no, I'm having the same problem. lmms worked prefeftly in jaunty but broke after karmic upgrade.

I tried reinstalling through synaptics, and also put the path in software repository and tried to upgrade through the terminal. 

Alsa says I have 5 plugins... all with their sliders turned to max. 
Still no sound:confused:

Still no sound after sys upgrade. I noticed this upgrade installed some audio files. Maybe the rest are currently being written?
Edit: While trying to edit my post, my system rebooted itself:confused:
And I checked lmms and the sound is now working!
Amazing!

---

### Post by northrup on 2010-01-05
Thank you all for your responses.  I'll try looking at the link to the LMMS site, though that was the first place I checked.  I'm away from the computer in question right now, but I'll be sure to report if any of these procedures worked :)

---

### Post by Ermin0s on 2010-01-17
> **a2z said:**
> Oh no, I'm having the same problem. lmms worked prefeftly in jaunty but broke after karmic upgrade.

I tried reinstalling through synaptics, and also put the path in software repository and tried to upgrade through the terminal. 

Alsa says I have 5 plugins... all with their sliders turned to max. 
Still no sound:confused:

Still no sound after sys upgrade. I noticed this upgrade installed some audio files. Maybe the rest are currently being written?
Edit: While trying to edit my post, my system rebooted itself:confused:
And I checked lmms and the sound is now working!
Amazing!


Well i have the same problem right now but i dint had jaunty.
i also have karmic and my lmms doesent give any sound and i also have the 5 plugins maxed out.
but all my other sounds works like rythmbox or with firefox.
so annoying because it looks like fl so i know how i works but no sound!!!!!
 
so im waiting till my system reboots:P 
havent you done anything that might solved it?

oh and when i wanted to shut down my pc there were like 20 lmms running but i closed them :S
and i also have a ati sound card 



Ermin

---

