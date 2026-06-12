---
title: "Wired Internet not working 9.10"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by cloudsymph on 2009-11-07
hey there everyone.

i'm absolutely noob to the ubuntu world and have just recently (today infact) installed 9.10 karmic koala.

so i'm actually having some problem with the internet.  problem is i'm not able to surf the web (despite my two other computers working fine - windows and mac on the same router).

i have done hours of searching how to fix this but have finally resorted to asking on these boards.

first off, the laptop i'm running 9.10 KK is an old dell inspiron 640m and my router is a d-link dsl-504t.

that being said could i grab a hand with this please.

also when asking if i could provide extra information through the use of the command line, could i get given the cmd line to type in please.

thanks in advance everyone.

---

### Post by darshana on 2009-11-07
Open a terminal  Application -> Accessories -> terminal
now type 
```
 ping google.com 
```

if you will get something like this.

```
64 bytes from yx-in-f100.1e100.net (74.125.45.100): icmp_seq=1 ttl=45 time=322 ms
64 bytes from yx-in-f100.1e100.net (74.125.45.100): icmp_seq=2 ttl=45 time=349 ms
64 bytes from yx-in-f100.1e100.net (74.125.45.100): icmp_seq=3 ttl=45 time=323 ms

```

Your Internet connection is ok 

press Ctrl+c to stop  pinging.

---

### Post by cloudsymph on 2009-11-07
> **darshana said:**
> Open a terminal  Application -> Accessories -> terminal
now type 
```
 ping google.com 
```if you will get something like this.

```
64 bytes from yx-in-f100.1e100.net (74.125.45.100): icmp_seq=1 ttl=45 time=322 ms
64 bytes from yx-in-f100.1e100.net (74.125.45.100): icmp_seq=2 ttl=45 time=349 ms
64 bytes from yx-in-f100.1e100.net (74.125.45.100): icmp_seq=3 ttl=45 time=323 ms

```Your Internet connection is ok 

press Ctrl+c to stop  pinging.

hi there thanks for the reply

the following is what i'm getting

```


[code]64 bytes from google.com (74.125.45.100): icmp_seq=1 ttl=51 time=268 ms
64 bytes from google.com (74.125.45.100): icmp_seq=2 ttl=51 time=269 ms
64 bytes from google.com (74.125.45.100): icmp_seq=3 ttl=51 time=269 ms
```i do know that the internet is connecting, but i can't go to any websites or download from the package manager.

is there anything else that would help anyone figure out what's going on?

i'm going to add the following for the *cat /etc/network/interfaces* as i've seen many different threads asking this.

```
auto lo
iface lo inet loopback
```

---

### Post by cloudsymph on 2009-11-07
the following is the output (whatever that is

```
lspci
```

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by cloudsymph on 2009-11-07
ok the next code is the

```
ifconfig -a
```

```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:69:72:7a  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::215:c5ff:fe69:727a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28661 (28.6 KB)  TX bytes:39366 (39.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:a5:32:6b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-A5-32-6B-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by darshana on 2009-11-07
Ok.. This seems you have the connection.. Do u have a proxy server?

---

### Post by cloudsymph on 2009-11-07
> **darshana said:**
> Ok.. This seems you have the connection.. Do u have a proxy server?

nope i don't use a proxy server.

i'm currently on my windows comp, and underneath the internet protocol i can see that everything is set up to be automatically obtained.  my IP and NDS.

EDIT:

ok so i went and set up another wired connection with the same name (eth0) and deleted the old one.  oddly enough i'm able to surf google.  however that is actually the extent that i can surf.  i can't go to any other websites other than goole, and the ubuntu that site.  i can't go to the ubuntu forums or antything.

---

### Post by shredder12 on 2009-11-07
Since you are able to ping so i guess dns shouldn't be an issue..
BTW what error does your browswer show?? and have you tried other browsers??

---

### Post by cloudsymph on 2009-11-07
> **shredder12 said:**
> Since you are able to ping so i guess dns shouldn't be an issue..
BTW what error does your browswer show?? and have you tried other browsers??

sorry i'm not sure by what you mean by errors?  (like look through command or just observational?)

well what's happening on the browser is the page just won't load.  and if it sits the long enough i get the - problem loading page - message.

also i haven't tried another browser yet (i'm completely new to linux so i don't know how to install stuff).

however i can tell you that the download manager doesn't work either.  so i'm boggled as to why i can't get internet despite the fact that i have a connection :S

are there anything else you would like me to run on the command line to see what the problem may be?

---

### Post by shredder12 on 2009-11-07
Observational errors.. the one shown on the page..
well, its strange that you are able to ping and you don't use any proxy server, you have auto eth0 configured. 
so why aren't you able to download packages or open webpages..
try running in the terminal (applications->accessories->terminal)
```
sudo apt-get update
```
do you see any downloading...
post the output..

---

### Post by cloudsymph on 2009-11-07
> **shredder12 said:**
> Observational errors.. the one shown on the page..
well, its strange that you are able to ping and you don't use any proxy server, you have auto eth0 configured. 
so why aren't you able to download packages or open webpages..
try running in the terminal (applications->accessories->terminal)
```
sudo apt-get update
```do you see any downloading...
post the output..

hey there sorry for the slow reply, was at a friends place.

well anyways, seems like the boot failed for ubuntu so i'm just reinstalling it now.  

anyways this is what i got for running 

```
sudo apt-get update
```

```
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
37% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu
```

this was done under the trial without changing anything to the comp.

also i would like to add that the internet doesn't work while i'm in this mode either.

i will post if the internet works on my mac when i run ubuntu from the disc as well.

---

### Post by Asuriel on 2009-11-07
Hi ! I've the same problem. I worked until last day with ubuntu 9.04. The network was ok and I had no problem. Yesterday I upgrade to ubuntu 9.10 and internet connection doesn't work. 
So, I try to configure manual static IP and don't change anything. 
It's resolve DNS, because when I ping a web site it shows IP address and also I can see my ADSL router. But I can't open the web site and I can't update nothing with sudo apt-get update.
I disable firewall with sudo ufw disable.

How can I do ?

---

### Post by dr_voodoo on 2009-11-07
I have exactly this problem running Karmic on an old Dell Dimension 4600 PC. Jaunty was problem-free. Even running from the LiveCD does not yield results. 

I have a suspicion it may be something to do with the network controller [Intel 82562EZ]  because my mum has exactly the same model of PC and there was no network on that either when I tried the liveCD.

---

### Post by kbeginner08 on 2009-11-08
Hi!
I have the same problem, the apt-get command isn't running. The problem is the DSL-504T and IPv6. I have modified the firefox configuration and I have connection in the firefox but only in the firefox.
To enable the connection in firefox:
   Write in the direction bar: about:config
   Accept the advise.
   An set this option to true:
     network.dns.disableIPv6
Now, firefox runs!

I hope that someone solves all the problem!

---

### Post by shredder12 on 2009-11-08
ya IPv6 could be an issue in this regard...
you may configure firefox to disable IPv6 and see if it was the real problem..
and you may even try adding this line at the end of the file /etc/sysctl.conf
```
net.ipv6.conf.all.disable_ipv6 = 1

```
It will disable IPv6 connectivity for the OS...

---

### Post by dungun on 2009-11-08
follow this thread. it worked for me. and disable ipv6 in mozilla.

[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

---

### Post by CherryInHove on 2009-11-08
I think I have almost the same problem. I upgraded to 9.10 2 days ago and everything was working fine until I got the updates yesterday. It continued to work fine but this morning when I booted the computer I could no longer connect to websites.

I can ping websites through a terminal but can't connect (I've tried in Firefox, Opera and Epiphany).

The strange thing is that I have found two websites that I can connect to and those are ubuntuforums and a small other forum I use. ([www.themockturtle.com](www.themockturtle.com)) This is bizarre that I can connect to these two and it has only happened since restarting after updates.

Any help would be greatly appreciated!

---

### Post by CherryInHove on 2009-11-08
> **dungun said:**
> follow this thread. it worked for me. and disable ipv6 in mozilla.

[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

Fantastic! I just followed those instructions and my internet is now working perfectly. Thanks very much!

---

### Post by dr_voodoo on 2009-11-08
BRILLIANT! Shame it took over a week to get there but I guess that's what you get for coming to the party early! 

nice one mate

that's what cracks me up about Linux, whatever the problem is, you can usually fix it with three lines of code... but I've got a looooong way to go before I would ever know what to look for myself!

---

### Post by dr_voodoo on 2009-11-08
WTF! no! I had connection to Facebook for about 5 minutes then it went away again... arrgh

---

### Post by dr_voodoo on 2009-11-08
...and it's back again... odd...

---

### Post by peepingtom on 2009-11-08
If your network connection works using a liveCD but not after upgrade, the problem is related to a configuration change you made in the earlier  installation. If networking works on the liveCD, a fresh install will solve your problem. If it doesn't, the problem is more complex.

---

### Post by cloudsymph on 2009-11-09
thanks for the replies.  i'm going to try that link out and see if it works, i'll post back in a bit.

also to "peepingtom"

i've tried my net with the live CD, but it was the exact same problem. :S  i also thought a fresh install would have worked, but it didn't T_T.

---

### Post by cloudsymph on 2009-11-09
ok so it seems it was that ipv6 which was the cause of the problem.

i followed this method.  (cause i didn't understand how shredder12 told me how to do it lol i'm so noob)

```
http://ubuntuforums.org/showpost.php?p=7087946&postcount=42
```anyways, there is a different problem i have now.  i can't install anything from the applications package manager.  for example adobe flash.  i should be able to just click on it and click install or something right, but what the installer says is the following:

```
Canonical does not provide updates for Adobe Flash plugins.
Some updates maybe provided by the Ubuntu community.
```this is the same with all the other installs.

so potentially still could be a problem with the Internet maybe.  i was playing around with the downloader, and i got this updating cache thing going on, but it's stuck at 10%

---

### Post by cloudsymph on 2009-11-09
ok so i did this again

```
sudo apt-get update
```

and this is what i'm getting, never changing at all

```
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to archive.canonica
```

but the thing is, my mozilla is now working thanks to the help i've gotten, but i did this to see why i couldn't get anything from the package download.

maybe i didn't turn off the ipv6 properly.

if anyone could give me the step by step terminal code that would be great (the exact stuff i need to write [ultra noob here])

also this is what i get for typing 

```
cat /proc/sys/net/ipv6/conf/all/disable
```

```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1
```

---

### Post by dungun on 2009-11-09
try this. 

[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

Your Problem:
DNS resolution via local router DNS relay has proven to be a common failure point in my experience.

Try this...
open a terminal.
run this command 
 	Code:
 	sudo gedit /etc/dhcp3/dhclient.conf 
search for this line... #prepend domain-name-servers 127.0.0.1; insert the following line
after that line. 
 	Code:
 	 prepend domain-name-servers 208.67.222.222,208.67.220.220; 
Save the file, disconnect and reconnect, then retest.

What this does...
It hardsets your machine to use OpenDNS nameservers.. you may swap 208.67.xxx.xxx with the IP's of your chosen nameservers, although I think you'll find the OpenDNS servers to be much more efficient.

So, no matter what DNS is handed to you by DHCP, your machine will always behave and use just the DNS servers you tell it to.


-Mark Williams

---

### Post by cloudsymph on 2009-11-09
> **dungun said:**
> try this. 

[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

Your Problem:
DNS resolution via local router DNS relay has proven to be a common failure point in my experience.

Try this...
open a terminal.
run this command 
     Code:
     sudo gedit /etc/dhcp3/dhclient.conf 
search for this line... #prepend domain-name-servers 127.0.0.1; insert the following line
after that line. 
     Code:
      prepend domain-name-servers 208.67.222.222,208.67.220.220; 
Save the file, disconnect and reconnect, then retest.

What this does...
It hardsets your machine to use OpenDNS nameservers.. you may swap 208.67.xxx.xxx with the IP's of your chosen nameservers, although I think you'll find the OpenDNS servers to be much more efficient.

So, no matter what DNS is handed to you by DHCP, your machine will always behave and use just the DNS servers you tell it to.


-Mark Williams

hmmm no luck with that T_T.  thanks though.

---

### Post by cloudsymph on 2009-11-09
ok so i've played around a bit more under system>admin>system sources.

somehow i've gotten to the point where i can click the install button on the package i want to install.  however i'm stuck with it not downloading...

this goes with the updates as well.  could this be to do with the authentication key or something?  if it is i'm really not going to understand where or how i get those.

i'm getting a message that says:

```
requires installation of untrusted packages
the action would require the installation of packages from not authenticated sources.

>details
compizconfig-settings-manager python-compizconfig
```

with adobe flash

```
requires installation of untrusted packages
the action would require the installation of packages from not authenticated sources.

>details
flashplugin-installer
```

---

### Post by peepingtom on 2009-11-11
The warnings of "untrusted packages" mean that the software packages are not official and have not been "signed". This is an issue of security, signing ensures that a package contains files that are identical to the ones that were put together by the package's creator.

In this case you probably added some new "software sources" (aka repositories), places for the ubuntu updater (apt) to look for new software. Sources generally come with a cryptographic "signing key", and you probably didn't add the key when you added the new sources. You can disable all the "third party sources" using "Software Sources" or "Synaptic", found in the Administration menu. Many new applications have been added in Ubuntu 9.10, so many of these third-party sources likely aren't necessary.

For more information about repositories, see the below link.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by cloudsymph on 2009-11-11
> **peepingtom said:**
> The warnings of "untrusted packages" mean that the software packages are not official and have not been "signed". This is an issue of security, signing ensures that a package contains files that are identical to the ones that were put together by the package's creator.

In this case you probably added some new "software sources" (aka repositories), places for the ubuntu updater (apt) to look for new software. Sources generally come with a cryptographic "signing key", and you probably didn't add the key when you added the new sources. You can disable all the "third party sources" using "Software Sources" or "Synaptic", found in the Administration menu. Many new applications have been added in Ubuntu 9.10, so many of these third-party sources likely aren't necessary.

For more information about repositories, see the below link.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

yeah i was looking at that page.  i kind of understand, but the thing is, the updater itself as well doesn't work.

---

