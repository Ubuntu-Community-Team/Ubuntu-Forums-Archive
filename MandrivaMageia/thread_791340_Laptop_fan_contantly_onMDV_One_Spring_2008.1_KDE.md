---
title: "Laptop fan contantly on:MDV One Spring 2008.1 KDE"
date: 2008-05-12
forum: Mandriva/Mageia
---

### Post by shuttleworthwannabe on 2008-05-12
I am dual booting with Ubuntu 8.04, so I can compare power and freq scaling in both. Ubuntu does with very neatly, but MDV KDe event though KPowersave is isntalled does nto seem to achieve the same freq scaling as does Ubuntu. Fan is contantaly on.
Is there another application that will automatically scale cpu freq when not in use (ondemand); and fire fans only when needed.

Thanks for the help,
S

---

### Post by shuttleworthwannabe on 2008-05-14
some feedback; gnome version does not have cpu scaling issues ( I have moved to GNOME now)

---

### Post by AdamWill on 2008-05-14
It's likely that there was nothing wrong with the actual scaling, but your CPU was genuinely being used more. I've been following a discussion on our development mailing list lately which notes a few things in 2008 Spring which likely cause quite high 'idle' CPU usage. You can check exactly what's going on by monitoring /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq , which gives you the actual current speed your CPU's running at.

---

### Post by dca on 2008-05-14
If it's a laptop, has anyone tried removing desktop kernel while installing laptop kernel?  Apparently when I tested Mandriva 2008.1, it installed the desktop kernel on my laptop which limited avail mem and a few other issue(s)...

---

### Post by AdamWill on 2008-05-15
One always installs the same kernel, desktop586, due to the way its installation system works. Free and Powerpack will install the correct kernel for the hardware.

Honestly, though, kernel-laptop doesn't really change much from desktop. We've actually dropped kernel-laptop from Cooker, post-2008 Spring, because there was little real difference between the two.

---

### Post by shuttleworthwannabe on 2008-05-16
How would one them explain the difference I am noting betweeing KDe and GNOME versions (note, I did not install GNOME over the KDE install)? 
Also, if this helps, browsing using Firefox (especially pages that scripts, like this one and GMAIL) just makes the cpu go up and down, then heating takes over. This is not visible in Opera. The behavior of FF is also presen tin Ubuntu, BTW.
How would one explain this behavior.
Luckily, GNOME Mandriva is behaving and heating (thank goodness) is not becoming an issue).
Thanks

---

### Post by AdamWill on 2008-05-16
Couple of things. One, PulseAudio is a CPU hog in the KDE version because of how aRts works together with Pulse. aRts is the KDE sound server. It seems to keep a channel open to Pulse all the time, even when it's not playing any actual sounds, which causes Pulse to run its resampling algorithm on nothing at all, constantly (on many systems), resulting in a constant load on the CPU. So the CPU never hits its idle state, which could potentially cause the effect you're noticing. You could test by booting the KDE version and disabling PulseAudio, to see if it helps.

Second, I've noticed a candidate update going through for KDE for another power-related issue. If I'm reading the advisory text right, it seems like the neat constantly-changing-background feature was refreshing far too often in KDE, which again eats unnecessary power. The update will significantly increase the refresh interval, which should alleviate that problem. The candidate update is kdebase-3.5.9-37.1mdv2008.1 , you can grab it from the /main/testing repository if you want to check it out.

I suspect those two issues combined might account for the difference.

---

### Post by dca on 2008-05-16
> **AdamWill said:**
> One always installs the same kernel, desktop586, due to the way its installation system works. Free and Powerpack will install the correct kernel for the hardware.

Honestly, though, kernel-laptop doesn't really change much from desktop. We've actually dropped kernel-laptop from Cooker, post-2008 Spring, because there was little real difference between the two.

Desktop kernel maxes out at 1GB MEM, laptop up to 4GB...  Other little differences as well...

---

### Post by AdamWill on 2008-05-18
Nope, desktop586 maxes out at 1GB. desktop supports up to 4GB.

desktop586 is built with only i586 optimizations and only supports up to 1GB; it basically exists because Mandriva still supports i586 CPUs. It only supports up to 1GB of RAM because basically no-one is running an i586 CPU with more than 1GB of RAM, and 'himem' support - supporting up to 4GB rather than 1GB of RAM - actually comes with an appreciable performance overhead that users of i586 machines would notice. This does leave a bit of a loophole in terms of One, though. One has to use desktop586 so it can be booted on i586 machines. If it used the regular desktop kernel (which is built with i686 optimizations), it couldn't.

In 2008 Spring, the only actual differences between the desktop and laptop kernels are:

i) timer lowered from 1000Hz to 300Hz, but we have NO_HZ enabled on both kernels anyway, so this actually makes very little difference to anything.

ii) Big kernel lock preempting disabled: this actually has no effect as it's only defined for an architecture we don't support.

iii) USB_SUSPEND enabled: post-2008 Spring this is no longer experimental so we've just enabled it in kernel-desktop.

iv) a bunch of modules for hardware that would never be in a laptop were not built to save a bit of space.

and that's it. That's the sum total of differences. Three that made no practical difference and one that's no longer necessary post-2008 Spring. That's why we dropped the laptop kernel in Cooker now. :)

---

### Post by Dutchmaster on 2008-05-18
> **shuttleworthwannabe said:**
> I am dual booting with Ubuntu 8.04, so I can compare power and freq scaling in both. Ubuntu does with very neatly, but MDV KDe event though KPowersave is isntalled does nto seem to achieve the same freq scaling as does Ubuntu. Fan is contantaly on.
Is there another application that will automatically scale cpu freq when not in use (ondemand); and fire fans only when needed.

Thanks for the help,
S

I ran the same setup cool as a cucumber on my laptop - markedly cooler than Ubuntu, which runs a little warm.

The regulator is called kpowersave. It shows up on the taskbar as a plug or battery icon on the right usually. Right click on it for preferences or something similar. There is a tab choice to address cpu frequency. Choose dynamic. That should do it.

---

### Post by shuttleworthwannabe on 2008-05-18
@AdamWill, thanks for the detailed explanation; I will try the update and see how it goes.

How about the Firefox issue--cpu fires each time I move page up or down (applies to all linux flavors); but using opera (and now tried with midori webkit or konquerer) this is not happening?

@Dutchmaster: Yes, thanks. I had it at dynamic, yet still gave me cpu issues.

---

### Post by AdamWill on 2008-05-20
Does your Firefox issue happen on *any* page? Or only ones with Flash, maybe?

---

### Post by shuttleworthwannabe on 2008-05-21
whenever I chnage the page (click on link to load page) it fires; it is worse on Ubuntuforums (ithink here uses javascripts??); and yes, flash is a no go zone. I have ntoiced this in Wondows FF as well (Flash issue).

---

### Post by AdamWill on 2008-05-21
Hmm, that does seem a bit odd. I'm not really qualified to tell if it's normal or a bug or it can be fixed, though. Maybe try disabling some plugins / extensions temporarily to see if they're causing it? I've heard that a lot of issues with 'Firefox' actually turn out to be extension problems, when you check...

---

### Post by shuttleworthwannabe on 2008-05-27
> **AdamWill said:**
> You could test by booting the KDE version and disabling PulseAudio, to see if it helps.



Adamwill: I have GNOMe on right now; but installed KPDF with the kdebase files; i notice the CPU heating and fans blowing now in GNOME- so it does seem to be the issues with KDE and either pulseaudi or kdebase as you suggested.

So I am:
1. installing update to the kdebase as you suggested,
2. trying to disable pulseaudio--but am not sure how to do this? Do you have a suggestion? Note: I am in GNOME Mandriva One Spring 2008.1

Many thanks
S

---

### Post by AdamWill on 2008-05-27
You can disable Pulse from the Mandriva sound configuration tool, 'draksound' (run it directly or find it in the Control Center). Once you've disabled it, you need to restart X or reboot.

---

