---
title: "Wireless DL very slow (Ralink RT2860/Realtek RTL8111)"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by utamore on 2011-06-30
Hey y'all, linux noob here (so of course I'm using Unity in Natty Narwhal).  My wireless download rate is absurdly low (0.3 mbps) compared to a faster upload rate (1.5 mbps).  My girlfriend's laptop running windows gets much higher download rate (20+ mbps).  Saw some posts with similar problems elsewhere and people ask for the info when you terminal lshw -C network so I'm posting that below.  Please keep in mind that while I'm willing to try anything I am still pretty green and could use some hand-holding in walking through a solution.  I have decided to swear off windows and macs and have moved over to 100% linux so I really want this to work and I would love to make use of the community support that I hear such great things about.  Thank you for your help in advance.

  *-network               
       description: Wireless interface
       product: RT2860
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 70:71:bc:df:e4:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f9ff0000-f9ffffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 6c:62:6d:c8:b0:d7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:d800(size=256) memory:fbdff000-fbdfffff memory:f8ff0000-f8ffffff memory:fbdc0000-fbddffff

---

### Post by utamore on 2011-07-01
Additional information: I receive a strong wireless signal so I do not think that is the culprit.  My wireless router is a Linksys WRT150N with the most recent firmware.  I also saw somebody ask about time wget [www.google.com](www.google.com) and time host [www.cisco.com](www.cisco.com) for a similar problem... here are my results:

amore@Revolution:~$ time wget [www.google.com](www.google.com)
--2011-07-01 05:44:14--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com](www.google.com)... 74.125.67.104, 74.125.67.105, 74.125.67.106, ...
Connecting to [www.google.com|74.125.67.104|:80](www.google.com|74.125.67.104|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 9,843       --.-K/s   in 0.04s   

2011-07-01 05:44:18 (268 KB/s) - `index.html' saved [9843]


real    0m4.019s
user    0m0.008s
sys    0m0.000s
amore@Revolution:~$ time host [www.cisco.com](www.cisco.com)
[www.cisco.com](www.cisco.com) is an alias for [www.cisco.com.akadns.net](www.cisco.com.akadns.net).
[www.cisco.com.akadns.net](www.cisco.com.akadns.net) is an alias for geoprod.cisco.com.akadns.net.
geoprod.cisco.com.akadns.net is an alias for [www.cisco.com.edgekey.net](www.cisco.com.edgekey.net).
[www.cisco.com.edgekey.net](www.cisco.com.edgekey.net) is an alias for [www.cisco.com.edgekey.net.globalredir.akadns.net](www.cisco.com.edgekey.net.globalredir.akadns.net).
[www.cisco.com.edgekey.net.globalredir.akadns.net](www.cisco.com.edgekey.net.globalredir.akadns.net) is an alias for e144.cd.akamaiedge.net.
e144.cd.akamaiedge.net has address 72.247.200.170

real    0m5.560s
user    0m0.000s
sys    0m0.008s

---

### Post by chili555 on 2011-07-01
Dr. Handhold is on the case! What I suspect we have here is a driver conflict. I think two or more drivers are loading and fighting for control. Let's check. Please open a terminal and do:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

If we find a conflict, we'll add what I believe to be the worst of the performers to a blacklist file, preventing them from loading and conflicting.

---

### Post by utamore on 2011-07-01
Dude you are the best.  When all this is said and done I would love some pointers on where I can go learn more so that I can help others the way you help us...  Anyways:

amore@Revolution:~$ lsmod | grep rt2
rt2860sta             494649  0 
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci

---

### Post by chili555 on 2011-07-01
Indeed a conflict. Let's shortcut it and I'll be back later to explain more. Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell me how it's working.

---

### Post by utamore on 2011-07-01
:KS It works :p it works!  Running super fast!  Could you explain how this fixed the problem?  You know, teach a man to fish kind of a thing.  Regardless, thank you so much!

---

### Post by chili555 on 2011-07-01
There are certain drivers including rt2860[COLOR="Red"]sta[/COLOR] that are in 'staging,' meaning they are being fine tuned for inclusion in the mainline kernel. That's a good plan, except it means the driver already in the kernel, rt2800pci also grabs your device and tries to drive it and conflicts. So we blacklist one or the other, rt2860sta or rt2800pci, and stop the conflict. I happen to think, based solely on observation, that rt2860sta does the better job. Here is good evidence:> It works it works! Running super fast! So, based on experience, I recommend blacklisting rt2800pci. That's what the echo command does; it puts the blacklist in the correct file. Afterwards, as your computer boots, it knows that we do not like rt2800pci and doesn't load it. That leaves rt2860sta to do its job without interference.

In some kernel version in the future, I have no idea which, rt2860sta is supposed to be folded in to rt2800pci. If your blacklist file is still in place, since rt2800pci is blacklisted, your wireless won't work at all. Either you will remember this and undo it, you will have a copy of this in your user directory or you will search for RT2860 on the forum and be reminded what to do.

I'm trying to explain this very clearly so the searchers will find it and understand it in the distant future when I've had the laptop lifted off of my lap by the county coroner.

---

### Post by utamore on 2011-07-01
Thanks for the explanation and thanks again for the help.  Any advice on where to start learning more of this "under the hood" stuff?  Most of the beginner-oriented linux books I see on Amazon are more about how to just run programs in the gui...

---

### Post by chili555 on 2011-07-01
> **utamore said:**
> Thanks for the explanation and thanks again for the help.  Any advice on where to start learning more of this "under the hood" stuff?  Most of the beginner-oriented linux books I see on Amazon are more about how to just run programs in the gui...Please see Private Messages at the top.

---

### Post by alfonso78 on 2011-10-12
> **chili555 said:**
> Indeed a conflict. Let's shortcut it and I'll be back later to explain more. Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell me how it's working.

Hi chili555,

I really wish you're still listening cause I tried your suggestion but the problem is still there.
I'm using Ubuntu 10.10 (Maverick Meerkat)

(the box is only connected via wifi)
```
dude@home:~$ lspci -nn | grep -i net
01:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
```

Before I blacklisted rt2800pci:

```
dude@home:~$ lsmod | grep rt2
rt2860sta             504703  0
rt2800pci               8852  0
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  2 rt2860sta,rt2800pci
rt2x00lib              27339  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231927  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              144790  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2800pci
```

After I blacklisted rt2800pci:

```
dude@home:~$ lsmod | grep rt2
rt2860sta             504703  1
crc_ccitt               1351  1 rt2860sta
```

I realized there were issues when I finish to configure my server and enabled samba. So I started to blame samba for the slow transfer rate. So reading a bit about it, I tried to compare it with scp, but I had similar (or even worse) performances.
The hard disks are fine since I can copy at around 80 MB/sec inside the server (maybe not stellar, but more than enough for me) and I tried to copy on both the big disks and the SSD OS disk.
I tried different solutions (and I always rolled back to the original situation if nothing changed):
editing /etc/nsswitch.conf
[http://ubuntuforums.org/showpost.php?p=9639724&postcount=14](http://ubuntuforums.org/showpost.php?p=9639724&postcount=14)

editing sysctl.conf
[http://ubuntuforums.org/showpost.php?p=9859813&postcount=20](http://ubuntuforums.org/showpost.php?p=9859813&postcount=20)

I wanted to try this but I wasn't capable:
[http://ubuntuforums.org/showpost.php?p=10987308&postcount=27](http://ubuntuforums.org/showpost.php?p=10987308&postcount=27)

I got the following error:

```
dude@home:~$ uname -a
Linux NAS 2.6.35-30-generic-pae #60-Ubuntu SMP Mon Sep 19 22:29:36 UTC 2011 i686 GNU/Linux
dude@home:~$ sudo apt-get install linux-backports-modules-compat-wireless-2.6.38-lucid-generic meta-package
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-backports-modules-compat-wireless-2.6.38-lucid-generic
E: Couldn't find any package by regex 'linux-backports-modules-compat-wireless-2.6.38-lucid-generic'
E: Unable to locate package meta-package
```

But it doesn't matter what I tried, my typical scp performance is between 80 and 120 kB/sec 

Sometimes the scp copy goes up to 300 kB/sec, but I don't seem to find a pattern. Sometimes it does, sometimes it stays around 100 kB/sec.

Your patch is the only one I left, since a driver conflict doesn't seem a good plan anyway.

Samba now is about 500 kB/sec, but this is still very slow (or is it?)

I also tried to rule out the wireless router (I have two) but I'm getting similar results for both.

the only thing I can't rule out is that it's my laptop rather then the server to be slow, since I have only a server and a laptop...

Any suggestion (even ideas for further tests) is really appreciated!

---

### Post by chili555 on 2011-10-12
> I really wish you're still listening cause I tried your suggestion but the problem is still there.Who, me? Like the other doctor says, "I'm listening."> I wanted to try this but I wasn't capable:
[http://ubuntuforums.org/showpost.php...8&postcount=27](http://ubuntuforums.org/showpost.php...8&postcount=27)

I got the following error:

Code:

dude@home:~$ uname -a
Linux NAS 2.6.35-30-generic-pae #60-Ubuntu SMP Mon Sep 19 22:29:36 UTC 2011 i686 GNU/Linux
dude@home:~$ sudo apt-get install linux-backports-modules-compat-wireless-2.6.38-lucid-generic meta-package
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-backports-modules-compat-wireless-2.6.38-[COLOR="Red"]lucid[/COLOR]-generic
E: Couldn't find any package by regex 'linux-backports-modules-compat-wireless-2.6.38-lucid-generic'
E: Unable to locate package meta-package

But then:> I'm using Ubuntu 10.10 ([COLOR="Red"]Maverick[/COLOR] Meerkat)Before we explore that, let's discuss a few things. The trouble with using scp between your laptop and your server is that you don't know whether it's a flaw in the server or a flaw in the laptop. There are many areas to consider, too. Not just Samba but the webserver software on the server (LAMP??). Do you need Samba if the server is also Linux? I don't think so. 

Is networking to the outside world good or slow on the laptop? Can you wget at a known good server at or close to your ISPs limit?

Have you reliably isolated the rt2860sta as the bottleneck?

---

### Post by alfonso78 on 2011-10-12
> **chili555 said:**
> Who, me? Like the other doctor says, "I'm listening."

Glad to hear that! :)

> **chili555 said:**
> 
But then:Before we explore that, let's discuss a few things. The trouble with using scp between your laptop and your server is that you don't know whether it's a flaw in the server or a flaw in the laptop. There are many areas to consider, too. Not just Samba but the webserver software on the server (LAMP??). Do you need Samba if the server is also Linux? I don't think so. 

Is networking to the outside world good or slow on the laptop? Can you wget at a known good server at or close to your ISPs limit?

Have you reliably isolated the rt2860sta as the bottleneck?

Let me state a few things: 
- laptop is Windows XP
- server is the Ubuntu box

From the server I'm downloading this file (I live in France) [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/dvd/current/oneiric-dvd-amd64.iso](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/dvd/current/oneiric-dvd-amd64.iso) and I get only 156 KB/sec with wget.

As I was looking for an other huge file (to test a different server) the download spiked to 1 MB/sec and more and now it's around 700K (I never got this speed between the two PCs).

So, at the very least, the Ubuntu box offers very unstable performances (now at 700 KB/sec).

I stopped the 1st and tried downloading this: [http://debian.mines.inpl-nancy.fr/debian-cd/current-live/amd64/net/debian-live-6.0.2-amd64-kde-desktop.tar.gz](http://debian.mines.inpl-nancy.fr/debian-cd/current-live/amd64/net/debian-live-6.0.2-amd64-kde-desktop.tar.gz) and I'm getting around 700KB/sec, sometimes close to 600, sometimes 800. Now more than 1MB. Now 600 KB/sec. A few secs later it shows 1.4MB/sec.

Is this fluctuation expected?

Just as a bonus experiment, I tried to download other two files from the same two servers using the ubuntu 10.04 I have running in VMWare in my XP laptop and I saw similar fluctuations from 200K to 1MB/sec (which doesn't help me prove anything...)

Dear doctor, I'll sleep now. I hope maybe tomorrow I can do some more tests and get to the bottom of it. Wireless performance is key to this project. Over the weekend I was planning to try 11.10 (to get latest drivers etc).

thank you!

---

### Post by chili555 on 2011-10-12
Sleep well. See you tomorrow.

I just tried the latter download and my speeds are also all over the place. Here are random readings from wget in K[COLOR="Red"]b[/COLOR]/s.> 317
205
283
342
199
275
85
193
328
232
271
83
232I believe that reflects the server speed and not my Ubuntu Linux machines speed. I downloaded a big pdf a few minutes ago that stayed in the 340 to 350 Kb/s range throughout.

---

### Post by alfonso78 on 2011-10-12
> **chili555 said:**
> I downloaded a big pdf a few minutes ago that stayed in the 340 to 350 Kb/s range throughout.

Thank you for helping! :)

So what should I expect as W-LAN internal transfer rate then?

Even a 1MB steady stream would be better than this. Bother laptop and server can reach such speed.

Both server and laptop can be hooked up to the router via cable, so I'll test all four possibilities hoping this will give me some additional insight over where is the problem.

see you tomorrow!

---

### Post by alfonso78 on 2011-10-13
So, here we are, a lot of data points! Hopefully some sense can come out of them.

First of all I changed my WiFi router (it required a reset every now and then and I had it since 3 years, so I thought it was a good idea anyway).

Yesterday I tested my dsl from both XP and Ubuntu over WiFi and I remember they were pretty comparable around 10-11Mbit/sec (maybe I remember wrong).

Results today (using speedtest.net):

wireless XP: 32ms (ping), 12.43 Mbit downstream, 0.74 Mbit upstream
wired XP: 32ms (ping), 12.12 Mbit downstream, 0.74 Mbit upstream
**wireless Ubuntu: 17ms (ping), [COLOR="Red"]7.61 Mbit downstream[/COLOR], 0.78 Mbit upstream**
wired Ubuntu: 17ms (ping), 12.60 Mbit downstream, 0.78 Mbit upstream

Would you agree these results alone indicate a problem on the wireless connectivity in Ubuntu?

I wanted to share these results. Now I will also test file transfer between the two when one of the two PCs is wired and when both are wired.

thank you!

---

### Post by alfonso78 on 2011-10-13
By the way, I was also thinking to try to look for the least polluted wifi channel (how?) but given the wireless XP results, I don't think it's a priority in order to solve this problem!

---

### Post by alfonso78 on 2011-10-13
So here are the test results using SCP (simply because winSCP shows the speed).
Test conditions: copying a 2GB file over SCP and watching at least 30 secs to see if the speed changes.


**wired XP and wired ubuntu: peaks of 2,700 KB/sec** but never below 2,200 KB/sec - a few secs it showed 1,500 KB/sec but then went back quickly to 2,500 KB/sec
**wireless XP and wired ubuntu: peaks of 1,300 KB/sec** but never below 1100 KB/sec
**wired XP and wireless ubuntu: [COLOR="Red"]peaks of 800 KB/sec[/COLOR]** then stays in the 300-400KB/sec range, then up to 800 again, then 600, then 400. It stays a bit at 400, then 600. It's really unstable.

Now I'm not sure what else to do (except praying for a miracle with the 11.10 drivers). If you have any test or suggestion, feel free!!!

Thank you!

---

### Post by phil338198 on 2011-10-13
Hello!
The original problem of this thread appeared again in oneiric.
I no longer have rt2860sta so right after the upgrade, my wifi did not work.
I removed the blacklisting of rt2800pci and my wifi worked again, but there is still some speed variations.

With rt2800sta, I had 54Mb/s all the time, now with rt2800pci, I'm usually at 45Mb/s but it varies between 10Mb/s ant 135Mb/s...

lsmod | grep rt2 gives me:
```
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
```Any help is welcome! If i could get my card to a steady 135Mb/s it would be great.

---

### Post by alfonso78 on 2011-10-14
Apologies for overlapping...

I noticed an other thing. In /var/log/messages there is a similar message posted every 2 minutes:

```
Oct 14 13:15:15 NAS kernel: [137913.398670] ===>rt_ioctl_giwscan. 36(36) BSS returned, data->length = 4658
```

and on this page this error message is connected to rt2860:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356807](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356807)

---

### Post by alfonso78 on 2011-10-19
So, now I'm also on 11.10 and scp throughput fluctuates between 200 and 600 K/sec

I also tried to blacklist [FONT="Courier New"]rt2800pci [/FONT]in [FONT="Courier New"]/etc/modprobe.d/blacklist.conf[/FONT] and add [FONT="Courier New"]rt2860sta [/FONT]in [FONT="Courier New"]/etc/modules[/FONT] but somehow it doesn't get loaded at startup.

if you're still out there, any help would be greatly appreciated! :)

also FYI and for my memory, I found this article which I followed:
[http://michael-peeters.blogspot.com/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html](http://michael-peeters.blogspot.com/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html)

but apparently (did I do something wrong?) there is no difference between the rt2860sta I manually compiled and the one found in /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/

they are binary identical.

But I can't test much if I can't load it.

---

### Post by utamore on 2011-10-19
> **chili555 said:**
> 
In some kernel version in the future, I have no idea which, rt2860sta is supposed to be folded in to rt2800pci. If your blacklist file is still in place, since rt2800pci is blacklisted, your wireless won't work at all. Either you will remember this and undo it, you will have a copy of this in your user directory or you will search for RT2860 on the forum and be reminded what to do.
I also upgraded to Oneiric Ocelot, and just as chili predicted, I forgot about this and sure enough my wireless didn't work at all.  I flipped out for about a day or so and then remembered this and went back on here and un-blacklisted rt2800pci, which solved the problem.  Not sure if that will help you, but that's what worked for me.

---

### Post by alfonso78 on 2011-10-19
Ok, so I manage to load rt2860sta and test it:

```
wpa_passphrase myESSID
```

which returns:

```
network={
        ssid="myESSID"
        #psk="password123"
        psk=---a-lot-of-stuff-here------
}
```

create /etc/wpa_supplicant and put the output of wpa_passphrase into it.

note that ra0 could also be wlan0, check it with iwconfig and ifconfig

```
sudo ifconfig ra0 down 

sudo rmmod rt2800pci

sudo depmod -a

sudo modprobe rt2860sta

```

you can check with module you have now installed with:

```

sudo lsmod | grep rt

```

I also added the following in /etc/network/interfaces

```
auto ra0
iface ra0 inet dhcp
        wpa-ssid myESSID
        wpa-psk password123 #password in plain text

```

and finally:

```

sudo /etc/init.d/networking restart ra0

```

So now I'm running using rt2860sta and STILL the scp performances are arond 200-300 KB/sec. Yes, maybe more stable (it doesn't go up to 600 KB/sec) but I want it to be stable up, not stable down!!

Remember than windows wireless can go at 1 MB/sec on scp (see my previous post with tests)

No more ideas at this point...

---

### Post by chili555 on 2011-10-19
Are you certain rt2860sta exists in 11.10? I'm sure the one you compiled, if you did so in 11.10, exists; however it is my understanding that it was to be folded into rt2800pci in kernels >= 3.0. Here is what my fully updated 11.10 machine says:> $ modinfo rt2860sta
ERROR: modinfo: could not find module rt2860staI think you should either compile rt2860sta for 11.10 (my least favorite solution) or un-blacklist rt2800pci and troubleshoot it. 

The end of the various staging modules in 3.0 is new ground for all of us. You may volunteer to be our pioneer/test pilot.

---

### Post by alfonso78 on 2011-10-19
> **chili555 said:**
> Are you certain rt2860sta exists in 11.10?


I've been wrong before. I did so many tests, I might be mistaken.

> **chili555 said:**
>  un-blacklist rt2800pci and troubleshoot it.


I'm already back on rt2800pci. If a fix doesn't solve a problem, I tend to roll back to most common solution.

> **chili555 said:**
> 
The end of the various staging modules in 3.0 is new ground for all of us. You may volunteer to be our pioneer/test pilot.

how can I be of service? I'd be glad to solve this. It would be a small step for mankind, but I giant leap for me.

---

### Post by chili555 on 2011-10-19
> **alfonso78 said:**
> how can I be of service? I'd be glad to solve this. It would be a small step for mankind, but I giant leap for me.Let's start by checking the system logs for clues:```
sudo cat /var/log/syslog | grep -e rt2 -e wlan -e etwork | tail -n25
```We could also disable hardware encryption and see if it makes any improvement:```
sudo gedit /etc/modprobe.d/rt2800pci.conf
```Add one line:```
alias rt2800pci nohwcrypt=1
```Proofread, save, close and reboot.

As in all experiments, we ought change one thing at a time. Post the log, then write the conf file, reboot and try your scp test again.

EDIT: Please see posts #36 and #37 below. It is actually:```
**options** rt2800pci nohwcrypt=1
```

---

### Post by alfonso78 on 2011-10-19
I had a bit of a fight with bluez tonight...

```
$ sudo cat /var/log/syslog | grep -e rt2 -e wlan -e etwork | tail -n25
Oct 20 01:09:12 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter
Oct 20 01:09:52 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter
Oct 20 01:12:12 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter
Oct 20 01:13:18 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter
Oct 20 01:13:41 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter
Oct 20 01:14:33 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter
Oct 20 01:20:37 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter
Oct 20 01:30:22 NAS NetworkManager[704]: <warn> bluez error getting default adapter: No such adapter

```

after creating (it wasn't there) the file and rebooting I don't have wlan0 anymore.

```
$ lsmod | grep rt
parport_pc             32114  1
parport                40930  3 parport_pc,ppdev,lp
$ sudo depmod -a
$ sudo modprobe rt2800pci
FATAL: Module nohwcrypt=1 not found.

```

---

### Post by chili555 on 2011-10-19
> $ sudo modprobe rt2800pci
FATAL: Module nohwcrypt=1 not found.That's mysterious. It is there:> $ modinfo rt2800pci
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     BB07E803E5CA12BF83E12AD
<snip>
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
vermagic:       3.0.0-12-generic SMP mod_unload modversions 686 
[COLOR="Red"]*parm:           nohwcrypt:Disable hardware encryption. (bool)*[/COLOR]
Also, it doesn't complain when I load it:> chili@LAPTOP60:~$ sudo modprobe rt2800pci nohwcrypt=1
[sudo] password for chili: 
chili@LAPTOP60:~$ May we proofread the file?```
cat /etc/modprobe.d/rt2800pci.conf
```Does it load manually?```
sudo modprobe rt2800pci nohwcrypt=1
```

---

### Post by alfonso78 on 2011-10-19
It does load manually!


```
$ sudo ifconfig wlan0 down
(I had to fight the GUI that kept the wifi coming up)
$ sudo rmmod rt2800pci
$ sudo depmod -a
$ sudo modprobe rt2800pci nohwcrypt=1
$ lsmod | grep rt
rt2800pci              18340  0
rt2800lib              48717  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
parport_pc             32114  1
parport                40930  3 parport_pc,ppdev,lp
$ sudo ifconfig wlan0 up
```

how can I make sure the nohwcrypt=1 directive has been taken in consideration?

scp starts off at 600 KB/sec and after 50 secs is still around 400KB/sec and now back to 600 KB/sec

It seems to me a step in the good direction, but what speed should I aim for??

Just to explain: my problem is I run x11vnc in my wireless NAS, so I need all the speed I can get. I can see a small improvement now, but not something completely different. Just to clarify: I always close the vnc client when I run the scp test. ;-)

But I don't want to waste your time. I'd like to know which speed to aim for!

thanks!

---

### Post by chili555 on 2011-10-19
> how can I make sure the nohwcrypt=1 directive has been taken in consideration?That's what the conf file is supposed to do; it has been taken into consideration if it loads on boot without complaint or warning, especially in dmesg. > May we proofread the file?
```
cat /etc/modprobe.d/rt2800pci.conf

```
I'm not sure what the capabilities of the driver-hardware-OS combination are. I don't write the drivers, I just wrangle them into submission the best way I can. After that, I suggest a bug report. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Of course, the flaw may well lie with a dependency:> $ lsmod | grep rt
rt2800pci              18340  0
[COLOR="Red"]rt2800lib[/COLOR]              48717  1 rt2800pci
[COLOR="Red"]crc_ccitt[/COLOR]              12595  1 rt2800lib
[COLOR="Red"]rt2x00pci[/COLOR]              14202  1 rt2800pci
[COLOR="Red"]rt2x00lib[/COLOR]              48114  3 rt2800pci,rt2800lib,rt2x00pci
[COLOR="Red"]mac80211 [/COLOR]             272785  3 rt2800lib,rt2x00pci,rt2x00lib
[COLOR="Red"]cfg80211[/COLOR]              172392  2 rt2x00lib,mac80211
[COLOR="Red"]eeprom_93cx6[/COLOR]           12653  1 rt2800pciWe could be at this a while...

---

### Post by alfonso78 on 2011-10-19
> **chili555 said:**
> That's what the conf file is supposed to do; it has been taken into consideration if it loads on boot without complaint or warning, especially in dmesg.

Do you want me to try to reboot again with the config file and look for something in dmesg?

> **chili555 said:**
> 
Of course, the flaw may well lie with a dependency:We could be at this a while...

I'm interested in fixing it, so as long as you have to time to suggest the next step, I'll try to implement it.

---

### Post by chili555 on 2011-10-20
I'd like to see your file first, to be sure there is no error. ```
cat /etc/modprobe.d/rt2800pci.conf
```Leave the file in place and reboot. Then run and post:```
dmesg | grep -i rt2
```> so as long as you have to time to suggest the next step,Let's see, I joined the forum in 2005...yep, I guess I have time!

---

### Post by alfonso78 on 2011-10-21
Hi chili555,

and thank you for all your support so far,

but before going any further, I think I need a more reliable testing strategy and a goal for a good performance.

I tell you this because yesterday I was downloading something and I got this from wget:

```
100%[=============>] 28,150,545  1.49M/s   in 20s
```

so you can see this is quite a nice speed!

so maybe scp is not a good test, or maybe I need to check conditions on the box, etc. But until I have a reliable test to tell me if the changes I try have any effect, it doesn't really make much sense to go on testing in my opinion.

I thought my tests [http://ubuntuforums.org/showpost.php?p=11338041&postcount=15](http://ubuntuforums.org/showpost.php?p=11338041&postcount=15) and [http://ubuntuforums.org/showpost.php?p=11338233&postcount=17](http://ubuntuforums.org/showpost.php?p=11338233&postcount=17) where pointing quite obviously to wifi on the ubuntu box, but clearly I'm wrong if then I can download so fast!

Any idea?

---

### Post by rodhull on 2011-10-21
This issue is obviously much more widespread...

Here is [another thread]("http://ubuntuforums.org/showthread.php?t=1849602") (incorrectly marked as solved when it's really not) where the RT3090 chipset in the Lenovo S205 is also loading the rt2800pci module and experiencing extremely throttled speeds under Oneiric...

Can anyone else offer any help?

---

### Post by chili555 on 2011-10-21
> **rodhull said:**
> This issue is obviously much more widespread...

Here is [another thread]("http://ubuntuforums.org/showthread.php?t=1794360") (incorrectly marked as solved when it's really not) where the RT3090 chipset in the Lenovo S205 is also loading the rt2800pci module and experiencing extremely throttled speeds under Oneiric...

Can anyone else offer any help?Hmmm. Didn't you give us a link back to this very thread?  :confused:

---

### Post by rodhull on 2011-10-21
> **chili555 said:**
> Hmmm. Didn't you give us a link back to this very thread?  :confused:

Oh dear! Schoolboy error, I'm afraid - way too many tabs open.

Apologies. I've corrected the link now...I obviously couldn't alter the link in your quote, however...

Hope you can help - you certainly appear to be somewhat of an authority on WiFi matters judging from some of your past posts...

---

### Post by rodhull on 2011-10-21
> **chili555 said:**
> ```
sudo gedit /etc/modprobe.d/rt2800pci.conf
```Add one line:```
alias rt2800pci nohwcrypt=1
```

I think this might be incorrect - shouldn't the .conf file read as follows?

```

options rt2800pci nohwcrypt=1
```Upon removing and re-loading it loads with no errors - if you use "alias" in place of "options" it produces a "FATAL"...

I haven't tested it long enough to see whether the speed has stabilised, however. It often starts out fine but after a time throttles drastically. I'll report back shortly...

**EDIT:**
Well, no luck I'm afraid. At first I thought it had worked and the speed was consistent, but I rebooted and tested for a few minutes and the speed dropped like it does every time. I did an rmmod/depmod/modprobe once more to be sure and the same behaviour occurred.

I've also tried forcing the rate to 54M via "iwconfig wlan0 rate 54M" rather than it settling on auto (where it used to choose 48M most of the time) this has no effect either. To be fair, my WLAN will never get above real-life speeds of ~15Mbps but at the moment with these issues with rt2800pci it's roughly a tenth of this rate...I'm lucky if I can sustain 100kb/sec downstream...

---

### Post by chili555 on 2011-10-21
> **rodhull said:**
> I think this might be incorrect - shouldn't the .conf file read as follows?

```

***options*** rt2800pci nohwcrypt=1
```You are correct. Sorry for the error.

---

### Post by alfonso78 on 2011-10-21
Hi,

I'm still in for supporting the testing effort, if we find a good testing methodology! :)

Let me know whenever you want me in!

---

### Post by chili555 on 2011-10-21
> **alfonso78 said:**
> Hi,

I'm still in for supporting the testing effort, if we find a good testing methodology! :)

Let me know whenever you want me in!The next highly experimental test I suggest is compat-wireless. Here is the process, except that you will want: ```
./scripts/driver-select rt2x00
```[http://ubuntuforums.org/showpost.php?p=11052203&postcount=6](http://ubuntuforums.org/showpost.php?p=11052203&postcount=6)

Let me know if you need more assistance.

---

### Post by rodhull on 2011-10-22
Well it loaded OK, and is being used in preference to the built-in rt2800pci (as you can see from the path):

```
$ modinfo rt2800pci
filename:       /lib/modules/3.0.0-12-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8E30BFA74F886356A33EB52
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```I've changed everything else I'd been experimenting with back to defaults (so removing "iwconfig wlan0 rate 54M" from */etc/pm/power.d/wireless*, and commenting out the hwcrypto line from */etc/modprobe.d/rt2800pci.conf*).

I'll test for a bit and report back - I did notice that the version number of the new module hasn't changed from the built-in one (its still 2.3.0). However, the compat-wireless source I downloaded was dated yesterday, so it should be a newer code-base in theory?

**EDIT:**

No joy either with this I'm afraid - exactly the same behaviour - it starts off fine but after a few minutes slows to a crawl. I've also tried the actual rt3090 module from Ralink rather than this "catch-all" open-source module but it doesn't work either!

However, it seems extremely difficult to compile it unless you are an expert in all the ins and outs of the source code - with no patches it fails to compile in Oneiric. [This thread]("http://ubuntuforums.org/showthread.php?t=1849602") has some helpful instructions to get it to successfully compile after manually patching one of the source files, but the module still doesn't work correctly.

Would be great if there was an Oneiric version of this PPA:
[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

---

### Post by chili555 on 2011-10-22
My 'ideas' list is getting very short. You certainly ought to file a bug report: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)  Look for a similar or, ideally, matching case and add your experience to it. 

Although I am a bit skeptical, you might check in your router to see what QoS settings exist. Is the performance improved with QoS on or off?

Another thing you might try is getting a transfer going and open a new terminal and do:```
sudo tail -f /var/log/syslog
```See if there are any messages that appear that may tell us why the slow-down is occurring.

Finally, although I regret even uttering the word...ndiswrapper.

---

### Post by alfonso78 on 2011-10-23
> **alfonso78 said:**
> Hi,

I'm still in for supporting the testing effort, if we find a good testing methodology! :)

Let me know whenever you want me in!

> **chili555 said:**
> The next highly experimental test I suggest is compat-wireless. Here is the process, except that you will want


Sorry, I wasn't very clear.

What I mean by *good testing **methodology*** is actually a test that everyone can perform to decide if their wireless performance is good or bad. As I mentioned before, my scp and x11vnc performances are not as good as I'd like them to be. So I'd like to find a common test to state "ok, now wifi is going better" or "too bad, performance is not getting any better".

Also, it would be nice to have a reference for this test: how much speed should I be satisfied with?

The reason why I ask is that I get only 200/300 KB/sec with SCP but more than 1 MB/sec with wget (see [http://ubuntuforums.org/showpost.php?p=11374688&postcount=32](http://ubuntuforums.org/showpost.php?p=11374688&postcount=32) ) so maybe my wireless works just fine!

> **chili555 said:**
> Let me know if you need more assistance.

Thank you!

---

### Post by moteprime on 2011-10-24
Hi. I got a Lenovo s205 (E-450) with a RT3090, and i can't get it to work at a decent network speed.
I reported a bug and opened a thread but they get no attention.
Bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/875659]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/875659")

I'm complete lost here.....

---

### Post by rodhull on 2011-10-24
Not really sure that it's a problem with "network-manager" - the package you've assigned the bug to - I'm leaning towards it being a problem with the core module that services the chipset (in this case "rt2800pci" which is provided by the rt2x00 project which is currently built-in to the kernel - is this right?).

I think what we really need is a working Oneiric build of the RT3090sta driver - but this doesn't appear to be possible yet...

---

### Post by moteprime on 2011-10-24
@rodhull

I did not know what package name to put on the bug, you are more than welcome to edit it. Nobody has responded to the bug although lots of people most have problem with this.

If anybody can provide more or better information to this bug report so that it gets noticed maybe we can get it solved.

---

### Post by rgm3 on 2011-11-08
I'm seeing the same extremely poor performance out of my Ralink corp. RT2860 under Ubuntu 11.10 Oneiric Ocelot.

I've tried disabling hardware encryption as mentioned in this thread but it didn't seem to help.  In general, the wireless on my Zotac ZBOX is known to perform poorly, but I'm only 20 feet from the router and am getting very slow (sub 802.11b) speeds to my LAN.

For now I worked aorund the problem by using my spare router in bridge mode and using an ethernet cable, but I'd really like to get the on-board wireless working well.

The mainboard has an AMD E-350 APU on it.

---

### Post by rodhull on 2011-11-09
> **rgm3 said:**
> I'm seeing the same extremely poor performance out of my Ralink corp. RT2860 under Ubuntu 11.10 Oneiric Ocelot.

I've tried disabling hardware encryption as mentioned in this thread but it didn't seem to help.  In general, the wireless on my Zotac ZBOX is known to perform poorly, but I'm only 20 feet from the router and am getting very slow (sub 802.11b) speeds to my LAN.

For now I worked aorund the problem by using my spare router in bridge mode and using an ethernet cable, but I'd really like to get the on-board wireless working well.

The mainboard has an AMD E-350 APU on it.

You're lucky that you're not stuck with having to use the wireless like any of us with a laptop such as the Lenovo S205 are!

PLEASE comment on moteprime's bug linked above - we need to bring this to the attention of the devs who decide on including the rt2x00 drivers into the kernel - the "rt2800pci" driver which is a "catch-all" driver that seems to service LOTS of slightly different Ralink chipsets is IMO pretty broken for RT3090 AND RT2860 chipsets under the Linux 3.x kernels in Oneiric.

I have tried the latest daily mainline kernel builds and the problem still persists. I've turned off hardware encryption too (although this will not "take" at boot having edited /etc/modprobe.d/rt2800pci.conf) - makes not a bit of difference.

I REALLY want to have the staging driver that is specific for the RT3090 - the source from Ralink will not build correctly without considerable manual patching, and even then the built module doesn't work correctly - there used to be lots of staging drivers in previous Ubuntu versions that were a lot more chipset-specific and often worked very well, but they've taken the decision to move to these catch-all style drivers that obviously don't cut it...

---

### Post by alfonso78 on 2012-01-30
Hello,

is there any update on this issue? I'm having the same problem: my RT2860 is deadly slow.

thanks,

---

### Post by chili555 on 2012-01-30
> **alfonso78 said:**
> Hello,

is there any update on this issue? I'm having the same problem: my RT2860 is deadly slow.

thanks,Please run and post:```
lspci -nn | grep 0280
uname -r
lsmod | grep rt2
```Thanks.

---

### Post by alfonso78 on 2012-01-30
> **chili555 said:**
> Please run and post:```
lspci -nn | grep 0280
uname -r
lsmod | grep rt2
```Thanks.

Hi!

I opened a new thread: [http://ubuntuforums.org/showthread.php?p=11652542](http://ubuntuforums.org/showthread.php?p=11652542)

thanks for helping!

---

### Post by Pithikos on 2012-04-05
Any update on the matter? I have the same issue on eee901 with Lubuntu :/

---

