---
title: "Strange phenomenon. Ubuntu-Windows dual boot network problem"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by r.osmanov on 2009-09-01
Hi, all.

I have just faced a strange thing. I've dual boot: Ubuntu & MS Windows XP.
Network is wired with static IP. Works through a couple of DNS.

Ubuntu is installed on the same hard drive as Windows, however separately from Windows on specially created partitions. And there were troubles with configuring Network Manager.
I had to remove it with *--purge* option and setup network myself from command line. 
Then I installed Network Manager just for indication if network is on.

The problem is: when I boot once on Windows, and then reboot on Ubuntu, my network stops working. All configuration is on it's place & network services are running. 
Furthermore, restarting, forcing reload, interface reconfiguration  etc. has no effect.
How do I solve it? Just 

[LIST]
[*]unplug cable
[*]reboot on Windows
[*]reboot on Ubuntu
[*]restart networking.
[/LIST]
And all works again. I made backups of all configs with *webmin* and then restored them with reloading network and much... Nothing fixed the problem. :confused:

 Any ideas?

---

### Post by eylisian on 2009-09-01
When you say networking is not working do you mean that the interface is not coming up, or is it coming up and you just can't get anywhere?

Need some more information before I'd hazard an opinion.

Regards.

---

### Post by r.osmanov on 2009-09-01
Thanks for reply.

The two interfaces, eth1 and lo are up. 
And that is strange. All the settings are the same as when it works.
I mind, I changed MAC address of eth1. However, it is right also.

At that time whether ping to any computer address in our LAN, or to a host in Web shows time out.

By the way, on my fresh install I had Network Manager showing network connection established.
But it was the same stuff. And it was the reason I removed the package.

---

### Post by mechdave on 2009-09-01
> The problem is: when I boot once on Windows, and then reboot on Ubuntu, my network stops working
What happens if you power off the pc between boots? Does that fix it... I have known of hardware that retains a Windows "setting" and stops it from working when you boot from Win to Ubuntu.

---

### Post by eylisian on 2009-09-01
eth1? How many interfaces are in that machine aside from lo (127.0.0.1)? If only one you might try changing eth1 to eth0 in /etc/network/interfaces

auto eth0
iface eth0 inet static
           address <addr-here>
           netmask <mask-here>
           broadcast <bcast-here>
           network <optional>
           gateway <gw-addr-here>

Then; sudo /etc/init.d/networking restart

Then check your /etc/resolv.conf file and make sure it has a good known name server in it.

Again, this is if the machine has one iface in it... Sure it could default to eth1 on a single iface machine, but chances are it's not.

---

### Post by eylisian on 2009-09-01
Oh, and before I started looking at hardware ROM holding onto winders settings, I'd clear the ARP/DNS caches on your network.

---

### Post by dmizer on 2009-09-01
If all you need is an activity display, then just install gnome-network-admin. Then you can manage your network via: System -> Administration -> Network

Uninstall network-manager. If you want a network indicator in your tray, right click on the toolbar and select: "add to panel" and "system monitor". Then you can edit the system monitor by right clicking on it and selecting preferences, then put a checkmark in networking. Uncheck "processor" if you like and then it will only show network activity.

---

### Post by r.osmanov on 2009-09-01
Power off does not fix it. 
I boot up on Windows, switch the PC off, boot on Ubuntu and have the trouble again.

---

### Post by r.osmanov on 2009-09-01
About eth0. I tried set up eth0 many times. I know, normally it should be eth0 as I have it at home.
But all failed. It says that device is not configured or something similar.

But it successfully lied on eth1. It works fine after all operations I mentioned.
Here is my network hardware:

```
$ lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth1
       version: 10
       serial: 00:1e:90:99:5d:78
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.86 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:78:65:82:ce:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```And the following is result of ifconfig command:

```
eth1      Link encap:Ethernet  HWaddr 00:1e:90:99:5d:78  
          inet addr:192.168.0.86  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe99:5d78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42118624 (42.1 MB)  TX bytes:11109490 (11.1 MB)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1524672 (1.5 MB)  TX bytes:1524672 (1.5 MB)
```

---

### Post by r.osmanov on 2009-09-01
> **dmizer said:**
> If all you need is an activity display, then just install gnome-network-admin. Then you can manage your network via: System -> Administration -> Network

Thanks for that. I'll try it on extra time. But Network Manager seems to work fine now. I reinstalled it then ;)
Although I know its behaveour is somewhat buggy, I think the problem is somewhere else.

---

### Post by eylisian on 2009-09-01
Interesting.

Maybe NetworkManager is still hassling you somehow (sounded messy =)

sudo update-rc.d NetworkManager remove

will take it out of startup if there is any doubt

sudo /etc/init.d/NetworkManager stop

and try restarting /etc/init.d/networking again.

---

### Post by r.osmanov on 2009-09-01
> **eylisian said:**
> ...
Maybe NetworkManager is still hassling you somehow (sounded messy =)

sudo update-rc.d NetworkManager remove

will take it out of startup if there is any doubt...
  

Okay, I have just began to suspect NetworkManager. Indeed, it is involved in startup... 
It really could misunderstand something. I feel, I have to follow your advice.

I'll try it now and then return to the thread.

Regards.

---

### Post by dmizer on 2009-09-01
Your problem is that you've configured your networking in both the CLI and in NetworkManager, but they do not cooperate. Since you only need basic static networking, I HIGHLY suggest simply uninstalling network manager as it's not giving you any advantage.

You can configure you network via the CLI, or you can install gnome-network-admin and configure it via GUI. This will give you a more robust network connection anyway.

---

### Post by eylisian on 2009-09-01
I was just wondering how the connection becomes more robust using a graphical tool as opposed to altering configuration files for a static setup?

I could see DHCP being more robust (graceful recovery from server hiccups etc...) but static?

Is there some secret that hasn't been announced in release notes I missed somewhere along the line cause I'll be all over that more robust stuff when I'm speaking w/ clients.

I do agree that NM and config file editing don't get along to well unless you plan to be sleazy (in a good way, I use NM for wireless connections and conf file for wired on my laptop) and that w/ static addrs NM isn't needed. Until it's disabled or removed from the system it'll keep popping up and hosing anything custom in config land.

Regards.

---

### Post by dmizer on 2009-09-01
> **eylisian said:**
> I was just wondering how the connection becomes more robust using a graphical tool as opposed to altering configuration files for a static setup?

I could see DHCP being more robust (graceful recovery from server hiccups etc...) but static?

CLI tools and the gnome-network-admin tool allow you to configure networking at the system level. This means you have networking all the time from boot to shutdown. NetworkManager only works at the user level. So you only have networking if you're logged in.

This is what I mean by more robust.

---

### Post by r.osmanov on 2009-09-02
Sorry for giving no reply for a long time. And thank you guys for helping me.

I removed NM and reconfigured network. All worked fine until I entered Windows to reboot immediately and loop at my problem state...
But Windows prepared a surprice -- along with it's "welcome" message on startup it poped me a warning:
"C:\Documents and Settings\All Users\Application Data\Symantec\SRTSP\StreTmp is damaged. Start CHKDSK"

and looped the annoying message at notification area. So I issued the CHKDSK command thinking of it causing noncritical errors, if any...
Results were unexpected:
```
C:\Documents and Settings\All Users\Application Data\Symantec\SRTSP>chkdsk
The type of the file system is NTFS.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Deleting an index entry from index $O of file 25.
Deleting index entry SrtETmp in index $I30 of file 16271.
Deleting index entry 4cab5ac587d2e519c7d35a0f74ffe143db5bd877.online.avatar in index $I30 of file 53588.
Deleting index entry 4cab5ac587d2e519c7d35a0f74ffe143db5bd877.original.avatar in index $I30 of file 53588.
Deleting index entry 4CAB5A~1.AVA in index $I30 of file 53588.
Deleting index entry 4CAB5A~2.AVA in index $I30 of file 53588.
Deleting index entry ce4a648c3916f19cec46e3af792e1bc066d09dfb.online.avatar in index $I30 of file 53588.
Deleting index entry ce4a648c3916f19cec46e3af792e1bc066d09dfb.original.avatar in index $I30 of file 53588.
Deleting index entry CE4A64~1.AVA in index $I30 of file 53588.
Deleting index entry CE4A64~2.AVA in index $I30 of file 53588.
Deleting index entry da7f0cbc26e01460a95903d5b58aa6e86ae9054d.online.avatar in index $I30 of file 53588.
Deleting index entry da7f0cbc26e01460a95903d5b58aa6e86ae9054d.original.avatar in index $I30 of file 53588.
Deleting index entry DA7F0C~1.AVA in index $I30 of file 53588.
Deleting index entry DA7F0C~2.AVA in index $I30 of file 53588.
Index verification completed.

Errors found.  CHKDSK cannot continue in read-only mode.
```

Then I decided to leave it on my free time and rebooted on Ubuntu. Anything could happen, but not this, my network denied. :(
I reloaded /etc/init.d/networking, added nameserver 127.0.0.1 to resolv.conf, used avahi daemon and dhcp. Nothing helped.

God, I really think of removing damned Windows at all and forever.

---

### Post by r.osmanov on 2009-09-02
The only reason I have Windows now is that my job concerned Web development. 
Hence, I should test sites on all popular browsers. Some browsers are not open-source
and even not supported in Linux, you know -- IE, Safari.

Wine not satisfied me. I tried it few months ago.

I think I should rather add a new hard drive to get rid of platform compatibility issues.

---

### Post by r.osmanov on 2009-09-02
Interesting. 
Hard reboot by pressing "reset" button on the PC box returns Ubuntu's network to life! :o
Wile "soft" reboot from Windows to Ubuntu causes the problem.

What does it mean? How could Windows save data about network so that Ubuntu fails to initialize it's own services? I cannot understand this.

---

### Post by dmizer on 2009-09-02
> **r.osmanov said:**
> Interesting. 
Hard reboot by pressing "reset" button on the PC box returns Ubuntu's network to life! :o
Wile "soft" reboot from Windows to Ubuntu causes the problem.

What does it mean? How could Windows save data about network so that Ubuntu fails to initialize it's own services? I cannot understand this.

Are you running Ubuntu in wubi? Please post the output of:
```
lshw -C network
```

Keep in mind that your problem may not even be related to your network configuration. It could just be a bad hard drive or some other problem.

---

### Post by r.osmanov on 2009-09-02
> **dmizer said:**
> Are you running Ubuntu in wubi? Please post the output of:
```
lshw -C network
```

Oh, no I'm not running wubi. I strive communicate with Windows as less, as possible.
The command shows
```
$ lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth1
       version: 10
       serial: 00:1e:90:99:5d:78
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.86 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:78:65:82:ce:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```> **dmizer said:**
> 
Keep in mind that your problem may not even be related to your network configuration. It could just be a bad hard drive or some other problem.

I ran *memtest86+* and *fsck*. No problems detected. Could [Acronis]("http://www.acronis.com") cause it? I installed it with Windows, and used for data backup and recovery.

---

### Post by peja_8 on 2009-10-31
I'm facing the same problem. Did you (or anybody else) find a solution to this?

Thank you.

---

