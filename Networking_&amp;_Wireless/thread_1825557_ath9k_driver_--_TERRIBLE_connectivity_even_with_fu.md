---
title: "ath9k driver -- TERRIBLE connectivity even with full strength signal"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by tdennist on 2011-08-15
I have an Atheros AR9285 wireless card which uses the 'ath9k' driver. I am having horrible connectivity issues, only in Ubuntu. The problems do not appear when I boot into my Windows partition, implying it is a driver issue rather than hardware.

I've tried numerous solutions from searching around, all of which have been unsuccessful:

1. Setting IPV6 to 'ignore'.
2. Installing backport drivers with the package 'linux-backports-modules-wireless-lucid-generic'.
3. Using option 'nohwcrypt=1' in my ath9k.conf file.
4. Installing the ath9k driver from here: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

And yet I still see upwards of 70% packet loss (as measured from letting 'ping google.com' run for a while) for all of those solutions.

I am on 10.04.2 LTS, with kernel 2.6.32-30-generic (32-bit).  I'm in the process of updating to kernel 2.6.38-10-generic as we speak -- I'll edit this post if that fixes the problem for some reason.

Does anyone have any ideas, or can I post more information to help diagnose my problem?

edit: kernel 2.6.38-10 does NOT fix the problem.

---

### Post by tdennist on 2011-08-16
No ideas beyond what I've already tried? Not even sure what my options are.

I should mention: it only seems to be flaky when on my work's wireless network. It's fine on my home network. But, again, I don't think it's hardware because my work network is fine when booted into Windows.

---

### Post by tdennist on 2011-08-17
I've tried one more solution with no success: installing and using the Windows XP driver via ndiswrapper.

ndiswrapper does not support a particular function of the XP driver, and generates an Oops during modprobe. I looked at their mailing list and saw someone with the same problem ([link to message]("https://sourceforge.net/mailarchive/message.php?msg_id=27466348")), and the developers' suggestion was to try the open source driver... Sigh.

No end in sight for terrible ath9k connectivity it seems.

---

### Post by TBABill on 2011-08-17
Any chance it's not actually the driver, but maybe network manager causing issues? It had done so on an older AR5001 I have and using wicd fixed mine up. That probably won't help your issue because it is different than mine, just curious if another connection manager may help.

---

### Post by airper on 2011-08-17
Hi tdennist,

there is a thread running here about the Atheros 9285 wireless card, it is causing quite a few people problems, with no, or poor connections.

[http://ubuntuforums.org/showthread.php?t=1821721](http://ubuntuforums.org/showthread.php?t=1821721)

This has not yet resulted in a solution, but people are researching and working on it, hope this helps you are not alone with this.

---

### Post by tdennist on 2011-08-19
> **TBABill said:**
> Any chance it's not actually the driver, but maybe network manager causing issues? It had done so on an older AR5001 I have and using wicd fixed mine up. That probably won't help your issue because it is different than mine, just curious if another connection manager may help.

I tried wicd but I can't get it to work... it refuses to acquire an IP address via DHCP (and I don't have a static IP to use).

[QUOTE=airper]there is a thread running here about the Atheros 9285 wireless card, it is causing quite a few people problems, with no, or poor connections.[/quote]

Thanks for the link.. I'll monitor that thread as well.

---

### Post by tdennist on 2011-08-30
I've found a temporary solution for my problem. I'm not marking the thread SOLVED because of how ridiculous this is.

Instead of dual-booting into Ubuntu, I'm now running a Linux VM inside my Windows 7 installation. The guest piggybacks on the network connection from my Windows installation, and everything works. What a ridiculously over-powered solution for this problem.

---

### Post by digl84 on 2011-10-11
Hey tdennist, any news? I have exactly the same issue, and it hasn't been solved by updated as it happened for the people on the other thread

it's quite annoying, in some places I can only get a reliable connection on windows

---

### Post by I-love-maverick on 2011-11-18
Same here with 10.10. After initial install it worked ok. But, after update/upgrade it is almost unusable.

---

### Post by zinadork on 2012-03-07
I also have the issue on 11.10 64 bit using the ath9k driver.  One thing I've done to alleviate the issue to tether my android phone while it is connected to wifi using easytether.  I know it is not practical.  One thing I've noticed and I'd like to hear if anyone has the same story.  My wifi works fine at my mother's house and terribly at my home while in Ubuntu, but it works very well in Windows on the same routers.  My other wifi devices also work in both locations, so it makes me wonder if any of you have issues on some routers and not others.  

My problem occurs on my Belkin f9k1002 v2 (01).

---

