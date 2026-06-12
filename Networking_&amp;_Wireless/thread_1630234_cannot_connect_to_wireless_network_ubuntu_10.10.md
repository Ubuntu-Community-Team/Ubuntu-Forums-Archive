---
title: "cannot connect to wireless network ubuntu 10.10"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by fight2survive on 2010-11-24
I am using ubuntu 10.10. downloaded it the day after it came out on my samsung n130 netbook and was having problems connecting to wireless networks. I visited these forums and saw this was a common problem, so i gave it a few weeks expecting that this would be fixed in a new kernel update...
so today i updated everything on my update manager but i am still having the same problems. i really need help with this because i do not have a working version of windows installed on this computer anymore and this is The only access to the internet i have at home.
please help!!!

---

### Post by Bucky Ball on 2010-11-24
Do you know what card it is using? Have you plugged an ethernet cable in, gotten online and got your updates? If not, good chance that will pick up the card and offer you the appropriate drivers and firmware.

Have you checked System->Administration->Additional Drivers? Anything?

Plug a cable in if you haven't already.

To find the card, open a terminal and:

```
lspci
```Down near the bottom you should find your network card. Copy and paste that section here or the whole output if you can't identify it.

---

### Post by Bucky Ball on 2010-11-24
Brief research indicates the wirless is a Realtek 8192. That should work out of the box so not sure what's happening. I see you have plugged in a cable already. Check additional drivers.

I know this sounds silly but ... there is not a button anywhere on the machine that switches the wireless off/on? Some machines have this.

Could you post the result of these TWO separate commands (don't enter them together, on after the other):

```
ifconfig

iwconfig
```My machine uses this:

```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. **RTL8191SEvB** Wireless LAN Controller (rev 10)
```You should be looking for a line like that in the output of 'lspci'. The part in bold is what we're after.

PS: With a recent release like Maverick you should probably update a little more often. :)

---

### Post by fight2survive on 2010-11-24
apparently i got: 
```
[B]02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
[/B]
```

---

### Post by fight2survive on 2010-11-24
and when i check for additional drivers i get
"no proprietary drivers are in use on this system"

---

### Post by Bucky Ball on 2010-11-24
Result of:

```
iwconfig
```... please.

What exact problem are you having? Trouble connecting to wireless networks but any one in particular? Are you roaming or trying to connect to your LAN (home network)? Static/Dynamic IP? Can't find APs (access points)?

Get specific. Sounds like there is no prob with the actual card if you can see the networks, just can't connect. :)

---

### Post by Neonii on 2010-11-25
Hi there!

I'm running ubuntu 10.10 with my Samsung NP-R522 and had the same problem as many else with my wireless network card not working.

**sudo lshw -C network** gave me:
```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: **RTL8192E Wireless LAN Controller**
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:a9:8c:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE driverversion=0015.1013.2010 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:f6000000-f6003fff

```

So, I found a solution from a guy who sent Intel an email regarding the issue. The original post can be found [_here_]("http://ubuntuforums.org/showthread.php?t=1239342&page=9"), though I'll post the letter here as well:

```
Dear Sir, 

Thanks for your email.

Please find the attached for latest RTL8192E 32bit and 64bit Linux driver which is the 
updated one different from the one you used.

Just kindly remind, please install by the below steps.

The following is the installing steps:
1. Change to the driver directory
2. sudo su
3. make
4. make install
5.reboot
6. ./wlan0up or ./wlan1up

Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).


If your OS is 64bit, maybe there is kernel self driver for RTL8192E, 
you should delete it first before install:

1) cd /lib/modules/2.6.3x.xx.xx/
2) find -name "r8192e_pci.ko"
3) delet all the r8192e_pci.ko
4) install our RTL8192E driver
5) reboot.

if there&#8217;s still any other problem, please let us know.

Thanks a lot

Regards,

Kidman
```

And the file is found here:  [http://www.box.net/shared/v1bpr94j8k](http://www.box.net/shared/v1bpr94j8k)

Hope it works for you people, it did for me.

---

### Post by buc1 on 2010-12-20
I am also having trouble getting my wireless card to work on maverick.  This is the first time i have used ubuntu and i am not exactly sure what i am doing. 

 *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1d:7e:f0:de:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.56+Linksys, A Division of Cisc latency=64 link=no multicast=yes wireless=IEEE 802.11g

---

### Post by Daouuu on 2010-12-20
I've been having a similar issues as well.  I travel a lot for work and I frequently cannot see the hotel wireless networks.  It's not that I can't connect, but they just don't show up.  These are not hidden networks either.  I know it's not a problem with my card because when I boot into XP they all show up and connect just fine.  Also I have no trouble with my home wireless or a number of other networks I connect to in my travels.  I really really dislike using windows, but I'm forced to until I can solve this issue.  In fact in writing this from XP right now :-x

---

### Post by Daouuu on 2010-12-22
Well I'm back in a hotel and once again I'm back to XP.  The network signal is weak in this room.  It will connect with Ubuntu if I stand in the right spot but it drops after a few minutes when I sit at the desk, even tho it is still recieving the signal.  Windows on the other hand will hold onto the connection all day despite being weak(one bar).

---

### Post by Daouuu on 2010-12-29
The part that annoys me the most is that I never had this problem on older versions running the same hardware.  I have no desire to return to Windows full time but maybe sticking to the LTS versions would cause fewer headaches.

---

### Post by PatchesTheCaveman on 2010-12-29
@Daouuu & @atif7865: Sorry you're having trouble with your wireless Internet and Ubuntu.  You might have different hardware than the original poster that could have a possible solution to these problems.  Please go to Applications > Accessories > Terminal, type the following in the black box that appears, and press Enter:
```
lspci -v
```

This will tell us what kind of wireless card you have and what driver its presently using.  There might be a better combination that could improve your performance.

Please copy and paste the output into a new post.  It gets confusing when we have to try and tackle too many different people's problems in one thread.

---

### Post by Daouuu on 2010-12-29
Here's what I have, I assume all you need is the info pertaining to the wireless network controller. 


02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fe0ff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-13-02-ff-ff-d0-4b-07
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

Sorry I posted this before I seen you wanted it in a new post.

---

### Post by Bucky Ball on 2010-12-29
> **Daouuu said:**
> The part that annoys me the most is that I never had this problem on older versions running the same hardware.  I have no desire to return to Windows full time but maybe sticking to the LTS versions would cause fewer headaches.

+1. Maverick has been out barely 2 months. 10.04 has been out since April. No brainer and one year extra support.

Shame on Ubuntu nothing. Try hassling Samsung or your wireless card manufacturer about writing appropriate, decent drivers for Linux so developers and users don't have to screw around for days, hours, weeks, months trying to make their hardware work. ;)

---

### Post by PatchesTheCaveman on 2010-12-29
One simple solution that could improve everyone in this thread's connections is installing the backported drivers from future versions of the Linux kernel.  Sometimes these drivers improve support for certain devices.

To install them, go to Applications > Accessories > Terminal and type the following in the black box that appears and press Enter:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

You might need to reboot to see an improvement.

---

### Post by Daouuu on 2010-12-29
Thanks, I'll give that a try.  Mine only acts up with the wireless in certain hotels, so I'll post back with the results.  It works fine here at home or with any other "home" wireless network.

---

### Post by PatchesTheCaveman on 2010-12-29
Sorry guys, I accidentally gave you the command to update your wired Ethernet drivers, not your wireless drivers.

The correct command is:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

I'll fix my original post too.

---

### Post by Bucky Ball on 2010-12-30
In that case, remove the wrong backport people. You might wind up with more probs than you started with unrelated to this issue.

---

### Post by irenioskamoska on 2011-03-01
Hello,
I´m really new with triying ubuntu, or any linux for that matter, and i´m triying to connect to the internet.
I followed what has been said here and at the point where i put the command to update the wireless drivers ; 
the answer is: 
sudo: apt/get: command not found

and for the update the ethernet it said that couldn´t find the package

in the part that says NETWORK: DISABLED

how do i solve the connection problem?

thanks : )

---

### Post by irenioskamoska on 2011-03-02
i´m triying to install or activate the drivers for the wireless connection via ethernet wired connection, updating ubuntu first , installing drivers then... let´s hope it works!:popcorn:

---

### Post by Yamipirogoeth on 2011-03-23
Hello, I'm having a similar issue in accessing wireless networks while using 10.10

Here is the results of lspci:

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ea:ea:4e  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feea:ea4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:124945150 (124.9 MB)  TX bytes:4030582 (4.0 MB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30400 (30.4 KB)  TX bytes:30400 (30.4 KB)

As far as my wireless connection goes, I utilise a WPA encrypted connection if that helps any

---

### Post by Bucky Ball on 2011-03-24
You would be much better to post a new thread of your own with a descriptive thread title that fits your issue and as much info as possible (what you have is good). You will get more help and more specific. For a start this card is a Realtek chip, yours is Broadcom (which should work out of the box) so your problem is *not* the same. Post a link to the new thread here if you like.

Your post here is buried deep in an old thread that is pretty much dead. ;)

If you haven't, plug in an ethernet cable, get online, get your updates, check System>Administration>Additional Drivers.

Don't tell me how you went here but on the new thread. :)

---

