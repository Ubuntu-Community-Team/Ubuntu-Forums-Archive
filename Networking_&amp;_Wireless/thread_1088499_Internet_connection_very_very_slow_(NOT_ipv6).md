---
title: "Internet connection very very slow (NOT ipv6)"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by m0n on 2009-03-06
Hi guys,
First of all this problem is NOT related to ipv6 cause it is disabled.

So recently I installed Ubuntu Iterpid on my friend's PC. It is quite old one (p3, 600mhz, 196mb RAM).

And internet speed is very slow, not only in Firefox but in package manager also, keeping speed of 232 **bytes**/sec :(

First of all I disabled ipv6 - that didn't help..
Then I tried to change to more lightweight Xubuntu (was thinking the problem is in PC specs.) - that didn't help either..

Now my guess is the problem could be in a driver/settings for the network card. The connection is DHCP enabled and working perfectly on my Ubuntu laptop.

One more thing to mention is that in firefox - google.com page and other very simple and light pages open w/o problems. As soon as web page is "bigger" then it is not loading.
And when package manager starts to download, first second it download with full speed and then speed falls to magic 232 bytes/sec.
And BTW ping shows normal times to websites I tried to open..

Could you please help me to find the problem?
Help is very appreciated, and if I succeed there will be one more Linux user in the world :)

---

### Post by ddrichardson on 2009-03-07
How much memory does this box has have?

---

### Post by m0n on 2009-03-10
> **ddrichardson said:**
> How much memory does this box has have?

192mb RAM

---

### Post by ddrichardson on 2009-03-10
Is this installed on the hard drive or running from CD? Is there a swap file installed? Does Firefox ever close without warning?

---

### Post by m0n on 2009-03-10
> **ddrichardson said:**
> Is this installed on the hard drive or running from CD? Is there a swap file installed? Does Firefox ever close without warning?

It is installed using alternate (it was not enough ram to run gui installer) installer, with everything by default on the hard drive. Swap is ~ 500 mb I think..

FF loads page very very long time and then just blank page is displayed w/o any warning or something.

What makes this problem very strange is that package installer download speed is also very slow, just some bytes per second... :confused:

---

### Post by ddrichardson on 2009-03-10
Ping is pretty unhelpful other than to establish a connection is responding - for speed measurement its no use.

What does```
lshw -C net
```
Say your card is?

---

### Post by m0n on 2009-03-11
Hi,
I will post results as soon as I get access to this pc..

---

### Post by m0n on 2009-03-11
```

 *-network
      description: Ethernet interface
      product: Netelligent 10/100 TX PCI UTP
      vendor: Compaq Computer Corporation
      physical id: 10
      bus info: pci@0000:00:10.0
      logical name: eth0
      version: 10
      serial: 00:80:5f:8b:fa:f4
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master ethernet physical
      configuration: broadcast=yes driver=tlan ip=xx.xx.x.xx
latency=66 module=tlan multicast=yes
 *-network DISABLED
      description: Ethernet interface
      physical id: 1
      logical name: pan0
      serial: b6:30:77:5c:8e:b5
      capabilities: ethernet physical
      configuration: broadcast=yes driver=bridge driverversion=2.3
firmware=N/A link=yes multicast=yes


```

---

### Post by bendybrock on 2009-03-11
I have exactly the same problem - its not just Ubuntu its any form of Linux OS I try to run on this network.

A Work around I Found was to install a proxy on a windows XP box on the local network, and set firefox to use that proxy. That way I get a full 1.1MB/s download speed.

without doing that and using a direct connection I get between 29kb/s and 700b/s.

Our network helpdesk say theres no firewall or ISA box that would check and limit devices by there operating system.

BUt like I say, running firefox through a proxy on the local network is a workaround. (it doesnt work if using an external proxy though :( )

---

### Post by m0n on 2009-03-11
> **bendybrock said:**
> I have exactly the same problem - its not just Ubuntu its any form of Linux OS I try to run on this network.

A Work around I Found was to install a proxy on a windows XP box on the local network, and set firefox to use that proxy. That way I get a full 1.1MB/s download speed.

without doing that and using a direct connection I get between 29kb/s and 700b/s.

Our network helpdesk say theres no firewall or ISA box that would check and limit devices by there operating system.

BUt like I say, running firefox through a proxy on the local network is a workaround. (it doesnt work if using an external proxy though :( )

It seems that this is not exactly my case cause the other Ubuntu laptop working fine on the same network (and even cable)  :(

---

### Post by ddrichardson on 2009-03-11
Can you post the output of```
sudo mii-tool
```

---

### Post by z-vap on 2009-03-11
I too am having sloooow browsing.  At first I tried disabling IPv6 and it didn't really seem to make much of a difference.  

I am on the search for a solution.  I ran the command you gave and it said that I didnt have a MII device.  

```
zvap@ubuntu:~$ sudo mii-tool
[sudo] password for zvap: 
SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found
zvap@stewart20:~$ 

```
I'm running a dual boot scenario, and from within XP I'm flying along smoothly.

---

### Post by m0n on 2009-03-13
> **ddrichardson said:**
> Can you post the output of```
sudo mii-tool
```

```
eth0: negotiated 100baseTx-FD, link ok
```

---

### Post by ddrichardson on 2009-03-13
How did you disable IPv6?

---

### Post by m0n on 2009-03-13
> **ddrichardson said:**
> How did you disable IPv6?

Well, I actually "double" disabled it by altering /etc/modprobe.d/aliases file, and added "blacklist ipv6" to blacklist file.
Command
```

ip a | grep inet6
```
shows no output...

---

### Post by ddrichardson on 2009-03-13
Assuming you've already reset the router, it only really leaves a bug report for you to raise. The DNS are set by the router aren't they? There was an issue with that card about three years ago but the output of mii-tool isn't consistant with that and it was patched years ago.

---

### Post by m0n on 2009-03-13
> **ddrichardson said:**
> Assuming you've already reset the router, it only really leaves a bug report for you to raise. The DNS are set by the router aren't they? There was an issue with that card about three years ago but the output of mii-tool isn't consistant with that and it was patched years ago.

some additional info about connection that might help: the Internet connection itself is from the cable modem, it gives direct internet IP automatically, so computer is not behind the NAT. The DNS set automatically also. (however I tried OpenDNS - no luck)...

---

### Post by z-vap on 2009-03-16
I wonder if any of the other browsers available for ubuntu are slow also.  If they are, then the issue is not with firefox.

---

### Post by m0n on 2009-03-17
> **z-vap said:**
> I wonder if any of the other browsers available for ubuntu are slow also.  If they are, then the issue is not with firefox.

Well, slow package manager download speed making this not a firefox problem I believe...

---

