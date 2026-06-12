---
title: "User new to Ubuntu with Networking Problems"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by ctm54 on 2012-07-08
Hey guys. Let me preface this by telling you where I'm at in general.  The machine I'm having trouble with is my first computer build, and this  is my first foray into Ubuntu. I'm at a power user level on Mac, so I  sort of understand syntax and a few basic commands in Unix. But when  I've looked at other threads for similar problems, the discussion has  been a tiny bit over my head. So forgive me if I have to ask for  clarification on what you say. With all of that out of the way...

The short version is *I can't connect to the internet via ethernet cable*. 

The cable is plugged in to the ethernet port on my motherboard. When I  tell Ubuntu to connect automatically with DHCP, it spins for a while and  then fails to connect. When I give it a manual address (and set up the  appropriate routing instructions on my router) it says it's connected,  but I cannot access the internet or even ping the router. 

Since this is my first computer build, I'm not ruling out that it's a  hardware or driver issue, but it seems unlikely since the OS clearly  recognizes that there is an ethernet port.

Here's what I'm working with:[INDENT]-ASROCK N68C-GS FX Motherboard (connecting the router directly to the ethernet port on the motherboard)
-Ubuntu Desktop 12.04 LTS
-Asus RT-N12 router[/INDENT]Any guidance would be greatly appreciated. Thanks!

---

### Post by snip3r8 on 2012-07-08
First off you will not be able to connect to the internet though your router with a static ip so that option is out . maybe try creating a new connection by clicking the networking icon in the top right corner of the screen and selecting edit connections, from here you should be able to create a new DHCP connection.

---

### Post by Lars Noodén on 2012-07-08
The wired networking has always been something that has worked out of the box for me.  What happens when you try to manually get a DHCP lease?

```

sudo dhclient eth0

```

---

### Post by ctm54 on 2012-07-08
snip3r8 - when I try to connect automatically with DHCP the connection icon spins for a while and then fails to connect.

Lars - when I enter that code in terminal, I get the same results as above.

Also, why won't I be able to connect with a static IP? I'm planning on using this machine as a media server so I static IP would be ideal.

---

### Post by lisati on 2012-07-08
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=2021123](http://ubuntuforums.org/showthread.php?t=2021123)

---

### Post by coffeecat on 2012-07-09
*Thread moved to **Networking & Wireless**.*

@ctm54, I've moved your thread from the Apple subforum because that is for people running Ubuntu on Apple hardware. I've also removed the "Mac" from the thread title since your problem is not with a Mac.

---

### Post by Cheesehead on 2012-07-09
Paste the result of the following commands here:
```
dmesg | grep eth
ifconfig -a eth
```

---

### Post by steeldriver on 2012-07-09
... also this one please

```
lspci -vnn | grep -A2 -e "\[0200\]" -e "\[0280\]"
```

---

### Post by ctm54 on 2012-07-09
Cheesehead - results of the gmesg one are:

[http://pastebin.com/867Zh7Fj](http://pastebin.com/867Zh7Fj)

results of the ifconfig are:

[http://pastebin.com/uKNsTFVH](http://pastebin.com/uKNsTFVH)

steeldriver - when I entered the command you suggested terminal just returned another entry line and didn't print anything out.

---

### Post by Cheesehead on 2012-07-09
What kernel are you running?
The command [FONT="Courier New"]uname -r[/FONT] will tell you. Please paste the result here.

I ask because this seems very much like a [bug in the forcedeth module]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174693") back from 2007-2008, long since fixed. If you happen to be running a 2.6.2x kernel, an upgrade would be the first thing to try.

If you're running a current 3.x.x version kernel, then it's probably not that long-fixed bug. I know this sounds silly, but I recomment testing your hardware - the cable and both NIC ports. While you may indeed have discoved a regression bug, it's more likely that you're trying to communicate through a bad cable or port.

---

### Post by ctm54 on 2012-07-09
3.2.0-23-generic-pae 

According to my limited research that's consistent with my running 12.04. 

For testing, I'm gonna plug the same cable from the same port on my router into my MBP and see if I can connect that way. If that works, is it safe to assume the ethernet port on my motherboard is no good. Should I exchange it for another one or should I just buy another PCI ethernet card.

---

### Post by ctm54 on 2012-07-09
As I expected, plugging the same cable from the same port into my MBP works perfectly well.

---

### Post by Cheesehead on 2012-07-10
> **ctm54 said:**
> 3.2.0-23-generic-pae
That is indeed a reasonably recent kernel, and good for 12.04.


> **ctm54 said:**
> Should I exchange it for another one or should I just buy another PCI ethernet card.
Either solution seems satisfactory.

I recommend one last test before going the hardware route - try a different LiveCD or LiveUSB (like 11.10), and see if you get the same result.

---

### Post by ctm54 on 2012-07-10
Yeah I've tried with several different Live CDs, same result. I guess I'll buy an ethernet card.

Thanks a bunch for your help.

Anyone know off the top of their heads a good, relatively inexpensive Gigabit PCI card that plays nice with 12.04?

---

### Post by spicedreams on 2012-07-26
> **Cheesehead said:**
> That is indeed a reasonably recent kernel, and good for 12.04.

Either solution seems satisfactory.

I recommend one last test before going the hardware route - try a different LiveCD or LiveUSB (like 11.10), and see if you get the same result.

My situation is close...
I upgraded a working dual boot (Linux Mint 12 Debian Edition 64-bit primary plus WinXP until I can be sure I don't need anything that won't run under Wine) to a new ASRock N68C-GS FX mobo which has onboard RTL8211Cl 10/100/1000 Mbps ethernet.

Windows XP just works after I installed the nVidia drivers (and re-validated my Windows licence).

Linux Mint initialises the card using the forcedeth driver but never gets an address via DHCP. dmesg reported "link not ready" and the lights are odd. I think that the card never negotiates an ethernet connection with the router at the other end- "2-wire" brand, model 2701HGV-W supporting 10/100 wired LAN ports. Naturally, the router is running *nix but with a GUI which stops you doing anything useful like disabling auto negotiation on the ethernet ports. 

The GUI shutdown process stops before turning off the power- I don't get a melted screen, but still no hard stop. Interestingly, "shutdown -h now" in a terminal does turn off the power correctly. 

I tried using ethtool to force 100 Mbps, but saw no improvement. ethtool runs runs only when we are a multiuser runlevel, and probably the router has finished wanting to negotiate by then. 

I tried Live CDs for Africa- Ubuntu 10.04 and 12.04 32- and 64-bit, 'raw' Debian, Puppy. All the same as Linux Mint.

I ended up sticking a very old ne2000 clone in and of course, it sprang to life immediately- but with a cost in expected performance. So I would like to solve this, if I can.

Any more ideas?

---

### Post by achkap on 2013-02-24
> **spicedreams said:**
> My situation is close...
I upgraded a working dual boot (Linux Mint 12 Debian Edition 64-bit primary plus WinXP until I can be sure I don't need anything that won't run under Wine) to a new ASRock N68C-GS FX mobo which has onboard RTL8211Cl 10/100/1000 Mbps ethernet.

Windows XP just works after I installed the nVidia drivers (and re-validated my Windows licence).

Linux Mint initialises the card using the forcedeth driver but never gets an address via DHCP. dmesg reported "link not ready" and the lights are odd. I think that the card never negotiates an ethernet connection with the router at the other end- "2-wire" brand, model 2701HGV-W supporting 10/100 wired LAN ports. Naturally, the router is running *nix but with a GUI which stops you doing anything useful like disabling auto negotiation on the ethernet ports. 

The GUI shutdown process stops before turning off the power- I don't get a melted screen, but still no hard stop. Interestingly, "shutdown -h now" in a terminal does turn off the power correctly. 

I tried using ethtool to force 100 Mbps, but saw no improvement. ethtool runs runs only when we are a multiuser runlevel, and probably the router has finished wanting to negotiate by then. 

I tried Live CDs for Africa- Ubuntu 10.04 and 12.04 32- and 64-bit, 'raw' Debian, Puppy. All the same as Linux Mint.

I ended up sticking a very old ne2000 clone in and of course, it sprang to life immediately- but with a cost in expected performance. So I would like to solve this, if I can.

Any more ideas?

i have the exact same problem. i have the N68C-GS FX asrock mb and it was working well. then i changed my cpu to fx 6300 amd with 2 ddr3 2gb ram and since then i don t have wired network. i have triple boot with windows 7 and windows 8 and the work fine. i tried live cd s from 9.10 untill 12.10 with no luck. i tried disabling and re enabling my lan from bios but still no luck. tried a clean install twice and nothing. tried both static and dhcp. ubuntu recognise my card normally and i don t know what to do. it is very frustrating. any ideas?

---

### Post by achkap on 2013-03-20
after contacting with as rock the guys there gave me the following answer.

Thank you for contacting ASRock.

 
> 
We did various test on BIOS but cannot improve this.

After doing some research, we found changing some driver(forcedeth) setting would help on this.

It seems that there's something wrong at LAN driver for NVIDIA chipset (forcedeth) working with AM3+ CPU.

And due to the non-working driver, you might also see the system not really powering off when shut down or freeze when restart system.

 

Here's the steps to temporarily enable the network:

step 1. Enter Ubuntu recovery mode:

            a. Power on system and press "Shift" during boot up for GRUB memu.

            b. Choose "Advanced options for Ubuntu" > Ubuntu, [kernal version] (recovery mode)

step 2. Choose "root" and key in below command:

            # rmmod forcedeth

            # modprobe forcedeth msi=0 msix=0

            # exit

step 3. Choose "resume" to resume normal boot

Now the network should be ok till next boot with AM3+ CPU.

 

If the trick works on your system, please modify below file to automatically run the script when boot up:

step 1. Add the line "exec rmmod forcedeth" at next line of "script" in the file /etc/init/module-init-tools.conf

           Add the line "modprobe forcedeth msi=0 msix=0" to /etc/rc.local

step 2. Restart system for check

For detailed steps, please have attached file for reference.

 

Reference: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297)

tried both things and they work great. it even reboots and shuts down normally. so if anyone has this try the above solution.

---

### Post by jesse3 on 2013-08-17
Package changed in 13.04
step 1. Add the line "exec rmmod forcedeth" at next line of "script" in the file /etc/init/kmod.conf

---

### Post by launchpad-net-aicardi on 2014-02-17
Same bug here, solved with the rmmod/modprobe workaround.

Please vote/comment bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297)
[https://bugs.launchpad.net/ubuntu/+bug/1264509](https://bugs.launchpad.net/ubuntu/+bug/1264509)

Thanks.

---

### Post by Jose_Eduardo_De_Lu on 2014-05-20
Same problem here - 3 months hunting for a solution! Finally solved with forcedeth module parameters.

Kernel: 3.11.0-12-generic
AMD Proc X8 FX8100

lspci -nnk | grep -iA2 net
```

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
	Kernel driver in use: forcedeth

```

Thank you!

---

