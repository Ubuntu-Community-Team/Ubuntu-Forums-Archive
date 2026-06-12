---
title: "Ubuntu 11.04 x64 slow internet connection, works fine in windows 7"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by daanjordaan on 2011-10-06
Hi guys,


I've installed Ubuntu x64 again, dual booting with Windows 7.
During the first install I got an error, so I wasn't surprised I had some weird issues afterwards.
I decided to run a clean install. This time I had no errors but it took ages. Normally Ubuntu installs really really quick.
This was probably due to the slow internet connection.

On Windows 7, the internet connection is as it should be. 
Ubuntu 11.04 x64 running within a virtualbox on this host also works fine.

But Ubuntu running natively has extremely slow download speeds.
Note that it is not confined to webbrowsing, the internet connection itself is extremely slow, about ten percent of what it should be.
I reccon a buggy driver, but I could not find anything on the webs.
Does anyone have a solution or the same problem?
I'm running it on an AMD Phenom 2 X4 965, with a Gigabyte GA970-UD3 motherboard.

Cheers,


Daan

edit: this Gigabyte motherboard uses a Realtek 8111E Lan chipset. Drivers can be found here: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

---

### Post by cool1007 on 2011-10-13
I'm having the same problem since I installed Natty over 2 weeks ago. I have Gigabyte motherboard with the same Realtek chip. I'm using drivers r8169.

Please help, it is really frustrating :/

---

### Post by praseodym on 2011-10-13
Hi,

does

```
lspci -nnk | grep -iA2 net
```

show the device ID **10ec:8168**? If yes, install the "right" driver r816[COLOR="Red"]8[/COLOR] according to this thread:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

Be aware that this driver does not yet build with kernel 3.x (Oneiric)

---

### Post by cool1007 on 2011-10-13
Yes, I already did switch to driver r8168 and thats what the command you requested to execute, shows.

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8168

I have already tried disabling ipv6 too and it didn't help. I'm running Ubuntu upgrade to version 11.10, but its doing it really slowly, at 20kbps. Speedtest runs report 1.2Mbps when my connection can go up to 3.5Mbps (I'm from Ecuador).

I'm getting really frustrated with this :(

---

### Post by praseodym on 2011-10-14
Install the package **ethtool** and show:

```
sudo ethtool eth0
ifconfig -a
route -n
cat /etc/resolv.conf
```

---

### Post by cool1007 on 2011-10-14
> **praseodym said:**
> Install the package **ethtool** and show:

```
sudo ethtool eth0
ifconfig -a
route -n
cat /etc/resolv.conf
```

sudo ethtool eth0 show:

```
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

```

ifconfig -a shows:

```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:26:ad:ab  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12339801 (12.3 MB)  TX bytes:3414232 (3.4 MB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3940 (3.9 KB)  TX bytes:3940 (3.9 KB)

```

route -n shows:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```


cat /etc/resolv.conf shows:

```
# Generated by NetworkManager
# domain cpe.satnet.net
# search cpe.satnet.net
# nameserver 192.168.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4

```

I tried changing my nameservers in the resolv.conf but it did not help :/

---

### Post by daanjordaan on 2011-10-14
Ok guys I found the weirdest solution on the net.

Are you guys running a dual boot?

---

### Post by cool1007 on 2011-10-14
> **daanjordaan said:**
> Ok guys I found the weirdest solution on the net.

Are you guys running a dual boot?
Yes, I am. Windows 7 x64, dual booting Ubuntu 11.10 in another drive.

---

### Post by daanjordaan on 2011-10-14
Okay dude,

I know this is going to sound weird, but I wan't you to try this:

Boot Windows 7.
Shut down.
Take out the power cable.
Wait 30 seconds.
Put it back in.
Start your pc.
Boot Ubuntu.
Check speedtest.net for your speed.

Get back to me.

---

### Post by praseodym on 2011-10-14
If this does not work, try:

```
sudo ethtool -s eth0 speed 100 autoneg off
sudo /etc/init.d/networking restart
```
Maybe taking anything off the current for 10 minutes helps to unload any firmware completely.

---

### Post by cool1007 on 2011-10-14
> **daanjordaan said:**
> Okay dude,

I know this is going to sound weird, but I wan't you to try this:

Boot Windows 7.
Shut down.
Take out the power cable.
Wait 30 seconds.
Put it back in.
Start your pc.
Boot Ubuntu.
Check speedtest.net for your speed.

Get back to me.

Pardon my skepticism, are you trying to figure out if the "wake on LAN" option in Windows is affecting Ubuntu?

Normally, during the night, I end up working on Windows, I shutdown the computer, and turn off the power source. The next morning, I boot up to Ubuntu and the slow speed persists. 

Does that have the same effect than your current exercise?

Thanks

---

### Post by cool1007 on 2011-10-14
> **praseodym said:**
> If this does not work, try:

```
sudo ethtool -s eth0 speed 100 autoneg off
sudo /etc/init.d/networking restart
```Maybe taking anything off the current for 10 minutes helps to unload any firmware completely.

Doing this, did not help. Speed Test still reports 1.2Mbps download speed tops. I'm going to try shutting down everything and unplugging power.

---

### Post by daanjordaan on 2011-10-14
> **cool1007 said:**
> Pardon my skepticism, are you trying to figure out if the "wake on LAN" option in Windows is affecting Ubuntu?

Normally, during the night, I end up working on Windows, I shutdown the computer, and turn off the power source. The next morning, I boot up to Ubuntu and the slow speed persists. 

Does that have the same effect than your current exercise?

Thanks

Yep, same thing, but i'm not trying to "figure out" anything.
I'm only telling you this method worked for me.
No additional driver. In fact I did this before I made a clean install again (the install could not download updates before ofcourse)
Just turned off the power for thirty seconds or so, did the trick

---

### Post by cool1007 on 2011-10-14
> **daanjordaan said:**
> Yep, same thing, but i'm not trying to "figure out" anything.
I'm only telling you this method worked for me.
No additional driver. In fact I did this before I made a clean install again (the install could not download updates before ofcourse)
Just turned off the power for thirty seconds or so, did the trick

Ok, I just did this. Shutdown, and power off everything. Still Speedtest.net reports 1.2Mbps download speed :(

---

### Post by daanjordaan on 2011-10-14
> **cool1007 said:**
> Ok, I just did this. Shutdown, and power off everything. Still Speedtest.net reports 1.2Mbps download speed :(

Bummer man, 
The method I tried before which worked as well, you've probably already found on the webs.
By just installing the r8168 driver?
Doesn't work with the new 3.0 kernel though.

Can't help you any further. 
For me it looked like Windows was messing with something. And this little trick fixed it.
Looks like it's a bit more complicated on your end.

Best of luck!

---

### Post by cool1007 on 2011-10-14
> **daanjordaan said:**
> Bummer man, 
The method I tried before which worked as well, you've probably already found on the webs.
By just installing the r8168 driver?
Doesn't work with the new 3.0 kernel though.

Can't help you any further. 
For me it looked like Windows was messing with something. And this little trick fixed it.
Looks like it's a bit more complicated on your end.

Best of luck!

Thanks friend. I am really running out of options, and its quite frustrating :(

---

### Post by daanjordaan on 2011-10-14
Last resort would be a cheap PCI Network Interface Card, meh:s
I thought about it when I couldn't get my box to work.
But come on, this is Ubuntu! Normally driver hassle free!

But if you're really out of options, buy a cheap Network Card.
It's a pretty incomplete list, but here's the support list of Ubuntu:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

Cheers,


Daan

---

### Post by varunendra on 2011-10-14
> **daanjordaan said:**
> 
By just installing the r8168 driver?
Doesn't work with the new 3.0 kernel though.
Didn't take a thorough look, so excuse me if I'm missing something important (will look at the details as soon as I get time), but if it is a kernel 3.x.x + r8168 compilation issue, then maybe this post can help: [http://ubuntuforums.org/showthread.php?p=11219508&postcount=10](http://ubuntuforums.org/showthread.php?p=11219508&postcount=10)
The post #6 on the same page was original solution for RTL8168B+r8169 problem, but for earlier kernels.

---

### Post by praseodym on 2011-10-15
Hi,
I recommend a mainlinekernel, namely 2.6.39-4-oneiric, Download here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/)

You need all 3 possible packages. Save them in "Downloads" and install via:

```
sudo dpkg -i ~/Downloads/linux-*.deb
```
Install additionally the tool startupmanager and choose 2.6.39 as default boot kernel. With this kernel the r8168 should work until the problem with kernel 3.x is solved.

---

### Post by cool1007 on 2011-10-15
Thanks for this, my friend. But i'm not sure booting with the r8168 driver would help either, since that was the first thing I tried before. This problem I have it for more than 3 weeks, since the first time I installed Natty.

Today I booted up directly into Ubuntu and my download speed seems to be faster, speedtest reports 2Mbps/2.35Mbps. My max speed goes around 3.5/4Mbps. Not perfect as in Windows, but an improvement. Could it be due to the fact that I did shutdown and turned on my comp to Ubuntu without ever going to Windows?

---

### Post by verymadpip on 2011-10-18
Hi guys.

I seem to be having the same problem.  Internet is veeeeeeeeeeery slow, sometimes failing to load pages completely.

I am dual booting  W7 x64 & Oneiric x64 on separate HDDs

I've noticed this is quite a big problem if I restart my machine & boot into Oneiric after gaming in Windows 7.  However, yesterday & today I've noticed that if I boot directly into Oneiric there seems to be far less of a problem.

It is indeed the r8169 driver that is in use on this box.
The output from the lspci suggested earlier command does look like it's telling me it'd prefer the r8168 driver.

I hope we get a solution to this soon.  I'm having more niggles with Ubuntu lately than I have in the past, & it's a bit scary :???:

---

### Post by cool1007 on 2011-10-18
> **verymadpip said:**
> Hi guys.

I seem to be having the same problem.  Internet is veeeeeeeeeeery slow, sometimes failing to load pages completely.

I am dual booting  W7 x64 & Oneiric x64 on separate HDDs

I've noticed this is quite a big problem if I restart my machine & boot into Oneiric after gaming in Windows 7.  However, yesterday & today I've noticed that if I boot directly into Oneiric there seems to be far less of a problem.

It is indeed the r8169 driver that is in use on this box.
The output from the lspci suggested earlier command does look like it's telling me it'd prefer the r8168 driver.

I hope we get a solution to this soon.  I'm having more niggles with Ubuntu lately than I have in the past, & it's a bit scary :???:
Hi verymadpip,

You described my exact problem and I still can't figure out how to fix it. It is rather frustrating and ironic that I have far more problems with Ubuntu than with Windows, xD

For someone new to Ubuntu like me, it is quite a bad impression.

Regards,

---

### Post by praseodym on 2011-10-18
Hello friends,

someone found a solution for kernel 3.0. I attached here

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

a "manipulated" driver package for Oneiric. Just copy/paste the according lines.

---

### Post by verymadpip on 2011-10-18
Hi cool1007, yeah, I'm having little niggly problems lately & it's just frustrating.  I was going to stick with 10.10 until 12.04 LTS came out, but for some reason I had no 3d graphics from my HD4870 after a hardware upgrade (mobo, CPU & RAM) & fresh install.  I gave 11.10 a whirl, & I must say I was really enjoying it until this reared its head.  I'm probably an average, or below user & if it's a kernel problem there's no point in even trying a different *buntu.

Thanks for the find praseodym.

Is that basically the same as this?:

[http://russell.ballestrini.net/r8168-driver-issues-after-ubuntu-11-10-upgrade-kernel-linux-3-0/](http://russell.ballestrini.net/r8168-driver-issues-after-ubuntu-11-10-upgrade-kernel-linux-3-0/)
[http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora](http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora)

From what I can tell the file edit happens first & then the rest.
Am I anywhere near being on the right lines here?

At the moment I have a choice between internet & no eye candy, by going back to 10.10, or prettiness & lousy internet with 11.10.  (11.04 is simply NOT an option for me TBH).  It  seems that I can't have both whichever version I opt for.  That is unless I go ahead with the driver fiddling & like I say I'm a very average user.  I don't do much hacking & I don't want to foul everyhting up completely.

If a knowledgable soul could clarify this a little I'd be willing to give it a go.

---

### Post by praseodym on 2011-10-18
Its the "last" of those installation instructions. The driver package is "manipulated" in that way.

---

### Post by verymadpip on 2011-10-19
praseodym, I do appreciate your effort to help me.  Unfortunately I'm really not familiar with these procedures.  for example I don't know what or where to find the Makefile that needs editing.  Or, do I NOT need to edit the Makefile, as it is provided already 'manipulated' in the link you have directed me to?

Perhaps I should start a new thread asking these questions, & for some more in depth guidance & instruction.

Sorry I'm so unknowledgeable, I've always liked Ubuntu because I don't have to deal with these things, although I fully appreciate the value of getting my hands dirty & undertaking tasks such as this.

Once again thanks for trying to help.

---

### Post by praseodym on 2011-10-19
You dont need to edit the "manipulated" file, its already done. Just copy/paste all of those lines one by one into the terminal.

---

### Post by verymadpip on 2011-10-19
Thanks again praseodym.

I'm going to try at the weekend when I have plenty of time so I can take it slowly .  Plus if it goes wrong I can do a reinstall if I have to.

I will let you know how things turn out.

---

### Post by verymadpip on 2011-10-20
Okay, at the moment this is all looking very good.
I've done the copy/paste from praseodym's link, restarted my rig & so far my wired connection is holding up well.
Thanks for being patient with a newbie who's afraid of the terminal.

I'd just say one thing, if the 'autogen' (it wasn't recognised for me) command doesn't work try 'autorun'

I also installed the packages 'build essential' & 'dkms'.  I don't know if I needed to, but I read in another thread that I might need them.

---

### Post by praseodym on 2011-10-20
Thanks for the reply. I corrected the link to "autorun"

---

### Post by phillgg on 2011-10-21
Previously I had v10, v11.04 installed (wired connection) slow download. Resolved it then had slow download after installing 11.10.
My solution is as follows
On upgrade, file /etc/dhcp/dhclient.conf is re-installed.  I believe this installs lines relevant to IPV6.  Edit this file to remove the lines
  dhcp6.domain-search, dhcp6.fqdn,
  dhcp6.name-servers, dhcp6.sntp-servers

Alternatively on upgrading don't accept changes to this file.  I allowed change but saved the old file and reinstalled it and slow downloads disappeared.

Don't thank me, I found this solution after hours of searching.

---

