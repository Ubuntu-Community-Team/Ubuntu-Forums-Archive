---
title: "no wired connection"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by SurferGTO on 2008-12-09
im not really sure what caused the wired network to cease to work, ive been using a wireless connection for a while now and havent had the need to use a wired connection, however i recently move and now need to use a wired connection. ive seen people had problems with finding a wired connection after upgrading and that may be it but as i said, not too sure. 

using wicd to attempt to connect, it apparently cant obtain an IP address... i searched posts for an answer but im a bit of a noob and none of the remedys seem to work... 

system>admin>networking tools
switching the device to ethernet interface
interface statistics shows transmitted bytes, received bytes, and received packets as receiving information, however clicking the configure button gives the message "the interface does not exist."

im unable to ping google thru 72.14.205.100

and most remedys that required me to edit anything in term gave messages that permission was denied or things along those lines.

(sorry i dont have the exact details ive been doing this for hours, and im on a diff. laptop so cant copy and paste. ill get more details as i continue to work around this and add them to the post but ill throw this up here for now and see if anyone has suggestions i havent tried.)

if anyone requires information just ask and ill be able to get it to you shortly, thanks in advance.

---

### Post by SurferGTO on 2008-12-09
bump + info

typing anything "eth0" in term gives error while getting interface flags: no such device.

anything eth1 (eg ifconfig eth1down)
siocsifflags: permission denied

---

### Post by SurferGTO on 2008-12-09
also (bump) is there an easy way to get the inputs from terminal from my laptop to my friends laptop (which im using now) otherwise i cant show anyone the outputs for ifconfig or anything for that matter

---

### Post by SurferGTO on 2008-12-09
attempting to ping [www.google.com](www.google.com) thru terminal ($ sudo ping [www.google.com](www.google.com) -c 5) gives result "unkown host"

attempting to ping 209.85.153.104 gives result  "destination host unreachable"

---

### Post by SurferGTO on 2008-12-09
buuump

---

### Post by Iowan on 2008-12-09
> **SurferGTO said:**
> also (bump) is there an easy way to get the inputs from terminal from my laptop to my friends laptop (which im using now) otherwise i cant show anyone the outputs for ifconfig or anything for that matter
There's the "sneakernet" (AKA floppy disk). For example, **ifconfig >>filename**, then copy filename to floppy. I suppose you could use USB stick or other removable media, too.

---

### Post by SurferGTO on 2008-12-09
true.. i dont have a USB flash drive or a floppy drive. and my DVDROM drive hasnt worked since i installed ubuntu (next fix)

very frustrating. i know its not hardware, because it used to work im assuming prior to some form of update. i dont want to, nor can i afford to at this time purchase a wireless router (and that shouldnt be the solution to fixing a problem anyway), and I am apparently receiving some form of data (according to the network tools)...

absolutely nothing ive searched has worked.

---

### Post by SurferGTO on 2008-12-09
bump

---

### Post by Iowan on 2008-12-09
I noticed a [SOLVED] thread where solution was turning on interface in BIOS.  I doubt that's your problem, but wouldn't hurt to check...
I suppose it's also possible that 8.10 has an updated driver that's not compatible with your interface (unfortunately, drivers are still out of my league).

---

### Post by Ayuthia on 2008-12-09
If you type ifconfig at the Terminal, does it display any eth devices?  If so, which one does it show?

Also, does dmesg show anything for that device:
```
dmesg|grep eth
```

As for the permission denied, it looks like you might have tried to bring the device down without using sudo.

---

### Post by SurferGTO on 2008-12-10
ifconfig shows what appear to be two eth devices...

eth1 and eth1:avahi

and yes dmesg shows some input from that code, however im having a hard time trying to come up with a way to transfer that info from laptop to laptop, outside of writing it all... some things that generally stick out...

"driver 'sd' needs updating - please use bust_type method
udev renamed network interface eth0 to eth1
wlan0 ethernet device ..... using ndis driver: bcmwl5....
eth1: no IPv6 routers present....

then repeatedly...
eth1: link down
eth1:link up...

than occasionally it says again no IPv6 Routers present...

im tryin to get a way to transfer the direct response.. sorry...

---

### Post by SurferGTO on 2008-12-10
also, im not using 8.10. sttill on 8.04, bump

---

### Post by SurferGTO on 2008-12-10
bump

---

### Post by SurferGTO on 2008-12-10
really? nothin?

---

### Post by scottuss on 2008-12-10
Firstly:
Have you tried running an update? The warning about your drivers suggests that they may be corrupt / not available.

In response to your ipv6 router error, I don't think it's related but if you dont use ipv6 you can turn it off:

gksudo gedit /etc/modprobe.d/aliases

Change

alias net-pf-10 ipv6
to
alias net-pf-10 off

Reboot. 

After that I don't really know what else to suggest (I'm not a networking expert, I wish I could help more!)

---

### Post by SurferGTO on 2008-12-11
how can i get new updates without connecting to the net?  and ill try the disabling thing thanks

---

### Post by Ayuthia on 2008-12-11
You might also try the following (if you haven't already):
```
sudo modprobe -r forcedeth
sudo modprobe forcedeth
sudo /etc/init.d/networking restart
```

EDIT: I am basing this driver on our conversations in getting your wireless to work.

---

### Post by SurferGTO on 2008-12-11
ok this isnt a copy and paste, its me simpley copying the output from sudo/etc/init.d/networking restart:

* Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 14585
removed stake PID file
Internet systems consortiom DHCP client V3.0.6
Copyright 2004-2007 Internet systems consortium
All rights reserved
for info please visit [http://www.isc.org/sw/dhcp](http://www.isc.org/sw/dhcp)

listening on LPF/eth1/00:1d:72:48:08:20
sending on (same)
sending on socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
internet systems consortium (same as above)

...
...
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in presistent database - sleeping.
eth0: ERROR wihle getting interface flags: No such device
there is already a pid file...blahblahblah
internet systems consortium yadayadayada

...
...
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

...........And thats basically it

---

### Post by Ayuthia on 2008-12-11
By any chance, are you using static ip or do you use dhcp?  I am asking because I saw 192.168.0.1 and I thought that most routers start with a higher number (I could be wrong though).

Is there anything in your /etc/network/interfaces file besides:
```

auto lo
iface lo inet loopback
```
If so, you might comment them out for now (put a # at the beginning of the line).

My other guess is that network manager is conflicting with the manual connection.  By any chance do you have the following files:
```
/etc/dbus-1/event.d/26NetworkManagerDispatcher
/etc/dbus-1/event.d/25NetworkManager
```If so, can you try the following:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo dhclient -r eth1
sudo dhclient eth1
```
The top two commands will stop network manager from running for this session.  It will be restarted when you reboot.

---

### Post by SurferGTO on 2008-12-11
honestly, i dont know if im using a static ip or dhcp lol.. how do i tell? 

noob question i know, but ive never gone through this before sooo..

interfaces file contains the following:

> auto lo
iface lo inet loopback

iface eth1 inet dhcp
address 24.187.143.253
netmask 255.255.248.0
gateway 24.187.136.1

auto eth1
auto eth0
iface eth0 inet dhcp


i disabled network manager but havent changed the interfaces file yet. the last two commands you gave showed what they have been showing any other time i ran them (see prior post)

---

### Post by Ayuthia on 2008-12-11
I am not for sure if this will work, but try changing the file to look like this:
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 24.187.143.253
netmask 255.255.248.0
gateway 24.187.136.1

#auto eth0
#iface eth0 inet dhcp 
```
Then try /etc/init.d/networking restart.

As for the static ip or dhcp question, if it is a static ip, you are telling the router what your ip address should be.  If you don't have one, then you ask the router to give you one (via dhcp).  This is probably not the correct technical answer, but that is how I think of it.

It looks like your configuration in the file is set for static instead of a dhcp.  I could be wrong though.

---

### Post by SurferGTO on 2008-12-11
k im gunna get to tryin that, got my fingers crossed...

as far as the difference between dhcp and static ip , i understand that, i just dont know if im SUPPOSED to be one or the other. i think the information shown is information i manually put into wicd at one point a while back, which is perhaps why its not working now?

is there a way to tell if im supposed to be one or the other?

---

### Post by Ayuthia on 2008-12-11
> **SurferGTO said:**
> k im gunna get to tryin that, got my fingers crossed...

as far as the difference between dhcp and static ip , i understand that, i just dont know if im SUPPOSED to be one or the other. i think the information shown is information i manually put into wicd at one point a while back, which is perhaps why its not working now?

is there a way to tell if im supposed to be one or the other?
Well, we could try it this way to see if it works.  If it does not, you can comment out the code and try to see if you can connect:
```
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet static
#address 24.187.143.253
#netmask 255.255.248.0
#gateway 24.187.136.1

#auto eth0
#iface eth0 inet dhcp
```Then do the sudo /etc/init.d/networking restart

---

### Post by SurferGTO on 2008-12-11
ok so i took out those two last lines, as stated, then went into system>admin>network and saw that the wired connection setting was set to DHCP so i changed it over to static to match the IP address listed. WICD is able to connect to that IP address, however firefox cant load any pages and i cant ping google.

---

### Post by Ayuthia on 2008-12-11
Is it able to ping the gateway (24.187.136.1)?

---

### Post by SurferGTO on 2008-12-11
it would appear not...

---

### Post by SurferGTO on 2008-12-12
bump

---

### Post by SurferGTO on 2008-12-12
bumpity

---

### Post by Ayuthia on 2008-12-12
Did you try the dhcp method in post #23?  It does not seem that the static version worked.

If this does not work, we should look at the computer that you are connecting to the internet to see how it is configured.

---

### Post by SurferGTO on 2008-12-12
DHCP method described in post 23 didnt work, I changed the system>admin>network>wired connection properties over to match DHCP connection and enabled it, than commented out everything in interfaces and ran etc/init.d/networking restart.

got received packet failed on eth1: network is down
failed to bring up eth1

---

### Post by Ayuthia on 2008-12-12
> **SurferGTO said:**
> DHCP method described in post 23 didnt work, I changed the system>admin>network>wired connection properties over to match DHCP connection and enabled it, than commented out everything in interfaces and ran etc/init.d/networking restart.

got received packet failed on eth1: network is down
failed to bring up eth1

If you have not done anything else to the computer yet, try and see if we can bring it up manually:
```
sudo ifconfig eth1 up
sudo dhclient eth1
```

---

### Post by SurferGTO on 2008-12-12
nope, manually doesnt appear to do anything different.  same output as before tho now:

receive packet failed on eth1: network is down
Terminated

---

### Post by SurferGTO on 2008-12-12
if you need to see the whole output i can manually type it in lol i dont really want to but ya know, i will

---

### Post by Ayuthia on 2008-12-12
Please don't.  I don't want to see you suffer more than you already are with the wired card.

From the computer that you are using right now, can you see what ip address it is assigned to?  I am not too familiar with Windows so if you are using it, you can find the information from the command prompt by typing ipconfig.  That is about all I remember from Windows.

---

### Post by SurferGTO on 2008-12-12
sure thats easy enough:

24.187.143.253

you need the subnet mask and gateway too?

---

### Post by Ayuthia on 2008-12-12
yes.

---

### Post by SurferGTO on 2008-12-12
subnet: 255.255.248.0
default gateway: 14.187.136.1

---

### Post by Ayuthia on 2008-12-12
> **SurferGTO said:**
> subnet: 255.255.248.0
default gateway: 14.187.136.1

Please try changing /etc/network/interfaces to:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 24.187.143.253
netmask 255.255.248.0
gateway 14.187.136.1

#auto eth0
#iface eth0 inet dhcp
```
Then try /etc/init.d/networking restart.  You will need to disconnect from the computer running Windows or else you will run into an ip conflict.  Hopefully this will get you to connect.

EDIT: You might need to double-check the gateway address because the first listing had 24.187.136.1 and this time I see 14.187.136.1

---

### Post by SurferGTO on 2008-12-12
nope that didnt work. im assuming i have the network settings right and that there isnt anything else i have to actually change over other than in interfaces... again, if i go into system>admin>network tools it does show data being exchanged even tho WICD wont actually connect, and earlier I was getting WICD to connect but couldnt load any pages or ping any address. now its just not connecting again, stopping at Obtaining IP address.

---

### Post by Ayuthia on 2008-12-12
Let's try to see if we can do this without wicd.  I am not for sure if we need it or not because we are trying to connect via a static ip address and not dhcp.

Go ahead and try the following:
```
sudo /etc/init.d/networking restart
route
```
If things are working right, route should show the gateway matching the one posted earlier and the destination should show the router ip address (not for sure if you know what the router ip address is).

You should also check /etc/resolv.conf.  See if there is any information listed there.  If there isn't, that would be the problem.  Unfortunately, I am not for sure what should be in there.  I know that mine has:
```
nameserver xxx.xxx.xxx.xxx
```and the x info is the gateway address.  You might try that in yours and then restart the networking again (sudo /etc/init.d/networking restart).  Just make sure that the gateway matches what is listed in Windows.

---

### Post by Clancy_s on 2008-12-18
PMJI: I think I may have a similar problem, in that wicd can't detect my wired connection in 8.10 (64 bit).  It doesn't seem to be able to find the ethernet card - I don't even get a light on the port when I connect a cable.

ifconfig doesn't find any ethernet.

My wireless works so it took a while for me to notice the problem.

My wired connection works OK with network-manager but that loses my wireless connection...

I have a thread about it in the wicd forums:

[http://wicd.net/punbb/viewtopic.php?pid=1478#p1478](http://wicd.net/punbb/viewtopic.php?pid=1478#p1478)

I'll watch this one and get back to you if I find a solution.

---

### Post by Naipes on 2008-12-18
I have the same stupid problem using Ubuntu 8.04.  I uninstalled Network Manager (NM) and installed WICD, but that didn't fix anything, except now eth0 remains up where NM used to shut it down.

When I look at the back of my computer I can see the light on my network card blinking as though the card is trying to talk to the router, but the machine cannot ping the gateway or get an IP address. I tried unplugging my computer from the wall for a while to see if that would help, but nothing changed.  Still no internet connection.

What is especially frustrating is that this connection worked flawlessly for over a year with the default settings!  I never did anything to get the internet to work when I first installed Ubuntu and I never messed with the settings.  It just worked, right out of the box.

I've always kept up to date with the updates, but it appears somewhere along the line my wired internet connection was hosed.  I've tried for days to resolve this problem, but screw it. I'm going back to Windows and use that for my file/print server instead of Ubuntu.  I guess the old adage is true, you get what you pay for and since Ubuntu is free, I can't complain, but it sure is disappointing.  My Ubuntu box talked to my XP box *and* my Vista box. Ubuntu served up files and printing services for *every* machine on my home network, even guests.  Now my Ubuntu box is useless and I have no idea what happened. :confused:

Currently, I'm in the process of painfully transferring all the files from my Ubuntu box over to a Windows XP machine that has no problem connecting to the network.  I may play with Ubuntu occasionally, but I don't think I'll use it for "mission critical" services anymore.

If I find a resolution to this problem, I'll be sure to post the answer for all to see.

---

### Post by ackattack on 2008-12-18
Before you give up completely, check the output of ifconfig, specifically the MTU value.  Should be 1500.  

Apparently there's a regression of a bug where some old routers report a bogus MTU value (64).

---

### Post by Naipes on 2008-12-18
Hmmm... here's my most recent ifconfig:

eth0    Link encap:Ethernet  HWaddr 00:e0:29:88:90:55
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0

	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
	Interrupt:3 Base address:0xec00

lo	Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
	RX packets:1056 errors:0 dropped:0 overruns:0 frame:0
	TX packets:1056 errors:0 dropped:0 overruns:0 carrier:0

	collisions:0 txqueuelen:0
	RX bytes:54676 (53.3 KB)
	TX bytes:54676 (53.3 KB)

I'm not sure what is going on... what about that inet6 addr? That looks a little funny to me.

---

### Post by Clancy_s on 2008-12-18
> **Clancy_s said:**
> PMJI: I think I may have a similar problem, in that wicd can't detect my wired connection in 8.10 (64 bit).  It doesn't seem to be able to find the ethernet card - I don't even get a light on the port when I connect a cable.

ifconfig doesn't find any ethernet.

My wireless works so it took a while for me to notice the problem.

My wired connection works OK with network-manager but that loses my wireless connection...

I have a thread about it in the wicd forums:

[http://wicd.net/punbb/viewtopic.php?pid=1478#p1478](http://wicd.net/punbb/viewtopic.php?pid=1478#p1478)

I'll watch this one and get back to you if I find a solution.

I've managed to make wicd work on my system: it turns out the ethernet card is now called eth1 in instead of eth0, I changed wicd's preferences for wired to eth1 and can now get a wired connection with wicd.

If I do make a wired connection it loses the wireless and can't reconnect 'til it's restarted.  I can live with that if I must but I will be looking for a fix...

I have a feeling that networking is generally a bit dirty in 8.10 and there's a number of slightly different problems here. :confused:

---

### Post by Naipes on 2008-12-18
hmmm... I thought eth0 was a wired connection and eth1 was wireless.

Since I have no wireless radio in my ubuntu box the only connection I'm offered is eth0.  Nothing else even comes close to working. 

When I tell WICD to make the wired connection it stalls at trying to get an IP address from the router.

I wonder if the router is starting to go bad?

---

### Post by 8pla.net on 2008-12-21
*FYI: In terminal...*

**ifup eth0**

*restarted the wired network, including internet, without a reboot.*

---

### Post by SeriyVolk on 2008-12-21
I'm having similar problems here. My sister has a Dell Latitude D600 with some kind of Gigabyte Broadcom on-board ethernet and Intel 2200 wireless. I had to look up the specs for this thing to figure out the Broadcom chip because lspci doesn't mention it. She said she can get wireless to work, but the wired connection is problematic.

Administration->Network doesn't have a Wired Connection listed, and lights on the back don't even stay on. I've searched through several threads here and tried the advice to no avail. This one seems closest to my troubles. I have to say I've never been so frustrated by a Linux issue. This is my first time messing with Ubuntu (Fedora user myself), and it's really disappointing, especially considering that Ubuntu has the reputation that it "just works" out of the box ](*,) .

Judging by the threads here it seems like Ubuntu has entered some kind of Dark Age of Networking :shock: . I'm thinking about trying to roll the system back to an older version of Ubuntu before it all started. Any suggestions (on where to start or how to fix this thing)?

I'd like to do it without downloading and installing wicd too, if possible. I'd prefer to uncover the problem rather than apply a band-aid. By the way this is also why some people get really upset when you include beta software (like Network Manager..) in your releases. Not that it's causing the problem, but from these posts it's only further complicating the issue.

---

### Post by SeriyVolk on 2008-12-21
*groan* Something goofed up and turned the ethernet adapter off in the BIOS. The wired connection is working now. I guess we'll find out if bad things happen again when we hook it up to a wireless network. Thankfully she's using 8.04, so I'll just forbid her from upgrading until the rest of this gets worked out... :D

---

### Post by SurferGTO on 2009-03-16
FYI: Since i only now got my wired connection working (for now) heres what appears to have fixed it..

as someone stated above, I too had to change my wired connection preferences in WICD from Eth0 to Eth1 and that fixed it. appears to have done the trick.

---

