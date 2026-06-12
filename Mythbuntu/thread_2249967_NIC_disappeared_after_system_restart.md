---
title: "NIC disappeared after system restart"
date: 2014-10-25
forum: Mythbuntu
---

### Post by Mike_Carron on 2014-10-25
I have a Master BackEnd (backend only) system on Mythbuntu 14.04.1 which has the motherboard network interface and an Intel PRO/1000 PCIe card. All were working fine with the Intel card connected to three HDHR Primes directly. I encountered a notice to restart the system when I logged on to it this morning. Following the system restart the Intel 4 port NIC had disappeared. ifconfig shows nothing there except eth0 and lo. eth1 through eth4 were present and working before the system restart, they are not gone. Has a recent update done something to the driver for that Intel NIC or for the Intel 82571EB chip which controls it?
Is there something in particular I should be looking at?

This is my system info from syslog: Linux version 3.13.0-37-generic (buildd@kapok) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 (Ubuntu 3.13.0-37.64-generic 3.13.11.7)

There is no reference to the Intel Pro/1000 in syslog but the following is from what had been the connections:
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    Ifupdown: get unmanaged devices count: 0
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    SCPlugin-Ifupdown: (36786720) ... get_connections.
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    SCPlugin-Ifupdown: (36786720) ... get_connections (managed=false): return empty list.
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile: parsing Wired connection 2 ...
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]: keyfile: ipv4.address1: address 169.254.1.102/16 gateway 0.0.0.0
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile:     read connection 'Wired connection 2'
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile: parsing Wired connection 3 ...
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]: keyfile: ipv4.address1: address 169.254.1.103/16 gateway 0.0.0.0
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile:     read connection 'Wired connection 3'
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile: parsing Wired connection 4 ...
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]: keyfile: ipv4.address1: address 169.154.1.104/16 gateway 0.0.0.0
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile:     read connection 'Wired connection 4'
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile: parsing Wired connection 1 ...
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]: keyfile: ipv4.address1: address 192.168.0.252/24 gateway 192.168.0.1
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    keyfile:     read connection 'Wired connection 1'
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    SCPlugin-Ofono: (36572688) ... get_connections.
Oct 25 13:56:20 12000mvd-mbe NetworkManager[1072]:    SCPlugin-Ofono: (36572688) connections count: 0

I need to get that NIC running again, any suggestions are welcome.

mike

---

### Post by JKyleOKC on 2014-10-26
I had something similar happen with a single-port Intel PRO/1000 card a couple of months ago; after a routine reboot, it refused to recognize its own checksum. Googling took me to an Intel forum where I found that their driver performed an unnecessary check that would fail at random, and a suggested patch. Before I had an opportunity to apply the patch, however, the 14.04.1 release came out and I did a clean install of it to a second hard drive -- and the problem vanished.

Something similar may be what's hitting you. I **am** curious, though, about the addresses being assigned to connections 2, 3, and 4. As I remember it, the 169.154.1.0/24 net is **not** a normal assignment -- and connection 1 does get a 192.168.0.0/16 address. Could something have altered an NVRAM on your card, or a boot-time configuration file?

I may be absent for a day or two due to minor surgery tomorrow, but others may have some ideas...

---

### Post by Mike_Carron on 2014-10-26
This is where I got the 169.254.x.y addressing: [http://www.silicondust.com/forum2/viewtopic.php?t=4088](http://www.silicondust.com/forum2/viewtopic.php?t=4088). It was working up to that restart.

I'm already at 14.04.1 but I'll continue to check to see if the NIC becomes visible after each future system update.

mike

---

### Post by JKyleOKC on 2014-10-27
I wasn't intending to suggest waiting for the update, rather going to the Intel forums to see if there might be a similar patch for the specific driver that you have. If they do have one I'd recommend installing it. As for the IP addresses, I've never used a multi-port card so don't know whether they might be needed, but as I recall those three are associated with the "avahi" package and they just might be the reason your gateways for those ports are set to all-zero instead of to the modem as is Connection 1... If the gateway doesn't go anywhere, then no connection could be established through the port!

---

### Post by Mike_Carron on 2014-10-27
Since the NIC disappeared following a system restart that itself was occasioned by installing a regular update I can only assume that it was something in the update that caused it. I've had no luck trying to find a driver patch so I guess I'm stuck with hoping that whatever it was that broke the NIC will eventually get backed out.

I created those IPs using the 169.254.x.y that Silicon Dust provided as the addresses to use for the HD Homerun. The third and fourth groups of the IP address were numbers I arbitrarily selected and can change to something else if that might accomplish anything.

mike

---

### Post by JKyleOKC on 2014-10-27
But what, if anything, did you p[rovide as the gateway address?

I suspect, based only on long experience with single-port cards, that the cards are expected to pick up DNS and Gateway addresses automagically from a DHCP or avahi server. If you had to enter the IPv4 addresses manually, then my best guess is that the boot procedures then did *not* access the DHCP server at all, leaving them blank. And as I said before, without a defined gateway address, the initial connection procedure would not be able to complete, leaving the port unusable.

However this is all guesswork; I've not had experience with multi-port cards, nor does your log excerpt indicate whether you even have a DHCP service running. If your addresses are assigned via the /etc/network/interfaces file, then it would help to know what your routing table contains. Hopefully someone with more experience than mine with regard to multi-port cards will chime in with better ideas!

---

### Post by Mike_Carron on 2014-10-28
The Silicon Dust instructions for direct connecting the HD HomeRun are fairly specific. Here is a direct quote:

Network configuration: Configure the PC to use a static IP address in  the 169.254.x.y range, e.g. 169.254.5.12, with a network mask of  255.255.0.0. No gateway address or DNS servers are needed. 

That is exactly what I did and is where the 169.254.1.101 etc IP addresses came from.

The installation had been running fine until an update required a system restart. It was only after the system restart that the NIC disappeared. I have to conclude that my problem began only after something in that update became active, which is why I remain convinced that if/when that something is backed out my problem will no longer exist.For the time being I have switched the HD HomeRuns off of direct connect and onto the network. If a future update restores the NIC to operation I will reconnect the HD HomeRuns directly.

mike

---

### Post by dannyboy79 on 2014-10-28
I'm betting you got a new kernel and that's what's preventing your 4 port NIC from working. At the grub boot menu choose a previous kernel to see if that fixes it. Only time ubuntu asks for a restart is if the kernel is updated to the best of my knowledge or if something with X server is updated. Most everything else can be restarted without restarting the computer

---

### Post by Mike_Carron on 2014-10-29
Thr GRUB menu offers 2 updates of the 3.13.0 kernel, 3.13.0-37 and 3.13.0-32. Neither can "see" that NIC.

mike

---

### Post by dannyboy79 on 2014-10-29
have you removed any kernels? i believe that's about the only system change that would make hardware stop working unless of course your hardware died. you should check the your kern.log for relevant info also after booting to an older kernel. can you try a live cd or live usb stick of any other linux distro to see if they show up in those OS's?

---

### Post by Mike_Carron on 2014-10-30
Kern.log didn't have anything I could identify as that 4 port NIC. I mainly look for a reference to the 82571EB chip that controls it. I have not removed any kernels. I tried the live usb stick that I originally installed the system from and it does not find the NIC. That's a problem for me because the install from that live stick ran the NIC fine until that one system restart. I have a real problem with the idea of hardware failing right at a system restart. I have a Mythbuntu 12.04.1 live usb stick around here somewhere and if I find it I'll see what it detects.

mike

---

### Post by dannyboy79 on 2014-10-30
if you don't think it's a hardware failure then let's see if the driver is being loaded. what chipset is the 4 port NIC?

```
sudo lshw -C network
```

after that, use the info it gives you to find out what kernel module is suppose to be loaded for that NIC to work, you would run (replace "drivernamehere" with the name you found for your NIC chipset. Example: your chipset is RT8765/43543, you would google "RT8765/43543 in linux", then you would find out that module rt87xx is the module name.
```
lsmod | grep drivernamehere
```
in my example you would fill in rt87xx for drivernamehere
if the driver isn't loaded than that's why its not showing up. you would load the module with
```
sudo modprobe drivernamehere
```
once loaded you could try to restart networking with
```
sudo service networking restart
```

Good luck

---

### Post by Mike_Carron on 2014-10-30
I'm beginning to wonder if my confidence in the hardware might be a bit misplaced.

sudo lshw -C network lists the ethernet interface on the motherboard, nothing else.

The controller ship is the INtel 82571EB and the driver for that chip is e1000e.

sudo lsmod | grep e1000e produced nothing.

sudo modprobe e1000e ran with no return message.

sudo lsmod | grep e1000e (after install):
e1000e                254433  0 
ptp                    18933  1 e1000e

sudo service networking restart failed
stop: Job failed while stopping
start: Job is already running: networking

Rebooted the machine and repeated the sequence, same result.

Found the live usb stick with Mythbuntu 12.04 and booted from it.

sudo lshw -C network produced only the motherboard ethernet interface, so now that distro, which had run the 4 port NIC properly now longer does so.

It looks like I'm facing a hardware issue, now I guess I need to figure out if it is the NIC or the PCIe slot on the motherboard.

mike

---

### Post by JKyleOKC on 2014-10-30
> **Mike_Carron said:**
> I mainly look for a reference to the 82571EB chip that controls it.While as I've said before I have no experience with multi-port adapters, I do have not one but three NICs in this machine since it serves as the gateway between my LAN and the outside world (one of the three is a spare). When I'm searching the logs, I grep for "eth" to pick up all references to the interfaces of all three, and that usually gives me good leads to the area causing the problem. If your interfaces use a different prefix, grepping syslog for that prefix might be helpful. You'll get a lot of extraneous noise hits (my *eth* search brings up every line containing "method" for example) but it's better than going through the log line by line.

It's not at all unlikely, though, that it could be a hardware failure. Conditions during the first few microseconds after application of power from a cold start are quite different from those a few hundred milliseconds later, and for many parts are much more stressful. You may have noticed that light bulbs tend to fail at the instant they're turned on, rather than simply burning out slowly later. That's because tungsten, the metal of which the filament is made, had a drastically lower resistance when cold than it does when hot. This allows much more current to flow during those critical microseconds, and as the filament nears the end of its life and becomes weaker, it cannot tolerate that current increase.

Similar things happen with electrolytic capacitors, and our hardware is filled with those little varmints. The increased stress at turn-on time is the main reason that some folk advocate leaving equipment powered up 24/7. I've had personal experience with an instant failure at turn-on, when such a power surge caused an arc in the power switch itself, that in turn created an induced surge on the motherboard that destroyed the entire system. It can, and does, happen.

The fact that even your original install media won't recognize the card any more does, actually, strongly support a diagnosis of hardware failure. Can Silicon Dust offer any suggestions for diagnostic procedures to test this possibility?

EDIT: I see that during the 90 minutes I was away from the keyboard and on the telephone, you're come to that conclusion. I would suggest that you try some known-good card in that PCIe slot; it need not be a NIC, if you have anything else available, since the purpose would be just to verify that the slot communicates properly. At that point, if the slot passes muster, I would be ordering a replacement NIC rather than spend a lot more time trying to pinpoint the failure. Of course, I have no idea how costly this approach would be...

Good luck!!!

---

### Post by Mike_Carron on 2014-10-30
Thanks. While I don't have a PCIe card handy to use for a test I do have another machine handy which has an unused PCIe slot. Since it is running PFSense already it should serve the purpose quite nicely.

I'm familiar with inrush current and its effect on electrolytic caps. Since the restart that seems to have triggered the problem should not have interrupted power to anything I don't think that played a role. If it was a hardware failure it was most likely a case of infant mortality.

Now I just need to find an opportunity to make the necessary mess.

mike

---

