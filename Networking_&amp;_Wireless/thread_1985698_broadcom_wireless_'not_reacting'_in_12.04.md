---
title: "broadcom wireless 'not reacting' in 12.04"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by dsikl on 2012-05-23
hey ppl, i think i'm about to go mad, there's thousands of threads about broadcom wireless and linux problems, none helps me!

lenovo s10-3s, there's a win7 partition on it, and it's using the broadcom wireless/ethernet/bt combination....wl is the bcm4313

i've upgraded from 10.04 to 10.10, everything worked fine
upgrading from 10.10 to 11.04 networking started acting strange and it still is doing the same, although i upgraded (via alternate iso) to 11.10 and up to 12.04 by now - no use!

in 11.04 i still had the broadcom sta proprietary driver installed, but that wasn't making any difference

it looks like this:

[IMG]https://lh4.googleusercontent.com/-nqrPVMMdmDs/T70sYeZ9u1I/AAAAAAAAABY/4WwTvp-EjOM/s288/Screenshot%2520from%25202012-05-23%252020_21_48.png[/IMG]

and i cannot enable wireless, it always disables itself after i click it......in some of the mentioned distros it would 'stay' enabled, but it wouldn't 'be' enabled as well, it would still say "wireless is disabled" as in the picture above, and wouldn't show me any networks, regardless of my position relative to router.....and you probably guessed it by now, my ethernet isn't working either, and it wasn't working under any of the last three mentioned distros, just like the wireless, so i wasn't able to go online with it at all since upgrade to 11.04

from what i've managed to figure reading all the thousands of threads on related issues so far, i'd probably be best installing the broadcom sta driver in my current distro, where it's not provided anymore, and i'd have to compile it

i've never ever managed to compile one single driver or program from a tarball (been using ubuntu for some three years now, but still bad at it, sorry), but i am always willing to try again..........however, this time i don't even have internet on the machine! i don't think it's impossible, but i couldn't find a way to do it offline

please, whoever tries to offer any kind of solution to my problem: please, please, consider the fact that i cannot use package manager, apt-get and similar and simply draw whatever may be needed, as i have absolutely no internet connection.....i can still go online with my win7 partition, and i also have another machine with 10.10 on it, and that's where i'm writing from right now, but within the 12.04 on the problem machine there is no communication with the outside world

i presume we're gonna need some outputs from my machine, i can provide whatever you ask, just tell me what to punch in to the terminal and i'll be at it in no time!

i am really really hoping someone can help me with this[-o<

---

### Post by chili555 on 2012-05-23
> i presume we're gonna need some outputs from my machine, i can provide whatever you ask, just tell me what to punch in to the terminal and i'll be at it in no time!Yup!```
lspci -nn | grep -e 0200 -e 0280
lsmod | grep -e b43 -e wl
rfkill list all
lsb_release -d
```> please, whoever tries to offer any kind of solution to my problem: please, please, consider the fact that i cannot use package manager, apt-get and similar and simply draw whatever may be needed, as i have absolutely no internet connection...Those other guys who didn't answer specialize in the very difficult. I like the impossible.

Thanks.

---

### Post by dsikl on 2012-05-23
hey chili555, thanks so much for replying! that was fast!

here are the outputs:

lspci -nn | grep -e 0200 -e 0280

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57790 Gigabit Ethernet PCIe [14e4:1694] (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

lsmod | grep -e b43 -e wl

returned nothing (does that mean i don't have the b43-driver installed? :)

rfkill list all

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsb_release -d

Description:    Ubuntu 12.04 LTS


> **chili555 said:**
> Those other guys who didn't answer specialize in the very difficult. I like the impossible.
hmm, a specialty, and a liking........they do differ to an extent :)


> **chili555 said:**
> Thanks.
my pleasure! ):P

but on the serious side, i'd already wanted to get a wireless dongle and get the damn thing done, but i wasn't sure if that would do it,  on the one hand, and i didn't realize that doing it offline was to be the way of the samurai, on the other ;)

will it make it easier for us if i go and buy a wireless dongle tomorrow? or will it just spoil the fun? :-k i mean, i'd love to know how to do things like this offline, but i don't have to torture you or anyone else with it

---

### Post by chili555 on 2012-05-23
> buy a wireless dongle tomorrow? or will it just spoil the fun? Most definitely! > i don't have to torture you or anyone else with itWhat doesn't kill you makes you stronger. I am feeling very strong today!> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01)This device is supposed to work with the driver brcmsmac that's already aboard. Let's make sure the conflicting drivers are blacklisted and it loads correctly. Open a terminal and do:```
sudo su
echo brcmsmac >> /etc/modules
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
```Now you have another problem; the module acer-wmi (Acer?!?) is blocking your wireless:> 0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
2: [COLOR="Red"]acer-wireless: Wireless LAN
Soft blocked: yes[/COLOR]
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: noSo, back to the terminal and do:```
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and give us your report.

---

### Post by dsikl on 2012-05-24
it's woooooooorrrrrrrrrrrrkiiiiiiiiiiiiiiiiiiiiiiinnnnnnnnnng!
IT'S WOOOOOOOOOOORRRRRRRRRRKIIIIIIIIIIIINNNNNNNNNNNNG!!!!!!!!!!!

:mrgreen::mrgreen::mrgreen::mrgreen::mrgreen:


THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU

> **chili555 said:**
> acer-wmi (Acer?!?)
yeh, i was wondering too......any idea what that's about? or i guess if it doesn't matter, we could just leave it........

however, my lan is still dead (checked the router side with the other laptop, all good).......but i guess that's a topic for another thread, this one is [SOLVED]!!! :mrgreen:

if i get my several other hw-ubuntu issues going with 12.04, i'm  chucking windoze out the window, i don't need to tell you how clumsy,  slow and useless it got by now

so thank you a MILLION and sorry about the wait, i'm in germany here,  and i saw your reply last night just before dosing off, and although you  replied again only minutes later, i was already snoring like hell by  then

all the best chilli555! ):P

---

### Post by chili555 on 2012-05-24
I'm ready to start on the ethernet right now. > Broadcom Corporation NetLink BCM57790 Gigabit Ethernet PCIe [14e4:1694] (rev 01)This device is driven by the driver tg3. Let's load it and see what happens:```
sudo modprobe tg3
ifconfig
```Can you hook up the ethernet cable and connect? If so, let's add the driver to the list of modules we want to load automatically:```
sudo su
echo tg3 >> /etc/modules
exit
```If it doesn't work and connect, let's look in the message file to see why:```
dmesg | grep -e tg3 -e eth0
```Glad the wireless is working!

---

### Post by dsikl on 2012-05-24
> **chili555 said:**
> Can you hook up the ethernet cable and connect?
yep! working now too! beautiful! :-)

here's the output of the ifconfig:

eth0      Link encap:Ethernet  HWaddr f0:de:f1:0c:34:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:35 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64 (64.0 B)  TX bytes:12001 (12.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86847 (86.8 KB)  TX bytes:86847 (86.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:82:99:3a:c7  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:82ff:fe99:3ac7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83470119 (83.4 MB)  TX bytes:4417672 (4.4 MB)


i changed the thread's title, so it's easier to find.......

again, thank you so much for teaching me the way of the samurai! it was fun! :mrgreen:

cheers!

---

### Post by chili555 on 2012-05-24
I was happy to have helped. Have fun!

---

