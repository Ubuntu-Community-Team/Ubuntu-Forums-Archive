---
title: "wake on LAN issue"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by koszta on 2010-02-18
Hi people,
I just cant wake-on-lan to work properly...Spent like 2 days with it, tried everything ... maybe you can help me 

My machine is Dell Poweredge 2400 with onboard Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 . The NIC uses these modules:
CODE: SELECT ALL
Kernel driver in use: e100
Kernel modules: e100, eepro100



1. MY current config - the situation is that when I poweroff the NIC stays on and when I send magic packets its blinking,working and receiving but the computer doesnt turn on. 
now all this is done by an init script at startup:
CODE: SELECT ALL
#!/bin/bash
ethtool -s eth0 wol g
echo DRAC > /proc/acpi/wakeup

there are the acpi related modules in the running kernel:

/lib/modules/2.6.26-2-686/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/asus_acpi.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/video.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/dock.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/ac.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/thermal.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/fan.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/processor.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/wmi.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/sbshc.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/toshiba_acpi.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/container.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/button.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/bay.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/battery.ko
/lib/modules/2.6.26-2-686/kernel/drivers/acpi/sbs.ko
/lib/modules/2.6.26-2-686/kernel/drivers/misc/thinkpad_acpi.ko
/lib/modules/2.6.26-2-686/kernel/drivers/pci/hotplug/acpiphp.ko
/lib/modules/2.6.26-2-686/kernel/drivers/pci/hotplug/acpiphp_ibm.ko

(I tried other things like adding "enable" to a /sys/class/net/eth0/wakeup but it throws an error - "bad argument". But I dont really think that it is the problem...


2. HOW IT WAS WORKING
Now I really REALLY think that the problem is somewhere in acpi which is either not recognizing the event from NIC or doesnt know how to respond to it. 

The funny part is that I got wakeonlan working before actually. I was messing around and at one of my attempts I tried adding "acpi=off" to my menu.lst line of the record I boot. I booted with this option and turned off again (it obviously wasnt even turning off properly, had to do it manually) So I went to menu.lst again removed the "acpi=off" and just left it as it was originally (no acpi options). Then I turned off and VIOLA I woke the machine with wakeonlan. But that worked only for that one time (next time turned off it wasnt responding again). The script listed above was always executed. 
It seemed like some sort of "strange acpi restart" (putting acpi=off and removing it from menu.lst) seems to do the trick but I am not 100% positive plus it would be a pain in the you know where to do this every time. 

note: i found this: [http://patchwork.ozlabs.org/patch/30055](http://patchwork.ozlabs.org/patch/30055) which seems like there is a driver problem but a) I dont fully get it. b) it says that "This looks like it has been broken since 2.6.28." but I have 2.6.26-2 

THANK YOU FOR ANY HELP PROVIDED

---

### Post by koszta on 2010-02-18
UPDATE: I did quite a lot of work around this in the afternoon and I found out that my problem is with acpi/apm. The thing is that my NIC seems to only support apm wakeonlan. When I boot with acpi=off option everything is great and I can use wakeonlan. Now I need to figure out how to turn off the computer properly - when I poweroff it says "system halted" and hangs. I know this is a known bug and I have tried a couple workarounds. The most common seems to be to try to boot with options: "acpi=off apm=on" and add "apm power_off=1" to /etc/modules. But this still hangs the computer at poweroff

SO I cant turn off using acpi since wakeonlan will not work (but the turnoff itself works good)
and I cant get apm to turnoff the computer properly (still get "system halted") but that is the only way how to enable wakeonlan. 

SO my question is: "How do I really turn off the computer completely using apm? "

---

### Post by tgalati4 on 2010-02-18
I'm using wake-on-lan with a Dell PowerEdge 1750.  It has a broadcom gigabit card.  My machine is powered off, with the PCI-bus still powered to keep the network card functioning.

I don't think apm can do a software powerdown.  That's an old protocol, on machines that had a physical power on/off button.  So you will need acpi to work to get the machine to do a complete poweroff.  You need to modify a system configuration file to keep the bus awake:

[http://ubuntuforums.org/showthread.php?t=1380776&highlight=wake](http://ubuntuforums.org/showthread.php?t=1380776&highlight=wake)

---

### Post by koszta on 2010-02-19
Hey, thanks :) but that doesnt solve the problem... I know that acpi is better and all that (and it really can turn the machine off). BUT when I use normal boot mode (default is acpi) then i my NIC doesnt respond to the magic packet. I mean the light on the card is on and it blinks when I send the packet but the computer doesnt wake up. 
This is happening even after I run this script at startup:

[FONT="Courier New"]#!/bin/bash
ethtool -s eth0 wol g
echo DRAC > /proc/acpi/wakeup[/FONT]

I have Intel Corporation 82557/8/9/0/1 Ethernet Pro 100. It uses e100 kernel driver. Do you think that it could be a driver problem? I am really getting kinda angry with the machine... 

So basically I followed the guide you sent me a link to(discussion with [http://www.htgi.ca/node/25]("http://www.htgi.ca/node/25")) (read it before anyway :D) and I do the same stuff as the tutorial (only in the init script above, but I also edited the /etc/network/interfaces accordingly)...Now the situation is back to what it was. The server turns off nicely and the card is powered up (LED is green), when I send the packet it receives it (LED is orange) but the computer doesnt turn on and nothing at all happens... :(

When i cat /proc/acpi/wakeup I see DRAC and PCI1 both enabled(those are pci devices representing the card - its labeled as DRAC as I learnt when reading some dell discussions). 

Any ideas? :)

---

### Post by koszta on 2010-02-19
[SIZE="2"]> **geethsimbu said:**
> First of all, you have to make sure that your USB card can support that feature. Some of them don't . Second, the easiest part is to give it a try. First shut down your computer, while the Wake on USB is active in your bios. Then look to see if your USB Network card is still powered / activated. Be aware that if your laptop is not plugged on a power source, or if the battery is low, it might not be activated. Then try to wake your computer remotely. Some router will provide you with an option in the menu. In other case, you will need the mac address and a software (that you can download on internet).
======================
snip 

Please try reading the discussion before replying. Not that I wouldnt want help of others but try reading the conditions that are set so that you dont look like an idiot.
 
a) my NIC supports wol *JUST READ IT ABOVE... freakin A :D*
b) have NO IDEA why should I deal with USB (I want wake on LAN through NIC, and the NIC is onboard -that means on motherboard). *JUST READ IT ABOVE... freakin A :D*
c) YES, the NIC stayes on after poweroff. [I]JUST READ IT ABOVE... freakin A :D
[/I]
d) Dell poweredge 2400 is hardly a laptop computer *JUST READ IT ABOVE... freakin A :D*
e) dont talk to me like an idiot. I know how to use wakeonlan, command line and such. I am not a linux newbie otherwise I would surely say so. I dont want to sound prideful either - but from the forums I expect experience of others and advices from (at least somewhat) experiened users.

---

### Post by tgalati4 on 2010-02-19
Check the BIOS--update it if you haven't yet (A12 or A15).  I had to change a setting, but can't remember what it was.  My poweredge has a separate BIOS for the network card.  Ctr-S on boot to get into it.  You have different hardware, so it could be anything.

Also, I have to send the magic packet 3 times to wake.  Don't know why, but it works.

Also I have to run a script to initialize the card for each cold boot because the wol setting is not persistant.  This is either a bug or a feature:

For Hardy 32-bit server:

-------------------

tgalati4@gc-development:/etc/init.d$ cat wakeonlanconfig


#!/bin/bash -x
 
#ensure acpi knows to keep device enabled during S5
#since acpitool acts as a toogle
#we only proceed if it needs enabling
wolKeyword="disabled"
pciNIC="pci0000:02"

wolEnabled=$(acpitool -w | grep "$pciNIC" | grep -o "$wolKeyword")
if [ "$wolEnabled" = "$wolKeyword" ]; then
  id=$(acpitool -w | grep "$pciNIC" | awk -F. '{print $1}' | sed 's/^[ t]*//')
  acpitool -W $id
fi

ethtool -s eth0 wol g
exit

----------------

Make sure that you have the correct pciNIC slot and then add the ethtool command at the end.

---

### Post by koszta on 2010-02-22
HEY GOT IT SOLVED...
I tried getting a newer kernel as a last resort kinda thing. During the installation of the kernel it gave me 
[FONT="Courier New"]firmware-linux: /lib/firmware/e100/d101m_ucode.bin
firmware-linux: /lib/firmware/e100/d101s_ucode.bin
firmware-linux: /lib/firmware/e100/d102e_ucode.bin[/FONT]

And e100 being the driver in use for my NIC. So I figured out it really is a driver problem. So I googled around some more and ANYBODY WHO USES Intel 100 kinda card and e100 in general MAY REALLY WANNA SEE THIS:
[http://blogs.koolwal.net/2009/05/11/tip-debian-linux-kernel-firmware-issues-ethernet-drivers-missing/]("http://blogs.koolwal.net/2009/05/11/tip-debian-linux-kernel-firmware-issues-ethernet-drivers-missing/")

thank you anyway :)

---

### Post by tgalati4 on 2010-02-23
So you were using a simple, reverse-engineered, open, e100 driver.  That gave you basic network functions, but not advanced ones like wol.  Glad you found the solution.

---

### Post by koszta on 2010-02-24
Sad day, it only worked once :) Oh well I think I will just give up and get a new NIC. The following thread sums it up nicely. Basically there is no way to get wake on Lan working with this card at this time... 
[http://ubuntuforums.org/showthread.php?p=8246703#post8246703]("http://ubuntuforums.org/showthread.php?p=8246703#post8246703")

---

### Post by koszta on 2010-02-24
Here we go with a very probable solution but it seems that you need to recompile the driver yourself :)

[http://www.mail-archive.com/netdev@vger.kernel.org/msg29552.html](http://www.mail-archive.com/netdev@vger.kernel.org/msg29552.html)

Dont have time for it but will try to compile the new driver version from intel with this fix tmrw and will let you know

---

### Post by sky5564 on 2010-03-16
im running 9.04 jaunty and i am interested in WOL.

i installed WOL and followed some instructions from this site 

[http://www.raneri.it/blog/eng/index.php/2008/12/14/enable-wake-on-lan-wol-on-an-ubuntu-pc/]("http://www.raneri.it/blog/eng/index.php/2008/12/14/enable-wake-on-lan-wol-on-an-ubuntu-pc/")

next i did everything it said to do but i got the following error below. apparently this was for an older version of ubuntu because the error says "missing lsb info" can someone tell me what i need to do to this script to make it work? im not very good at scripting.



```
skilo@skilo-desktop:~$ gksudo gedit /etc/init.d/wol.sh
skilo@skilo-desktop:~$ sudo chmod a+x /etc/init.d/WOL.sh
chmod: cannot access `/etc/init.d/WOL.sh': No such file or directory
skilo@skilo-desktop:~$ sudo chmod a+x /etc/init.d/wol.sh
skilo@skilo-desktop:~$ sudo update-rc.d wol.sh defaults
update-rc.d: warning: /etc/init.d/wol.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/wol.sh ...
   /etc/rc0.d/K20wol.sh -> ../init.d/wol.sh
   /etc/rc1.d/K20wol.sh -> ../init.d/wol.sh
   /etc/rc6.d/K20wol.sh -> ../init.d/wol.sh
   /etc/rc2.d/S20wol.sh -> ../init.d/wol.sh
   /etc/rc3.d/S20wol.sh -> ../init.d/wol.sh
   /etc/rc4.d/S20wol.sh -> ../init.d/wol.sh
   /etc/rc5.d/S20wol.sh -> ../init.d/wol.sh
skilo@skilo-desktop:~$ 
```

here is the script i used

```

 
 #!/bin/bash
ethtool -s eth0 wol g
exit

```

when i run it i get this

```

skilo@skilo-desktop:~$ /etc/init.d/wol.sh
Cannot get current wake-on-lan settings: Operation not permitted
  not setting wol
skilo@skilo-desktop:~$ 

```

when i run ethtool i get this

```

skilo@skilo-desktop:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000001 (1)
	Link detected: yes

```

---

### Post by tgalati4 on 2010-03-16
You should get something like:

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
        Link detected: yes

-----------------

Notice the statement:   Supports Wake-on: g
Wake-on: g

-----------------

What kind of card do you have?

Is there a setting in BIOS to turn WOL on?

What happens when you:

sudo ethtool -s eth0 wol g

ethtool eth0

If your card doesn't support wol, then it's difficult to get wol to work.

---

### Post by sky5564 on 2010-03-16
> **tgalati4 said:**
> You should get something like:

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
        Link detected: yes

-----------------

Notice the statement:   Supports Wake-on: g
Wake-on: g

-----------------

What kind of card do you have?

Is there a setting in BIOS to turn WOL on?

What happens when you:

sudo ethtool -s eth0 wol g

ethtool eth0

If your card doesn't support wol, then it's difficult to get wol to work.

hey thanks for replying so fast =)

i get this

```

skilo@skilo-desktop:~$ sudo ethtool -s eth0 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol
skilo@skilo-desktop:~$ ethtool eth0
Settings for eth0:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000001 (1)
Cannot get link status: Operation not permitted
skilo@skilo-desktop:~$ 

```

also i went into my bios and turned on "remote wake"

my system is an older dell optiplex pentium 4 512ram machine

what command do i do to see what type of NIC i have? i did lspci -vv

```

02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
	Subsystem: Dell Device 00fe
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2500ns min, 2500ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at dc80 [size=128]
	Region 1: Memory at ff6ffc00 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at 30000000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x


```

---

### Post by tgalati4 on 2010-03-16
Well, that is strange.  Most modern 3com cards support wol.  You are running the 3c59x driver, but the card is 3c905c TX Tornado.  (I guess that means it's fast.)

If you can't set the wol switch with ethtool, then you can't use wol.  

It's possible that wol was dropped as a cost-saving feature by Dell.  They probably saved 30 cents on the chipset by not using the wol version.

I don't know what else to say.  If you turned it on in BIOS, but ethtool can't set it or show it's status, then you may be out of luck.

Did you try sending the magic packets anyway while the machine was asleep to see if the network card blinks at all.

Remember, when the machine goes to sleep, the network card must remain powered (blinking lights at the network cable) otherwise wol will not be detected.

It could be a kernel module issue.  It's possible the 3c59x mddule doesn't expose the wol functionality of the 3c905c chipset.  You will have to do some research.

---

### Post by sky5564 on 2010-03-17
> **tgalati4 said:**
> Well, that is strange.  Most modern 3com cards support wol.  You are running the 3c59x driver, but the card is 3c905c TX Tornado.  (I guess that means it's fast.)

If you can't set the wol switch with ethtool, then you can't use wol.  

It's possible that wol was dropped as a cost-saving feature by Dell.  They probably saved 30 cents on the chipset by not using the wol version.

I don't know what else to say.  If you turned it on in BIOS, but ethtool can't set it or show it's status, then you may be out of luck.

Did you try sending the magic packets anyway while the machine was asleep to see if the network card blinks at all.

Remember, when the machine goes to sleep, the network card must remain powered (blinking lights at the network cable) otherwise wol will not be detected.

It could be a kernel module issue.  It's possible the 3c59x mddule doesn't expose the wol functionality of the 3c905c chipset.  You will have to do some research.

good news and bad news.

the good news is i got wol to work on that card.

the bad news is it only works running windows xp .

but i was mainly just going to use this box for a media server anyway so windows xp will do the job.

i did try to send the magic packet but the lights on the nic and the router port was off not blinking. so far i have been able to wake the machine up from standby mode in windows xp.

o well maybe ubuntu will add support for it later on although i would recomend any one with that card just replace it with a nic that supports wol because i have seen them on newegg for $13 lol

thanks for your help anyways though.

---

### Post by tgalati4 on 2010-03-18
You need to keep the pci bus powered after  sleep.  Search acpitool.

---

