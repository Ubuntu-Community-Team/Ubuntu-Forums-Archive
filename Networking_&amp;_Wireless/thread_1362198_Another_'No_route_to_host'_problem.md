---
title: "Another 'No route to host' problem"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by garryknight on 2009-12-22
Before I get started, I should tell you that I've Googled my problem for some time and also done an exhaustive search on the Ubuntu forums for an answer to this problem. The nearest I've come to finding a solution was in one post from ["]_someone with a similar problem_]("http://ubuntuforums.org/[url=http://ubuntuforums.org/showthread.php?t=1311741) who put it down to a bug in wicd. But I'm using Kubuntu and I don't think Kubuntu uses wicd. Anyway...

Below is a diagram of my current LAN setup. The Internet comes in on my cable modem to which is attached a Netgear WGT624 wireless router with 4 ethernet sockets. All pretty standard. My PC is plugged into socket 4. My EeePC and my Advent netbook (Wind clone) connect to the LAN wirelessly. The PC and Advent both had Kubuntu 9.04 installed from scratch then upgraded to 9.10. My EeePC has Kubuntu 9.10 installed from scratch. All are current with software updates at the time of writing. All 3 machines are set up to use DHCP and I've set the router to always hand out IPs as shown in the diagram below, allocated by MAC address. Ok, here's how that looks:

```

                 Cable Modem
                      |
             --------------------
             |  Wireless Router |
             |    192.168.1.1   |
             |------------------|
             W     1    2   3   4
             |                  |
     ----------------          PC
     |              |     192.168.1.2
     |              |
   EeePC         Advent
192.168.1.4   192.168.1.3

```Now, PC has a route to EeePC and Advent and they have a route back to PC. EeePC and Advent both have a route to the PC but not to each other. Attempts by each netbook to ping the other result in similar behaviour: on the Advent, a message is displayed after a ping attempt "Destination Host Unreachable", while the EeePC just hangs waiting for a response to the first ping; I put this difference in behaviour down to different software versions, but maybe I'm wrong about this.

My route table looks like this on both the EeePC and the Advent:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```The route table on the PC is identical except for a metric of 1 for LAN addresses and eth0 in the Iface column. As you can see from the bottom line, every machine has the same default gateway. In other words, it looks (to me at least) as if every machine is reachable from every other machine. Since the router has built-in firewalling, every other machine on the network has ACCEPT rules on every chain. (At least, while the machines are on the LAN they have; when I take the netbooks out, I enable the firewall on them.)

What I don't understand is that, if they all seem to have a default route through their network interfaces to the router (192.168.1.1), how come EeePC and Advent can't talk to each other? Am I missing or misunderstanding something here? Do I need to go back to Networking 101? :-)

---

