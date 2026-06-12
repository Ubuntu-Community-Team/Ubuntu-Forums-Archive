---
title: "Upgrading Killed My Internet! Help!"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by Throne777 on 2006-06-09
After getting the internet to work wirelessly on Breezy Badger, I decided today to upgrade, and after hours, I finally got it all updated. The only problem was that now my internet is now not working.
I ran:
```

ndiswrapper -l

```
It returned with;
rsc4usb      driver present, hardware present
If I go into networking the eth1 connection is there (i.e. the wireless one) and it claims it is not active. I typed in the ESSID (well, I typed in the SSID-don't know if that's the same or not, my wireless manual from U.S. Robotics only mentions that one) an d set it at DCHP (which it was on before). I don't know whether to set it at hexidecimal or the default one.
Anyway. I click activate. After AGES it activates. I then click OK and after another long enough waiting period it closes and I open up Firefox. Naturally, the internet doesn't work.
I open Networking back up again and lo and behold, the eth1 connection claims it is not active.
What do I do?

Throne777

---

### Post by shamrock_uk on 2006-06-09
Open up a console properly and we'll just try a couple of things:

```
sudo lsmod | grep ndis
```

That should return a line saying ndiswrapper on it - that just checks that it's loaded correctly. 

Assuming that's ok, do this:

```
sudo ifdown eth1
```

and then bring it back up with 

```
sudo ifup eth1
```.

That should either work, or give you some error message - if you can post it here that would be helpful. 


You could also do:

```
sudo gedit /etc/networking/interfaces
```

scroll to the bottom and check you have something like this:

> iface eth1 inet dhcp
wireless-essid XXXXX

auto eth1

---

### Post by Throne777 on 2006-06-09
OK, after typing in the 'ifup' code, I got a massive error of death;

```

SCIOSIFFLAGS: No space left on device
SCIOSIFFLAGS: No space left on device
Listening on LPF/eth1/00:3d:b4:00:00:00
Sending on LPF/eth1/00:3d:b4:00:00:00
receive_packet failed on eth1: Network is down
DCHPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DCHPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DCHPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DCHPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DCHPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DCHPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DCHPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
send_packet: Network is down
No DCHPOFFERS received
No working leases in persistant database - sleeping

```

That sounds like fun :)
Thanks for the help by the way, much appreciated. Want me to run those other commands you suggested?

Throne777

---

### Post by Throne777 on 2006-06-10
Does anyone know what the error message means?
I really need the wireless internet back up, so if anyone can help, I'd really appreciate it.

Throne777

---

### Post by Throne777 on 2006-06-10
I just ran the ```

sudo gedit /etc/networking/interfaces
```
and it came up with a box of sorts which had nothing on it. Absolutely blank.
Does that help? (I'm guessing it means bad things have happened)

Throne777

---

### Post by Blind-Summit on 2006-06-10
Don't worry buddy - you're not alone here. Althought I have a different card to you (I have a belkin high speed 125mbps 7001 UK card) I have the exact same issue. ndiswrapper says all is well but, the network manager sees my card (but calles it eth2 instead of 5.10's wlan0) and I also can't get the net.

I was told to blacklist / or remove this bcm43xx.ko file (the bundled wifi driver with dapper) but that killed my system.

You could try backing up this file - I forget where it is - under the kernel then drivers / net / wifi or something similar - then rename it and then try booting and loading ndiswrapper again. remove the inf files then add them again

Good luck - and let me know if this works or not

---

### Post by shamrock_uk on 2006-06-10
please disregard

---

### Post by shamrock_uk on 2006-06-10
[QUOTE=Throne777]I just ran the ```

sudo gedit /etc/networking/interfaces
```
and it came up with a box of sorts which had nothing on it. Absolutely blank.
Does that help? (I'm guessing it means bad things have happened)

Throne777[/QUOTE]

Hi Throne, sorry for the delay. 

Sorry, I was on a Windows system at the time and my memory was dodgy:

```
sudo gedit /etc/network/interfaces
```

is the command. The fact it was blank was simply because you had the wrong address for the file, nothing more worrying than that :) Note - <tab> for autocompletion is your friend when working on the command line and will help compensate for bad instructions ;)

Just checking - it says no DHCP Offers received - your wireless network is working in Windows, right?

Blind-summit is spot on with his advice, blacklisting the native driver is often a surefire way to get ndiswrapper working, but I thought we'd check the config file first (new command above) just as it may be something simple.

---

### Post by miceagol on 2006-06-10
I have the same problem as Throne777. My wlan worked perfectly with ndiswrapper under Breezy, I upgraded to Dapper, and the wlan card was suddenly disabled. When running "ifup eth1" I get the same error messages as Throne777.

You may be a hero for two persons here now, shamrock_uk. ;) 

This was in my config file concerning eth1 (ssid and key censored for security purposes):
```

iface eth1 inet dhcp
wireless-essid XXXXX
wireless-key XXXXX

auto eth1

```

Tell us where to go next.

---

### Post by tzcomwiz on 2006-06-11
I also had the same problem, although mine was Intersil Corporation ISL3886.

But luckily I found another driver for this card and everything works fine with the new driver.

Maybe you can try to find another driver? Sorry I'm also as clueless as to why this happens.

---

### Post by KuifjePDX on 2006-06-11
This morning I got my wireless card to work in Dapper using the instructions in this ([http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61)) forum post. The only thing I had to tweak was adding instruction (h) to the Dapper instructions to make it boot properly. Initially I did receive the 'No DHCP Offers Received' error but a quick check using 'iwconfig' showed that my SSID was empty because I had misspelled my identifier. After that it worked just fine.

Now the interesting thing is that I can connect to my network and browse networked drives and print to networked printers, I can even do a Traceroute on google.com and ping it, but when I open my Firefox browser I cannot navigate to *ANY* website I tried so far (including google.com).

I just did a clean install of Edubuntu 6.06 LTS (i386) and used the upgrade manager to update about 20 components. Any ideas as to what might prevent  my internet to work?

Doei!

---

### Post by Blind-Summit on 2006-06-11
It's crazy really. If you know of a thread with a fix for this - I've already tried it! And nothing has worked for me so far. I've tried that backlist, I've removed the .ko file itself, Installed ndiwwrapper (latest) also tried the GUI version, network manager and I'm now going in for a spot of Wifi_radar.

I've tried the drivers from my CD and I've also tried the latest drivers.

How can it work so easily in Breezy, yet be so very very broken in Dapper! It's got to a point where I am looking for different Linux distros now because clearly no internet is going to be an issue.

I will post my findings with this wifi radar!

Please someone help me!

---

### Post by Kamek on 2006-06-13
[QUOTE=Blind-Summit]I was told to blacklist / or remove this bcm43xx.ko file (the bundled wifi driver with dapper) but that killed my system.

You could try backing up this file - I forget where it is - under the kernel then drivers / net / wifi or something similar - then rename it and then try booting and loading ndiswrapper again. remove the inf files then add them again[/QUOTE]

I was having the same problem as everyone else here, until I tried killing that file you mentioned. Now my internet works perfectly again, just like it did in Breezy. Thanks!

---

### Post by miceagol on 2006-06-13
Hmm, I'll give that file-killing thing a try. Seems like it may help. But now on friday it's my exam, so I have no *time*. :neutral: I'll report my findings this weekend.

---

### Post by miceagol on 2006-06-17
Hooray, I fixed it. :D

After fumbling around with ndiswrapper and the included bcm43xx-driver, it all just seemed pretty messed up. So I just downloaded the Dapper iso image, and installed Dapper Drake from scratch.

The first thing I did was to blacklist the bcm43xx-driver which is included in Dapper Drake. How to blacklist it is explained [here]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-cf3f0ec9146ae9441b39c4bed74e5d044ef78d2f") in the first paragraph.

Thereafter I downloaded ndiswrapper 1.17. I specifically did not install it with the package manager, as that gave me some problems before. I followed the instructions [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") in detail, and after I installed the drivers, my card didn't show up as disabled or unclaimed anymore. :) A huge progress.

You may experience the following issues during the process:
1. When running "make", it didn't find the kernel build files, so I had to install linux-kernel-headers from the package manager.
2. I wasn't able to connect to the Internet to start with, but a reboot did the trick.

---

