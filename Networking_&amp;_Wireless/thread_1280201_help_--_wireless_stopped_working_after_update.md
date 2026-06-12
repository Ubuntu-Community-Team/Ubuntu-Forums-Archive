---
title: "help -- wireless stopped working after update"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by bionnaki on 2009-10-01
hello.

I am installing Ubuntu on a Toshiba Satellite M45. I originally installed with a Ship-It disc and wireless worked quite well.

After updating the system and rebooting, wireless cannot connect anymore. Wireless networks are shown, but cannot fully connect. 

lspci –v | less shows: 

02:02.0 Ethernet controller: Atheros Communications Inc AR2413 802.11bg NIC (rev 01)
Subsystem: Askey Computer Corp Device 7094
Flags: bus master, medium devsel, latency 168, IRQ 17
Memory at c0200000 (32-bit, non-prefetchable) [size-64K]
Capabilities: <access denied>
Kernel driver in use: ath5k_pci
Kernel modules: ath_pci, ath5k

I am attempting to connect to a WEP network. The same password and configuration worked before the update and works on my desktop. 

Any ideas on how to solve this problem? Thanks.

---

### Post by lyndaj70 on 2009-10-01
I'm not sure if this will help, but I had the same thing happen on my Toshiba satellite after update. It would see the network but not connect.

I turned off the computer waited a minute (actually I was stepping away to keep from breaking something :P).  When I turned it back on I waited and it actually connected on it's own!

Since then it's done that exact same thing a couple of times I have turned it on, and after a reboot or two it just works.  I have an atheros card as well so maybe it's a driver issue?

Anyhow, not sure if that will help you, but wanted to contribute to the thread jic it gives someone an idea on how to help you.

Peace!
Lynda

---

### Post by bionnaki on 2009-10-02
thanks

I tried rebooting and turning off the laptop a few times -- still does not work. 

I also deleted the partition and re-installed ubuntu. Fresh from the install, wireless works perfectly. But once I upgrade the system beyond what is on the disc, wireless just dies. I still see the networks but I cannot connect. No configuration changes have been made.

I figure there is a problem with the upgrade somewhere, but I cannot put my finger on it.

If anyone has any ideas I would greatly appreciate it. I am putting ubuntu on my mom's laptop while she is visiting from out of town because she keeps getting spyware and viruses while on windows. Everything else is working well, except for wireless post upgrade.

---

### Post by bionnaki on 2009-10-02
after a little bit of testing, it appears wireless is not stopping due to an update, but rather it is triggered by an event -- as odd as it sounds, I think whenever a sound event occurs -- say someone logging in or out in pidgin, that's when my wireless stops running. 


basically, I have no idea what's going on with this Toshiba.

---

### Post by wilee-nilee on 2009-10-02
I have had wireless problems on all my laptops (3) and found that installing WICD fixed one and installing WICD then reinstalling network manager fixed the other 2. Add the WICD site source link in /etc/apt/sources.list and make sure your plugged in with Ethernet if you decide to try this.None of my laptops are Toshiba's but I have a feeling there is a bug in the network manager.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by bionnaki on 2009-10-02
I will try wicd -- thanks. 

If I disable sound, wireless works just fine. But if I bring the sound up and a sound event occurs, wireless stops and the sound becomes distorted -- sounds like a cd skipping. 

My wireless come back if I bring the sound levels down and reboot the computer. If I never connect to a wireless network, sound works fine. 

Very odd.

---

### Post by bionnaki on 2009-10-02
problem still exists with wicd. I am thinking it's a problem with sound. sound from flash or movies or music works just fine -- it's the internal "event sounds" from pidgin or nautilus or whatever that kill the wireless.

no idea.

---

### Post by _duncan_ on 2009-10-03
Hi. We have different cards, but experienced the same issues with sound and wireless. Here are the details of my wireless card.

```
00:05.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)
	Subsystem: Atheros Communications Inc. Device 2055
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at ea000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: **[COLOR="Red"]ath5k[/COLOR]**
	Kernel modules: ath_pci, ath5k

```

The major difference between your lspci report and mine is that my card is using the ath5k driver, while you are using ath_pci.

IIRC, my fresh install used to prefer ath_pci until I installed the '[COLOR="Blue"]linux-backports-modules-jaunty'[/COLOR] package. After reboot, the card switched to the ath5k driver, and the sound issue was resolved. I am also getting better signal strength using this (ath5k) driver.
[COLOR="Blue"]
Note that we have different cards, so this solution may not work for you.[/COLOR]

---

