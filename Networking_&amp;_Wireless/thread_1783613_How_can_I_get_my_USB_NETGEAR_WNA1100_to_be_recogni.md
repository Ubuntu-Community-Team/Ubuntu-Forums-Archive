---
title: "How can I get my USB NETGEAR WNA1100 to be recognized"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by JASONFUSARO on 2011-06-16
I have been checking threads, Google etc. from what I have gathered I might have wasted my money on the Netgear adapter, I have not had any problems connecting to the network but I am operating at 54 MBs on my Realtek internal adapter

jasonfusaro@jasonfusaro-ML6720:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 0458:00cc KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
**[COLOR="Red"]Bus 002 Device 006: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader[/COLOR]**
Bus 002 Device 005: ID 03f0:4507 Hewlett-Packard 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 0846:9030 NetGear, Inc. 
Bus 002 Device 002: ID 1058:071a Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**[COLOR="#ff0000"]Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter[/COLOR]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



[COLOR="Red"]In Windows Vista on my dual boot everything is ok but it only operates at 65 MBs. But it is recognized, and I tried to locate a linux driver but can't find one. Also would I have better luck with a Belkin adapter that was my first choice but you know salesman, convinced me otherwise! Had originally bought a dual band for 600 Mbs but that didn't work either, the router is a Netgear N150.[/COLOR]


===========================================================
jasonfusaro@jasonfusaro-ML6720:~$ sudo lshw -short -quiet
H/W path               Device       Class       Description
===========================================================
                                    system      ML6720 ()
/0                                  bus         Motherboard
/0/0                                memory      108KiB BIOS
/0/4                                processor   Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.
/0/4/5                              memory      64KiB L1 cache
/0/4/6                              memory      1MiB L2 cache
/0/f                                memory      3GiB System Memory
/0/f/0                              memory      1GiB DIMM DDR2 Synchronous 533 MHz (1.9 ns
/0/f/1                              memory      2GiB DIMM DDR2 Synchronous 533 MHz (1.9 ns
/0/100                              bridge      Mobile PM965/GM965/GL960 Memory Controller
/0/100/2                            display     Mobile GM965/GL960 Integrated Graphics Con
/0/100/2.1                          display     Mobile GM965/GL960 Integrated Graphics Con
/0/100/1a                           bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1a.1                         bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1a.7                         bus         82801H (ICH8 Family) USB2 EHCI Controller 
/0/100/1b                           multimedia  82801H (ICH8 Family) HD Audio Controller
/0/100/1c                           bridge      82801H (ICH8 Family) PCI Express Port 1
/0/100/1c.2                         bridge      82801H (ICH8 Family) PCI Express Port 3
/0/100/1d                           bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1d.1                         bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1d.2                         bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1d.7                         bus         82801H (ICH8 Family) USB2 EHCI Controller 
/0/100/1e                           bridge      82801 Mobile PCI Bridge
/0/100/1f                           bridge      82801HEM (ICH8M) LPC Interface Controller
/0/100/1f.1            scsi0        storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE Controlle
/0/100/1f.1/0.0.0      /dev/cdrom1  disk        DVDRAM GSA-T20F
/0/100/1f.1/0.0.0/0    /dev/cdrom1  disk        
/0/100/1f.2            scsi2        storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Con
/0/100/1f.2/0.0.0      /dev/sda     disk        500GB WDC WD5000BEVT-0
/0/100/1f.2/0.0.0/1    /dev/sda1    volume      378GiB Extended partition
/0/100/1f.2/0.0.0/1/5  /dev/sda5    volume      375GiB Linux filesystem partition
/0/100/1f.2/0.0.0/1/6  /dev/sda6    volume      3061MiB HPFS/NTFS partition
/0/100/1f.2/0.0.0/2    /dev/sda2    volume      87GiB Windows NTFS volume
/0/100/1f.3                         bus         82801H (ICH8 Family) SMBus Controller
/0/1                   scsi5        storage     
/0/1/0.0.0             /dev/sdb     disk        500GB My Passport 071A
/0/1/0.0.0/1           /dev/sdb1    volume      465GiB Windows NTFS volume
/0/1/0.0.1                          generic     SES Device
/0/2                   scsi6        storage     
/0/2/0.0.0             /dev/sdc     disk        319GB External HDD
/0/2/0.0.0/1           /dev/sdc1    volume      297GiB Windows NTFS volume
/0/2/0.0.1             /dev/cdrom   disk        Virtual CD 4507
/0/2/0.0.1/0           /dev/cdrom   disk        
/0/2/0.0.1/0/1                      volume      1KiB Apple partition map
/0/2/0.0.1/0/2                      volume      881KiB Apple HFS
/0/3                   scsi7        storage     
/0/3/0.0.0             /dev/sdd     disk        7969MB SCSI Disk
/0/3/0.0.0/1           /dev/sdd1    volume      7596MiB Windows NTFS volume
/1                                  power       Lithium Ion Battery
[B][COLOR="#ff0000"]/2                     wlan0        network     Wireless interface
/3                     wlan1        network     Wireless interface[/COLOR][/B]


Which one of the above is the realtek and which one is the NETGEAR??



This is my first post, and I don't know if this is too much info to place in a message. Also if anyone responds with help, could you please comment with an explanation of any commands, I am new to Linux, but I am real happy and impressed and really don't wish to be a Windoean anymore, I wish to become a full fledged Linuxean.

Thanks

---

### Post by JASONFUSARO on 2011-06-16
I found this command so I am kinda answering my own question there both working but wlan1 seems to be the Netgear adapter **[COLOR="Red"]IEEE 802.11bgn[/COLOR]**

jasonfusaro@jasonfusaro-ML6720:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"270guest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E2:91:F5:70:B1:0F   
         [COLOR="#ff0000"] Bit Rate=54 Mb/s[/COLOR]   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:0ff   Fragment thr:0ff
          Power Management:0ff
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2719  Invalid misc:2749   Missed beacon:0

wlan1     IEEE 802.11bgn ESSID:"270guest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E2:91:F5:70:B1:0F   
          [COLOR="Red"]Bit Rate=1 Mb/s[/COLOR]   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:0ff   Fragment thr:0ff
          Power Management:0ff
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

vboxnet0  no wireless extensions.



I wonder if I disable wlan0 if it will have any effect on wlan1 and if I will operate at 150Mbs. I don't want to mess with it just yet because everything is working ok, you know If it works don't mess with it, but I would like to be running at 150 instead of 56. whats up with that bit rate there of 1 Mb/s ????

---

### Post by JASONFUSARO on 2011-06-16
jasonfusaro@jasonfusaro-ML6720:~$ sudo iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: E2:91:F5:70:B1:0F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"270guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001aae078bf4
                    Extra: Last beacon: 1100ms ago
                    IE: Unknown: 00083237306775657374
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


wlan1     Scan completed :
          Cell 01 - Address: E2:91:F5:70:B1:0F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"270guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001aae26d6d8
                    Extra: Last beacon: 410ms ago
                    IE: Unknown: 00083237306775657374
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

[COLOR="Red"]this is the output from the iwlist command[/COLOR]

should I do a sudo restart to reset manually????

---

### Post by nbound on 2011-06-16
The N150 is an ar9170 device afaik. ur probably using the ar9170usb driver, which is b/g only. if ur using 11.04 u can blacklist ar9170usb, and use the carl9170 driver instead which supports b/g/n :)

---

### Post by walt.smith1960 on 2011-06-16
What do you see when you left-click network manager? Do you see two connections? If so, can you click "disconnect" on the RealTek one? I'm typing this from a machine using the Netgear WNA1100.  It was plug & play in 11.04.  Here are the relevant entries in lsmod:

mac80211              294370  1 ath9k_htc
ath9k_common           13851  1 ath9k_htc
ath9k_hw              323077  2 ath9k_htc,ath9k_common
ath                    23773  2 ath9k_htc,ath9k_hw
cfg80211              178528  3 ath9k_htc,mac80211,ath

Do you have something similar?  If so, your WNA is recognized and installed.  If you can disconnect the RealTek adapter temporarily in network manager and you still have a wireless connection you could blacklist the realtek module to prevent it loading in the future.

---

### Post by JASONFUSARO on 2011-06-16
Where is network manager? I have Network indicator Applet on my top panel, that shows me available network connections. Is in apps or something I don't think I have it installed?

Nope I don't but there are three or four Wicd, Network, Network selection,Knetwork Manager, which do I install?

---

### Post by walt.smith1960 on 2011-06-16
> **JASONFUSARO said:**
> Where is network manager? I have Network indicator Applet on my top panel, that shows me available network connections. Is in apps or something I don't think I have it installed?

Network indicator applet is it.  When I've had two wireless adapters active in the past, both have showed up. I was able to disconnect or disable one to be sure the other was indeed working before disabling the other permanently.  I had a similar situation to yours in that I wanted to disable a pci 54G device that seemed to be preferred over a USB N device.

---

### Post by JASONFUSARO on 2011-06-16
I have my wlan1 active and wlan0 inactive which is the realtek, but I am running at a snail pace of 1MB/s?? Otherwise it appears to be functioning ok!

How do I blacklist the realtek again, can you comment the the terminal commands, ie. simple explanation of what it does and will the process be reversible?? Just in case

Thank you

---

### Post by JASONFUSARO on 2011-06-16
I installed the IEEE 802.11bgn - Rutilt

It shows

Mode                   Managed

Channel                 11(2.462 GHz)

Tx rate                  1 Mbps

Link quality                 44%


Signal level               -67 dBm


should I select the options up and change interface or something???

I installed wireshark to took a quick peek seems kinda complicated, can I do anything with that software?
or xfld configure network that is showing both cards


Could it be a router problem? I am using a guest hookup off my neighbor downstairs, he has the router. I first bought a Netgear Dual band 600, but that was returned, he was up here trying to get it going, the router is an N150 so I returned it and got this adapter but 
it still 1Mb/s???

---

### Post by walt.smith1960 on 2011-06-16
> **JASONFUSARO said:**
> I have my wlan1 active and wlan0 inactive which is the realtek, **but I am running at a snail pace of 1MB/s?? **Otherwise it appears to be functioning ok!

How do I blacklist the realtek again, can you comment the the terminal commands, ie. simple explanation of what it does and will the process be reversible?? Just in case

Thank you

My device says the same thing-1 MB/sec.  Don't believe it.  I pay attention to how long it takes down a file relative to the Internet connection speed.  If you have another networked machine, time how long it takes to transfer a largish file there and back.

As far as how to blacklist the RealTek adapter,  you need to open a text editor in an administrator account and open with sudo privileges.  Navigate to /etc/modprobe.d/blacklist.conf. Scroll to the bottom of that file and add a line blacklisting the RealTek module.  Save then restart.  If you want to undo, reopen the file and delete that line, or add # to the start of that line and save to disable temporarily. That should do it, I think.

---

