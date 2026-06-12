---
title: "Linux and no internet connection"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by fettuohi on 2008-12-18
Well, since mid November I have nothing but problems with my Arch Linux machine. I can't get any internet connection on that machine. I have a network at home with 3 windows machines (XP, Vista & Vista), a Windows 2003 server running as an Exchange server and DNS server and Domain controller and a ps3, xbox 360 and Wii. The two windows machines run on a static IP, the ps3, xbox 360 and Wii run on dhcp. All machines run on LAN through a switch except the Wii it runs on wireless. Now my Arch Linux machine also runs on static IP set up as described in the installation guide via rc.conf, hosts and resolv.conf. As mentioned earlier since mid November I haven't been able to get any internet connection on that machine. I haven't changed anythnig in my setup on the machine or the network. when i start the machine for the first time during a day I actually do the get internet connection and network connection but if I restart then I lose it. I am not able to ping the gateway or the DNS server. I can get interrnet back again I turn off the machine and turn off the motherboard and let the machine cool off for 20 minutes. Then if I turn it on again I have internet again but if i'll have to restart then the problem reappears.
After two weeks with this issue I decided to get network card but that didn't help either I still had the problem. Then I simply bought a new machine (DELL Studio) and did a fresh installation of Arch and STILL the problem exists and it is driving me FREAKING CRAZY NOW!!! I tried to my machine on dhcp but still the same issue. internet on first boot, reboot no internet or network, shutdown machine and motherboard (unplug machine) --> internet again after waiting 20 minutes. None of my other machines running windows or the consoles have problems getting internet. I've tried to run distros on the machines (Ubuntu Live CD) but I have the same problem. I am very close to going back to windows and I REALLY don't want to (been using Linux since 2003) but this problem here is a show stopper/EPIC FAIL. I am very very happy with Arch Linux and really don't want to change distro either. I need suggestions now on what I can look for in order to find the problem. I've already changed network cards, bought a new machine and even bought new switch because we thought it might be the switch causing the problems (8 port switch) because turning off the switch would give me my internet back. Again it is only my Linux machine that is having the connection problems none of the other machines have those.

PLEASE HELP!!!

Kind Regards

André

PS. I know this question pertain to Arch Linux but I also with Ubuntu 8.04 and 8.10 and had the same issues.

---

### Post by The Cog on 2008-12-18
You say you are not able to even ping the local gateway when the problem occurs? In that case, forget the internet and concentrate on the gateway - it will remove a lot of confusing distractions.

When the problem occurs, use the command **ifconfig** and look at a couple of details like this:
```
wlan0     Link encap:Ethernet  HWaddr 00:1d:92:c7:1b:08  
          inet addr:192.168.8.99  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fec7:1b08/64 Scope:Link
          **[COLOR="Red"]UP[/COLOR]** BROADCAST **[COLOR="Red"]RUNNING[/COLOR]** MULTICAST  MTU:1500  Metric:1
          RX packets:**[COLOR="Red"]4083[/COLOR]** errors:13 dropped:3261 overruns:0 frame:0
          TX packets:**[COLOR="Red"]3286[/COLOR]** errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3719122 (3.7 MB)  TX bytes:443535 (443.5 KB)
          Interrupt:17 Memory:f8f70000-f8f70100 

```Check that the interface is RUNNING - if not then you may have a cable fault. Also see if transmit and receive packet counts are incrementing when you ping the gateway.

Beyond that, perhaps capture a few packets while trying to ping the gateway. Capture the packets with this command:
**sudo tcpdump -n -i eth0**
We are looking to see what goes out and comes back. Post the output here if you have trouble understanding it.

---

