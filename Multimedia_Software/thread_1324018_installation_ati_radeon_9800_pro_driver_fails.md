---
title: "installation ati radeon 9800 pro driver fails"
date: 2009-11-12
forum: Multimedia Software
---

### Post by lamunk on 2009-11-12
Hi all,

After switching video cards with a friend of mine, I've been trying to get an Ati Radeon 9800pro up and running on Ubuntu 9.10. 

Currently it uses the standard linux drivers, but those don't use the full card potentional, and the fan of the card is spinning at top speed which is quite noisy. 

After spending quite some time trying to get the official ati driver up and running, I decided to write this post because I haven't been able to find any solutions.

When I install the driver from my terminal I get this error:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

My question is: could anyone please help me with this thing?

Thanks 

ps.
I'm into ubuntu for just a few months now, so I guess you could say I'm a noob.

---

### Post by bailout on 2009-11-12
I am running karmic on a 9800pro as well and finding performance is quite poor with the default drivers. Can't offer any solution as I haven't found one yet.

The driver from ati no longer supports the 9800pro so you can't use that.

---

### Post by lamunk on 2009-11-13
Well apparently Ati still offers the 9.3 driver for the 9800pro card but it only runs on old linux kernels (below 9), which is crap as there is no support for that either. 

The thing is when I install any ati synaptic package and reboot, I get this beautiful rainbow of colors where my login screen should be... and the default drivers hardly use the video card hardware, so it actually slows down my system quite noticeably. 

There should be proper linux drivers for this card but which ones?

---

### Post by zalnn on 2009-11-16
anybody? anything?

---

### Post by Dimarchi on 2009-11-16
The default drivers are your only option (not strictly true, but for the sake of your sanity, let's just put it that way ;)).

If you wish, you can always test the latest and the greatest default driver version, which may require you to go through ordeals you would rather avoid.

---

### Post by zalnn on 2009-11-16
my problems is that i have dual heads and performance is pretty bad.
i mean moving windows around is really choppy.

i have a fresh install; haven't tried installing any drivers etc.

---

