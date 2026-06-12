---
title: "Internet problem on Eee900"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by Alessandro Allegri on 2010-12-29
Hi, I have an Eee900 series netbook with Lucid.
Everything was working fine, but eventually something happened last night, with the netbook hibernated, and after an upgrade (if I remember correctly, also including a kernel version, always within 10.04).

Now what happens is that no matter what I do I don't seem able to connect to the internet. The wireless is working correctly (I can access and manage my router through firefox), but whenever I tell my browser to look for web sites beyond the router it gives the same "looking for..." - "server not found" answer as when there is a dns problem.

But there is no dns problem: connected to the same router there are two more machines, one Lucid and one Vista, both working pretty well on the net.

The router has the correct static ip's of all three little pigs, but the small one can't get through it. Besides, both my Lucid machines have exactly the same networking configuration, except for the ip: same dns list, same ignore on ipv6. The only difference is the driver: the functional laptop has a b43 driver, whereas the disfunctional netbook has an ath5k driver.

I suppose there must be some kind of conflict between this driver and the new kernel version installed yesterday (although the problem didn't arise immediately).

Any similar problem reported and, more importantly, any clue about how to address it?

ThankS.

---

### Post by Alessandro Allegri on 2010-12-29
Nobody knows? :-)

---

### Post by PatchesTheCaveman on 2010-12-29
If you're connecting to the wireless successfully your driver is probably working correctly.

Try pinging a straight IP address from the broken computer.  That is, go to Applications > Accessories > Terminal and type this and press Enter:
```
ping 8.8.8.8
```

Does that work or does it time out?

---

### Post by Alessandro Allegri on 2010-12-29
Thanks a lot for answering.

Ok, well the only addresses I could ping were:
192.168.1.1 (the router)
192.168.1.3 (the other linux box)
nothing to do with the windows thing and nothing to do with several other wan ip's (I especially tried all the dns ip's I had at hand).

Now something even more worrying happened. I restarted the netbook and there is now no sign of the little beacon-like icon indicating the status of network-manager-applet. No network activity at all.
Switching on and off (Fn+F2 on my keyboard) several times the wifi, I got back the icon, no connection and a nice red exclamation mark to stress it.
No amount of disable-enable work on networking and wireless is effective in launching the only wifi connection or sniffing the wifi router.

What now? Ah yes, here are the if-w-configs:
```
eelsho@eelsho:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:16:2b:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116931 (116.9 KB)  TX bytes:116931 (116.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:a0:b0:19  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1360  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eelsho@eelsho:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```


Where are these configs stored now? Because in /etc/network/interfaces I have no mention of eth0...

Thanks to anybody who can help.

---

### Post by PatchesTheCaveman on 2010-12-29
Run this command:
```
uname -a
```

I have a feeling Canonical gave LTS the same broken kernel they gave us on 10.10.  If it says *2.6.35-24-generic* that's probably it.

Try going back to the older kernel by rebooting.  If you dual boot with Windows or another OS, pick the 2.6.25-23-generic or older kernel from the GRUB menu.  If you don't, you will need to hold SHIFT before Ubuntu starts to get the GRUB menu and select the older kernel.

See if that fixes your problem.

---

### Post by Alessandro Allegri on 2010-12-30
Right: the kernel! Let's see:

```

eelsho@eelsho:~$ uname -a
Linux eelsho 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

```

Is this one known to be faulty?
TAL.

---

### Post by Alessandro Allegri on 2010-12-30
Anyway, no, it doesn't matter which kernel I choose, the no-networking situation holds on...

Sigh.

Reinstall? (Sigh again)

---

### Post by PatchesTheCaveman on 2010-12-30
It's hard to tell.  Ubuntu 10.04 LTS uses an earlier version of the kernel than Ubuntu 10.10 where I and everyone else experienced the problem.

It's highly unlikely that they broke two different versions of the kernel at the same time in the same way.  Lightning doesn't strike twice, does it?

Okay, so maybe we should check to be sure?  :p

Try going back to the older kernel by rebooting. If you dual boot with Windows or another OS, pick the older kernel from the GRUB menu. If you don't, you will need to hold SHIFT before Ubuntu starts to get the GRUB menu and select the older kernel.

The older kernel for 10.04 LTS should be 2.6.32-26-generic.

---

### Post by Alessandro Allegri on 2010-12-30
Thanks.
I went back to 2.6.32-26-generic and 2.6.32-25-generic with no practical result. 
The ifconfig and iwconfig are still the same, no-show of the network manager applet (although it says one instance is already running), and if I iwconfig manually with the correct data I get stuck with the ap, which I'm not able to associate.

---

### Post by PatchesTheCaveman on 2010-12-30
Run ```
lspci -v
``` and copy the section that describes your wireless card here.  I think you might be able to try a different driver.

---

### Post by Alessandro Allegri on 2010-12-30
Here is what (sudo) lspci says:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Device 1a3b:1026
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k
```

---

### Post by PatchesTheCaveman on 2010-12-30
Go to System > Administration > Additional Drivers.  You should be able to install the *madwifi* driver from there.  Many users seem to think that works better than the open soruce ath5k driver with Atheros 5xxx chips.

---

### Post by Alessandro Allegri on 2010-12-30
Negative. I don't have "Additional drivers", but "Hardware drivers", which kindly tells me that "No proprietary drivers are in use on this system" and that's all thank you very much.
I am afraid that without an internet connection there is little for me to do on this netbook. Maybe I should look for an old cable and plug it into the router. But then, what should I remove/install?

---

### Post by PatchesTheCaveman on 2010-12-30
With it plugged into the router, try
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid-generic
sudo reboot
```

That should give you an improved ath5k driver.

---

### Post by PatchesTheCaveman on 2010-12-30
If you're comfortable with compiling and installing kernel modules (it's not as scary as it sounds), you can also build the madwifi driver yourself.

You can download it at [http://madwifi.org/](http://madwifi.org/) and follow the instructions at [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) to build and install.

If it doesn't tell you to you'll need to install the compilers and stuff first:
```
sudo apt-get install build-essentials
```

---

### Post by Alessandro Allegri on 2010-12-30
Ok, I'm growing weary of all this.

I wired my netbook into the router. NM-applet doesn't see a thing and is missing in action.
After some ifup-ifdown play I was able to have a sort of connection.
The router is reachable, and I can manage it through firefox.
Beyond that, I can ping few addresses (208.67.222.222 and 208.67.220.220 which my Vista laptop uses as dns's; 8.8.8.8 suggested in a previous message but I have no idea what that is), but all the interesting stuff keeps out of reach.
Firefox still doesn't know how to reach addresses (actually he refuses even faster than before, without even trying to look for them).

Gosh.
Thanks for your time...

---

### Post by PatchesTheCaveman on 2010-12-30
When you manually configure your network on the command line, you need to add your DNS servers to /etc/resolv.conf like so:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

I'm not sure why NetworkManager isn't working properly.  Try running:
```
killall nm-applet
```
to kill it and then press Alt+F2 and run nm-applet again.  (If you run nm-applet from a terminal you'll lose it when you close the terminal window.)

8.8.8.8 and 8.8.4.4 are public DNS servers run by Google.  I use them for ping tests because they're short and easy to remember.  :-)

---

### Post by PatchesTheCaveman on 2010-12-30
Since NetworkManager does seem to be the culprit here, you can uninstall it and try using *wicd* instead, which pretty much does the same thing as NetworkManager, but some people find it works better.

To do so, plug in via Ethernet to your router, and run these commands:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

Note that you'll need to have the *universe* repository enabled to install it.  If you don't have that enabled, before running *apt-get update*, run this command:
```
gksudo software-properties-gtk
```
Check *Community maintained Open Source software (universe)* and click *Close*.

---

### Post by Alessandro Allegri on 2010-12-30
Nope. I spent all afternoon trying to wire the connection, but the most I could get is an extremely slow one, able only to ping websites but not to download packages (apt-get remains stuck on "waiting for headers: 0%") nor to browse the net.

Could that be some kind of firewall problem? I have no ideas left...

---

### Post by PatchesTheCaveman on 2010-12-30
It's unlikely, but you can run
```
sudo service ufw stop
```
to disable your firewall and check.

I don't understand why your wired connection isn't working properly.  Generally they work great in Linux.

If you can, uninstall NetworkManager:
```
sudo apt-get remove network-manager
```

Then download these packages on another machine and flash drive them over to the netbook to install them:
[http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-iniparse/python-iniparse_0.3.2-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-iniparse/python-iniparse_0.3.2-1_all.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/python-wicd_1.7.0+ds1-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/python-wicd_1.7.0+ds1-5_all.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.0+ds1-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.0+ds1-5_all.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.0+ds1-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.0+ds1-5_all.deb) 
[http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-gtk_1.7.0+ds1-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-gtk_1.7.0+ds1-5_all.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.7.0+ds1-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.7.0+ds1-5_all.deb)

You can double-click on them to install them or run *sudo dpkg -i* in a terminal.  If you install them in the order linked you shouldn't get any dependency errors.

---

### Post by Alessandro Allegri on 2011-01-01
Thank you so much for the packages.
I installed them and was able to do without NetworkManager.
I couldn't get to connect to the internet yet, though.
First of all I discovered that my netbook is known to have an electronic problem at the wifi antenna, so that it needs to be out of power (without battery) ever so often to release all the static and do all the necessary antenna yoga.
So, I let it chill out and lo and behold, wicd can sniff the network.
Still it can't connect to it. I appreciate wicd's transparent behaviour,as it tells me that the problem is in verifying the ap. I've checked there are no sw/hw blocks on the wifi; but dmesg says something weird: immediately after the link to the ap gets available, there is a line saying "deauthenticating from XX:XX:XX:XX:XX by local choice (reason=3)". 
Now I left it there to chill some more, and I'm going to try and find out about this weird wrong local choice someone is taking against my will.
This is why I love linux: you get to learn your stuff.
This is why I hate it too: if you don't have the time you need, you don't get the work done.
Thank you again for your help... I'm not giving up, are you? :-)

---

### Post by Alessandro Allegri on 2011-01-08
Ok, this is the status now.

I reset the router, no weird stuff from there. Now all 3 computers here have the very same permissions on the router (except of course for their IP's, statically different).

The Vista and Lucid Notebooks (both HP's with different fillings) had and have no problems whatsoever during this whole nightmare the Lucid Netbook is going through.

The Lucid Netbook: through wicd I am able to connect both wired and wireless to the router. The icon says so, iwconfig says so, dmesg says so. No sw/hw locks on the wifi (rfkill says so). 
Nevertheless, when I ping the router I get "Destination Host Unreachable". Far less am I able to go beyond the router into the Wild Wild Web.
I also tried with a Live CD, restoring the system at least temporarily as it was when it worked perfectly, without luck.

Any ideas?
Thanks!

---

### Post by PatchesTheCaveman on 2011-01-09
Make sure your connected to the wireless and run these commands and copy/paste the output:
```
sudo dhclient wlan0
ifconfig -a
sudo iwconfig
```

---

### Post by Alessandro Allegri on 2011-01-09
Here they are:

dhclient:

```
eelsho@eelsho:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:15:af:a0:b0:19
Sending on   LPF/wlan0/00:15:af:a0:b0:19
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Note: at the first DHCPDISCOVER the so-called connection is reported lost by wicd.
Upon re-"connection", through ifdown-ifup and wicd's intervention, ifconfig gives:

```

eelsho@eelsho:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:16:2b:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5762804 (5.7 MB)  TX bytes:5762804 (5.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:a0:b0:19  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fea0:b019/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1360  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:675732 (675.7 KB)

```

Finally, iwconfig:
```

eelsho@eelsho:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"G604TWIRELESS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:3D:B2:AA:E4   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I now realize that ifconfig gives an ipv6 address, whereas dmesg always remarks that the router has no ipv6 extensions. Could it be something in that line?

---

### Post by Alessandro Allegri on 2011-01-09
Ok, I was able to disable ipv6.
No difference.

---

### Post by PatchesTheCaveman on 2011-01-10
Try running
```

sudo ip route del defualt dev wlan0
sudo ip route add default via *<router IP address>* dev wlan0
```

The first line might give you an error, which actually is a good thing.  It means the second line should definitely fix your problem.

If it does, check and make sure the "gateway" in your static IP configuration is correct.  If not, copy/paste the output of:
```
ip route
```
in case something else is wrong there.

---

### Post by Alessandro Allegri on 2011-01-10
```

sudo ip route del defualt dev wlan0
sudo ip route add default via *<router IP address>* dev wlan0
```

No error after the first.
No pinging after the second.

```
ip route
192.168.0.1/24 dev wlan0 proto kernel scope link src 192.168.1.10
169.254.0.0/16 dev wlan0 scope link metric 1000
default via 192.168.1.1 dev wlan0
```

What is this 169.254.0.0 thing?
Is 192.168.0.1 correct?

Thx

---

### Post by PatchesTheCaveman on 2011-01-10
Not if you're using 192.168.1.x addresses, as indicated by your ifconfig output.

Are you using NetworkManager or wicd to configure your wireless connection?

---

### Post by Alessandro Allegri on 2011-01-11
> **PatchesTheCaveman said:**
> Not if you're using 192.168.1.x addresses, as indicated by your ifconfig output.

Are you using NetworkManager or wicd to configure your wireless connection?

I'm using wicd, but it has problems in verifying the ap, so I set a bash script that I run every time with 

-ifdown
-iwconfig ap
-iwconfig essid
-ifup

which is enough to make the wicd background connect.
So where do i change those ip's (I've never met them throughout weeks of wanderings!)

Thanks.

---

### Post by PatchesTheCaveman on 2011-01-11
Give ```
sudo ifconfig wlan0 *<your IP>*
``` a shot.  Also run the *route ip* command from earlier just in case.

And do you have WEP or WPA?  I need to know to make the above fix permanent and/or try another solution.

---

### Post by Alessandro Allegri on 2011-01-11
> **PatchesTheCaveman said:**
> Give ```
sudo ifconfig wlan0 *<your IP>*
``` a shot.

This has the effect that at least I'm able to ping the router. Any other ping does not even start:
```
eelsho@eelsho:~$ ping 8.8.8.8
connect: Network is unreachable
```

Then:
```
eelsho@eelsho:~$ ip route
192.168.1.0/24 dev wlan0 proto kernel scope link src 192.168.1.1

```

I guess what happened is that my netbook is now mr.192.168.1.1 and of course it can selfping, but the router, who is also 192.168.1.1 won't recognise it, far less let it pass through.

> And do you have WEP or WPA?  I need to know to make the above fix permanent and/or try another solution.
I have wep with passphrase. I know it's not the best, but I'm already without one computer, if I switch now to wpa I wouldn't like to get rid of the others' connectivity too. :-)

---

### Post by PatchesTheCaveman on 2011-01-11
Sorry I meant for you to run:
```
sudo ip route add default via <router IP address> dev wlan0
```

I'm pretty sure you'll be able to ping the Internet after that.  You'll need to run that ifconfig line from post 30 too if you rebooted.

ETA:  If that fixes it, add the following to your /etc/network/interfaces to make the command line changes persist through reboots:
```
auto wlan0
iface wlan0 inet static
  wireless-essid *<network name>*
  wireless-key *<WEP key>*
  address *<computer IP>*
  netmask 255.255.255.0
  gateway *<router IP>*
```

You'll still be able to use wicd to manage your connection and connect to a different network if needed but it will default back to that one when you reboot.  But it least it will work!  :-D

---

### Post by Alessandro Allegri on 2011-01-11
Reboot, wicd with auto-connect.
Wicd tells me "disconnected" upon restart.
```

eelsho@eelsho:~$ ip route
192.168.1.0/24 dev wlan0 proto kernel scope link src 192.168.1.10
169.254.0.0/16 dev wlan0 scope link metric 1000
default via 192.168.1.1 dev wlan0 metric 100
```
Sudo-run the connect.sh script (ifdown wlan0, iwconfig wlan0 essid G604TWIRELESS, ifupwlan0). Once, nothing happens.
Open wicd, it scans the networks and finds the router. Make it connect. It hangs ad ap verification. Disconnect and close it.
Run again the script: apparently it connects.
Ip route is the same.

> **PatchesTheCaveman said:**
> Sorry I meant for you to run:
```
sudo ip route add default via <router IP address> dev wlan0
```

does simply add another identical line to the ip route (without the metric 100)



> I'm pretty sure you'll be able to ping the Internet after that.
I wish it was so... :-( No pinging of the router (Destination Host Unreachable), nor of the Internet (same message).

>  ETA:  If that fixes it, add the following to your /etc/network/interfaces to make the command line changes persist through reboots:
```
auto wlan0
iface wlan0 inet static
wireless-essid *<network name>*
wireless-key *<WEP key>*
address *<computer IP>*
netmask 255.255.255.0
gateway *<router IP>*
```

You'll still be able to use wicd to manage your connection and connect to a different network if needed but it will default back to that one when you reboot.  But it least it will work!  :-D

My /etc/network/interfaces looks almost identical (no wireless-essid or wireless-key, which give a "SET failed on device wlan0 ; Invalid argument" message, but simply essid and key) already...

Gosh...

---

### Post by PatchesTheCaveman on 2011-01-11
Okay, on the flip side, try erasing all references and config info for wlan0 and configuring everything with wicd.

If it's still broken then, run another full suite of diagnostics:
```
sudo iwconfig
ifconfig -a
ip route
cat /etc/resolv.conf
arp -vn
dmesg | grep -i ath
```

If *ifconfig* shows the right IP address and *ip route* shows the right default gateway, check to see if if your router is listed in the output from *arp*.  

If it's not, try manually adding it.  You'll need to figure out your router's LAN MAC address (not it's WAN address), which you can find sometimes on the bottom of it, or in the documentation, or in the router configuration.  You can also run *arp -vn* on another computer that runs Linux, Mac, or other Unix-like OS to find it.  Then, run this command:
```
sudo arp -s *<router IP>* *<MAC>*
```

If it's still not working, copy/paste all that info into a reply and we'll take another look at it.  My gut tells me we're missing something silly.  :-/

---

### Post by Alessandro Allegri on 2011-01-11
Ok I might have found something:
the router's mac address is: 00:0f:3d:b2:aa:e3 (found using arp on the other linux machine and vigorously confirmed by the router himself).
Now in /etc/wicd/wireless-settings.conf there is a different address: 00:0f:3d:b2:aa:e4. But whenever I try editing this file, wicd will change it back to the wrong mac. (No wonder the ap verification fails).
How to address this? What causes the undoing of my changes?

---

### Post by PatchesTheCaveman on 2011-01-11
Your local configuration might be clobbering it.  Check the connection settings in *wicd-client*.

---

### Post by Alessandro Allegri on 2011-01-12
> **PatchesTheCaveman said:**
> Your local configuration might be clobbering it.  Check the connection settings in *wicd-client*.

I couldn't find wicd-client, so it wasn't installed.
I then apt-get purged wicd wicd-daemon wicd-gtk and reinstalled them together with wicd-cli.
It still tries to connect to the wrong ap.
If I ifdown wlan0 there is this message:
> RTNETLINK answers: No such process
SIOCDELRT: No such process

Then I can iwconfig essid and ap and ifup wlan0. The consequent iwconfig shows the right essid but the ap is Not-Associated, while arp -vn shows the router with "incomplete" HWaddress. I can manually set it to the right thing but iwconfig wouldn't associate the ap.

Wicd is of no greater help here, as I don't know how to make it change its wrong hw address...

As I remember, in Network Manager there was the possibility to explicitly declare the mac address. I could uninstall (and purge again) wicd and reinstall nm... is it worth the try?

---

### Post by PatchesTheCaveman on 2011-01-12
Upon further investigation I have discovered that my router has three separate MAC addresses.  One for the WAN port, one for the LAN, and one for the WLAN.  I think *arp* is showing the LAN one while *wicd* is getting the WLAN.  So that part might actually be working properly.

I went back over the thread and noticed the wired connection wasn't working before.  Is that still the case?

---

### Post by Alessandro Allegri on 2011-01-12
> **PatchesTheCaveman said:**
> Upon further investigation I have discovered that my router has three separate MAC addresses.  One for the WAN port, one for the LAN, and one for the WLAN.  I think *arp* is showing the LAN one while *wicd* is getting the WLAN.  So that part might actually be working properly.

I went back over the thread and noticed the wired connection wasn't working before.  Is that still the case?

Haven't tried it in a while, but last time I checked it wasn't working.

As for the mac address, shouldn't two machines connected wireless to the same router arp the same mac?

---

### Post by Alessandro Allegri on 2011-01-12
No, I see the point: my malfunctional netbook was NOT arping any mac address until *I gave* him the one the router was showing and the other notebook was arping.

---

### Post by PatchesTheCaveman on 2011-01-12
Apparently not.
```
patches@paleolithic:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"CaveNet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:EC:C8:DA   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-32 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:119  Rx invalid frag:0
          Tx excessive retries:37415  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

teredo    no wireless extensions.

patches@paleolithic:~$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:18:39:ec:c8:d8   C                     eth1
```

But if your wired connection also doesn't work, then the wireless definitely isn't the issue.  Something screwy is going on somewhere in your TCP/IP stack.

Can you ping other machines on the network?  If not, try adding one of their MAC addresses via *arp*.  Does it work then?

---

### Post by Alessandro Allegri on 2011-01-12
1) iwconfig on both my linux machines gives the same mac for the router, which is different from the one given by arp and by the router specifics. So I guess that is settled.

2) No pinging of other machines on the net. But after pinging them, arp -vn shows them all with incomplete hwaddresses.

3) Adding one of them gets the arp -vn correctly show the mac address for it, still no pinging, but this time it doesn't say "Destination host unreachable", but simply no answer until I break the command (or maybe I was too impatient, waited about 30 secs).

4) My arp flags are not "C" but "CM".

---

### Post by PatchesTheCaveman on 2011-01-12
So your card is associating with the router, but not actually communicating with it at all.  Weird.

Can you boot from a live CD/DVD/USB?  That way we can see if it's a configuration issue or if something's up with a driver somewhere.

I believe the 'M' indicates a manual addition.

---

### Post by Alessandro Allegri on 2011-01-12
Strangely enough, I have a startup usb key (the one I used to install ubuntu in the first place), but the netbook won't boot from it anymore.
I also have a live cd working properly.
Maybe I should reboot from there? Or backup and reinstall?

---

### Post by PatchesTheCaveman on 2011-01-12
> I also have a live cd working properly.
Does the LiveCD work properly or the network?

If it was the former, try it from the LiveCD first and see if it works.

If it does, there are a few more things we can try on the existing installation to try and get it running.  Of course, if your tired of this nonsense and just want to reinstall, I wouldn't blame you one bit!  (Reinstalling is *so* Windows though.  :-P )

---

### Post by Alessandro Allegri on 2011-01-12
Nope, not working from live CD either.
At this point I wonder if resintalling would make any difference at all.
I just can't imagine what happened, since it was working perfectly...

---

### Post by PatchesTheCaveman on 2011-01-12
If it doesn't work from the LiveCD, reinstalling is pointless.

If you can, download Ubuntu 10.10 Maverick Meerkat and burn a LiveCD or create a LiveUSB stick and see if it works with that.  Maverick has an updated version of the Linux kernel that might fix your issue.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Alessandro Allegri on 2011-01-13
> **PatchesTheCaveman said:**
> If it doesn't work from the LiveCD, reinstalling is pointless.

If you can, download Ubuntu 10.10 Maverick Meerkat and burn a LiveCD or create a LiveUSB stick and see if it works with that.  Maverick has an updated version of the Linux kernel that might fix your issue.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Yup, the Live Meerkat works.
I'll backup and try installing it, with fingers crossed. So what was it? The driver? The kernel? Both fighting for their minute of glory?

---

### Post by PatchesTheCaveman on 2011-01-13
> what was it? The driver? The kernel?
[Yes.](http://tvtropes.org/pmwiki/pmwiki.php/Main/ptitle3zaap0y7ym6o)  Driver's are deeply integrated into the Linux kernel so it's hard to say what was going on where.  

I'm glad we finally found a way to fix it, though.  This is the first instance I'm aware of in which Maverick works better than Lucid.  Most posters here seem to believe the opposite.

---

### Post by Alessandro Allegri on 2011-01-14
Lol. Ok, well I must say I'm finding 10.10 a bit puzzling. For example I don't know how to mount remote folders shared on my other linux machine, but filezilla is working so I have time to find out.
Thanks for your time & help. Really appreciated.

---

### Post by Alessandro Allegri on 2011-01-14
Lol. Ok, well I must say I'm finding 10.10 a bit puzzling. For example I don't know how to mount remote folders shared on my other linux machine, but filezilla is working so I have time to find out.
Thanks for your time & help. Really appreciated.

---

### Post by PatchesTheCaveman on 2011-01-14
If you just want basic Nautilus mounting you can just go to Places > Connect to Server and mount any SFTP directory you can get with FileZilla.

If you want good old-fashioned command-line folder on the filesystem mounting, you can use *sshfs*:  [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

[CENTER]:guitar:[/CENTER]

You're very welcome.  Glad to hear everything's working now!

---

