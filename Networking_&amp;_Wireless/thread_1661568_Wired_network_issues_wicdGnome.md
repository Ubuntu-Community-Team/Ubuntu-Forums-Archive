---
title: "Wired network issues wicd/Gnome"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by isee on 2011-01-06
Hi All!

I'm having some network issues.  The native Lucid network manager (Gnome but I dont know the whole name) boots me if I upload or download too fast.  Im limited to 45 KB/s up and 350 down, or I get disconnected. (Using Transmission). 

This doesn't happen on my g/f laptop, still running Jaunty I believe, but with wicd installed because of prior network issues, nor does it happen in my new Win7 drive.  These sustain 600+ down and 50-120 up set at unlimited speed.

wicd will only connect to my router, not my ISP's modem.  If Im plugged into my ISP's modem, wicd shows as being connected, but it's not.  It says connected to 192.168.0.100, but I know that is my router address.

Questions
Can I get wicd to connect directly to my Isp's modem, or do I have to use a router with wicd?

Why is the Gnome network manager booting me if I don't throttle my own traffic?

Thanks very much for any help.

Cheers!

---

### Post by isee on 2011-01-06
One stinkin' view?  Should I repost this in the Beginner or General forum?  I'd appreciate it if someone could provide some direction or insight, as I believe I will be a lifetime NOOB in Linux.

Thanks again.

or "Bump" as I've seen done.

---

### Post by PatchesTheCaveman on 2011-01-07
What kind of ISP do you have?  *wicd* doesn't presently support PPP-over-Ethernet (PPoE), which most DSL providers require.  That's not too terribly difficult to get working via the command-line though:  [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by isee on 2011-01-08
Thanks very much PatchesTheCaveman!!  I was hoping there might be another option.

I also hope the documentation is compatible with 10.04, as it is written for 9.10.  I guess I'll find out :)

That does leave me with 2 questions, one of which I asked before:
Why does NetworkManager always disconnect at high KB/s volume for me?

Does using this command line conection use the same...umm...system (process, tools, or whatever) as NetworkManager, and I may face disconnection at high KB/s rates anyways?  (yes I'm that much of a computer noob in general)

Again, thanks for the great direction!
Cheers

PS NetworkManager never disconnects when I run Update Manager, even though it downloads 400-500 KB/s, which I know is too fast when using Transmission because it will disconnect at that rate.

wicd never disconnects either, however my stupid old router does, so in that way wicd is useless for me unless I buy a new router.  :)

---

### Post by isee on 2011-01-08
Well  pppoeconf worked but right now has caused problems.

1. My NetworkManager Applet disappeared from my panel when I rebooted.  I'd really like to get it back.

2. It starts on boot-up, which is fine, but I can't get offline.  If I run
```
poff dsl-provider
```
I get this error
> kill: Operation not permitted
/usr/bin/poff: /bin/kill failed.  None stopped.


3.  If I start a connetion using wicd, I go offline (i guess pppoeconf gets killed).  If I then disconnect wicd (never really online 'cause its plugged into my modem) and try to start a connection with
```
pon dsl-provider
```
I get this error
> Error: only members of the 'dip' group can use this command.

I have what I'd call a root-only copy of dsl-provider on my desktop as a backup of the original, as well as the now modified one in /ect/ppp/peers.  Could this be causing problems with the "pon" and "poff" commands?

How can I get my NetworkManager applet back in my panel?

---

### Post by PatchesTheCaveman on 2011-01-08
> Why does NetworkManager always disconnect at high KB/s volume for me?
This is one of the great mysteries of life.  Lots of people have had plenty of difficulties with NetworkManager but nobody has ever said why.

> Does using this command line conection use the same...umm...system (process, tools, or whatever) as NetworkManager, and I may face disconnection at high KB/s rates anyways?
Yes and no.  Everything ultimately relies upon the networking stack and drivers in the Linux kernel.  But, as I previously said, NetworkManager seems to break a lot of stuff for no apparent reason.

> NetworkManager never disconnects when I run Update Manager, even though it downloads 400-500 KB/s, which I know is too fast when using Transmission because it will disconnect at that rate.
The update manager will have use one single persistent high-bandwidth connection.  BitTorrent will use a large number of smaller connections that change rapidly.  Perhaps it is the number of connections that is causing problems, not the speed.

> wicd never disconnects either, however my stupid old router does, so in that way wicd is useless for me unless I buy a new router.
If wicd gave you no trouble, connecting via the command line shouldn't either.

---

### Post by isee on 2011-01-08
> Perhaps it is the number of connections that is causing problems, not the speed.  ahhh... i see.  That is something I will be looking into then.

For now I'd just really like to figure out why the on/off commands aren't working, right now my options are using wicd to kill pppoeconf to get offline, and rebooting the computer to get back online.

I am really glad that it somehow installed with an on-at-boot option enabled.

---

### Post by isee on 2011-01-08
You have to use sudo with pon and poff.
[https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203)
Connection seems stable:) YAY!

---

### Post by isee on 2011-01-08
Just one more post if you don't mind, and I think this is as far as I can go with this, I ran ```
sudo adduser me dip
``` and rebooted, and I can now sign on with just pon dsl-provider (sans sudo), but I still need to use sudo to end it.

Thanks!  And I think I can mark this solved.  Im off to try and find my lost NetworkManager.

PS  Big thanks Patches for taking the time to explain some of the mysteries to me! :KS

PSS  You only have to use the sudo command with poff once, after that you don't need sudo again until you reboot your computer.

---

