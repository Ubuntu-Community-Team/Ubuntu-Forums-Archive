---
title: "Getting my wireless connection to work."
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by newyorkpaulie on 2009-11-14
I am using a T30 Thinkpad and Ubuntu (the new PhoenixOS-FlameHawk) which has Ubuntu 9 as its base. My wired connection works great, but I don't have the wireless capability. How can I correct this?

---

### Post by t0mppa on 2009-11-14
Like said on the sticky that so many posters don't seem to read, you have to provide more information before anyone can offer any reasonable help. So, how about for starters opening up a Terminal, running **lshw -C network** and posting back with the output?

---

### Post by newyorkpaulie on 2009-11-14
> **t0mppa said:**
> Like said on the sticky that so many posters don't seem to read, you have to provide more information before anyone can offer any reasonable help. So, how about for starters opening up a Terminal, running **lshw -C network** and posting back with the output?Thanks for the speedy response and the slap on the wrist. I was hoping my query would prompt someone to offer some help for me to determine what my hardware is so I could search more intelligently (for drivers as an example). I tried your suggestion but got the response: Ishw: command not found. I retried using all lowercase and then got: ishw: command not found.

---

### Post by phishie on 2009-11-14
> **newyorkpaulie said:**
> Thanks for the speedy response and the slap on the wrist. I was hoping my query would prompt someone to offer some help for me to determine what my hardware is so I could search more intelligently (for drivers as an example). I tried your suggestion but got the response: Ishw: command not found. I retried using all lowercase and then got: ishw: command not found.

That's an L but in the lowercase.

---

### Post by t0mppa on 2009-11-14
Apologies if it sounded too unfriendly, just that the "procedure to get help" part is there for a reason.

Anyway, it's a lower case L as in love, not an I as in Internet. The whole command is an abbreviation from **l**i**s**t **h**ard**w**are.

---

### Post by newyorkpaulie on 2009-11-14
Running the command: lshw -C network produced the following:

  *-network:0
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list
       configuration: driver=airo latency=64 maxlatency=4 mingnt=4
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:0d:60:3b:2c:11
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.67 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by t0mppa on 2009-11-14
Ok, the interface seems to be up and have a driver associated with it. Looks good so far. Can you pick up any networks (can check with **sudo iwlist scanning** from terminal)? If not, does **dmesg** offer any clues towards what could be wrong?

---

### Post by newyorkpaulie on 2009-11-14
> **t0mppa said:**
> Ok, the interface seems to be up and have a driver associated with it. Looks good so far. Can you pick up any networks (can check with **sudo iwlist scanning** from terminal)? If not, does **dmesg** offer any clues towards what could be wrong?
sudo iwlist scanning gives this:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

dmesg produces a very long list that I'm not able to understand.

---

### Post by t0mppa on 2009-11-14
Ok, you could try **dmesg | grep airo** to limit the amount of information displayed. Usually the drivers output at least something there and often they complain about things that go wrong.

Personally, I had never even heard of Aironet before reading your posts, so can't be of too much help with this, I'm afraid. One thing to try though is listed as a cure for older versions of Ubuntu in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34998") and that is unloading and reloading the module with:```
sudo modprobe -r airo
sudo modpobe airo
```

---

### Post by newyorkpaulie on 2009-11-14
> **t0mppa said:**
> Ok, you could try **dmesg | grep airo** to limit the amount of information displayed. Usually the drivers output at least something there and often they complain about things that go wrong.

Personally, I had never even heard of Aironet before reading your posts, so can't be of too much help with this, I'm afraid. One thing to try though is listed as a cure for older versions of Ubuntu in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34998") and that is unloading and reloading the module with:```
sudo modprobe -r airo
sudo modpobe airo
```When I enter the above 1st line I don't get my prompt back... just the black verical rectangle on the far left of the next line.
Also, I use an Actiontec DSL modem/router and I don't think there is software for Linux users, so even if I got the wireless up and running I would still have the Actiontec hurdle.

---

### Post by t0mppa on 2009-11-14
Don't get your prompt back? That sounds very odd, like the command you typed was left performing in an endless loop and that shouldn't be happening. Are you sure you typed the command properly? If not, you can just copy & paste it from the forum.

Anyway, a router shouldn't need any special software on your machine to run, any computer independent of OS should be able to connect to it. Some routers might limit changing their configuration to specific programs that only run on Windows (or so the rumour says, never run into one myself), but even that shouldn't be too hard, since then you only needed one Windows box (or one with a Windows on dual-boot) whenever you wanted to change some things, which is usually pretty rare.

---

### Post by newyorkpaulie on 2009-11-14
> **t0mppa said:**
> Don't get your prompt back? That sounds very odd, like the command you typed was left performing in an endless loop and that shouldn't be happening. Are you sure you typed the command properly? If not, you can just copy & paste it from the forum.

Anyway, a router shouldn't need any special software on your machine to run, any computer independent of OS should be able to connect to it. Some routers might limit changing their configuration to specific programs that only run on Windows (or so the rumour says, never run into one myself), but even that shouldn't be too hard, since then you only needed one Windows box (or one with a Windows on dual-boot) whenever you wanted to change some things, which is usually pretty rare.Not only did I not get my prompt back... I ran into some difficulty with my sound system. Upshot is, I had to run a restore. Luckily I backup often. As to going back into Windows, that is no prob as I have a dualboot setup. WinXP is SOOOOO much slower for me tho.... hence Linux. As to not typing in the correct entry, I am afraid I was correct, so I am at a loss. No problem, life goes on. Thanks for your help though, another enigma which gets my juices flowing.  Love a challenge!

---

### Post by t0mppa on 2009-11-15
Well then, that's a first I've ever heard of it happening. Hope it didn't cause you too much trouble.

And yeah, Windows is slow, but since it's much more reliable with strange hardware, I keep a dual boot lying around as well.

---

