---
title: "jack, xruns, rt-kernel???"
date: 2008-01-16
forum: Multimedia Production
---

### Post by studiesinsound on 2008-01-16
I know these things have been covered in other threads here on this forum however I have tried all of the suggestions but still have problems.

specifically:
I have a dell vostro 1000
2.0 gHz AMD64 x2 processor
2 gigs of ram
external usb m-audio fast track pro audio card.

running the latest Ubuntu Studio with teh real time kernal
running jack via jack control and sooperlooper

no matter how I tweak the settings in jack I get tons of xruns.  I really should have sufficient hardware so I'm a little baffled.

Like I said I read all the threads on here about tweaking jack and hacking the limits.conf file etc.
no good.

so here are my questions:
If I installed Ubuntu Studio, and when I get to the grub menu I boot into the -rt kernal, is that really getting me the realtime kernel?
Does this work out of the box so to speak or is more tweaking of the kernel needed.

The reason i ask is that I found this thread:
[http://tapas.affenbande.org/wordpress/?page_id=6](http://tapas.affenbande.org/wordpress/?page_id=6)
and related to that thread this one:
[http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

Do I need to do any of this stuff?
I thought UbuntuStudio would be tweaked for real time processing of the bat. no?

Thanks for any advice.

-John

BTW: great forum!  very active.

---

### Post by studiesinsound on 2008-01-18
bippity bump?

---

### Post by Drunky on 2008-01-19
Yes, the real-time kernel is set up for real-time preemption.

If you are using Qjackctl is the realtime box checked?

Have you checked the "soft mode" button.  This is stolen from a Dave Phillips email ..."Ignores xruns reported by an ALSA driver, making JACK
less likely to disconnect unresponsive ports when run without realtime
status. You might select this option to avoid too-copious error reports."

Also, have you considered that your usb external audio card might be the problem since your processor seems more than adequate?  USB isn't the fastest connection when compared to Firewire or pci cards.

---

### Post by studiesinsound on 2008-01-19
thanks for the reply

yes I have realtime checked but have not tried that soft mode.

i have considered the usb a the weak link,  the scond article I posted above has some steps to set the priority of the soundcard above the priority of jack, while both are set fairly high.

i'll mess with that.

i hope I can get these xruns down.

---

### Post by studiesinsound on 2008-01-21
so I followed the tutorial here:
[http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

and have gretly reduced xruns.

now I can get very low latency (1.2 ms, with no xruns.
new problem:
If I use sooperlooper 1.0.8 which is the latest version in the repos, I get frequent pops in the audio and then infrequent xruns.
However when the xrun happens, the audio coming otu of sooperlooper gets very bad and fuzzy.  Rebooting sooperlooper fixed the problem, until the next xrun.

I know it's sooper looper because I tested just running my signal through jack and then through some jack rack effects and had no issues.

I love you sooperlooper but you are killing me!!!

---

