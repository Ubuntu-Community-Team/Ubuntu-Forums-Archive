---
title: "Wireless &quot;device not ready&quot;"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by Carlsbad on 2010-05-09
I just installed Ubuntu 10.04 Netbook Remix.

Before I had Win XP  Pro and Internet worked great.

Right after the install, the  network connection icon was some kind of signal image. Looked like a  tornado.

There was not a single network available. 1 hour before  in Windows there where 10-20 wireless networks.

[FONT=Verdana]I checked with "[/FONT][FONT=Verdana]lspci" and found the wireless lan card there..
I  checked with "[/FONT][FONT=Verdana]sudo  lshw -C network[/FONT][FONT=Verdana]"  and found the driver there..

I right clicked at the network icon  and unchecked "Enable Wireless". And then i checked it again, trying to  reenable it. From that point on, when i left click the network icon, it  say Wireless Networks "device not ready".

when I check sudo lshw  -C network it say:

[FONT=Fixedsys]*-network:0
description:  Ethernet interface[/FONT]
[FONT=Comic Sans MS]and a bunch of  other info...[/FONT]
[FONT=Fixedsys]*-network:1
description:  Network controller
product: BCM4318 [AirForce One 54g] 802.11g  Wireless LAN Controller[/FONT]
[FONT=Fixedsys][FONT=Comic Sans MS]and a bunch of other info...[/FONT]
*-network  DISABLED
description: Wireless interface
physical id: 1
logical  name: wlan0
[FONT=Comic Sans MS]and some other information...

[FONT=Verdana]So in short, at first it didn't find any networks.. when  I disabled it and try to enable it again it stays disabled.. 

greatful  for any help at all
[/FONT][/FONT][/FONT][/FONT]

---

### Post by Carlsbad on 2010-05-10
I am thinking maybe there is a command for enabling it? Why wouldn't it work when I just check the "Enable Wireless"-checkbox?

---

### Post by bradydehart on 2010-05-14
I am having the same problem, any solutions out there? Thanks!

---

### Post by oneheaton on 2010-05-26
i have the same problem.  Just installed a Tenda 11n wireless adapter, based on ralink rt2760 chipset and tried to install mythbuntu 10.04.  I get the same "device not ready" on the desktop as well as the "*-generic DISABLED" line from the lshw command.

Also in the hardware drivers program it says "this driver is activated but not currently in use"

Any suggestions?

Thanks

---

### Post by dfarrell07 on 2010-05-28
This infrequently happens to me, both with my current 10.04 boot and the last few distros. I've tried flipping my laptops hardwire wireless cutoff and enabling/disabling wireless from the icon with no effect. Fortunately, it has always fixed itself after a simple reboot. It might be that we have totally different issues though, and yous is not so simple. I'm running a Lenovo T61p with the standard wireless card that they shipped with and Ubuntu default drivers, even though my system suggests that I can use proprietary ones as well.

---

### Post by SlidingHorn on 2010-05-28
> **Carlsbad said:**
> *-network  DISABLED
description: Wireless interface
physical id: 1
logical  name: wlan0
and some other information...

That other information is probably the most important part...could you post it please?  if all the info doesn't fit on your terminal, just use 

```
sudo lshw -C Network | less
```

---

### Post by erjoalgo on 2010-06-02
Same problem.
10.04
Dell Studio Laptop 64bit
Dont really know what else is uselful

---

### Post by Lazy123 on 2010-06-06
Same problem here with Lenovo T61P. Sometimes after laptop has waken up from sleep Network Manager says "device not ready". Reboot always helps, but it still sucks that I can't use sleep mode reliably with my laptop.

---

### Post by Caytee on 2010-06-15
Im brand new to Ubuntu a complete noob at it but after having it for a couple of days with only a few teething problems this major problem happened.
It was working completely fine for 4 days and then last night all of a sudden my connection was lost and Im getting "Wireless device not ready".
I tried plugging my ethernet cable in to see if that would connect and all I get is "not connected - working offline"
The option "wireless enabled" is checked. Im pulling my hair out and cant get online on my own laptop. Can anyone help me?

also, rebooting didnt work either.

---

### Post by tamashumi on 2010-06-20
I have this issue too on VAIO SZ laptop.

It is "auto-fixing" if I boot with wireless switch on but still annoying.

---

### Post by zagabar on 2010-06-20
Same problem here.

---

### Post by tomgrafton on 2010-06-25
Exact same problem.

---

### Post by morgan.beeby on 2010-06-30
In many of these cases, it may be a simple matter of installing the proprietary drivers in Administration -> Hardware drivers... should take three minutes...

Hope that helps.

---

### Post by tomgrafton on 2010-07-06
> **morgan.beeby said:**
> In many of these cases, it may be a simple matter of installing the proprietary drivers in Administration -> Hardware drivers... should take three minutes...

Hope that helps.

Hi there. I installed the proprietary drivers and that hasn't resolved the problem. Can anyone else comment?

---

### Post by sethupathy on 2010-07-13
[SIZE=4][FONT=Arial][SIZE=4]using [/SIZE][/FONT][FONT=Courier New][SIZE=4]'ifconfg'[/SIZE][/FONT][FONT=Arial][SIZE=4][FONT=Courier New] [/FONT]or [/SIZE][/FONT][FONT=Courier New][SIZE=4]'iwconfig'[/SIZE][/FONT][FONT=Arial][SIZE=4] find the name of wi-fi... 
[/SIZE][/FONT] [FONT=Arial][SIZE=4]e.g., mine is [/SIZE][/FONT][FONT=Arial][SIZE=4]'eth1'
[/SIZE][/FONT] [FONT=Arial][SIZE=4]
then....
[/SIZE][/FONT] [FONT=Courier New][FONT=Arial][SIZE=4]
[FONT=Courier New]sudo ifconfig eth1 up[/FONT]

[/SIZE][/FONT]  [FONT=Arial][SIZE=4]execute the above command in 'terminal'.. this solved my 'device not ready problem'..
Is it useful? :)
click [here]("http://ubuntup.blogspot.com/2010/07/wireless-device-not-ready-problem.html") to know more
[/SIZE][/FONT] [/FONT][/SIZE]

---

### Post by X-Void on 2010-09-26
Same problem. Dell inspiron. Intel wimax card.

I think it's the drivers.	:-(

---

### Post by tenwiseman on 2010-09-26
For the Broadcom BCM4318 chipset for the first post, and probably most of the others in this thread (if broadcom wireless), see this page

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Particularly the 'Installing BCM43xx drivers' section halfway down.

---

### Post by kai_kan on 2010-10-02
> **tenwiseman said:**
> For the Broadcom BCM4318 chipset for the first post, and probably most of the others in this thread (if broadcom wireless), see this page

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Particularly the 'Installing BCM43xx drivers' section halfway down.

WaHOO!

Dell StudioXPS 64bit and this worked for me! Ran:

```
~$ sudo apt-get install b43-fwcutter
```

per the page given. Once completed I can use the soft-button to turn WiFi on and off without issue or reboot. No more "device not ready"!

Big Thanks :KS

---

### Post by gevious on 2011-10-01
I had a similar problem on my mac mini. After tailing /var/log/syslog I discovered this


ctrl_iface exists and seems to be in use - cannot override it
Oct  1 14:45:14 geviousMini wpa_supplicant[1060]: Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Oct  1 14:45:14 geviousMini wpa_supplicant[1060]: Failed to initialize control interface '/var/run/wpa_supplicant'.#012You may have another wpa_supplicant process already running or the file was#012left by an unclean termination of wpa_supplicant in which case you will need#012to manually remove this file before starting wpa_supplicant again.


after removing /var/run/wpa_supplicant/wlan0 and restarting my wireless card worked.

---

### Post by joebuirski on 2011-11-02
Same problem here!
been at it for hours, tried every procedure on the forum
now getting "device not ready"

seriously considering ditching 11.10 and going back to 10.04....never been so difficult. At least before when the kernel updated every time, one could just recompile . not this time it seems.....

someone please help! 

I got a Ralink  RT5390 wireless on HP G62 laptop...

:confused:

(wish there were smilies for tearing hair out)

---

### Post by asuastrophysics on 2012-04-24
Same problem, but completely different hardware
```
*-network DISABLED
description: Wireless interface
product: AR5008 Wireless Network Adapter
Vendor: Atheros Communications Inc.
```
It always fixes itself after a reboot, but I shouldn't have to do this. This has been a bug on my computer for over 3 years now. Surely 3 years is long enough for the community to fix a bug. 

I don't believe this has anything to do with your Broadcom drivers, as my Atheros drivers do the same thing (unless by some minuscule chance both have the same bug).

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
SIOCSIFFLAGS: Input/output error
```

And this bug has been going around for ages, at least since kernel 2.6.38.
Here's another thread with the same problem, no solution:
[http://ubuntuforums.org/showthread.php?t=1944134](http://ubuntuforums.org/showthread.php?t=1944134)
Yet another thread. Again, no solution:
[http://ubuntuforums.org/showthread.php?t=1134328](http://ubuntuforums.org/showthread.php?t=1134328)

So, this bug affects at least 5 different wireless drivers on 5 different sets of hardware and has remained unsolved for the last 3 years. If somebody with any technical expertise could post a solution, it would be great. Otherwise, I'm filing a bug report.

/var/log/syslog
```
Apr 24 18:30:39 jake-desktop kernel: ath: Unable to reset hardware; reset status -5 (freq 2437 MHz)
```

---

