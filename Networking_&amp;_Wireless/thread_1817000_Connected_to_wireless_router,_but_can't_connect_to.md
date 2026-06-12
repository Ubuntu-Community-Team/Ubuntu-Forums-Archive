---
title: "Connected to wireless router, but can't connect to Internet"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by sauerpauer on 2011-08-02
I think something weird is going on.  On a fresh installation of 11.04,  I seem to be connected to my router just fine, but I can't reach the internet or anywhere else on my network.  Anybody see my problem from what I've posted? The computer is only connected via wireless (so I don't know why eth0 would be connected as well).  I can't think of what I'm missing...:(

My system seems to be connected to my router on two interfaces.  "ip addr" gives:```
1: lo <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state **DOWN** qlen 1000
    link/ether 22:00:00:00:00:22 brd ff:ff:ff:ff:ff:ff
    **inet 192.168.1.120/24** brd 192.168.1.255 scope global eth0
    inet6 fe80::21e:ecff:fe5d:6905/64 scope link
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 11:00:00:00:00:11 brd ff:ff:ff:ff:ff:ff
    **inet 192.168.1.100/24** brd 192.168.1.255 scope global wlan0
    inet6 fe80::21f:3cff:fe18:55cc/64 scope link
       valid_lft forever preferred_lft forever

```, and these are reflected in my router's connected device list:```

interface     MAC                IP               name
eth1	11:00:00:00:00:11	192.168.1.100	old_name
br0     22:00:00:00:00:22       192.168.1.120   new_name

```

Running nm-tool gives the correct settings for wlan0 (not so sure about eth0):```
NetworkManager Tool

State: connected

- Devicce: wlan0 [network] ---------------------------------
  Type:            802.11 WiFi
  Driver:          iwl3945
  State:           connected
  Default:         yes
  HW Address:      11:00:00:00:00:11

  ...

  IPv4 Settings:
    Address:       192.168.1.100
    Prefix:        24 (255.255.255.0)
    Gateway:       192.168.1.1

    DNS:           192.168.1.1

- Device: eth0 ------------------------------------
  Type:            Wired
  Driver:          r8169
  State:           unmanaged
  Default:         no
  HW Address:      22:00:00:00:00:22

  Capabilities:
   Carrier Detect: yes
   Speed:          10 Mb/s

  Wired Properties
    Carrier:       off 
```

---

### Post by °-° on 2011-08-02
Do you have Internet access via wired connection?

---

### Post by sauerpauer on 2011-08-02
The wired port isn't connected, and I was unable to connect to the internet via wired.  I'm fairly certain that it's due to an issue with /etc/network/interfaces, but I didn't think an eth0 problem would affect wireless.

Currently /etc/network/interfaces reads:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    network 192.168.0.1
    broadcast 192.168.1.255
    gateway 192.168.1.1
    dns-nameservers 192.168.1.1
    dns-search hostname.dns.org

```

---

### Post by °-° on 2011-08-02
Perhaps it is a problem with your ISP.

---

### Post by sauerpauer on 2011-08-02
Shouldn't be anything wrong with my ISP - every other computer on the network can access the internet.

---

### Post by °-° on 2011-08-02
Have you checked your router settings? Maybe it has a MAC address filter.

---

### Post by sauerpauer on 2011-08-03
The router does have a MAC address filter, but I made sure it was off.  If it was on, the router wouldn't be able to allow the machine to connect.  I'm thinking a clue might be given by the fact that I can connect to the router fine, but can't use any network apps on the machine I'm talking about...  This is a fresh install, so is there a configuration file somewhere I need to set up for this to work?  I don't think it's a DNS error, since I can't access the router's web-interface nor its command-line interface from the machine in question.

---

### Post by dineshs on 2011-08-03
Is there any specific reason for editing /etc/network/interfaces ?
I suggest you make /etc/network/interfaces to read only the first two lines,ie
auto lo
iface lo inet loopback
then do manual configurations for eth0 and wlan0 via Network Manager.ie click NM icon on right top then edit connections......
Note:Your /etc/network/interfaces has a line
network 192.168.0.1
I think it should be 
network 192.168.1.0 (though it is for eth0)

---

### Post by sauerpauer on 2011-08-03
I edited /etc/network/interfaces in an attempt to be able to use a wired connection.  The line "network 192.168.0.1 was automatically put there during the install process-I'm not sure what that line is even responsible for.  Changing it to 192.168.1.0 didn't seem to help, nor did deleting the line entirely.  As of now, the only three properties specified in the eht0 stanza are address, netmask, and gateway.  I think that the lack of wired connectivity I'm experiencing might be tied to the fact that NetworkManager lists the wired network as "device not managed", but I don't know what the problem there is either.

There is currently no entry in /interfaces for wlan0, and commenting out the eth0 stanza didn't seem to change anything.  I did try to add a wired connection in Network Manager, but it still hasn't allowed  me to connect and it still lists the device as "not managed".

It still seems like I'm able to establish a wireless connection with my router, but I'm not able to pass any information through that connection.  Anybody have any other ideas?

Thanks to those who have already tried to help :-).

---

### Post by wildmanne39 on 2011-08-03
Hi, the only thing that is suppose to be in ```
cat /etc/network/interfaces
```
is
```
auto lo
iface lo inet loopback 
```
Thank you

---

### Post by sauerpauer on 2011-08-03
An update.  Restarting the computer after disabling the eth0 interface still allows me to connect to the router, and in fact firefox can now get to the internet (I think maybe /etc/init.d/networking wasn't restarting cleanly), but update manager, synaptic, and apt still aren't able to download anything.  Firefox seems to be the only app able to use the internet connection.  Any thoughts?

---

### Post by wildmanne39 on 2011-08-03
Hi, run this command in a terminal and post the errors here.
```
sudo apt-get update
```
Thank you

---

### Post by sauerpauer on 2011-08-03
it hangs for a while at:```
0% [Connecting to us.archive.ubuntu.com (91.189.88.31)] [Connecting to security
```then puts out: ```

Err http://extras.ubuntu.com natty InRelease                                   
  
Err http://archive.canonical.com natty InRelease                               
  
Err http://archive.canonical.com natty Release.gpg                             
  Unable to connect to archive.canonical.com:http:
Err http://extras.ubuntu.com natty Release.gpg                                 
  Unable to connect to extras.ubuntu.com:http:
Ign http://security.ubuntu.com natty-security InRelease

...

Reading package lists... Done
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to archive.canonical.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by wildmanne39 on 2011-08-03
Hi,run these commands and post the outcome here please.
```
cat /etc/apt/sources.list
```
```
ls /etc/apt/sources.list.d/
```
Thank you

---

### Post by sauerpauer on 2011-08-03
The sources should be the exact same as a default install, with universe and multiverse enabled.  ```
# 

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110426)]/ natty main restricted

#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110426)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
chris@newbuntu:~$ 

``````
ls -la /etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 2011-04-07 05:13 .
drwxr-xr-x 6 root root 4096 2011-08-02 05:17 ..
```

---

### Post by wildmanne39 on 2011-08-03
Hi, you do not need those ppa's so open synaptic and click on settings,repositories,
other software and uncheck them, but pay close attention and make sure you uncheck the right ones.
Thank you

---

### Post by sauerpauer on 2011-08-03
Why would those ppa's being enabled affect my ability to connect to the Internet with any app except Firefox?

Not sure what was causing any of my problems, but connectivity is suddenly allowed.  I'm going to mark this as solved (even though there are no real solutions in the thread, something must have magically fixed itself).  Thanks to those who tried to help.

---

### Post by wildmanne39 on 2011-08-03
Hi, because they are not on the server anymore.

---

### Post by sauerpauer on 2011-08-03
Ah, which ones aren't on the server anymore?  Or how will I be able to tell which ones are or aren't?

---

### Post by wildmanne39 on 2011-08-03
The four with the error message when you ran sudo apt-get update.

---

### Post by sauerpauer on 2011-08-03
Makes sense.  :oops:

I will remove those.  Still don't know why pidgin and other work suddenly, but hey, I'll take what I can get :-).  Thanks for your help!

---

### Post by wildmanne39 on 2011-08-03
Hi, your welcome! I hope that solves the update issue if not it will help, so if it still gives errors post them back here they should be different errors if you have any.

---

