---
title: "Attempting to share an Internet connection with a Windows XP client"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-01-25
Over the last several days, I've been trying like hell to share my (wired) Internet connection with a netbook, running Windows XP, attached via crossover cable to my desktop's extra NIC (eth0).  The eth0 link is established, but I can't get to the Internet from the Windows XP machine.

I can ping one machine from the other, but any bits sent from the Win XP netbook mysteriously disappear when trying to reach any website.

Kernel forwarding is enabled via the command:
```
sudo sysctl net.ipv4.ip_forward=1
```
so I can't figure out where in hell my packets are going!

There is no firewall running on the Ubuntu machine as far as I know.  Windows Firewall is likewise disabled on the Windows XP machine.  The Ubuntu machine connects to the Internet through another wired NIC, eth1.

In Windows XP parlance, what I am trying to do would be called "bridging," where eth0 and eth1 would be the two parts of the bridge.  In fact I already made it work, with both the netbook and my desktop running Windows XP.  It took about 5 minutes.

I can't believe what a huge pain this has been in Ubuntu.  I'm pretty much ready to give up.  There seems to be no way to get an Ubuntu system and a Windows XP system to share an Internet connection.

---

### Post by oldefoxx on 2010-01-25
Can't help with your particular approach, because there is a better one available which I regularly use.  I use VirtualBox and set up my client under it.  Under VirtualBox I enable settings so that I can share the network adapter, USB devices, any ports, and things like DVD/CD drive,
ISO images as though drives, and designated shared folders (which can actually be set at partition roots so whole drive is shared).  No extra cable or adapter required, and both host and client have access to network, internet, and even each other if I set them up that way.

So why do it the hard way?  Unless to try and prove a point.  Oh, and VirtualBox is not the only choice among virtual machine managers, just my preferred choice.

---

### Post by chewearn on 2010-01-25
> **Objekt said:**
> 

In Windows XP parlance, what I am trying to do would be called "bridging," where eth0 and eth1 would be the two parts of the bridge.  In fact I already made it work, with both the netbook and my desktop running Windows XP.  It took about 5 minutes.

I can't believe what a huge pain this has been in Ubuntu.  I'm pretty much ready to give up.  There seems to be no way to get an Ubuntu system and a Windows XP system to share an Internet connection.

Au contraire.  ICS in Ubuntu is as simple or as complicated as in WinXP.  You are not encountering difficulties in WinXP because you already know what to do in WinXP; prior experience and all that.

Here is my How-To, which apply to older Ubuntu Intrepid, but should still work (possibly with minor GUI differences) in latest Ubuntu:
[http://blog.chewearn.com/2009/01/28/internet-connection-sharing-in-ubuntu-intrepid/](http://blog.chewearn.com/2009/01/28/internet-connection-sharing-in-ubuntu-intrepid/)

---

### Post by Objekt on 2010-01-25
Simply marking the extra NIC as "shared" in NetworkManager was the first thing I tried.  It didn't work and still doesn't.

Something is very wrong.  I have to disconnect the extra NIC (eth0) in NetworkManager, or I can't get to the Internet.  It seems as if my Ubuntu system is trying to get to the Internet through the wrong connection (eth0) when it is connected, instead of using eth1 as it always did before.  I have no idea what settings would cause it to do that.  How can I reset networking to defaults?

---

### Post by Iowan on 2010-01-25
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is another help page for ICS.

---

### Post by Objekt on 2010-02-08
> **chewearn said:**
> Au contraire.  ICS in Ubuntu is as simple or as complicated as in WinXP.  You are not encountering difficulties in WinXP because you already know what to do in WinXP; prior experience and all that.

Here is my How-To, which apply to older Ubuntu Intrepid, but should still work (possibly with minor GUI differences) in latest Ubuntu:
[http://blog.chewearn.com/2009/01/28/internet-connection-sharing-in-ubuntu-intrepid/](http://blog.chewearn.com/2009/01/28/internet-connection-sharing-in-ubuntu-intrepid/)

Au contraire to your au contraire.  I have been trying for about THREE WEEKS to share an Internet connection with a client connected to a second NIC.  It simply does not work!

I am beyond frustrated with this.  There is no reason it should be this hard.

---

