---
title: "ubuntu 10,04 rt3090 problem"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by garic on 2010-05-03
Hey guys,

Just bought a small vot120 desktop as an add on extra with no os as wanted to boot with ubuntu.

The wireless is a ralink rt3090

Installed the new 10.04 release just find and are having a nightmare with getting wireless to work.

Spent several hours surfing for different fixes. These are the things I haved tried.

Used ndiswrapper and installed the windows driver from the cd that came with it, this made it able to sense my network but wouldnt connect with wpa and kept trying to ask for password before disappearing.

Went to the ralink website and downloaded there driver for linux from there, make installed it following these instructions [http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html) but with rmmod rt3090sta instead of rt2860 as there was none in the module but was rt3090sta.

also tried both ppa packages from [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") with no prevale

so lastly thought I'll post and see what everyone thinks.
Am more than happy to write out print outs from the terminal or anything for diagnosing purposes just ask what you need

iwconfig gives

ra0 Ralink STA ESSID; " " Nickname :"RT2860STA"
Mode:auto Frequency:2.412 GHZ Access point:Not-Associated

etc

cheers in advanced

---

### Post by orionds on 2010-05-04
Hi,

I had the same problem, but found this thread and the workaround worked for me:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

It's actually this post:

[Alan]("https://launchpad.net/%7Emrintegrity")             wrote             on 2010-04-22:                                                             [  #21]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/21")                                                        I would just like to confirm that the  workaround suggested by Carsten seems to work perfectly (so far).
 As root:
 mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
 It is then possible to connect via network manager.
 /Alan


Hope it works. Worked for me.


Cheers.

---

### Post by garic on 2010-05-04
Thanks for your reply,

Sadly didn't help, network manager still is not sensing any connections.

When I run dmesg I get a readfile error "/etc/Wireless/RT2860STA.dat" failed(errCode=0)!
Tried copying the dat file I got from the driver file downloaded from ralink website with no prevale (think its just empty aswell)

another line of the dmesg

rt3090sta: module is from the staging directory, the quality is unknown, you have been warned
rt3090 0000:02:00.0: PCI INT A -> GSI 17 (level,low) -> IRQ 17
rt3090 0000:02:00.0: setting latency timer to 64
===> rt30xx read powerlevelmode = 0x3
===> rt30xx F write 0x83 command = 0x3

When I install the markus package dmesg readfile error is not there as it doesnt search for the file

thanks for your help

---

### Post by chili555 on 2010-05-04
Please post:```
dmesg | grep -e rt2 -e rt3
lsmod | grep -e rt2 -e rt3
ls /etc/Wireless
```Thanks.

---

### Post by Nw01f on 2010-05-04
My wireless card is [SIZE=1]RT3090  Wireless 802.11n 1T/1R PCIe. It cannot connect [/SIZE]to my wireless router. After applying the above trick, the result is the same. Here is the information:


```

**#:~$ dmesg | grep -e rt2 -e rt3**
[   12.013989]  rt3090sta: module is from the staging directory, the quality is unknown,  you have been warned.
[   12.135489] rt3090 0000:02:00.0: PCI INT A  -> GSI 16 (level, low) -> IRQ 16
[   12.135527] rt3090  0000:02:00.0: setting latency timer to 64
[   20.193007] <====  rt28xx_init, Status=0
[   20.193991] ====> rt30xx Read  PowerLevelMode =  0x3.
[   20.193995] ====> rt30xx F Write 0x83  Command = 0x3.

**#:~$ lsmod | grep -e rt2 -e rt3**
rt3090sta              751243  1 

**#:~$ ls /etc/Wireless**
RT2860STA

``````

**#:~$ iwconfig wlan0**
wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

**#:~$ lshw**

[SIZE=2]id:[/SIZE][SIZE=2]network[/SIZE][SIZE=2]
description: [/SIZE][SIZE=2]Wireless interface                 
[/SIZE][SIZE=2]product: [/SIZE][SIZE=2]RT3090  Wireless 802.11n 1T/1R PCIe
[/SIZE][SIZE=2]vendor: [/SIZE][SIZE=2]RaLink
[/SIZE][SIZE=2]physical id: [/SIZE][SIZE=2]0
[/SIZE] [SIZE=2]bus info: [/SIZE][SIZE=2]pci@0000:02:00.0
[/SIZE] [SIZE=2]logical name: [/SIZE][SIZE=2]wlan0
[/SIZE][SIZE=2]version: [/SIZE][SIZE=2]00
[/SIZE] [SIZE=2]width: [/SIZE][SIZE=2]32  bits  
[/SIZE][SIZE=2]clock: [/SIZE][SIZE=2]33MHz
[/SIZE] [SIZE=2]capabilities: [/SIZE][SIZE=2]pm msi pciexpress  bus_master cap_list ethernetphysical wireless
[/SIZE][SIZE=2]configuration:[/SIZE][SIZE=2] broadcast[/SIZE][SIZE=2]=[/SIZE][SIZE=2]yes[/SIZE][SIZE=2] driver[/SIZE][SIZE=2]=[/SIZE][SIZE=2]rt3090[/SIZE][SIZE=2] latency[/SIZE][SIZE=2]=[/SIZE][SIZE=2]0[/SIZE][SIZE=2] multicast[/SIZE][SIZE=2]=[/SIZE][SIZE=2]yes[/SIZE][SIZE=2] wireless[/SIZE][SIZE=2]=[/SIZE][SIZE=2]RT2860 Wireless
[/SIZE][SIZE=2]resources:[/SIZE][SIZE=2] irq[/SIZE][SIZE=2]:[/SIZE][SIZE=2]16[/SIZE][SIZE=2] memory[/SIZE][SIZE=2]:[/SIZE][SIZE=2]fdff0000-fdffffff[/SIZE]

``````

#:~$ uname -a
Linux olevia 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```************************************************

The problem is solved after restart
and by command sudo ifconfig wlan0 up

Cheers

---

### Post by garic on 2010-05-05
Hey Chilli555 thanks for your response.

Printouts as follows:


dmesg | grep -e rt2 -e rt3
[   20.138664] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   20.408491] rt3090 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.408539] rt3090 0000:02:00.0: setting latency timer to 64
[   21.694179] <==== rt28xx_init, Status=0
[   21.694890] ====> rt30xx Read PowerLevelMode =  0x3.
[   21.694896] ====> rt30xx F Write 0x83 Command = 0x3.

lsmod | grep -e rt2 -e rt3
rt3090sta             674216  1 

 ls /etc/Wireless
RT2860STA

Thanks for your help

---

### Post by garic on 2010-05-05
Update:

Tried upgrading to the newer kernel via this thread I found [http://ubuntuforums.org/showthread.php?t=1473629%E2%80%8F](http://ubuntuforums.org/showthread.php?t=1473629%E2%80%8F) still with no prevale.

---

### Post by chili555 on 2010-05-05
I wonder if it still complaining about the .dat file. Please let us see:```
dmesg | grep dat
```What are your symptoms? Does Network Manager show your network? Does it try to connect?

---

### Post by garic on 2010-05-05
Doesn't show me any network connections at all. No result from scanning. 

Checked for dat in dmesg and there is nothing there that sayin anything about rt2860.dat 

If I use ndiswrapper with a driver that I get with the cd that came with my machine (windows) then it can find my network, but cannot connect as it keeps prompting me for my wpa password then disconnects and cannot see the network anymore. 

This is as close as I got to getting the wifi working.

Cheers for your help mate

---

### Post by garic on 2010-05-05
Ok noting that it will be near impossible to diagnose problem if I keep trying solutions I find and changing things, I changed my kernel back to 2.6.32 and then ran the commands that make install the driver using chris barkers step through and website drivers. Thus having the most up to date driver which is probably the best starting point. Re-ran all the commands giving the following outputs

dmesg | grep -e rt2 -e rt3
[   19.210457] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   19.352357] rt3090 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.352418] rt3090 0000:02:00.0: setting latency timer to 64
[   20.602290] <==== rt28xx_init, Status=0
[   20.617265] ====> rt30xx Read PowerLevelMode =  0x3.
[   20.617275] ====> rt30xx F Write 0x83 Command = 0x3.
[  345.284807] rt28xx_close call RT28xxPciAsicRadioOff fail !!
[  483.865612] rt3090sta: module license 'unspecified' taints kernel.
[  483.890686] rt2860 0000:02:00.0: setting latency timer to 64
[  483.960721] <==== rt28xx_init, Status=0
[  483.963311] ====> rt30xx Read PowerLevelMode =  0x3.
[  483.963323] ====> rt30xx F Write 0x83 Command = 0x3.

 lsmod | grep -e rt2 -e rt3
rt3090sta             874536  1 

ls /etc/Wireless
RT2860STA

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lshw
*-network
                description: Wireless interface
                product: RT3090 Wireless 802.11n 1T/1R PCIe
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: ra0
                version: 00
                serial: 00:17:c4:a2:ac:6f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.4 latency=0 multicast=yes wireless=Ralink STA

lsmod | grep rt
rt3090sta 874536 1

with nothing related to the rt3090 coming up from the search in dmesg for dat. Is it a problem that ls /etc/Wireless shows up rt2860sta instead of rt3090?? slash might be the reason it aint coming up with dat error any more? 

Once again cheers for your help. I am pretty committed to getting ubuntu wireless working as it seems like a great interface.

---

### Post by chili555 on 2010-05-06
> Ok noting that it will be near impossible to diagnose problem if I keep trying solutions I find and changing things, Absolutely correct. Please try:```
sudo iwconfig ra0 mode managed
sudo iwlist ra0 scan
```If you do not get scan results, please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file dmesg.zip in your user directory. Please attach it to your reply.

---

### Post by garic on 2010-05-06
no results from scan, here's the attachment you requested.

Something else of interest maybe??? when I run the make file before the driver installation there is one warning saying : modpost: missing MODULE_LICENSE() in /"directory"/rt3090sta.o file , still successfully compiles and installs tho. 

Thanks again.

---

### Post by garic on 2010-05-13
Ok reading through some other forums is that you have to manually setup the dat file that gets copied into the wireless folder. Will try this and get back to you.

Didn't work, 
I have a couple of questions.. am I right in saying the driver itself is the rt3090sta.ko . In what directory is this driver meant to be installed?

Thanks

---

