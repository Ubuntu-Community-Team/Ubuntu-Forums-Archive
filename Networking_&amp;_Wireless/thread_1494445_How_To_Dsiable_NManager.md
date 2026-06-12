---
title: "How To Dsiable NManager"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by elliteforce on 2010-05-26
I'm Newbie.
I'm A **UBUNTU 9.10** User.Im Having A Dual Boot System With Windows Xp As Another Partition.

I Uses Broadband Via Ethernet,Since Last Few Days It Worked Fine For Both Windows & UBUNTU.

But Recently I Changed The Default Login Method Of Broadband.Before It Was Using Network Manager To Login ,But Now It Uses Router Configuration For Login.
It Works Nice For My Widows As I Don't Have To Make Dial Up For Connecting,But It Doesn't Work For My UBUNTU.

I Hadnt Changed Any Configuration In NManager After That.Unable To Connect Now,& I Dont Wana Use Windows.

**Please Give A Possible Solution For This Problem,Other Than** _Fresh Installation_**.**

---

### Post by 2hot6ft2 on 2010-05-27
Welcome to the forum elliteforce,

For broadband with DHCP by the router without using network manager it's pretty easy. I'm guessing this is what you want since your post is a little confusing.

Open a terminal
Applications > Accessories > Terminal
and run

```
gksu gedit /etc/network/interfaces
```
add 2 lines so it looks like this
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
save and close
Then go to
System > Preferences > Startup Applications
Find Network Manager and clear the box
Close, then open it again and make sure it's still unchecked.
You may have to repeat until it stays unchecked.
Reboot

You can always undo it by reversing what you did
```
gksu gedit /etc/network/interfaces
```
remove the 2 lines so it looks like this
> auto lo
iface lo inet loopback
save and close
Then go to
System > Preferences > Startup Applications
Find Network Manager and check the box
Close, then open it again and make sure it's still checked.
You may have to repeat until it stays checked.
Reboot
:guitar:

---

### Post by elliteforce on 2010-05-27
I Tried What You Had Said,Bt Its Not Working.
Thanx In Advance

---

### Post by elliteforce on 2010-05-27
A Very Suspicious Thing What I Found Out,After running ifconfig -a
Please Tell Me Is This Output Is Correct Or Not??

```
ifconfig -a

OUTPUT

eth0
        Link encap:Ethernet  HWaddr 00:30:18:ab:96:d4
        inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
        inet6 addr: fe80::230:18ff:feab:96d4/64  Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

        RX packets:2 errors:0 dropped:0 overruns:0 frame:0

        TX packets:31 errors:0 dropped:0 overruns:0 carrier:0

        collisions:0 txqueuelen:1000 

        RX bytes:644 (644.0 B)  TX bytes:5396 (5.3 KB)

        Interrupt:27 Base address:0xe000 

lo
        Link encap:Local Loopback  
        inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```

```

sudo dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 1736
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:18:ab:96:d4
Sending on   LPF/eth0/00:30:18:ab:96:d4
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 40705 seconds.


```

---

### Post by puppywhacker on 2010-05-27
your ubuntu uses eth0 and receives the ip-address 192.168.1.2 from the dhcp server on your router.

From your first post I didn't quiet understand if you need to pppoe (dial-up-over-ethernet) or not?

You have to provide more information on what exactly is not working and what kind of connection you have? also if network-manager was working before, why do you want to disable it?

---

### Post by dobelden on 2010-05-27
IMHO, Network manager is use for re add IP address and DNS for automatic network.

If you disable this function, you can put ip address manually at : /etc/network/interfaces.

network manager for ubuntu dekstop only, not installed on ubuntu server.

---

### Post by elliteforce on 2010-05-27
I'm Sorry,Mine English Is Not To Good,That's Why The Confusion Exists.

Before This Problem Started I Was Using PPPOE Connection Using(Dial Up Over Ethernet)  , But Usually I Have To Restart My Computer If Link Of DSL Fails To Connect.During This Time I Had Configured My Network Manager, And Had Provided Username & Password For It.

After That I Had Bought A New DSL Router,& I Had Configured It In Such A Manner That I Didn't Need To Dial Again and Again.It Stores The User name & Password In Itself,And Dials Automatically.
This Configuration Works Fine For My Windows Partition But Can't Make It For My UBUNTU Partition.

I Was Wondering What Must Be The Problem,At last I Came To Conclusion That It Must Be Because Of Network Manager Configuration,As  During Release time It Was Reported Of Wrong Configuration In Network Manager.
Please Do Correct Me If I'm Wrong

---

### Post by elliteforce on 2010-06-13
Please AnyBody Help me,
I Hate Windows.
I Guide Me So That I Can Use My Lynx Again
Thanx In Advance..!!

---

