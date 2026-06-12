---
title: "'Device not ready' state to all of my network adapters"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by Mesopotamia on 2012-05-01
Hi all,

Strangely that my 3 Quad port network adapters can be recognised when I write the 'ifconfig' command, but they all seem to be in 'Device not ready' state when I click on the networking tab at the toolbar (please see pictures below).

At the 'System Setting' they all seem to be recognised but again, their state doesn't change when I plug a network cable into them.

Could anybody advise if there is a solution to this problem? I'm a new Linux user (Have been using it for the past month).

The network adapters I have are the D-Link DFE-580TX.

From the Toolbar menu, it says that it's a 'Wired Network (D-Link DL 10050 Sundance Ethernet).

Thank you all.
[IMG]http://img.skitch.com/20120501-ms4rsd8fica2nxhw3pp6d7pwc4.png[/IMG]

[IMG]http://img.skitch.com/20120501-kqhdq9tw7tah65ushw6274ckbf.png[/IMG]

[IMG]http://img.skitch.com/20120501-myxmn93c2dkij44pm6w56cpc6s.png[/IMG]

---

### Post by Mesopotamia on 2012-05-01
Anybody? :)

---

### Post by Mesopotamia on 2012-05-01
Just to complement my post above, the cards work fine on the Ubuntu 11.10 but not the 12.04.

Could you guys help?

---

### Post by Mesopotamia on 2012-05-02
That many viewers and nobody could help me where to start looking :popcorn:

Today's bump..

---

### Post by Mesopotamia on 2012-05-03
Anybody ? :confused:

---

### Post by Mesopotamia on 2012-05-10
Bump.

---

### Post by Mesopotamia on 2012-05-18
Bump.

---

### Post by dpm41 on 2012-05-21
I had a similar problem with a D-link DFE-550TX NIC.  Network Manager reported a "Device not Ready" regardless if a ran the Live CD  or installed the alternate version of Ubuntu 12.04 (Regular CD install crashed with the error: "The installer encountered an unrecoverable error").  IFCONFIG showed network device with no apparent IPV4 addresses and LSPCI showed my NIC using the Sundance driver.

What worked for me was to either disable or uninstall the Network Manager and configure my network setting in the /etc/network/interfaces file.  Uninstalling Network Manager did the trick, but it also caused system error messages to pop up every once in a while.  The second time I tried just disabling it and haven't had a problem yet.

There are other posts that step through disabling Network Manager and setting up network devices in the interfaces file.  If you want me to step through what worked for me, Let me know ...

---

### Post by Mesopotamia on 2012-05-31
> **dpm41 said:**
> I had a similar problem with a D-link DFE-550TX NIC.  Network Manager reported a "Device not Ready" regardless if a ran the Live CD  or installed the alternate version of Ubuntu 12.04 (Regular CD install crashed with the error: "The installer encountered an unrecoverable error").  IFCONFIG showed network device with no apparent IPV4 addresses and LSPCI showed my NIC using the Sundance driver.

What worked for me was to either disable or uninstall the Network Manager and configure my network setting in the /etc/network/interfaces file.  Uninstalling Network Manager did the trick, but it also caused system error messages to pop up every once in a while.  The second time I tried just disabling it and haven't had a problem yet.

There are other posts that step through disabling Network Manager and setting up network devices in the interfaces file.  If you want me to step through what worked for me, Let me know ...

Thanks for that. I set up my account to send me an email once someone replies, but it never did!

I will try and install 12.04 during the weekend and see if disabling or uninstalling Network Manager would help. 

Thanks again mate :)

---

### Post by Mesopotamia on 2012-06-03
> **dpm41 said:**
> I had a similar problem with a D-link DFE-550TX NIC.  Network Manager reported a "Device not Ready" regardless if a ran the Live CD  or installed the alternate version of Ubuntu 12.04 (Regular CD install crashed with the error: "The installer encountered an unrecoverable error").  IFCONFIG showed network device with no apparent IPV4 addresses and LSPCI showed my NIC using the Sundance driver.

What worked for me was to either disable or uninstall the Network Manager and configure my network setting in the /etc/network/interfaces file.  Uninstalling Network Manager did the trick, but it also caused system error messages to pop up every once in a while.  The second time I tried just disabling it and haven't had a problem yet.

There are other posts that step through disabling Network Manager and setting up network devices in the interfaces file.  If you want me to step through what worked for me, Let me know ...

I've got some good and bad news here.

I finally installed 12.04 again and the 'device not ready' remained unchanged.

Once I typed the following command, NetworkManager was able to actually identify all three NIC:

```
sudo killall -9 NetworkManager
```

I'm not too sure what have been causing this problem, but from what I could see is that the Network Manager MAY have been loaded before the kernel identifies the NIC!

I'm not an expert, but it looks like killing the application AFTER booting the OS has fixed the issue.

Anybody care to clarify why this is happening? Is there a permanent solution given that the NIC work fine with 11.10?

Thanks

---

### Post by dpm41 on 2012-06-04
This is what I did to solve my networking issue ...

1.  Left click on Network Manager icon (probably looks like a quarter circle) and click on edit connections.
2.  Delete Wired Connection 1 or anything else in the wired portion of network connections.
3.  Let's start by modifying NetworkManager.conf

```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```4.  Under the [ifupdown] category, change managed=false to managed=true
5.  Save NetworkManager.conf file
6.  Open the network interfaces file

```
sudo gedit /etc/network/interfaces
```7.  What worked for me was to add two additional lines:
auto eth0
iface eth0 inet dhcp

Since you have more than one NIC, you'd have to setup each and every eth0 - 12.  I've configured it to receive an ip address from my router.  If you wanted to assign a static ip address to each eth#, I'd recommend looking up interfaces file examples.

8.  Save network interfaces file.
9. Restart computer

```
sudo shutdown -r 0
```If everything goes well, all of your NICs should be connected without having to type anything in each time you boot up the computer.  

What's interesting is that early on after applying my little fix, Network Manager showed the quarter circle and System Settings | Network reported that my network cable was unplugged even though I didn't have any problems connecting to the internet or pinging my other computers.  

After a few recent Ubuntu updates, I noticed that the quarter circle changed to the up/down arrows and the System Settings | Network reported that I now have a wired connection.  I thought, "Great ... they fixed the problems with Network Manager" so I undid all of the things I mentioned above.  No dice.  I changed it back to the way I had it and it's working again.

I believe the problem has something to do with the sundance driver behaving badly with Network Manager.  Just a guess really since I don't profess to be an Ubuntu expert.  Has the Sundance driver undergone any changes since Ubuntu 11 or maybe needs some changes to work with 12.04?

As far as the boot order of Network Manager, supposedly it loads after the desktop loads up.  I would think that the kernal drivers would've already been loaded before Network Manager starts.

Thanks for pointing out the killall command.  Coming from a Windows and Mac background, still learning the Ubuntu / linux ropes.

---

### Post by Mesopotamia on 2012-06-07
Thanks mate.

I followed your steps and I confirm that all the 12 NICs work fine but not through NetworkManager.

Given that I only need one IP address for the main ethernet port (eth0), and the rest could have ANY value as I will be using them with GNS3 to connect virtual routers to real switches, I'm quite happy with the setup.

I ran into an issue accessing the internet, but this was fixed after I removed the gateway options from all other ethernet ports.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.10
gateway 10.0.0.1
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
dns-nameservers 10.0.0.1

auto eth1
iface eth1 inet static
address 10.1.1.1
#gateway 10.1.1.254
netmask 255.255.255.0


auto eth2
iface eth2 inet static
address 10.1.2.1
#gateway 10.1.2.254
netmask 255.255.255.0


auto eth3
iface eth3 inet static
address 10.1.3.1
#gateway 10.1.3.254
netmask 255.255.255.0



auto eth4
iface eth4 inet static
address 10.1.4.1
#gateway 10.1.4.254
netmask 255.255.255.0


auto eth5
iface eth5 inet static
address 10.1.5.1
#gateway 10.1.5.254
netmask 255.255.255.0


auto eth6
iface eth6 inet static
address 10.1.6.1
#gateway 10.1.6.254
netmask 255.255.255.0



auto eth7
iface eth7 inet static
address 10.1.7.1
#gateway 10.1.7.254
netmask 255.255.255.0


auto eth8
iface eth8 inet static
address 10.1.8.1
#gateway 10.1.8.254
netmask 255.255.255.0



auto eth9
iface eth9 inet static
address 10.1.9.1
#gateway 10.1.9.254
netmask 255.255.255.0



auto eth10
iface eth10 inet static
address 10.1.10.1
#gateway 10.1.10.254
netmask 255.255.255.0



auto eth11
iface eth11 inet static
address 10.1.11.1
#gateway 10.1.11.254
netmask 255.255.255.0


auto eth12
iface eth12 inet static
address 10.1.12.1
#gateway 10.1.12.254
netmask 255.255.255.0

```

---

### Post by joeblackis on 2012-08-31
> **Mesopotamia said:**
> I've got some good and bad news here.
 
I finally installed 12.04 again and the 'device not ready' remained unchanged.
 
Once I typed the following command, NetworkManager was able to actually identify all three NIC:
 
```
sudo killall -9 NetworkManager
```
 
I'm not too sure what have been causing this problem, but from what I could see is that the Network Manager MAY have been loaded before the kernel identifies the NIC!
 
I'm not an expert, but it looks like killing the application AFTER booting the OS has fixed the issue.
 
Anybody care to clarify why this is happening? Is there a permanent solution given that the NIC work fine with 11.10?
 
Thanks
 
 
After hours of googling for answers this line saved the day for me.
 
```
sudo killall -9 NetworkManager
```
 
I searched everywhere for everything possible and it turns out that it was the network manager that needed to be killed.

---

### Post by dpm41 on 2012-10-29
I wiped out 12.04 and installed 12.10.  Network Manager is working perfectly in regards to my D-Link NIC.  I've tried both static and dynamic IP addressing without any hiccups.
I'm not sure if the previous problem was due to a bug in the sundance driver or Network Manager, but it's working fine in 12.10. :)

---

### Post by Mesopotamia on 2012-10-31
> **dpm41 said:**
> I wiped out 12.04 and installed 12.10.  Network Manager is working perfectly in regards to my D-Link NIC.  I've tried both static and dynamic IP addressing without any hiccups.
I'm not sure if the previous problem was due to a bug in the sundance driver or Network Manager, but it's working fine in 12.10. :)

That's good to hear mate.

I've applied a lot of tweaks to m system so installing 12.10 is out of the equation at this stage.

Thanks for the feedback :)

---

### Post by khizer2 on 2013-08-14
> **Mesopotamia said:**
> Thanks mate.

I followed your steps and I confirm that all the 12 NICs work fine but not through NetworkManager.

Given that I only need one IP address for the main ethernet port (eth0), and the rest could have ANY value as I will be using them with GNS3 to connect virtual routers to real switches, I'm quite happy with the setup.

I ran into an issue accessing the internet, but this was fixed after I removed the gateway options from all other ethernet ports.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.10
gateway 10.0.0.1
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
dns-nameservers 10.0.0.1

auto eth1
iface eth1 inet static
address 10.1.1.1
#gateway 10.1.1.254
netmask 255.255.255.0


auto eth2
iface eth2 inet static
address 10.1.2.1
#gateway 10.1.2.254
netmask 255.255.255.0


auto eth3
iface eth3 inet static
address 10.1.3.1
#gateway 10.1.3.254
netmask 255.255.255.0



auto eth4
iface eth4 inet static
address 10.1.4.1
#gateway 10.1.4.254
netmask 255.255.255.0


auto eth5
iface eth5 inet static
address 10.1.5.1
#gateway 10.1.5.254
netmask 255.255.255.0


auto eth6
iface eth6 inet static
address 10.1.6.1
#gateway 10.1.6.254
netmask 255.255.255.0



auto eth7
iface eth7 inet static
address 10.1.7.1
#gateway 10.1.7.254
netmask 255.255.255.0


auto eth8
iface eth8 inet static
address 10.1.8.1
#gateway 10.1.8.254
netmask 255.255.255.0



auto eth9
iface eth9 inet static
address 10.1.9.1
#gateway 10.1.9.254
netmask 255.255.255.0



auto eth10
iface eth10 inet static
address 10.1.10.1
#gateway 10.1.10.254
netmask 255.255.255.0



auto eth11
iface eth11 inet static
address 10.1.11.1
#gateway 10.1.11.254
netmask 255.255.255.0


auto eth12
iface eth12 inet static
address 10.1.12.1
#gateway 10.1.12.254
netmask 255.255.255.0

```

Dear ,
I am facing the similar problem and I have spent three days but unable to resolve the issue. Can you please tell step by step how did you resolved the issue. My onboard Ethernet is eth2 which is dynamically getting IP address from my router for internet access. I am also using the same topology as you for CCIE RS and I also wanted to know why you have given IP Addresses to your interfaces as those 12 interfaces needed to be connected to switches!!! 
An urgent reply would be much appreciated.

---

### Post by khizer2 on 2013-08-14
Dear All,
I have tried myself the above methods but im unable to get my quad nics working. I have set network manager= false in the networkmanager config file and put all the entries in the /network/interfaces file.
1. What i tried is that I took a cable and connected my onboard nic card with with ports of  the quad nic one by one and the quad nic started responding. However when I again attached the cable with one of the quad nic port and my 3550 switch; the green lights doesnt come up.I have checked the switch and the ports there are not administratively down.
2. I remove the cable from quad nic and attach it to the onboard nic card (with other end connected to 3550) and it came up. I tested it with gns3 and i can able to see the switch in show cdp neighbor!! 
Can someone please explain what I am doing wrong!! its been 4 days and I cant make those quad nic work with my switches!!!

---

