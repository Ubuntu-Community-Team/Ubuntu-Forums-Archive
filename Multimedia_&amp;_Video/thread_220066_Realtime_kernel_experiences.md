---
title: "Realtime kernel experiences"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by Sheik Yerbouti on 2006-07-20
Audio on Linux has been an interesting road for me so far. I won't share all the gory details as it's enough for a whole book. Just suffice to say that it has taken a solid month of constant tweaking, testing, adjusting and what not to get the setup where I am happy with it.

Here are some things I have discovered along the way.

1. Make sure the audio card you plan to use with jackd is not sharing an IRQ with something else.

see [here]("http://www-128.ibm.com/developerworks/library/l-hw2.html") for further explanation 

2. When compiling the vanilla kernel with realtime pre emption patch seriously consider using the CONFIG_PREEMPT_DESKTOP option and not the CONFIG_PREEMPT_RT for a couple of reasons. 

With the CONFIG_PREEMPT_RT my system was ten kinds of unstable and from reading different forums and such this is not all that uncommon with this setting. I experienced many complete system freezes, graphical anomalies, alsa going out to lunch and never coming back etc.... 

Keep in mind with the stock Ubuntu kernel it was rock solid stable. A friend of mine suggested backing it off a notch to  CONFIG_PREEMPT_DESKTOP and he was right on. I have low latency 5 msec no xruns and rock solid stability. In my mind 5 msecs is great. I mean I was getting 7 msecs with ASIO under Windows.

Also when I was running the CONFIG_PREEMPT_RT kernel vmware would not compile against that kernel. I am guessing the full spinlocks for IRQ handlers was tripping it up. With the CONFIG_PREEMPT_DESKTOP vmware compiles fine against it. Note: the vmware any any [patch]("http://ftp.cvut.cz/vmware/") is required though to get it to compile. This is huge for me since now I can stay in my realtime kernel full time. But the biggest thing by far is the stability and it is really night and day.

I would suggest that the CONFIG_PREEMPT_DESKTOP option be really highlighted on the wiki. If not the recommended default for Ubuntu Studio. given that Ubuntu seems to attract the desktop set. Also the Planet CCRMA folks default to the CONFIG_PREEMPT_DESKTOP settings for there core  but offer a second kernel with the CONFIG_PREEMPT_RT option noting that it might be unstable.

Also I originally started out with ubuntu but have since moved to kubuntu (sudo apt-get install kubuntu-desktop). Reason being is that things like qjackctl and rosegarden seem to run better under KDE. For example with qjackctl and low latency the gnome task bar would flicker and such and no such graphical anomolies happen under KDE.

Also one last thing to share some interesting advanced musings on audio settings and linux.

[http://tapas.affenbande.org/?page_id=40](http://tapas.affenbande.org/?page_id=40)

I found this intersting reading all though I did not end up using a lot of these tweaks because I am happy with what I have now and am full sick of tweaking for now. I did however change the realtime priority of jack in qjackctl to 70 and that does seem to improve things quite a bit.

Anyway sorry for the long post but I felt the need to do a brain dump here.

---

### Post by dolson on 2006-07-20
CONFIG_PREEMPT_DESKTOP on a -rt patched kernel **is the same** as CONFIG_PREEMPT on the Ubuntu default kernel. There is no difference, except that you have recompiled a kernel with less drivers, patches, etc.

The wiki will not change what is stated there, because what you are suggesting is already the default in Dapper. I will add a note about stability, however.

Again, the entire point of the -rt patch is to give the CONFIG_PREEMPT_RT option.

Not everyone has the stability issues, but it is not shocking either, considering that this is a meg and half or so of largely untested and ever-changing kernel source code changes.

---

### Post by Sheik Yerbouti on 2006-07-21
I did not realize that that is very interesting. Hrmm I don't see similar performance between the two that is for sure. The one I compiled is able to do lower latencies and with less xruns than the stock kernel. Perhaps as you said it is because it has less patches and modules. So this setting is not affected by the RT patch at all?

---

### Post by dolson on 2006-07-21
You would need to confirm this 100% with Ingo himself, but I'm about 99% sure that the -rt patch only changes the name of the config flag, and adds in the -RT option, which implements all the changes. There might be other changes outside of preemption that affects performance though.

Also, you should try recompiling Dapper's kernel with the hires timer enabled and set the resolution to 1000Hz. The last I checked, they changed it back down to 250Hz, which is CRAP for audio.

---

### Post by Sheik Yerbouti on 2006-07-21
Ok so you piqued my curiosity Dana. I thought for sure I was done tweaking this stuff for now.

But I did as you suggested and recompiled the stock Ubuntu kernel without the RT patch and simply changed the system timer to 1000 hz.

And you were largely right this significantly improved jackd latency performance over the current stock kernel compiled with the 250 hz option.

Interestingly the RT kernel with CONFIG_PREEMPT_DESKTOP was still better than the stock kernel with 1000 hz timer. 

What I do to test my audio setup is load up qjackctl and try and push it as hard as I can by loading up tons of audio stuff. Usually I load.

ams with the demo patch
hydrogen with jazz kit demo playing at 50 bps
Amsynth
Horgand
2 Whysynths
Nekobee
Hexter

I link all of the softsynths to my novation xstation simultaneously. And try and get as many voices as I can to push the DSP usage meter past 50% in qjackctl.

Doing this test under the RT kernel at 128 frames with CONFIG_PREEMPT_DESKTOP produces 
0(0) xruns.

With the stock plus 1000hz timer I got 2(3) xruns.

Really though the stock kernel with 1000hz timer was much more usable than the current stock with 250 hz timer.

I did discover this though. With the RT patched kernel and CONFIG_PREEMPT_DESKTOP. I could run chrt from the schedutils package. And change the realtime priority of things. So for example what I did was change the priority of the IRQ handler of my soundcard like this.

sudo chrt -f -p 82 `pidof "IRQ 66"`

IRQ 66 being the irq for my Delta 66 (the 66 is a coincidence) and then ran jackd with a RT priority of 70 as outlined [here]("http://tapas.affenbande.org/?page_id=40")

And low and behold I could drop down to 64 frames or 2.67 msecs with zero xruns driving the system over 50% dsp usage.

That's pretty sweet.

You know though had I had the 1000 hz compiled kernel to start with like a month ago I would probably have never had to go past that.

Which begs the question how can we fix this for new people.

I recently filed the system timer 250 hz issue as a bug with the Ubuntu devs even before this discussion and I was told.

"1000HZ is way to high for a lot of systems. Particularly laptops, where
the high timer resolution causes uneeded battery drain.

How does MIDI require 1000HZ? MIDI has been working in Linux a long
time, likely predating the time where the kernel worked with anything
except 100HZ."

So if it really does drain laptop batteries I can understand the change.

I am going to update the bug I submitted with this new info and suggest there be a 1000hz system timer kernel option in the dapper repositories.

And if they won't do it shouldn't we build it and put it in the repositories?

I am willing to do it if someone can explain to me how to do it the right way. In terms of making it just like the Ubuntu kernel with different architecture targets and the pretty splash and all that.

---

### Post by dolson on 2006-07-21
You are right. I would like to provide this kernel,  but I want it built properly, and it has to be kept up with Ubuntu's constant upgrades. Forest knows how to do it, so I will ask him about it. In the meantime, a wiki article about it is in order.

I don't understand why the Ubuntu devs would change this after they had it at 1000Hz for a long time. They should make a -laptop kernel for laptop users. Just my opinion.

If they are arguing that MIDI worked back in the 100Hz days, then they obviously don't know anything about using MIDI beyond playback, and they aren't really in a position to talk about it.

The chrt program may only work with Ingo's patches? That could be another further change in his code, I don't know. I haven't even touched chrt yet. :)

---

### Post by floogy on 2006-08-13
I vote for a simple kernel option to tweak the frequency such as **sys_hz=1000**, but I'm not shure, if such a kernel patch is simple to develop and if the kernel-dev's would agree to something like that.

---

