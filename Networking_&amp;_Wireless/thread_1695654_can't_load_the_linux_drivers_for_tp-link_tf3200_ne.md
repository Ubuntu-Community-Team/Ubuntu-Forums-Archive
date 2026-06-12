---
title: "can't load the linux drivers for tp-link tf3200 network adapter"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by markpag on 2011-02-26
Hi,
I have tried to install tp link tf3200 network adapter without success . the os is 8.04 hardy

loading drivers is new to me.

the driver is sundance (i think)  and the output from the make command is shown below.
Can anyone point out where I go from here? have thought about using ndiswrapper but could probably dig myself an even deeper hole with that !

many thanks

PS a bit off topic but the unable to resolve host bit bugs me is there any way to fix it ( i know its probably easy!)

pag@paghomelinux:~$ cd /media/cdrom0/TF-3200/LinuxDriver
pag@paghomelinux:/media/cdrom0/TF-3200/LinuxDriver$ sudo make all
sudo: unable to resolve host paghomelinux
make -C /lib/modules/2.6.24-28-generic/build SUBDIRS= modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-28-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-28-generic'
make: *** [all] Error 2
pag@paghomelinux:/media/cdrom0/TF-3200/LinuxDriver$

---

### Post by chili555 on 2011-02-26
I think you may have two problems here. First is the hostname issue and second is that you are trying to run the 'make' process from the CD. Make writes new files depending on your kernel and gcc version. It can't write to the CD. 

Let's solve one at a time. Please run and post:```
cat /etc/hosts
cat /etc/hostname
ls /media/cdrom0/TF-3200/LinuxDriver
```The last command is just because I am interested in the exact details of the driver that came with your device. I hope we will have no difficulty marrying it to your older 2.6.24 kernel.

---

### Post by markpag on 2011-02-26
Thanks for the reply

pag@paghomelinux:~$ cat /etc/hosts
127.0.0.1 localhost paghomelinux.home

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.3 paghome
127.0.1.1 paghomelinux.home
pag@paghomelinux:~$ cat /etc/hostname
paghomelinux
pag@paghomelinux:~$ ls /media/cdrom/TF-3200/LinuxDriver
compat.h  ethtool.h  mii.c  readme.txt
crc32.h   Makefile   mii.h  sundance_main.c
pag@paghomelinux:~

The Drivers were dated sept 2007 so i am think they are the most recent (have trudged around the web looking) they came with the card and appear to be the same as the IP100A drivers 

I ran the make command with the files copied to the desktop and the results were pretty much the same.
Regards
markpag


pag@paghomelinux:~/Desktop/LinuxDriver$ sudo make all
sudo: unable to resolve host paghomelinux
[sudo] password for pag: 
make -C /lib/modules/2.6.24-28-generic/build SUBDIRS= modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-28-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-28-generic'
make: *** [all] Error 2
pag@paghomelinux:~/Desktop/LinuxDriver$

---

### Post by chili555 on 2011-02-26
Please do:```
sudo gedit /etc/hosts
```Make the change I have highlighted:```
127.0.0.1 localhost paghomelinux.home
[COLOR="Red"]127.0.1.1 paghomelinux
[/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```Remove this line entirely: 192.168.1.3 paghome

Proofread carefully, save and close gedit. 

Reboot immediately. Now try the make process again and let me have your report. > $ ls /media/cdrom/TF-3200/LinuxDriver
compat.h ethtool.h mii.c ***readme.txt***
crc32.h Makefile mii.h sundance_main.cPlease also post the readme.txt.

---

### Post by markpag on 2011-02-26
Chili555, thanks for sorting the unable to resolve hosts
Below is the output from the make command followed by readme.txt
regards
markpag

pag@paghomelinux:~$ cd ./Desktop
pag@paghomelinux:~/Desktop$ cd ./LinuxDriver
pag@paghomelinux:~/Desktop/LinuxDriver$ sudo make all
[sudo] password for pag: 
make -C /lib/modules/2.6.24-28-generic/build SUBDIRS= modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-28-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-28-generic'
make: *** [all] Error 2
pag@paghomelinux:~/Desktop/LinuxDriver$ 

Readme.txt below
||||||||||||||||
VVVVVVVVVVVVVVVV

           
                       Linux Driver  
 
Contents: 
----------- 
1. File Description 
2. Driver Installation for Linux 
3. Driver Parameter 
4. None EEPROM 
5. EEPROM MP (OEM Only) 
 
1. File Description 
------------------- 
 
Filename                Description 
====================    ======================================================= 
sundance_main.c         Linux Driver Source Code. 
                        This file is the main part of Linux Driver. 
 
compat.h                Network interface message level settings. 
 
crc32.h                 Crc function for early Linux 2.4.19pre kernel inclusion 
 
ethtool.h:              Defines for Linux ethtool. 
 
mii.h                   definitions for MII-compatible transceivers. 
 
mii.c                   MII interface library. 
 
makefile                Make File For IP100 Linux Driver. 
                        Using "make all" for your kernel. 
 
readme.txt              A summary of the contents for Linux Driver. 
                        This file, which you are reading me now. 
 
 
 
2. Driver Installation for Linux 
----------------------------------------- 
a. for kernel 2.4.x 
   a1. Redhat 7.3 (linux kernel 2.4.18) 
   a2. Mandrake 8.1 (kernel 2.4.8) 
b. for kernel 2.6.x 
c. automatically load and configure at next boot time 
 
   a.for kernel 2.4.x 
   ------------------- 
     a1. Redhat 7.3 (linux kernel 2.4.18) 
     a1.1. install way 1: 
         #make all =>generate sundance.o 
         #cp sundance.o /lib/modules/2.4.18-3/kernel/drivers/net/ 
         #insmod ./sundance.o 
         #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy 
            eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1... 
            xxx  is your ip address, ex: 192.168.102.211 
            yyy  is your netmask address, ex:255.255.255.0 
 
     a1.2.  install way 2: 
        #make all =>generate sundance.o 
        #cp sundance.o /lib/modules/2.4.18-3/kernel/drivers/net/ 
        #insmod./sundance.o 
        #setup 
        [network configuration] =>to setup your ip address 
        #ifup eth0 
           eth0 is your network adapter, ex: eth0, eth1...     
 
 
     a2. Mandrake 8.1 (kernel 2.4.8) 
       #make all  => generate sundance.o 
       #cp sundance.o /lib/modules/2.4.8-26mdk/kernel/drivers/net 
       #insmod ./sundance.o 
       #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy 
           eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1... 
           xxx  is your ip address, ex: 192.168.102.211 
           yyy  is your netmask address, ex:255.255.255.0 
 
 
   b. for kernel 2.6.x 
   ------------------- 
      #make all  => generate sundance.ko 
      #insmod ./sundance.ko (or sundance.o) 
      #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy 
            eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1... 
            xxx  is your ip address, ex: 192.168.102.211 
            yyy  is your netmask address, ex:255.255.255.0       
    
   c. automatically load and configure at next boot time 
   ----------------------------------------------------- 
     c1. cp sundance.o /lib/modules/`uname -r`/kernel/drivers/net 
     *note: The `uname -r` is a command. Don't replace `uname -r` with 
            2.4.18, 2.4.20smp, or some others. Must type `uname -r` directly. 
 
     c2. Add the following lines at /etc/modules.conf: 
                
          alias eth0 sundance 
          options sundance <optional parameters> 
                               
     c3. Run "netconfig" or "netconf" to create configuration script  
 
              ifcfg-eth0 located at /etc/sysconfig/network-scripts or  
              create it manually. 
              [see - Configuration Script Sample] 
 
     c4. Driver will automatically load and configure at  
              next boot time. 
               
     c5. Configuration Script Sample 
     =========================== 
         Here is a sample of a simple configuration script: 
 
         DEVICE=eth0 
         USERCTL=no 
         ONBOOT=yes 
         POOTPROTO=none 
         BROADCAST=207.200.5.255 
         NETWORK=207.200.5.0 
         NETMASK=255.255.255.0 
         IPADDR=207.200.5.2 
               
 
3. Driver Parameter 
------------------- 
  If you want to change the link speed, you could use parameter after  
  insmod command. 
   
  insmod sundance.o <optional parameter>    ; add parameter 
 
  ======================================================================== 
   example: insmod sundance.o media=100mbps_hd 
   or        insmod sundance.o media=3 
   or        insmod sundance.o media=1,2,3,4    ; for 4 cards or IP100 
  ========================================================================               
   
  Parameter Description 
  ===================== 
  You can install this driver without any addtional parameter. However, if  
  you are going to have extensive functions then it is necessary to set  
  extra parameter. Below is a list of the command line parameters supported  
  by the Linux device driver. 
 
media=xxxxxxxxx            - Specifies the media type the NIC operates at. 
                  autosense    Autosensing active media. 
                  10mbps_hd    10Mbps half duplex. 
                  10mbps_fd    10Mbps full duplex. 
                  100mbps_hd    100Mbps half duplex. 
                  100mbps_fd    100Mbps full duplex. 
                  0        Autosensing active media. 
                  1        10Mbps half duplex. 
                  2        10Mbps full duplex. 
                  3        100Mbps half duplex. 
                  4        100Mbps full duplex. 
                  By default, the copper devices operate at  
                  autosense, the fiber devices operate at 
                  100Mbps full duplex. 
                  Note that, the fiber adapter only support  
                  100Mbps half/full duplex types.     
 
  If wanting to change speed, this driver needed to be unloaded and reloaded with  
  new media parameter. Use rmmod to unload and insmod to reload driver. 
  ======================================================================== 
   example: rmmod sundance.o  
           insmod sundance.o media=3 
  ========================================================================     
 
flowctrl=[0|1]            - Specifies the flow control function. 
                  0    Disable flow control.     
                  1    Enable flow control.     
 
4. None EEPROM 
-------------- 
  If you want to use none eeprom solution. Please put EEPROM EEDO pin to GND. 
  And, please add following -DNO_EEPROM define in Makefile, and re-compile again. 
 
MAPPING_MODE= -DUSE_IO_OPS -DNO_EEPROM 
 
5. EEPROM MP (OEM Only) 
----------------------- 
  This is a special tool for OEM embedded system to burn eeprom value with  
  MAC address. It is not for normal user. If you need this tool, please contact 
  us directly. Thanks. 
   
  5.1. unzip mp.zip and put 'mp directory' in the same directory with 
  sundance_main.c 
 
  5.2. Change Makefile: 
  Form: "MAPPING_MODE= -DUSE_IO_OPS" 
  To: "MAPPING_MODE= -DUSE_IO_OPS -DMP_EEPROM" 
 
  Rebuild and load driver 
 
  5.3. Read MAC address form EEPROM 
  #cat /proc/ICPlus_eth0/IPF_EEPROM 
 
  5.4. Write MAC address to EEPROM 
  #echo "001122334455">/proc/ICPlus_eth0/IPF_EEPROM 
 
  5.5. Convert EEPROM.TXT to eeprom_data.h 
  run eep_cvrt.exe will convert EEPROM.txt to eeprom_data.h for linux driver 
  use.

---

### Post by chili555 on 2011-02-26
> #insmod ./sundance.ko (or sundance.o) Hmmm!

Please try:```
modinfo sundance
```If the module is already on your system, then try:```
sudo modprobe sundance
ifconfig
```Did an interface get created, eth0 perhaps? Can you connect?

---

### Post by markpag on 2011-02-26
Hi Chili555
have done as you suggested

eth1 i think is the card in question 
still cannot connect have tried pinging the router (the same one that is connecting me at present via wireless).



pag@paghomelinux:~/Desktop/LinuxDriver$ modinfo sundance
filename:       /lib/modules/2.6.24-28-generic/kernel/drivers/net/sundance.ko
license:        GPL
description:    Sundance Alta Ethernet driver
author:         Donald Becker <becker@scyld.com>
srcversion:     D84D78652F71C987C21286C
alias:          pci:v000013F0d00000200sv*sd*bc*sc*i*
alias:          pci:v000013F0d00000201sv*sd*bc*sc*i*
alias:          pci:v00001186d00001002sv*sd*bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001040bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001012bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001003bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001002bc*sc*i*
depends:        mii
vermagic:       2.6.24-28-generic SMP mod_unload 586 
parm:           media:array of charp
parm:           debug:Sundance Alta debug level (0-5) (int)
parm:           rx_copybreak:Sundance Alta copy breakpoint for copy-only-tiny-frames (int)
parm:           flowctrl:Sundance Alta flow control [0|1] (int)
pag@paghomelinux:~/Desktop/LinuxDriver$ sudo modprobe sundance

pag@paghomelinux:~/Desktop/LinuxDriver$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:73:71:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 74:ea:3a:84:96:b9  
          inet6 addr: fe80::76ea:3aff:fe84:96b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:310 (310.0 B)  TX bytes:468 (468.0 B)
          Interrupt:16 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100040 (97.6 KB)  TX bytes:100040 (97.6 KB)

pag@paghomelinux:~/Desktop/LinuxDriver$ ping 192.168.1.1

---

### Post by chili555 on 2011-02-26
> eth1 i think is the card in question
still cannot connect have tried pinging the router (the same one that is connecting me at present via wireless).Do you have more that one ethernet card? Why would that be? What does this tell us?```
sudo dhclient eth1
sudo ethtool eth1
```Are you certain the ethernet cable is attached to the TP-Link? Thanks.

---

### Post by markpag on 2011-02-26
There are 2 ethernet cards on this machine.
confession time 
l was trying to configure a second twin router as a wireless repeater. 
worked a treat for a short while with encryption disabled. re-enabled the encryption to wep and the router just about bricked up.

reconfigured the router 

it worked fine with laptop but not with paghomelinux, started running slowly then intermittently then not at all
so I suspected the onboard ethernet card (eth0) so bought the tplink.

Managed to get both working on xp (used for emergencies!). So then thought ah hah it must be the drivers - which brings us neatly to where this thread started.

I can confirm that the ethernet cable is known good and is connected to eth1

the output is shown below 
regards
markpag

pag@paghomelinux:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 6083
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/74:ea:3a:84:96:b9
Sending on   LPF/eth1/74:ea:3a:84:96:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
pag@paghomelinux:~$ sudo ethtool eth1
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Current message level: 0x00000001 (1)
    Link detected: yes
pag@paghomelinux:~$

---

### Post by chili555 on 2011-02-26
I don't see anything obviously wrong (and fixable) here. It says it's indeed connected to an ethernet cable:> Transceiver: internal
Auto-negotiation: on
Current message level: 0x00000001 (1)
[COLOR="Red"]Link detected: yes[/COLOR]I'm not worried yet about dhclient failing to get an IP address. Network Manager will probably not cooperate with manual methods. I simply asked that the command be run so we could see if it tries and gives out no error messages, warnings, smoke, sparks, etc. It passed the test.

Where is Network Manager in all this? When you click the icon, does it try to connect?

I wonder if we ought to blacklist the driver for the original ethernet card so it doesn't interfere. Please post:```
sudo lshw -C network
```

---

### Post by markpag on 2011-02-26
below is the output, network manager (is that system>administration>network) shows two wired connections with ticks to them. there is not an icon to click to connect.
regards
markpag

I have also appended a chunk of syslog in case that gives any clues.
In the past I have manually applied ip addresses without problems ( there are no clashes that i am aware of)


pag@paghomelinux:~$ sudo lshw -C network
[sudo] password for pag: 
  *-network:0             
       description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY
       vendor: Sundance Technology Inc / IC Plus Corp
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 31
       serial: 74:ea:3a:84:96:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full latency=32 link=yes maxlatency=10 mingnt=10 module=sundance multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0a:e6:73:71:e7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
pag@paghomelinux:~$ 

FROM SYSLOG

Feb 26 21:45:54 paghomelinux kernel: [   88.935823] NETDEV WATCHDOG: eth1: transmit timed out
Feb 26 21:45:54 paghomelinux kernel: [   88.935840] eth1: Transmit timed out, TxStatus c0 TxFrameId 1d, resetting...
Feb 26 21:46:06 paghomelinux kernel: [  100.920514] NETDEV WATCHDOG: eth1: transmit timed out
Feb 26 21:46:06 paghomelinux kernel: [  100.920527] eth1: Transmit timed out, TxStatus c0 TxFrameId 1d, resetting...
Feb 26 21:46:54 paghomelinux kernel: [  148.859278] NETDEV WATCHDOG: eth1: transmit timed out
Feb 26 21:46:54 paghomelinux kernel: [  148.859291] eth1: Transmit timed out, TxStatus c0 TxFrameId 1d, resetting...
Feb 26 21:51:58 paghomelinux kernel: [  452.655254] NETDEV WATCHDOG: eth1: transmit timed out
Feb 26 21:51:58 paghomelinux kernel: [  452.655269] eth1: Transmit timed out, TxStatus c0 TxFrameId 1d, resetting...

---

### Post by markpag on 2011-02-26
The router dhcp table showed a lease to paghomelinux which then expired!
regards
markpag

---

### Post by chili555 on 2011-02-26
It sounds like it connected at some point. That's good.> Transmit timed out, TxStatus c0 TxFrameId 1d, resetting...I'm not...yet...concerned about this. Let's see what happens when we reliably connect.

Let's blacklist the tricky via-rhine:```
sudo su
echo "blacklist via-rhine" >> /etc/modprobe.d/blacklist.conf
exit
```Now do:```
sudo rmmod -f via-rhine
```Now does Network Manager show an option to connect with the TP-Link?

---

### Post by markpag on 2011-02-26
will have to pack up for this evening -wife grief! thanks chili555

---

### Post by chili555 on 2011-02-26
See you tomorrow. Have a pleasant evening.

---

### Post by markpag on 2011-02-26
Have blacklisted via rhine.

Last post i can do tonight, 
have tried rebooting to xp - eth1 works fine there

rebooted to linux on booting up a lease is shown to the router, but can't ping fromthe router to paghomelinux. lease expires after 2mins (approximately ) timed out ?

tried to connect but won't thanks for all your help on this
regards
markpag

---

### Post by chili555 on 2011-02-27
This is depressing:  [http://www.google.com/search?source=ig&hl=en&rlz=&=&q=bug+ubuntu+sundance&btnG=Google+Search&aq=f&aqi=&aql=&oq=](http://www.google.com/search?source=ig&hl=en&rlz=&=&q=bug+ubuntu+sundance&btnG=Google+Search&aq=f&aqi=&aql=&oq=)

What is quite interesting is that in many cases, the problems with your driver are overcome with Ubuntu version 10.04 and later; you are running 8.04. Do you have any ability to upgrade to the latest 10.10 version? If you burn the live CD of 10.10, you could try it live without disturbing your current install.

Of course, you could get a different ethernet card, although I hate solving problems by throwing money at it.

I'll be around today, although in and out, so post back and we'll hopefully solve this.

---

### Post by markpag on 2011-02-27
Will try 10.10 on a cd

, today I have tried re-installing network manager (although i did not know how to clear down the config files for it.)

The ip address of paghomelinux appears in the arp table on the router but I can't ping in either direction.

will let you know how i get on

markpag

---

### Post by markpag on 2011-02-27
What a big circle!

loaded 10.04 from cd the via_rhine (eth0)  configured and could ping the router but no eth1 (tplink) and would not http but would ping the isp gateway.

10.10 much the same 

by accident (burned the wrong image) loaded a 8.04 from cd again via-rhine(eth0) ok tplink no good.

thought Hmm I wonder what would happen if i removed tplink (physically (and with prejudice:)) the via-rhine connected straight through to google.

rebooted back to the original 8.04. http straight through to google streamed some nice guitar music from youtube to test speed. works fine.

Will take a full backup

My only conclusion is that the tplink will not co exist with the via-rhine

Anyone want to buy a tplink tf3200 yours for the postage!

Chili555 manymany  thanks once again for all your help on this 
regards
markpag

---

### Post by markpag on 2011-02-28
Getting closer to the root of the problem downloaded and installed updates and somewhere between kernel 2.6 24-26 and 24-28. the network card (via-rhine eth0)  is not detected.  I have repeated the reboot several times with consistent results.

---

### Post by chili555 on 2011-02-28
Is the behavior the same if you explicitly load the module?```
sudo modprobe via-rhine
```You can get it to load automatically with:```
sudo su
echo via-rhine >> /etc/modules
exit
```Are there any informative messages here:```
dmesg | grep -e rhine -e eth
```

---

### Post by markpag on 2011-03-02
Loaded kernel 24-28 tried modprobe -via rhine, it still didn't find the card unfortunately I was rushing this morning when i tried it. I will try again this evening.
regards
markpag

---

### Post by chili555 on 2011-03-02
I'll look for your report. If the card doesn't start, run and post:```
dmesg | grep -e rhine -e eth
```Have fun at work!

---

### Post by markpag on 2011-03-02
Clearly I was half asleep this morning

kernel 24-28
loaded the card w/ modprobe then looked at the icon in the systray which showed disconnected. However it did connect for an hour or so this evening then gave up! and disconnected.

the report below is after running the modprobe command, I haven't yet tried the >>/etc/modules
regrds
markpag

pag@paghomelinux:~$ dmesg |grep -e rhine -e eth
[   29.865939] Driver 'sd' needs updating - please use bus_type methods
[   29.866203]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  159.592951] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[  159.592962] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[  159.599042] eth0: VIA Rhine II at 0xe2003000, 00:0a:e6:73:71:e7, IRQ 20.
[  159.599760] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[  159.611933] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  170.011714] eth0: no IPv6 routers present
pag@paghomelinux:~$

---

### Post by chili555 on 2011-03-02
> eth0: link up, 100Mbps, full-duplex, lpa 0x45E1Looks connected to me.

---

### Post by markpag on 2011-03-02
i will run kernel 24-28 until it gives up again and then do a dmesg
thanks again.
the line that I noticed was broken bios ! didn't like the sound of that!
regards
markpag

---

### Post by chili555 on 2011-03-02
> the line that I noticed was broken bios ! didn't like the sound of that!It is a bit scary. However, it seems to have undertaken the fix by itself. You could try updating the BIOS, or I'd also see if the later versions of Ubuntu works better. 8.04 is a bit ancient. You could try the live CD without risk.

---

### Post by markpag on 2011-03-03
Its now been running a whole day w/o falling over. Thanks for your advice I will try to move it onto 10.04 this weekend. It makes a lot of sense to be sorting problems with a new system rather than an old one. 
regards
markpag

---

### Post by chili555 on 2011-03-03
> Its now been running a whole day w/o falling over.Excellent! Are you ready to mark the thread Solved under Thread Tools?

---

### Post by seyfer on 2013-01-07
> **chili555 said:**
> Do you have more that one ethernet card? Why would that be? What does this tell us?```
sudo dhclient eth1
sudo ethtool eth1
```Are you certain the ethernet cable is attached to the TP-Link? Thanks.
**chili555**. Registered just say thank you. It's solved my problem!

---

