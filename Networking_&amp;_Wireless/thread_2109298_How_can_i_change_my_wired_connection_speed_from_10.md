---
title: "How can i change my wired connection speed from 100Mb/s to 10Mb/s??"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by vinfospot on 2013-01-27
Please help me!
I'm using Ubuntu 12.10 x64.
I've a problem with my wired connection. My LAN/NIC card is weak. So it doesn't work in Speed 100MB/s. I need to change it into 10Mb/s..
But I don't know how to do it..
Anyone here to help me out???

---

### Post by kc1di on 2013-01-27
Hello vinfospot and welcome to Ubuntu,

This [Page ]("http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html")may be of help to you.

all the commands on that page are accomplished in the terminal you can simply copy and past them in a terminal and it should work for you  good luck

---

### Post by vinfospot on 2013-01-27
> **kc1di said:**
> Hello vinfospot and welcome to Ubuntu,

This [Page ]("http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html")may be of help to you.

all the commands on that page are accomplished in the terminal you can simply copy and past them in a terminal and it should work for you  good luck


Thanks. but it doesn't work.

I tried *sudo ethtool -s eth0 speed 10 duplex half* command. But it replies *sudo: ethtool: command not found*  :(

---

### Post by kc1di on 2013-01-27
did you do the first step and install the tool?

---

### Post by vinfospot on 2013-01-27
> **kc1di said:**
> did you do the first step and install the tool?

Here is the output of the first command

[I]"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ethtool is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ethtool' has no installation candidate"[/I]

---

### Post by kc1di on 2013-01-27
Ok there are two possibilities here.  
one - that it's no longer offered in 12.10 
two - it may be in the universe or multi-universe repositories.

go to software center and see if it is offered there if it is try to install **ethtool** from there.

I don't have 12.10 installed at the moment only 12.04 and it's in 12.04.

---

### Post by sanderj on 2013-01-27
> **kc1di said:**
> Ok there are two possibilities here.  
one - that it's no longer offered in 12.10 
two - it may be in the universe or multi-universe repositories.



Neither of those options ... it's just available 12.10 main; see [http://packages.ubuntu.com/search?keywords=ethtool&searchon=names&suite=quantal&section=all](http://packages.ubuntu.com/search?keywords=ethtool&searchon=names&suite=quantal&section=all)

Installing works fine on my 12.10 64-bit:

```
sander@R540:~$ sudo apt-get install ethtool
[sudo] password for sander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  spawn-fcgi
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  ethtool
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 100 kB of archives.
After this operation, 306 kB of additional disk space will be used.
Get:1 http://nl.archive.ubuntu.com/ubuntu/ quantal/main ethtool amd64 1:3.4.1-1 [100 kB]
Fetched 100 kB in 0s (370 kB/s)   
Selecting previously unselected package ethtool.
(Reading database ... 473857 files and directories currently installed.)
Unpacking ethtool (from .../ethtool_1%3a3.4.1-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up ethtool (1:3.4.1-1) ...
sander@R540:~$
```

---

### Post by vinfospot on 2013-01-27
Oh.
But anyway.. ThankYou!

---

### Post by sanderj on 2013-01-27
> **vinfospot said:**
> Oh.
But anyway.. ThankYou!

So ... let's investigate further:

Are you on a normal Ubuntu 12.10 you installed from CD/DVD/USB on your own hardware? Or is it a VPS?

What happens when you run:

```
sudo apt-get update
apt-cache search ethtool
```

The first command should be without errors or warnings.

That last command results on my system in:

```
sander@R540:~$ apt-cache search ethtool
ethtool - display or change Ethernet device settings
ifplugd - configuration daemon for ethernet devices
python-ethtool - Python bindings for the ethtool kernel interface
sander@R540:~$ 

```

---

### Post by vinfospot on 2013-01-27
> **sanderj said:**
> Neither of those options ... it's just available 12.10 main; see [http://packages.ubuntu.com/search?keywords=ethtool&searchon=names&suite=quantal&section=all](http://packages.ubuntu.com/search?keywords=ethtool&searchon=names&suite=quantal&section=all)

Installing works fine on my 12.10 64-bit:

```
sander@R540:~$ sudo apt-get install ethtool
[sudo] password for sander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  spawn-fcgi
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  ethtool
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 100 kB of archives.
After this operation, 306 kB of additional disk space will be used.
Get:1 http://nl.archive.ubuntu.com/ubuntu/ quantal/main ethtool amd64 1:3.4.1-1 [100 kB]
Fetched 100 kB in 0s (370 kB/s)   
Selecting previously unselected package ethtool.
(Reading database ... 473857 files and directories currently installed.)
Unpacking ethtool (from .../ethtool_1%3a3.4.1-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up ethtool (1:3.4.1-1) ...
sander@R540:~$
```



Yea i visit the links you've attached.. Its available for 12.10.
But what is wrong with my one??

---

### Post by vinfospot on 2013-01-27
Thanks to both of you!
My problem is solved.
The source was selected as United State.
I've changed it into "Main Server" & try again to install it.. And It's worked. :-)

Thanks again.

---

### Post by kc1di on 2013-01-27
According to your post  ethtool  was installed and should work.
go back to the original page and try the commands to alter your LAN speed again.

Never mind didn't see you last post. 
glad it worked for you 
cheers!

---

### Post by tgalati4 on 2013-01-27
The bigger issue is why do you need the slower speed?  Do you have a cabling or crimp problem?

---

