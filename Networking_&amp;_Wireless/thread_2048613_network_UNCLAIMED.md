---
title: "network UNCLAIMED"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by ulisesmakana on 2012-08-27
Hi! I am new to Ubuntu and I have a problem with my broadcom 4318 card. I have been reading literally hundreds of posts regarding the broadcom 43xx card (since many people seem to have problems with those cards), tried quite a few things, but I am still unable to make the wireless work.

From what I was able to gather, I think it might have to do with this "network: UNCLAIMED" message I get whenever I run the 'lshw -C network' command on my terminal.

The whole string is: 
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:0b:d2:3c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.110 latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:c0204000-c0205fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```


Am I doing something wrong? Does anyone know how I could "claim" it? As I said, I read a few posts on the issue but none of them seemed to address mine fully. Also, I have read there is a way of doing it with the NdisWrapper, but since it said it should only be used as last resort, I have refrained from using it so far.

Any help will be fondly appreciated!!

---

### Post by OM55 on 2012-08-27
It would be helpful to view the wireless system log that is generated during the attempt to connect.
Here is you do it: 
1. Leave your laptop idle for a few of minutes (wireless off, so the  connection attempt of the time stamp in the log will be clear) and then  try to connect to the wireless router. 

2. Right after the unsuccessful attempt to connect to the wireless router, type in terminal:


   ```
  cat /var/log/syslog | grep NetworkManager > WirelessLog.txt 
```
then:

 ```
    gedit WirelessLog.txt 
```
We will start looking at the events with the time stamp of the  moment you tried to connect to the wireless connection. The events we  are interested in will start at the last time-stamp jump and have  "NetworkManager" at the beginning of the line. 

Normally you would see reports on the network SSID it is connecting to,  two DNS servers being assigned, IP address being assigned by the DHCP  etc.
In your case some of it is not happening and you may be able to see what  it is trying to do and cannot, resulting in no-wireless connection.

So this may give us some hints as for what is NOT happening that should, and why.
If you post the WirelessLog.txt file here as an attached file (only the  bottom lines, starting at the last time-stamp jump), we should be able  to help you find a clue and identify the problem.


_**For general information**_ - There is a known bug with  Network Manager that happens with some specific drivers on specific  hardware and it has been reported before several times. I think there is  a patch available for Network Manager but not yet updated in the  repositories.


[SIZE=3]_So, regardless of inspecting the log files for clues, here is a quick possible workaround that may work for you anyway:_
[/SIZE] 
You can replace Network Manager and use Wicd instead (**[https://launchpad.net/wicd](https://launchpad.net/wicd)**),  it is in the Software Center and the Ubuntu repositories. Wicd is a  nicer graphical interface for wired/wireless network management that  pretty much replaces all the functionality of Network Manager.

The only small risk in doing this exchange - you have to be careful and  do things step by step, or might be left without any network  connection... Given that in Ubuntu everything is done via the Internet  connection, it wont be fun when that happens... (you will need to  download the .deb file of Network Manager using a different laptop,  transfer to this one and install).

To install Wicd and properly disable Network Manager, follow the  instructions in the following link (coincidentally, it was done to solve  the exact same problem you have):
[http://www.techrepublic.com/blog/australia/fixing-fedoras-wi-fi-with-wicd/463](http://www.techrepublic.com/blog/australia/fixing-fedoras-wi-fi-with-wicd/463)

You can install Wicd directly from Software Center, or try the latest version from the developer's website

IMPORTANT: It is critical that you will disable Network Manager only  after Wicd is working, or will be left without a networking connection.

Hope that the above will finally resolve your wireless hassle!
Let us know if Wicd worked for you.

---

### Post by Finnicella on 2012-08-27
Did you try to go in system settings and try to see if in additional driver there are driver for your wireless card.
Network Unclaimed means that missing drivers.
Let me know if you solve it.
Bye 
Finny

---

### Post by ulisesmakana on 2012-08-27
> **Finnicella said:**
> Did you try to go in system settings and try to see if in additional driver there are driver for your wireless card.
Network Unclaimed means that missing drivers.
Let me know if you solve it.
Bye 
Finny

Yes, I have. What puzzles me is that it keeps telling me "The driver is active and currently in use". What I have noticed, however, is that ever since I installed the driver, the card is no longer hard blocked.

---

### Post by Finnicella on 2012-08-27
So doesn't it work?
If you give this command what is the output?
```
sudo rfkill list all
```
Bye
Finny

---

### Post by ulisesmakana on 2012-08-27
Thank you for your help!

OK, I will try to make it work with Wicd, but before doing that I thought I'd paste the log I got after running those commands:

```
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): carrier now ON (device state 20)
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Auto-activating connection 'Wired connection 1'.
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) starting connection 'Wired connection 1'
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> dhclient started with pid 3956
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Beginning IP6 addrconf.
Aug 27 14:20:31 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   address 192.168.1.110
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   prefix 24 (255.255.255.0)
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   gateway 192.168.1.1
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   hostname 'ulises-Presario-V2000-EK572LA-ABM'
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   nameserver '200.115.192.29'
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   nameserver '200.115.192.30'
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   nameserver '190.55.60.129'
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info>   domain name 'cpe.telecentro.net.ar'
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 27 14:20:32 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Aug 27 14:20:33 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> DNS: starting dnsmasq...
Aug 27 14:20:33 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Aug 27 14:20:33 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Aug 27 14:20:33 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Aug 27 14:20:33 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) successful, device activated.
Aug 27 14:20:33 ulises-Presario-V2000-EK572LA-ABM NetworkManager[706]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
```

If I have to be absolutely honest with you, I do not know how to read it...
I might also add that at first I tried to do it without being connected through a LAN cable, and got absolutely nothing. Then I plugged that cable in and this is the log I got.

---

### Post by ulisesmakana on 2012-08-27
With the "rfkill list all" command, what I get is this:

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by ulisesmakana on 2012-08-27
OK, so it seems we're getting to the bottom of this. I installed wicd and got it running, but it detects no wireless connections, when my computer is right next to the wireless router and the neighbours' connections should be also showing.
I'm only speculating here, but it seems as if my wireless card isn't really installed, even if everything tells me that it is.

---

### Post by ulisesmakana on 2012-08-27
A quick update, guys!
Thank you very much. I think I finally managed to get it to work. Wicd didn't do the trick, but after reading and re-reading dozens of threads with similar issues, I finally did it. The trick was typing the command "sudo modprobe 43"...It was frustrating because I'm pretty positive I had done that already!
After that, I had wireless. Just to make sure, though, I rebooted the computer to find that my wireless was gone again. Fortunately, I re-performed all the steps (including the "apt-get update" and "apt-get upgrade") and regained connectivity. Then I changed the log that indicates the modules to be loaded upon boot, and wrote in "b43". I haven't rebooted since, but I think might have worked for good.:guitar:

Thanks for the help!

---

