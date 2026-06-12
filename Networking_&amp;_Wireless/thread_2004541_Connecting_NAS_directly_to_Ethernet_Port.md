---
title: "Connecting NAS directly to Ethernet Port"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by JustinR on 2012-06-16
Hey everybody,

I have a Western Digital My World Book Live NAS device. (Runs Debian Squeeze, Kernel: 2.6.32-11, PowerPC architecture) Currently, I'm using the device on a router that has no ethernet ports on it (a Verizon mobile hotspot). So I can't connect the NAS to a router.

I can't figure out how to setup the ethernet connection on my Ubuntu 12.04 box. Also, since I can't access my NAS, it doesn't appear as though that I can modify or change things like dhcp > static and vice versa.

So far it appears that if I manually assign the IP address/subnet mask/gateway/dns server in the Network manager for the ethernet port it appears to connect but when opening the NAS in a internet browser or through SSH it seems like the assigned IP address is only a loopback device for my own computer. E.g, connecting through ssh with the static IP connects me to my Ubuntu box and not the NAS, and the http request is denied (as my computer doesn't have open ports).

Is this a problem with the /etc/hosts file or am I way off?

The Verizon mobile hotspot it setup like this:
IP Address: 192.168.1.1
     Range: 192.168.1.2-192.168.1.6
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.1
DNS Server: 192.168.1.1

The manually configured ethernet port is setup the same way with the exception of the IP address being 192.168.1.7.

Thank you for your help.

Edit: According to Western Digital Customer Help:
> 
You can connect the My Book Live, WD My Book World Edition, or WD ShareSpace hard drive to your computer's Ethernet port and set the computer to use a dynamic IP Address to locate the hard drive. Reboot the computer and the WD My Book World Edition or WD ShareSpace hard drive once you've connected the drive directly to the computer and have reconfigured the computer's Ethernet port to use DHCP. Once the drive has been assigned a DHCP IP Address, MioNet should recognize the drive.


If your network uses DHCP or if you've connected the drive to your computer after configuring it for DHCP, you should be able to connect to the drive by using the following address in your web browser: [http://mybooklive/UI/](http://mybooklive/UI/) [http://mybookworld/](http://mybookworld/) or [http://WDShareSpace/](http://WDShareSpace/). If you changed the name of your device, you should instead use the name you changed to.


---

### Post by JustinR on 2012-06-16
Solved

Network Manager > Wired Connection > Method: Link Local.

I can now see the mybooklive through network places and it's shares. The UI can be accessed through [http://mybooklive.local:80/](http://mybooklive.local:80/). If you go to network it will give you an IP address that can be used with telnet/ftp/ssh.

---

### Post by BrianPierson on 2013-01-03
I am still not seeing my HD. Can one of you post some step by step instructions? I'm just assuming I'm missing one step. I'm trying to figure this out as soon as possible cause I'm deploying soon and I'm trying to take my movies with me. I'm operating on Win7

> **JustinR said:**
> Solved

Network Manager > Wired Connection > Method: Link Local.

I can now see the mybooklive through network places and it's shares. The UI can be accessed through [http://mybooklive.local:80/](http://mybooklive.local:80/). If you go to network it will give you an IP address that can be used with telnet/ftp/ssh.

---

### Post by howefield on 2013-01-04
Try...

1. Open Network Connections.
2. Press Add button and name the connection, eg MyBookWorld.
3. Select MAC address from the Device MAC drop down box in the Wired tab.
4. From the IPv4 Settings tab, select Link-Local Only from the Method drop down box.
5. Then save.

Optional whether you have it connect automatically or not.

You should then see the device in Nautilus > Browse Network > ect ect.

---

