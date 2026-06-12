---
title: "Help! Replaced NIC and new NIC not recognized"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by kalahari875 on 2006-07-05
I'm using Kubuntu 6.06 as a firewall/router in addition to other duties. My eth0 external NIC died last night; it was showing enabled, but was not getting an IP address, and I confirmed via a spare PC that the cable modem is fine. eth1 (internal NIC) was working fine.

I swapped out my dead eth0 NIC for the NIC in the spare PC. (I had used that NIC to confirm that the internet connection/cable modem were working fine, so I know it's good.) However, when I boot Kubuntu, systemsettings only sees one NIC and is calling it eth2. No mention of eth0 or eth1. Additionally, it will not enable this NIC. When I issue ifconfig, all I see is lo. ](*,) 

I know the NIC is good and the hardware is good, because I am writing this post via Knoppix running on the same hardware communicating through the new eth0 NIC. I've replaced NICs before in other distributions without issue. Is there something special I need to do to fix my networking?

Thanks!

---

### Post by Dr. Nick on 2006-07-06
I would run lsmod while in knoppix and see which module it is using for the card that will not work in kubuntu, then restart into kubuntu and see if that module is loaded using lmsod.

Also take a look at the file /etc/network/interfaces

That file controls the names of the ethernet cards

---

### Post by kalahari875 on 2006-07-06
OK... I've now gotten a Kubuntu 6.06 live CD and confirmed that when it boots on the same hardware as the installed Kubuntu 6.06, it sees both eth0 and eth1 just fine, enables eth0 with DHCP and provides a connection. (I also replaced the eth1 NIC because the live CD boot was not seeing it originally.) However, when I boot the machine now, I have only two NICs: eth2 and eth3 (see ifconfig output: [ATTACH]12323[/ATTACH]). This in spite of the contents of /etc/network/interfaces  ([ATTACH]12321[/ATTACH]) specifying only eth0 and eth1. In addition, it takes forever to enable eth2 (external), and when it does, I get no IP address; this is the problem that occurred to my original eth0 NIC that I replaced.

The NICs seem to be using the same module under both Knoppix and Kubuntu, 3C59X (see lsmod output from Knoppix: [ATTACH]12322[/ATTACH] and from Kubuntu: [ATTACH]12324[/ATTACH]). I know the Kubuntu module should be good enough because the live CD would use the same thing as the HD-installed one, correct?

HELP!!! 

Any other suggestions/things I can look into?

Is there some sort of repair/reinstallation that won't destroy all my customizations and added apps on the HD-installed version? (Is it time to look into that?)

Desparately yours,

kalahari875

---

### Post by Dr. Nick on 2006-07-07
Similar problems going on here
[http://ubuntuforums.org/showthread.php?t=197438&page=3&highlight=network+cards](http://ubuntuforums.org/showthread.php?t=197438&page=3&highlight=network+cards)

I have never been able to have ubuntu give me 2 ips on 2 different interfaces myself (1 wired, 1 wireless) I to have done the 2 wired cards for a router on other distributions a long time back.

Just to clarify, Everything works properly on the kubuntu live cd? All cards detected in a timely manner, ip's assigned, etc?

---

### Post by kalahari875 on 2006-07-07
> **Dr. Nick said:**
> I have never been able to have ubuntu give me 2 ips on 2 different interfaces myself (1 wired, 1 wireless) I to have done the 2 wired cards for a router on other distributions a long time back.

Just to clarify, I'm not trying to get DHCP-assigned IPs on both cards. In my case, eth0 is attached to the cable modem and has a DHCP-assigned IP. eth1 has a static IP and is the gateway for the local network. I am running dhcp3-server bound to eth1.

> **Dr. Nick said:**
> Just to clarify, Everything works properly on the kubuntu live cd? All cards detected in a timely manner, ip's assigned, etc?

Yes. The live CD gets an IP from the ISP for eth0 and doesn't do anything for eth1, but it is properly detected. I can assign a static IP to eth1 as I have on the HD-installed distro.

---

### Post by Dr. Nick on 2006-07-07
I have a idea that may work, Their is a program called etherconf that will walk you through the process of configuring your ethernet cards, It will overwrite your previous configuration if you let it.

Only problem is that it is not intalled by default, It is in the universe repository. It should be installable from adept in kubuntu if you have extra repos enabled. 
And it apperas that you can not get online in kubuntu if your eth2 isnt getting an ip. It may be necessary to use just one network card that you know should work and remove the others from your system temporarily so that you can get online to install.

Also you could download etherconf and its dependences from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and try to install it manually

Only othr thing I could think to do is boot off the live cd and save/copy all the configuration files that you see related to networking (/etc/network/interfaces) somewhere then overwrite the hd installed versions

Sorry i cant be of more help, them types of problems get frustrating since you know it should work but deosnt.

---

### Post by kalahari875 on 2006-07-08
First of all, thanks for all your help. Keep reading...

> **Dr. Nick said:**
> I have a idea that may work, Their is a program called etherconf that will walk you through the process of configuring your ethernet cards, It will overwrite your previous configuration if you let it.

Unfortunately I can't install etherconf. It depends on dhcp-client, and I have dhcp3-client installed; these versions conflict.

> **Dr. Nick said:**
> Only othr thing I could think to do is boot off the live cd and save/copy all the configuration files that you see related to networking (/etc/network/interfaces) somewhere then overwrite the hd installed versions

The thing is, the /etc/network/interfaces contains the correct definitions. There is no mention of eth2 or eth3 in this file. However, when booting from the HD, Kubuntu systemsettings steadfastly displays the cards as eth2 and eth3. Where in the $@%#@!$# is it getting this? It isn't coming from /etc/network/interfaces.

I tried removing both network cards and commented out everything in /etc/network/interfaces except for lo. I rebooted; systemsettings showed no network interfaces. Then I put one of them back. When I rebooted, systemsettings detected it as eth2.

The live CD continues to show the cards as eth0 and eth1 when booted on the same hardware.

Other than /etc/network/interfaces, where can networking be defined? It MUST be pulling it from somewhere else. Are there any other utilities I can try other than etherconf that might not conflict with existing packages?

Thanks so much.

---

### Post by Dr. Nick on 2006-07-08
Where did you see they conflict?

I have etherconf and dhcp3-client installed, but dont have dhcp-client installed

I am not sure where it would be getting the eth2 and eth3 from...

If you get etherconf installed tun it by this

** sudo dpkg-reconfigure etherconf**

---

### Post by kalahari875 on 2006-07-08
> **Dr. Nick said:**
> Where did you see they conflict?

I have etherconf and dhcp3-client installed, but dont have dhcp-client installed

I am not sure where it would be getting the eth2 and eth3 from...

If you get etherconf installed tun it by this

** sudo dpkg-reconfigure etherconf**

Weird... I downloaded [etherconf from the dapper repository]("http://packages.ubuntu.com/dapper/net/etherconf") on packages.ubuntu.com as you suggested. When I went to install it, dpkg it told me it depended on dhcp-client and that I did not have dhcp-client installed. Reading the linked page more closely now, I see that it pretty clearly says it depends on dhcp-client.

dpkg tells me dhcp-client can't be installed because it conflicts with dhcp3-client.

So... what happens if I take the live CD and tell it to install over top of my existing Kubuntu 6.06 installation? Is it going to wipe out all the apps I've installed and customizations I've made (chrooting bind, etc.)?

---

### Post by Dr. Nick on 2006-07-08
Depending on your partitions it may not wipe it all out. If you have a seperate home partition you can choose not to format it. But chroots and other installed applications may not be in the home partition and thus would dissappear. 

You may look into saving a few config files if you decide to reinstall

EDIT

hmm weird that the packages.ubuntu says it need dhcp-client, i installed from synaptic without issue

---

### Post by kalahari875 on 2006-07-08
I ended up putting the original two NICs back in the Kubuntu machine. Low and behold, they are now showing up in systemsettings as being eth0 and eth1! No more eth2 and eth3.

There has to be some other location where Kubuntu hangs onto the network card device assignments--bound to the MAC address or something. If anyone can tell me how this mechanism works, I would greatly appreciate it. It turns out it was my stupid cable modem flaking out that prevented the lack of DHCP assignment that caused me to replace eth0 in the first place. But, if I ever do have to replace these NICs, it's going to hose my system.

HELP!!

---

### Post by Dr. Nick on 2006-07-08
Heh, That is something. I would have never thought it would do that. I hope you can find out where all the other network settings are stored because I have never seen that before, I always though /etc/network/interfaces is what ruled them all, thats all ive ever used.

It may be something built into kde, I dont have much of a idea as I dont get into kde as often

---

### Post by kalahari875 on 2006-07-09
I have a [thread going on linuxquestions.org]("http://www.linuxquestions.org/questions/showthread.php?p=2325892") trying to find out. Don't have the answer quite yet. Apparently other distributions have an /etc/modprobe.conf that defines the aliases. 

Anyone know where this is in Ubuntu/Kubuntu/Debian?

---

### Post by Frank-Hamersley on 2006-07-09
G'day Kalahari (et al),

I have encountered this issue with Dapper Server where I replaced the 2 (different) NIC's that were present during the install with a pair of identical NIC's from another manufacturer.

Ubuntu registered these new cards duly as eth2 and eth3 - I presume because "new" device drivers were loaded whilst the "old" device drivers still being loaded (and hanging on to eth0 and eth1).

I have managed to adjust for this temporarily by using the ip command to rename the devices, but this is lost at reboot.  I could put the statements in /etc/init.d/??? but they would have to be run quite early in the sequence and is not a very pretty solution IMO.  FWIW the command is something like ...

  # ip link set eth2 name eth0

The proper solution will be to wipe out the original device drivers from the loaded modules ... but I haven't worked out how to do this just yet.  No doubt it will unvolve lsmod and friends plus some hacking at /etc/modules or /etc/conf.modules

Prolly will start looking here ...

  [http://www.linuxplanet.com/linuxplanet/tutorials/1019/1/](http://www.linuxplanet.com/linuxplanet/tutorials/1019/1/)

Any suggestions/short cuts will be greatfully received otherwise will post here the outcome.

Cheers, Frank.

---

### Post by kalahari875 on 2006-07-10
> **Frank-Hamersley said:**
> I have encountered this issue with Dapper Server where I replaced the 2 (different) NIC's that were present during the install with a pair of identical NIC's from another manufacturer.

In my case, I replaced both eth0 (some SMC card) and eth1 (3Com 3C905B-TX) with two different 3C905B-TX or 3C905B-TXNM cards (I ended up trying several different 3Com cards of this permutation). It never gave up eth1 though even though the same module/driver should have handled the original card as its replacement. It almost seems like something is bound to the MAC address somewhere that needs to get cleared out.

---

### Post by michaelwayneharwood on 2006-08-11
You probably have your logical ethx interfaces mapped to specific mac addresses - try looking in /etc/iftab

---

### Post by kalahari875 on 2006-08-14
Thanks--that is the missing link. The file contains assignments for both eth0 and eth1: 

eth0 mac 00:e0:29:70:69:af
eth1 mac 00:50:04:c2:93:13

I assume the Kubuntu installer made these entries. In previous distributions of Linux I've used, the position of the PCI slot the card is in determined the ethx number (lowest PCI slot got eth0, I believe). 

If I remove these assignments from /etc/iftab, what happens?

---

### Post by Dan Luevano on 2006-08-17
I was just about to suggest editting /etc/iftab when I saw this last post. I don't know what happens when you delete the entries, because I just modified them myself, and it worked fine.

Anyway...I was hoping to pick your brain a little. See I'm having an unusual problem with 2 nic cards. Here's my problem...

eth0 is on a router with a static ip connected to the internet. eth1 is on a switch with a DHCP address connected to the local network. If I have eth1 enabled, I cannot ping eth0 (with the static IP address) from outside the network...it just goes dead. If I disable eth1 (with 'ifdown eth1') then it begins to send and receive requests, automatically.

I noticed that you've successfully used two nic cards...was there anything special you had to do to allow dual communications?  Also, if I run ethtool to look at the devices I get the same PHYADR for both nic cards...is this normal?

Any help you can provide would be greatly appreciated.  You can email me directly at [email]dan@twinvisioninc.com[/email]

Thanks!

Dan Luevano

---

### Post by kalahari875 on 2006-08-17
> **Dan Luevano said:**
> I noticed that you've successfully used two nic cards...was there anything special you had to do to allow dual communications?  Also, if I run ethtool to look at the devices I get the same PHYADR for both nic cards...is this normal?

My eth0 is DHCP assigned by my ISP, and eth1 is static (the gateway IP for my local network). I have dhcp3-server running on my eth1 interface. Since I am using the machine in part for internet connection sharing, I installed Firestarter and told it to enable internet connection sharing. This took care of my communication setup.

I ran ethrool on my NICs (see output: [ATTACH]14461[/ATTACH]) and they have different physical addresses. I'd suspect this is part, if not all, of your problem. I'm not familiar with the mechanism that assigns that physical address though.

---

### Post by Dan Luevano on 2006-08-18
Thanks to Kalahari875 for your reply.

I've had others tell me that their 2 nic cards have the same PHYADR, so I'm not so sure that's the problem...but it could be...I haven't found enough info to help me figure that one out.

BTW, I posted on another one of my Threads the following:

The saga continues....

I ran a [COLOR="Red"]route [/COLOR]command (see below) and noticed that I had two entries for "default", one for each nic card. When I removed the entry for the eth1 card, I was then able to ping eth0 (the static IP) from outside my local network.

**How does this get created and is it something I can force or prevent on a reboot?**

username@hostname:~# route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
72.54.107.144 * 255.255.255.248 U 0 0 0 eth0
10.0.10.0 * 255.255.255.0 U 0 0 0 eth1
default ddg.twinvisioni 0.0.0.0 UG 0 0 0 eth1
default 72.54.107.145 0.0.0.0 UG 0 0 0 eth0
username@hostname:~# route del default eth1


Once I did this...I was able to keep both nic cards up, without having to disable the local network card (eth1) just so that I can get the external network card (eth0) to work.

Still trying...

Dan

---

