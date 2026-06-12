---
title: "Wifi Guru Wanted."
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by meeki on 2006-02-08
Hi all, more wifi woes.

I've just upgraded to Breezy and have so far spent 2 days trying to get my wireless t'internet working. My IEEE802.11g adapter isn't recognised, so I've read the threads and followed the advice - it still isn't recognised.

I have tried the guide posted by Lambert today with some odd results.

I ran through the guide installing MadWifi-ng. At the end of the procedure I inserted the module and on creating the interface was indrmed that the device was not found. However, looking in system>admin>networking, ath0 wireless was there and active. I configured it and all seemed well, but then no internet. The connection to the router failed. After a reboot, ath0 had dissapeared??

I uninstalled madwifi and ran through the process again - no wireless connection.

I then tried running through using madwifi-old, with exactly the same results. I have posted the results from madwifi-old here, but like I say, they were identical for the -ng version.

Any help would be gratefully received.

Results from the make step


code:

ian@ubuntu:/usr/src/madwifi-old$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
[COLOR="Red"]sed: can't read SNAPSHOT: No such file or directory[/COLOR]
echo -n '#define SVNVERSION "' > svnversion.h

Blah Blah......

(export MODULEPATH=/lib/modules/2.6.12-10-386/net; /sbin/depmod -ae)
make -C ./tools  install || exit 1
make[1]: Entering directory `/usr/src/madwifi-old/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig; do \
        install $i /usr/local/bin/$i; \
        strip /usr/local/bin/$i; \
done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/usr/src/madwifi-old/tools'


insert and create

code:

ian@ubuntu:/usr/src/madwifi-old$ sudo modprobe ath_pci
ian@ubuntu:/usr/src/madwifi-old$ wlanconfig ath0 create wlandev wifi0 wlanmode sta
[COLOR="Red"]wlanconfig: ioctl: No such device[/COLOR]
ian@ubuntu:/usr/src/madwifi-old$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]

Absolutely any help appreciated.

---

### Post by meeki on 2006-02-08
By the way, trying to get the linux modules to pick my card up I get : FATAL: Could not open '/lib/modules/2.6.12-10-386/net/ath_pci.ko': No such file or directory

This is linux hell.

---

### Post by Lambert on 2006-02-08
The wlanconfig ath0 create...... command is only used for -ng so it won't work for -old (new features in -ng)

With -old all you should have to do is insert the module

```
sudo modprobe ath_pci
```

Then configure the interface ath0

You can do this from system-->Administration-->Networking for open or wep network configuration.

So with device inserted and ath_pci module loaded, run these commands. (assuming you're using dhcp for network settings)

```
sudo ifconfig ath0 up
sudo dhclient ath0

```

Then run these commands and post output here.

```

sudo lshw -C network
sudo iwconfig
sudo ifconfig
route -n

```

There's also a links in my signature, both which will lead you to a wirelesstroubleshooting guide. You can walk through those steps for help.

---

### Post by meeki on 2006-02-08
Lambert,

You are truly a leader of men. Simply one step too many, but all's well now.

Just one more question, how do I mark a post as resolved?

Many thanks, Ian.

---

### Post by Lambert on 2006-02-08
Don't believe there is a way to mark resolved except edit your first post and eidt the title box to show something like 

(solved)

By the way, no guru, just a user....Glad to see your problem was solved...

---

### Post by meeki on 2006-02-15
Welcome back to my hell.

Yesterday, this:

 *-network:0 UNCLAIMED
             description: Ethernet controller
             product: AR5212 802.11abg NIC
             vendor: Atheros Communications, Inc.
             physical id: 9
             bus info: pci@00:09.0e 
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:30010000-3001ffff irq:11

was my wireless connection.

Today it's nothing again!! The card was automatically picked up by Ubuntu after a fresh install of breezy (which surprised me in itself), but lo and behold a reboot later and it's gone again.

So, I know that that the card works because I was using it for eight hours yesterday. I know that Ubuntu has the drivers already because it detected and installed the card all by itself.

I can't keep manually installing this just to see the setup lost after each new start. Any ideas??

I'm thinking maybe another distro might be worth a look, which is a shame because other than wireless probs I really like the look, feel and functionality of Ubuntu.

Cheers all, Ian.

---

### Post by meeki on 2006-02-15
It just keeps getting better, the bloody card appears and disappears as and when it feels like it. There seems to be a stability problem here :-k 

What hope Dapper??:rolleyes:

---

### Post by Lambert on 2006-02-15
Each time you reboot or unplug/replug your card look at the output of 

```
 dmesg 
```


See if there is any output there about the card. I'm wondering if there is a pci bridge problem as some bridges do cause problems with atheros devices.

I'm curious if you're getting this error

```

unable to attach hardware: Hardware didn&#8217;t respond as expected, (HAL status 3)"

```

If so there is a work around

> 
PCI bridges exist which pose difficulties to Atheros cards (and maybe other hardware too). To get your card working, you first have to find your PCI bridge's PCI ID with lspci. Then you have to set the SUBORDINATE_BUS option for this PCI ID with the setpci tool. 

For example: 

# lspci | grep -i "pci bridge"
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge
# setpci -s 0:1e.0 SUBORDINATE_BUS=0A

If you have problems with your Cardbus card instead, you should try with the PCI ID of your PCI to Cardbus controller, which you can find by running lspci | grep -i "cardbus bridge".


But this may not be your problem, it may lie elsewhere. POst what ever looks relevant from dmesg.

There is also a way to turn on debugging for the driver to dump more output into the logs. I'll have to look that one up and come back.

---

### Post by meeki on 2006-02-15
Hi Lambert, 

Unfortunately it's not a HAL status 3 or 13. 

At the moment I can't even post any output because it's identifying the wifi card with every startup now. Why???

There's obviously some real issues around the Atheros drivers though. Problems with Atheros and wifi seem to be prevelent on these boards, as well as others that I've looked at. The worst of it is, now that the acrd is being picked up with the startup, other problems are occuring to do with configuration:

The card is never active after a restart, so obviously manual intervention is required to get online (Ball ache #1).

Anything to do with wireless and config is all but stopped from running (Ball ache #2). Take a look at wifi manager? 5 minutes to load.
Fire up Firefox? Another 5 minutes.
Look at the //interfaces file? Yep 5(+) minutes.

Madness? I think so. Buggy? Probably. Stable? Hehe.

I wouldn't waste any of your time on this one Lambert mate. I have internet access via ethernet so am not lost, it's just a pain in the arse. I'll look into this as and when. Cheers anyway though.

Ian.

---

### Post by Lambert on 2006-02-15
Madwifi is still a beta driver so yes it could have problems. 

Wireless in linux is very problematic with just about any driver in various cases.

I had many problems with linux and wireless for a while. When I bought my atheros based card 5 months ago, I haven't had a single problem since. I just bought a second one and no problems again. 

It is probably rare for someone to start a thread praising something, most are for technical support with a problem. So you will find the majority of posts stating problems with devices/chipsets. 

All I can say is find what works for you and as much patience as possible with linux. It's come a long way and there are still some parts like wireless that needs attention. Look at WPA, it's been around for a couple years and still no graphical management of wpa encrypted connections. Network manager has just got there with a patch but it's rare and takes somebody with a little skill to get it working.

---

