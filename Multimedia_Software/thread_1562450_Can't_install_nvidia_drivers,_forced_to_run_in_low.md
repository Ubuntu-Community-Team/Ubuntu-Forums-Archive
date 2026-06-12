---
title: "Can't install nvidia drivers, forced to run in low-res."
date: 2010-08-27
forum: Multimedia Software
---

### Post by /bee/ on 2010-08-27
10.04 64-bit
+
NVIDIA GeForce 8500GT 256MB

So I kind of had ubuntu working, but then I tried updating to the newer nvidia drivers and I broke it.  I had to uninstall/purge nvidia so as to get ubuntu past the black screen/no signal to monitor...

I had been using a "Broadcom B43 wireless driver" which used fwcutter to extract firmware from various source files.  I have never been able to get this install working with nvidia drivers and am about ready to try anything (including yet another reinstall).

**Nvidia drivers 96, 173, & current cause my system to freeze, lock up, reboot, fail to boot, etc.  You name it and it's happened.**

I tried using synaptic, jockey and the terminal to install nvidia drivers.  Then I tried adding the swat ppa and installing through System-Admin-Hardware Drivers to no avail.

Every time I start my PC it displays this window.
[img]http://imgur.com/PbWEl.png[/img]


And when I open Hardware drivers this is what appears.
[img]http://imgur.com/O3jD9.png[/img]


I'm in over my head.  All help is appreciated, I am determined to fix this instead of throwing in the towel and giving up.

I will gladly add any helpful log files or terminal outputs asked for.  I'm just not sure what would be of help.

---

### Post by Rilion on 2010-08-27
Why don't you try Envy? It worked fine for me, it let's you change the resolution high. I have a GeForce MX 440 64MB, which uses the 96 driver. You might want to remove any drivers other than the default before installing. The best thing in Envy, that it configures everything on it's own, you don't need to mess with the xorg.conf - you only set the size and refresh rate in the System>Administration>NVidia X Server settings, as it was meant to be. I know you said that the most common drivers cause your PC to die, but I haven't seen any other drivers around. Maybe you need to reinstall Ubuntu first, then set the new driver on a blank OS. By the way, I still use 9.10, though I'm not sure that has to do anything with the drivers.

Good luck,

Rilion

---

### Post by /bee/ on 2010-08-27
I reinstalled Ubuntu and immediately went to the Hardware Drivers window to select the Nvidia driver "version current".  Rebooted and got the black screen/no signal dilemma again.  Tried purging nvidia in rescue mode but still can't get it to boot.  I'm giving up and reinstalling yet again and I'll give Envy a try.


edit: for some reason I was mistaking that Broadcom driver for my video card, but it's actually for my wireless network card.

---

### Post by Rilion on 2010-08-27
> **/bee/ said:**
> for some reason I was mistaking that Broadcom driver for my video card, but it's actually for my wireless network card.

That's why I was surprised - I never heard of a video card manufacturer called "Broadcom". Besides, there are no third party drivers - not common, not advised. The driver which the synoptic installs by default isn't good for me either - sometimes the newest isn't the best. And there are just too many problems with installing from a source file in lvl 3 (with UI turned off).

---

### Post by /bee/ on 2010-08-27
And envy isn't supported in Ubuntu 10.04, you're supposed to use jockey instead... which hasn't worked with my card.

So, a quick recap/update:

1. I started with a fresh install of 10.04 64-bit.  Opened jockey to select proprietary driver -- 173 and current were my only choices.  Tried current version first and rebooted.  Screen froze and pixelated just before login screen.

2. Another fresh install of 10.04 64-bit.  Opened jockey and installed 173.  Rebooted and it got hung up after I entered my password and pressed "Enter" to log in.  Subsequent boots didn't often make it that far.
Rebooted and held shift.  Dropped to root shell and purged nvidia*.  Now I can boot into low-graphics mode again, but all available nvidia drivers fail.


I'm bewildered and in desperate need of some help!

---

### Post by Linuxforall on 2010-08-27
For your card you need nvidia current.

---

### Post by /bee/ on 2010-08-28
That's quite unfortunate because then it simply refuses to boot.  I posted another problem thread similar to this ages ago, but it was never solved and has since been closed.

Let me try to be more clear.  Installing any iteration of nvidia driver causes system instability that results in a seemingly unavoidable system crash during all subsequent boot attempts.  None of the other threads regarding the black/blank screen (no signal to LCD) have helped resolve my problem.

I reinstalled Ubuntu 10.04 64-bit 3 times yesterday and tried using jockey to download/install nvidia's drivers (including current), but each time, the system hangs during the required reboot.

I know my way around Ubuntu fairly well, but without any further help, the only option I see is to avoid installing any proprietary drivers until I can afford a card that will (theoretically) work better than my current one.  No compiz makes me rather sad... especially since this machine worked so nicely under Hardy.

Thanks anyways.

---

### Post by /bee/ on 2010-09-07
I hate to bump a thread, but does anyone have any insight for me at all?

---

### Post by /bee/ on 2010-09-19
And so my problem persists...

---

