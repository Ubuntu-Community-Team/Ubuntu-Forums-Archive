---
title: "From 10.04 32bit to 10.10 64bit with raid and I can't get wired internet to work"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by Alcareru on 2010-11-28
Hi
Because I wanted to have RAID I had to use the alternate install disc. I also decided to opt for the 64 bit version as well at this time. I can plug in a 32 bit live ubuntu and the internet works out of box. But on the 64 bit alternate HDD install dhcp gets no response. But the problem isn't really in dhcp I suppose as eth0 wont work with static settings either. It's like the card isn't working? Any thoughts?

EDIT: See [the last post]("http://ubuntuforums.org/showthread.php?t=1632973&page=2#post10405375") for a summary.

---

### Post by johnmay on 2010-11-28
There is a slight possibility that your nic is not supported in 64 bit. Does it show up in Network Connections at all? I am currently using 10.10 on one of my machines and have had no problem with it, worked out of the box. I would try reinstalling the network config files, though I don't know the names of them. There is a decent tutorial here: [Tutorial]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") on nix craft. 

try ifconfig or ifconfig eth0 to see if the card is recognized.

---

### Post by uncaspi on 2010-11-28
if it's not detected it's probably a driver problem.

---

### Post by johnmay on 2010-11-28
Can you post the results of ifconfig?

---

### Post by Alcareru on 2010-11-29
> **johnmay said:**
> There is a slight possibility that your nic is not supported in 64 bit. Does it show up in Network Connections at all? I am currently using 10.10 on one of my machines and have had no problem with it, worked out of the box. I would try reinstalling the network config files, though I don't know the names of them. There is a decent tutorial here: [Tutorial]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") on nix craft. 

try ifconfig or ifconfig eth0 to see if the card is recognized.

Ok. I think I just confirmed it's a 64bit issue. No internet on 64 bit live cd either...

As for what ifconfig says it seems to be all correct. On dhcp the result is this:
eth0      Link encap:Ethernet  HWaddr 00:16:76:da:bc:55  
          inet6 addr: fe80::216:76ff:feda:bc55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3410 (3.4 KB)  TX bytes:5191 (5.1 KB)
          Interrupt:20 Memory:93200000-93220000 


If I set up static settings the settings come up just fine with ifconfig eth0 but the connection just doesn't work.

lspci tells me:
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)

lshw tells me:
   *-network
             description: Ethernet interface
             product: 82566DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:16:76:da:bc:55
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.1-0 latency=0 multicast=yes
             resources: irq:47 memory:93200000-9321ffff memory:93224000-93224fff ioport:30e0(size=32)



lscpu tells me:
lscpu 
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              6
CPU MHz:               2394.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              4096K

---

### Post by Alcareru on 2010-11-29
P.S. I was just about to say that it did actually work once and then I thgouth that it worked when I booted to the installed os from the live cd. I did that again and it works again. So magically internet works if I use the live cd for booting? What's with that?

---

### Post by Alcareru on 2010-11-29
Ok I'm getting officially pissed off here. After I managed to get internet working I ofc did some updateds. Now after that new kernel update I can't get internet working. Not even if I boot using the live cd.

---

### Post by albtross on 2010-11-29
have you tried to load the driver?

sudo modprode r8169  

I have similar issue after upgrading 10.04 to 10.10 (64bit), where I have to keep loading the driver with the command above every time I reboot - very frustrating
running kernel 2.6.35-23-generic.

doing lots of searches with no success yet

---

### Post by Alcareru on 2010-11-29
> **albtross said:**
> have you tried to load the driver?

sudo modprode r8169  

I have similar issue after upgrading 10.04 to 10.10 (64bit), where I have to keep loading the driver with the command above every time I reboot - very frustrating
running kernel 2.6.35-23-generic.

doing lots of searches with no success yet

Thanks for the suggestion. However doing:
modprobe -r e1000e && modprobe e1000e
makes no difference. Might be some other module that's not getting loaded properly.. or perhaps it's wrong module or something. I'm not rly too familiar with the modules, but at least modprobe -r e1000e makes ifconfig eth0 fail so I guess I was on to something? Anybody having any more ideas?

---

### Post by johnmay on 2010-11-29
What about the BIOS for you mainboard? Is it the latest and greatest? Looks like your nic is just a generation or two away from mine and I am having no problems. (so far)

---

### Post by Alcareru on 2010-11-30
> **johnmay said:**
> What about the BIOS for you mainboard? Is it the latest and greatest? Looks like your nic is just a generation or two away from mine and I am having no problems. (so far)

I'll look into that. Ty for the suggestion. I'll report how it worked.

---

### Post by s_raiguel on 2010-12-01
I have this same exact NIC, and had exactly the same problem: it would connect about one out of every 6-8 reboots under 64-bit 10.10, but yet there were no problems either with 64-bit 10.04 or with 34-bit 10.10 What finally fixed it was downloading the e1000e driver from the Intel website and installing it by untarring, then doing make install. Now, I get a connection with (almost) every reboot. I'm not sure what was going on, but I had the vague impression that maybe there was some kind of timing problem at boot.

---

### Post by Alcareru on 2011-01-19
Thank you everybody for your responses. Sorry for not being very active with this.. I've found my self too busy with other things so I just installed the 32 bit version and used it. I've had some weird issues with that one too but at least the internet works.

Anyhow, now I'm back to try to get this 64 bit OS working. I decided to start out by first installing it again. No surprise the installation process failed to connect to internet. This time I already knew specifying static settings would not work so I just skipped that face all together. When I dully booted up the new operating system, lo and behold she's alive. The network just works. Next, I did several reboots and eth0 is up and working after each one. This is certanly starting to look promesing. Will this dream be shattered after kernel update? With my fingers crossed I'm anxiously waiting for all the updates to get installed... rebootting... and ta'da no internet connection. Damn.

Ok, lets dig deeper. I modified /etc/default/grub and ran update-grub. My intention was to make grub accessible at boot time so that I could choose the old kernel to test it was indeed the kernel update that broke things. Well, this had some interesting effect as well. Grub was not coming up (I set the hidden timeout to 4 and hidden timeout quiet to false and even uncommented the grub init tune to make it beep when grub loads, but no beeps, no counters, no nothing no matter what I press during startup). However now my network is working again. What on earth is going on here? I then revoked my changes to grub settings, ran update-grub and rebooted. After 5 more reboots I concluded that for some weird reason just running update-grub after the kernel update was probably all that was required to fix the network problem created by kernel update.

Well, lets see how long this'll keep running smoothly. Perhaps bios update and/or compiling the lates intel provided drivers wouldn't be too bad idea on the long run, but for now this seems to work well enough.

Thanks everybody. I'll mark this thread solved if no more problems occur withing the next couple of days.

---

### Post by Alcareru on 2011-01-19
[deleted duplicate]

---

### Post by Alcareru on 2011-01-19
[deleted]

---

### Post by Alcareru on 2011-01-20
Ok. After a good nights sleep, the problem is back. Or was back. I booted up this morning and after long struggle to get the thing on (a some sort of "brown screen booting syndrome", of which I will be making another thread soon) I get to log in and no internet connection. Just to be sure I rebooted, no internet connection. As ridiculous as the "update-grub fix" sounds I decided to try it anyhow. I changed nothing, instead I only ran update-grub, followed by reboot. Now internet works.

I think I'll be upgrading the BIOS next (if updates are available). Now, if it is a timing problem as s_raiguel suggested what could cause it and could timing problems cause trouble with graphics drivers (not) getting (properly) loaded (also causing the "brown screen booting syndrome")? Could bios update help and why self compiled drivers might help?

---

### Post by Alcareru on 2011-01-20
I've updated the BIOS to latest version. I'm still unsure of its effects on this. Last time it worked. Though as I was struggling with _[my other problem](http://ubuntuforums.org/showthread.php?p=10378148#post10378148)_ I did try the "magic trick" update-grub and reboot. It didn't work for it, though, and I'm not sure if I even managed to execute it 'cos I couldn't see what I was doing.. I'll report some more about this soon. In the mean time I'd appreciate some help with that other issue if you can spare the time.

---

### Post by Alcareru on 2011-01-20
I've updated the BIOS to latest version. I'm still unsure of its effects on this. Last time network worked. Though as I was struggling with _[my other problem](http://ubuntuforums.org/showthread.php?p=10378148#post10378148)_ I did try the "magic trick" update-grub and reboot. It didn't work for it, though, and I'm not sure if I even managed to execute it 'cos I couldn't see what I was doing.. I'll report some more about this soon. In the mean time I'd appreciate some help with that other issue if you can spare the time.

---

### Post by Alcareru on 2011-01-21
I've updated the BIOS to latest version. I'm still unsure of its effects on this. Last time it worked. Though as I was struggling with _[my other problem](http://ubuntuforums.org/showthread.php?p=10378148#post10378148)_ I did try the "magic trick" update-grub and reboot. It didn't work for it, though, and I'm not sure if I even managed to execute it 'cos I couldn't see what I was doing.. I'll report some more about this soon. In the mean time I'd appreciate some help with that other issue if you can spare the time.

---

### Post by Alcareru on 2011-01-22
Today I witnessed my first network fail after BIOS update. It also started to work after 3 reboots without running update-grub. Perhaps running update-grub makes no difference and it was just an unlikely coincident that the problem resolved twice right after doing that. I guess I need to try compiling the driver next. Anyhow, I think it's the problem isn't so bad as it used to be. I mean originally when I created this thread I was literally unable to connect to internet. Now it seems more like it works most of the time.

---

### Post by Alcareru on 2011-01-24
I compiled the latest e1000e driver from Intels site. It seems to work a bit better, but it still doesn't work every time. However as of so far running:
sudo modprobe -r e1000e && sudo modprobe e1000e
seems to do the trick, when it doesn't work.

---

### Post by Alcareru on 2011-01-28
Today I updated kernel again. Along with the new kernel came new old e1000e drivers. Naturally no internet connection after boot. So I decided to do some testing.
The old driver version that shipped with kernel 2.6.35-25-generic
is 1.0.2-k4 *. The newest version available (afaik) is 1.2.20-NAPI. So with the old driver I tried many many many times removing the module and reloading it, but to no avail. However when I installed the new driver for this kernel too and then reloaded the driver eth0 gets right up.

So to conclude this all. The best solution so far is to use a newer driver. Version: 1.2.20-NAPI seems to work ok. Sure you need to recompile it every time you upgrade to a new kernel and it still seems to fail sometimes, but (with this driver) reloading it seems to always fix that. At least you don't need to go through some crazy rebooting hell.

Thanks you all for your help. Special thanks to s_raiguel for ultimately providing the best solution!

* You can check the driver version by running: ethtool -i eth0

---

