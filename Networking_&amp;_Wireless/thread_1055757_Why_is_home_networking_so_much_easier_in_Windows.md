---
title: "Why is home networking so much easier in Windows"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2009-01-31
Last October I struck problems on my home network. I posted [here]("http://ubuntuforums.org/showthread.php?t=947172") and [here]("http://ubuntuforums.org/showthread.php?t=947210").

Today [the problem struck again]("http://ubuntuforums.org/showthread.php?t=1055564"). 

Essentially, the linux pcs on our home network cannot access the internet. Windows PCs work fine. 

I've replaced routers and have done all I can think of and have now given up until the brain clears. 

However, the wife's had to get online for work and because I couldn't sort her ubuntu PC out I have put it back to WInXP. Needless to say the internet connection came up without any fuss. After today I doubt that I'll be able to persuade her to go back to Linux even if I do manage to get the internet connected again. 

What I really don't get is why this behaviour occurs. AFAIK I have made no changes on the system. No software has been installed in recent weeks and it's been two weeks since I ran an upgrade. Routers are good, ISP is good (as proved by the WinXP connection)

I am now contemplating the other PCs, although it will be a real disappointment if the MythBox has to be downgraded WinXP MCE.

BTW, this is also being typed on Windows. 

So back to the subject, if windows can provide an idiot proof network configuration, why can't it be done linux? <sigh>

Yours absolutely frustrated,

---

### Post by cariboo on 2009-01-31
Networking in Linux is actually easier than WIndows, if you take Network Manager out of the equation. What I do is uninstall network-manager-gnome, and install network-manager-admin. You lose the Network Manager Icon in the top panel, but I can do without it. My system autoconnects on startup and I never worry aobut it.

By the way my home network consists of 9 computers running a mix of dynamic and static ip addresses, wireless and wired connections and a mix of 2 windows computers and the rest Ubuntu and other linux varients, plus a Mac G3.

Jim

---

### Post by GuiGuy on 2009-01-31
> **cariboo907 said:**
> Networking in Linux is actually easier than WIndows, if you take Network Manager out of the equation.


That's probably my point, Jim, although after a day I've had I can't be sure. It's the network manager that makes it easy. Or if it really gets tuff, uninstall the drivers, reboot and the beast steps you through a new setup.

Nevertheless, I too have the applets you mention. None are of any help, of course, because the network works. It's the internet that can't be accessed from Linux PCs. 

Anyway, it was a little rant that made me feel better. Not. Tomorrow is sunday and I'll work something out then. Let's hope I won't need to get the Windows CDs out.

Cheers

---

### Post by puppywhacker on 2009-01-31
Hi,

windows may be idiot-proof, but it certainly isn't genius-proof.

Essentially networking is the same in Windows as in Linux, the commands may be slightly different, but they come from the same litter (BSD being the mommy)

So if windows is connecting to the internet and your local network is running, it is the next level which breaks the chain. As somebody requested in October: post your route config.

**route -n**
and
**iptables -L -n**

because what is probably happening is that your windows has a default route set up to your router, which than does a NAT to your internet. Probably your Linux machines are lacking a default route. which could be fixed (temporarily) by this command:
[B]
sudo route add default gw 192.168.1.1[/B]

The iptables command is to show the firewall rules.

I bet that if you look at your network in a systematic way and post us some commands and outputs we'll figure this out.

---

### Post by capnjim on 2009-02-12
> **cariboo907 said:**
> Networking in Linux is actually easier than WIndows, if you take Network Manager out of the equation. What I do is uninstall network-manager-gnome, and install network-manager-admin. You lose the Network Manager Icon in the top panel, but I can do without it. My system autoconnects on startup and I never worry aobut it.

By the way my home network consists of 9 computers running a mix of dynamic and static ip addresses, wireless and wired connections and a mix of 2 windows computers and the rest Ubuntu and other linux varients, plus a Mac G3.

Jim

Where do you get network-manager-admin from? I can't see it in Synaptic.

---

### Post by lykwydchykyn on 2009-02-12
Well in a nutshell, when it comes to wireless the technology is new and constantly evolving.  Linux is the second class (third class?) citizen as far as device manufacturers are concerned, if they're even concerned at all.  So there are going to be problems.

Regarding your threads, let me say this:
 - I haven't experienced a problem like this before, ever.  I'm willing to bet few of us have, and so nobody can just drop out the "magic bullet" fix because this is not a well-known issue.  I mean, sometimes there are problems that tons of people have had and the fix is well known, so you post about it and people can go "oh yeah, we know what that is, just do this".  Your problem isn't one of those.

 - Because of that, you have to provide us with some information if you want anyone to help you with your problems.  You had several people in those threads asking you to provide some specifics and diagnostic output, and you haven't done so.

I'm trying to say that as nicely as possible, because I know your frustrated and my intent is not to flame you but to put you in a productive state of mind.  I'd suggest that if you want to keep running Linux to return to those threads and provide people with the information they need to help you out.

---

