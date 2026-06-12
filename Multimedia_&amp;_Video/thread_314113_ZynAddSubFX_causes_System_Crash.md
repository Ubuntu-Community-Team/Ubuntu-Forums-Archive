---
title: "ZynAddSubFX causes System Crash"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by Spenser_Gilliland on 2006-12-07
Hello,

I just got done with my first install of the ubuntu studio stuff.  I'm trying to follow the jack connection tutorial but when i launch zynaddsubfx the system crashes.  As in no ctl alt F1 console, and no ctl alt backspace end X.  I dont know why or how.  I have Dapper64 installed. I spent countless hours trying to install cinelerra before i installed the ubuntu studio stuff(tried from CVS, tried converting RPM, finally found a deb).  Therefore i have every codec known to man, along with there dev info.  Please help me out.  I'm trying to do something really cool for my school but im getting to the point where im gonna have to start studying for finals or else. lol.

Thanks,
Spenser

---

### Post by Spenser_Gilliland on 2006-12-09
anyone?

---

### Post by sgx on 2006-12-12
zyn is great...try starting all audio as root from the command line...I think zyn defaults to 48000, so
after a fresh reboot or startup, type these lines
one by one...
sudo jackd -d alsa -r 48000
sudo qjackctl
sudo vkeybd
sudo zynaddsubfx

don't select 'beginner' view
at startup...

connect audio then midi ins/outs in qjackctl
to vkeybd, or your midi keyboard, and to
alsa_pcm out 1 and 2 (left/right)

play...
(find zyns own larger virtual keyboard on its panel
if desired)
click on 'instrument' from the top menu,
select 'show instrument bank',
a large empty bank appears, so, to the left of
the 'refresh bank list' button, click that
little black triangle widget, and 19 choices
appear, each with roughly between 10 and 20 patches,
great sounds in there, I'll check back, please confirm
progress...hope this helps...

---

