---
title: "no wired lan connection"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by irohaphoto on 2009-10-22
Hello
I just installed ubuntu v9.04 on a new Acer notebook KAV60
dual boot with xp for now.
Ubuntu  works great but I can't get my wired LAN internet connection to work.
It works fine when I plug the cable in on the XP side but not ubuntu.

I followed the directions here:
[http://ubuntuforums.org/showthread.php?t=1212637&highlight=wired+lan+connection](http://ubuntuforums.org/showthread.php?t=1212637&highlight=wired+lan+connection)

IP 192.168.24.51 (for my desktop)

IP 192.168.24.53 for acer notebook)
subnet mask 255.255.255.0
gateway 192.168.24.1

and still no connection
is there anything I can try to type in terminal to check?

any help would be appreciated.
thanks

---

### Post by chili555 on 2009-10-22
Can you ping the router?```
ping -c3 192.168.24.1
```What did you enter for DNS nameservers? You can gather that information on the XP side with *ipconfig /a*.

---

### Post by irohaphoto on 2009-10-23
Thanks chili555 for your reply
When I ping the router I get:

connect: Network is unreachable

This is what I got for DNS nameservers when I type 

ipconfig /all 

 on the XP side:

Dhcp Enabled: Yes
Autoconfiguration enabled: Yes
IP Address: 192.168.24.53
Subnet mask: 255.255.255.0
Default Gateway:192.168.24.1
DHCP Server: 192.168.24.1
DNS Servers: 192.168.24.1

I was reading the beginners guide and they say that ubuntu also has the same network icon for wireless as windows (the 3 bars) and for the wired LAN network (the 2 overlapping monitors). On my system I get the wireless icon but  no wired double monitor icon. Is there code to bring up the wired icon I could try entering?

Thanks in advance

---

### Post by chili555 on 2009-10-23
May I assume you put these settings in Network Manager, the little icon you referred to?> IP 192.168.24.53 for acer notebook)
subnet mask 255.255.255.0
gateway 192.168.24.1May we please see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by irohaphoto on 2009-10-23
Yes I did put these

IP 192.168.24.53 for acer notebook)
subnet mask 255.255.255.0
gateway 192.168.24.1

into the network manager and  this

cat /etc/network/interfaces
gave me:

auto lo
iface lo inet loopback

---

### Post by chili555 on 2009-10-23
It all looks perfect! It's my favorite kind of problem: everything is perfect, except it doesn't work! Let's start at the beginning. Do we actually have an eth0 interface? Please run:```
ifconfig
```Is there an interface eth0? You don't have to post the whole output, just tell us if there is an interface. Does ifconfig recognize your IP address, 192.168.24.53?

When you click the Network Manager icon, does 'Wired Network' show? Is it selectable? See attached.

---

### Post by irohaphoto on 2009-10-24
ifconfig gets

Code:

lo        Link encap:Local Loopback
          inet addr: 127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:24:e9:22
             UP BROADCAST MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-24-E9-22-00-00-00-00-00-00-00-00-00-00
                UP BROADCAST MULTICAST  MTU:1500  Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:1000
                RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Sorry I had to include all of it but I don't know what to look for.
It appears there is no eth0 but there is an ethernet. ? This IP address, 192.168.24.53
doesn't seem to be present but mask and gateway seem to be there.

By the looks of your thumbnail is that a wireless connection? As far as I know my wireless is working but I cannot use it because I don't have a network key/password. At work the wireless network name "APU-NET" shows up and when I boot up down town at the train station I get a bunch of networks just like your screen shot, but they are secured so I can't login.

Let me know what I can provide next, thanks again for your patience.

---

### Post by chili555 on 2009-10-24
Well, the plot thickens! It appears you have no eth0 interface. Perhaps no driver has attached to your ethernet card in order to trigger an interface. Please post:```
sudo lshw -C network
```We'll figure out what kind of card you have and which driver it needs. Ideally, we'll load the driver and you'll be all set.

Yes, I was connected, at the time, to a wireless network. You will notice it also listed 'Wired Network' albeit grayed out. That's because there is no wire attached and Network Manager knows it can't use a wired connecting without a detected link to the router.

---

### Post by Iowan on 2009-10-24
**ifconfig -a** *should* show all available interfaces. **lshw -C network** might show more details about eth0. Does Network Manager have the "Connect automatically" box checked for your connection?

Oops... about 5 minutes late...

---

### Post by irohaphoto on 2009-10-24
Yes "Connect Automatically" is checked in the network manager.
 here is the output for **lshw -C network** 
 
 Code:
 
 *-network
    description: Wireless interface
    product: AR242x 802.11abg Wireless PCI Express Adapter
    vendor: Atheros Communications Inc.
    physical id: 0
    bus info: pci@0000:01:00.0
    logical name: wmaster0
    version: 01
    serial: 00:24:2c:24:e9:22
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
    configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes  wireless=IEEE 802.11bg
 *-network UNCLAIMED
    description: Ethernet controller
    product: Attansic Technology Corp.
    vendor: Attansic Techonology Corp.
    physical id: 0
    bus info: pci@0000:03:00.0
    version: c0
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress vpd bus_master cap_list
    configuration: latency=0
 *-network DISABLED
    description: Ethernet interface
    physical id: 2
    logical name: pan0
    serial: le:b5:e9:c0:3d:0a
    capabilities: ethernet physical
    configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by chili555 on 2009-10-24
Well, that's a bit brief! All we know is that it's an Attansic. There are a couple of versions but we might get lucky. This might be the L1C version. Please try:```
sudo modprobe atl1c
sudo ifconfig eth0 up
```If there are no complaints or warnings about eth0, then you should be able to click Network Manager and connect.

If there is an error, we have guessed the wrong driver and we need more information. Please do:```
sudo lspvi -n | grep 03:00
```Post the output and we'll google up some additional clues.

---

### Post by irohaphoto on 2009-10-24
Well that is interesting. no luck at all.

sudo ifconfig eth0 up

gets:

eth0: ERROR while getting interface flags: No such device

and 

sudo modprobe atl1c

gets:

FATAL: Module atl1c not found   

so enter:

sudo lspvi -n | grep 03:00

gets:

sudo: lspvi: command not found

---

### Post by Iowan on 2009-10-24
Typo? 
**sudo lspci -n | grep 03:00**?

---

### Post by chili555 on 2009-10-24
> sudo lspci -n | grep 03:00Yep, that's a c there, once I clean off these old trifocals! Sorry.

---

### Post by irohaphoto on 2009-10-24
Thanks for the correction Iowan

sudo lspci -n | grep 03:00

gives:

03:00.0 0200: 1969:1062 (rev c0)

---

### Post by irohaphoto on 2009-10-25
If:
sudo lspci -n | grep 03:00

gives:

03:00.0 0200: 1969:1062 (rev c0)

then does that mean that my network card is Atheros(R) AR8121/AR8113 PCI-E ?
as shown here:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

**02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b**
cannot be the same as 03:00.0 0200: 1969:1062 (rev c0) or is it?

I would like a confirmation on this before going ahead. thanks

---

### Post by irohaphoto on 2009-10-25
I decided to go ahead and take a risk with:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

but I would really like to have some idea as to what to do here:

4) cd into <HOME_DIR>_**/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src**_

this folder is all unpacked and on my ubuntu desktop but not sure what this #4 does?
i get no such directory.
 please help.

5) then i ran: sudo KBUILD_NOPEDANTIC=1 make
6) then i ran: sudo KBUILD_NOPEDANTIC=1 make install
7) that worked and put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

---

### Post by chili555 on 2009-10-25
This part:> cd into [COLOR="Red"]<HOME_DIR>[/COLOR]/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/srcis a clumsy was of saying, 'change directories to wherever you unpacked the .tar.gz.'

It looks like you got it built and *insmod*-ed. Afterwards, was an *eth0* inteface created? Can you connect?

---

### Post by irohaphoto on 2009-10-25
Totally lost
cd /home/projecth2o/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src 			 		

all I get is "no such directory"

the "LinuxDrivers" folder is on my ubuntu desktop. what should I do.

4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
5) then i ran: sudo KBUILD_NOPEDANTIC=1 make
6) then i ran: sudo KBUILD_NOPEDANTIC=1 make install

#6 is just make a directory "install" but what is going into it?

7) that worked and put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

#8 makes no sense.

---

### Post by irohaphoto on 2009-10-25
I think I made it as far as 
7) that worked and put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko

but I cannot figure out 
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

If /lib/ is in my Filesystem then what comes before that when cd?

Well the driver is in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko
because I checked so I will call it a day and figure this out tomorrow.

---

### Post by chili555 on 2009-10-25
> 8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

If /lib/ is in my Filesystem then what comes before that when cd?
You don't have to worry about this; if a module is in /lib/modules/etc. etc., you should be able to simply do:```
sudo modprobe atl1e
```> the "LinuxDrivers" folder is on my ubuntu desktop. what should I do.

4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/srcThis means you should do:```
cd Desktop/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
```However, it sounds like you got it figured out, if you got the 'make' and 'make install' done without errors.

---

### Post by irohaphoto on 2009-10-25
I am not sure what I did wrong but when I **sudo modprobe atl1e**
it produces no output. Somehow in the "make"/"make install" area I saw an error saying cannot write to folder or something but when I look into "Filesystem" I see this
**/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src**
so it appears I did make and install it.

---

### Post by chili555 on 2009-10-26
> I am not sure what I did wrong but when I sudo modprobe atl1e
it produces no output.I am pretty sure you did nothing wrong. When you issue a command and there is no output, that generally means the command was accepted and completed and there are no warnings or errors to report. Let's check to see if the module is loaded with:```
lsmod | grep atl
```Does *atl1e* appear? If so, let's see if it attached to your device with:```
sudo lshw -C network
```Does your Attansic (nee Atheros) now have an interface, *eth0*, perhaps? Can you click on the Network Manager icon and connect?

---

### Post by irohaphoto on 2009-10-26
Entering this:
**lsmod | grep atl**

Gets no output and **sudo lshw -C network**
Looking at the output I think I see that the wireless is definitely there but 
the other networks don't have  eth0

Now is the time I really wish there was a place to try the wireless or a password
just to try.

---

### Post by chili555 on 2009-10-26
After you first did:```
sudo modprobe atl1e
```did you reboot? If so, the module would go away, unless we take specific, affirmative steps to reload it on boot. Please try:```
sudo modprobe atl1e
lsmod | grep atl
ifconfig
```Please report any errors or warnings. Does ifconfig have an *eth0*?

---

### Post by irohaphoto on 2009-10-26
I tried this again from the beginning.

so far good up to **sudo KBUILD_NOPEDANTIC=1 make**
Then when I enter [B]sudo KBUILD_NOPEDANTIC=1 make install
[/B]I get [B]

find /lib/modules/2.6.28-11-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e/atl1e.ko
/sbin/depmod -a  true
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
man -c -P'cat > /dev/null' atl1e || true
man:
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.

[/B]This is the last 8 lines before the command promptbecause I think everything else is ok until that error.any suggestions would be appreciated.

---

### Post by MrKlean on 2009-10-26
From my last week of experience LOL!! If you're running 64 bit OS,,, and you're drivers are 32 bit... It ain't gonna work LOL!!  I found what were supposed to be 64 drivers for my WG311v3 and could get connected no matter what..I switched to 32 bit Karmic and it works no problems... just a thot !!

---

### Post by irohaphoto on 2009-10-26
Karmic? that's the new 9.10? I was wondering about that if I delete or un install 9.04  will I still ned to get the atl1e driver for LAN? Then the 3 day wait is worth it...

---

### Post by chili555 on 2009-10-26
> cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.This has to do with the creation of a manual page, I believe, and is trivial. It may safely be ignored.> will I still ned to get the atl1e driver for LAN?The atl1e module is included even in later kernel versions than you have. You have 2.6.28-11. I have 2.6.28-15 and I have:> /lib/modules/2.6.28-15-generic/kernel/drivers/net/atl1e/atl1e.koI am not quite sure if I have this because it's natively included in -15 or if I got it with *linux-backports-modules-jaunty*. If you don't have internet connectivity, it will be very, very hard for you to get either an updated kernel or *backports*.

As well, we have to figure out if *atl1e* is the correct module, or else, *atl1* or *atl1c*. We will know when an interface is created, indicating that your card and the correct module have fallen in love and gotten married.

So, to repeat, after you modprobed *atl1e*, was an interface created???

---

### Post by irohaphoto on 2009-10-26
Everything up to this worked
**sudo KBUILD_NOPEDANTIC=1 make install**

Then I did this:
**sudo modprobe atl1e**
no output
then 
**lsmod | grep atl**

and got:

**atl1e        40084 0**

then **ifconfig**

output same as before no eth0

One thing I really want to try is 

cd into **/lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e**
(I think) and the **sudo insmod ./atl1e.ko**

according to the directions given on 
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

BUT I can't figure out what I need to write before /lib/modules/...
everything I try so far to cd there I just get no such dir.
do I stay in the /home/[COLOR=Red]username[/COLOR]/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src 			 		
in order to cd to the /lib/modules/.... /atl1e folder or go back to the home prompt?
The next few posts on that thread he gives 
cd /home/[COLOR=Red]username[/COLOR]/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src                      

which was useful for that path but no useful for the /lib/  path.

---

### Post by chili555 on 2009-10-26
> One thing I really want to try is

cd into /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e
(I think) and the sudo insmod ./atl1e.koIt doesn't matter what directory you are in, simply do:```
cd /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e
```Then you can list the contents of the directory with:```
ls
```Do you see *atl1e*? This highlighted part is wrong:> sudo insmod [COLOR="Red"]./[/COLOR]atl1e.koIt should be:```
sudo insmod atl1e
```Or, more properly:```
sudo modprobe atl1e
```However, you have atl1e inserted already:> lsmod | grep atl

and got:

atl1e 40084 0Yet, it didn't attach to your network card. That suggests, but may not always be true, that *atl1e* is not the correct module.> then does that mean that my network card is Atheros(R) AR8121/AR8113 PCI-E ?
as shown here:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device [COLOR="Red"]1026[/COLOR] (rev b
cannot be the same as 03:00.0 0200: 1969:[COLOR="Red"]1062[/COLOR] (rev c0) or is it?

I would like a confirmation on this before going ahead. thanksNO! 1062 is not the same as 1026. I believe your device is actually an Atheros AR8132 / [COLOR="Blue"]L1c[/COLOR] Gigabit Ethernet Adapter. What is the result if you do:```
sudo rmmod atl1e
sudo modprobe [COLOR="Blue"]atl1c[/COLOR]
ifconfig
```Any interface now?

---

### Post by irohaphoto on 2009-10-26
I see now.
**sudo rmmod atl1e**

says **ERROR: Module atl1e does not exist in /proc/modules**

**sudo modprobe atl1c**

**FATAL: Module atl1c not found**

I think it may be easier to recover the files from within XP and start fresh by deleting 9.04
This computer is new and I have nothing to lose. unless ofcourse recover will not completely delete ubuntu.

---

### Post by chili555 on 2009-10-26
Before I went back to XP, I would download and try Koala, version 9.10. The RC (release candidate) is not going to be that much different from the final version coming out in a few days. 9.10 will have both *atl1c* and *atl1e*. You can try the live CD and know for sure before you install.

---

### Post by irohaphoto on 2009-10-28
Thanks to the help of all who posted especially chilli555 
not exactly solved but temporarily so I did end of installing 9.10 and did connected to wired lan but I still have 9.04 installed on another partition ext3 and 9.10 on ext4 (I read that this was not as stable as ext3)
so in the future I hope either to delete 9.04 from terminal or reinstall 9.10  with new partitions, the problem was I was afraid I would delete XP, which I don't want to do just give it less space.

---

### Post by chili555 on 2009-10-28
> in the future I hope either to delete 9.04 from terminal or reinstall 9.10 with new partitions, the problem was I was afraid I would delete XP, which I don't want to do just give it less space.Gparted will do what you want to do; however, it's a bit dangerous to just start moving, deleting and enlarging partitions! Please read, then read some more and ask questions on the forum before you fire up your chain saw!

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I am glad your ethernet is working! Good luck and have fun!

PS - Was the driver *atl1c*? The searchers want to know. Find out in 9.10 with:```
lsmod | grep atl
```Thank you for your help.

---

### Post by irohaphoto on 2009-10-30
> **chili555 said:**
> Gparted will do what you want to do; however, it's a bit dangerous to just start moving, deleting and enlarging partitions! Please read, then read some more and ask questions on the forum before you fire up your chain saw!

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I am glad your ethernet is working! Good luck and have fun!

PS - Was the driver *atl1c*? The searchers want to know. Find out in 9.10 with:```
lsmod | grep atl
```Thank you for your help.


Yes the driver is a **atl1c **

---

