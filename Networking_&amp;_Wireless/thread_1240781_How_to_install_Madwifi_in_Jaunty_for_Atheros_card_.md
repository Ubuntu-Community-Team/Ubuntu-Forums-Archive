---
title: "How to install Madwifi in Jaunty for Atheros card in Dell Vostro"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by drpjkurian on 2009-08-15
Hi Everybody

Well i was using Ubuntu Hardy in my Dell Vostro A860 with an Atheros Wireless card. Initially i was not able to access my wireless which was solved by installing Madwifi. When Jaunty was released i upgraded it to Jaunty. But lo my wireless died again this time.
I tried several threads but no avail. Well i tried my luck by using this method. Please give it a try. It may work for you. Open terminal by going to Applications-->Accessories-->Terminal and type the following

1.```
sudo nano /etc/apt/sources.list
```
From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER".


2.```
sudo apt-get update && sudo apt-get upgrade
```


3.```
sudo apt-get install build-essential libssl-dev
```


4.```
sudo apt-get install linux-headers-`uname -r`
```


5.```
sudo apt-get install subversion
```


6.```
sudo -i
```


7.```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```


8.```
cd madwifi-ng
```


9.```
echo "" >> /etc/modprobe.d/blacklist
```


10.```
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
```


11.```

echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
```


12.```
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```



13.```
make && make install
```



14.```
echo ath_pci >> /etc/modules
```



Restart your machine. It should work.

Thanks for Nxion

Please note that your madwifi driver will not function after kernel updates.You have to enter as root. For that please enter the code 'sudo -i' in terminal and follow the steps from 8 as mentioned above.It worked for me, So it should work for you.

If it does not work in KDE (kubuntu) after the installation of the drivers, then please install Wicd. The code is 
```
sudo apt-get update

```
```
sudo apt-get install wicd
```

With regards
Dr Kurian

---

### Post by xpinsx on 2009-08-17
OH MY GOSH.....THANK YOU SO MUCH. i uninstalled & reinstalled ubuntu 9.04 close to 8 times, installed linux mint 7, then installed 9.04 again just to try and fix this problem. wow........amazing solution to a problem i'm sure a LOT of people face

---

### Post by Cuba71 on 2009-08-17
I'm just curious, what's wrong with doing System > Hardware Drivers and installing madwifi from there?

---

### Post by drpjkurian on 2009-08-18
Hi Cuba

This step was not working for me.

---

### Post by ladi on 2009-08-18
hi,

after following these steps, my wlan0 stopped working. i.e after typing code.... iwconfig... i get 

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

hso0      no wireless extensions.

i tried other troubleshootings and always get this message

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

i need help to get my wireless net. adapter working again. pls help.

---

### Post by pytheas22 on 2009-08-19
> I'm just curious, what's wrong with doing System > Hardware Drivers and installing madwifi from there?

The procedure above gives you a more recent version of the madwifi driver, because you're downloading the latest source code from the subversion repository and compiling it.  If the version that ships with Ubuntu works for you, it's best to stick with that, but some people benefit from a more recent build.

```

after following these steps, my wlan0 stopped working. i.e after typing code.... iwconfig... i get

lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

hso0 no wireless extensions.

i tried other troubleshootings and always get this message

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

i need help to get my wireless net. adapter working again. pls help. 
```

What's the output of these commands, in this order:
```

lsmod | grep ath
cat /etc/modprobe.d/blacklist.conf
sudo rmmod ath_pci
sudo rmmod ath9k
sudo rmmod ath5k
sudo rmmod ath_hal
sudo modprobe ath9k
sudo modprobe ath5k
lshw -C Network
dmesg | grep -e ath -e wlan
```

---

### Post by ladi on 2009-08-19
[quote=pytheas22;7809951]The procedure above gives you a more recent version of the madwifi driver, because you're downloading the latest source code from the subversion repository and compiling it.  If the version that ships with Ubuntu works for you, it's best to stick with that, but some people benefit from a more recent build.

```

after following these steps, my wlan0 stopped working. i.e after typing code.... iwconfig... i get

lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

hso0 no wireless extensions.

i tried other troubleshootings and always get this message

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

i need help to get my wireless net. adapter working again. pls help. 
```What's the output of these commands, in this order:
```

lsmod | grep ath
cat /etc/modprobe.d/blacklist.conf
sudo rmmod ath_pci
sudo rmmod ath9k
sudo rmmod ath5k
sudo rmmod ath_hal
sudo modprobe ath9k
sudo modprobe ath5k
lshw -C Network
dmesg | grep -e ath -e wlan
```[/quoe]  

after following above steps..... thanks for your concern.:confused:



ladi@lado:~$ lsmod | grep ath
ath_pci               215224  0 
wlan                  240496  1 ath_pci
ath_hal               371616  1 ath_pci
ladi@lado:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
ladi@lado:~$ sudo rmmod ath_pci
[sudo] password for ladi: 
ladi@lado:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
ladi@lado:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
ladi@lado:~$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
ladi@lado:~$ sudo rmmod ath_hal
ladi@lado:~$ sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ladi@lado:~$ sudo modprobe ath5k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ladi@lado:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:20:bb:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:0f:d6:64
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:97:98:c6:c2:93
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ladi@lado:~$ dmesg | grep -e ath -e wlan
[    4.166186] device-mapper: multipath: version 1.0.5 loaded
[    4.166189] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 4822.244628] ath9k: 0.1
[ 4822.244741] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4822.244767] ath9k 0000:08:00.0: setting latency timer to 64
[ 4822.688588] phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 4822.734764] Registered led device: ath9k-phy0:radio
[ 4822.734793] Registered led device: ath9k-phy0:assoc
[ 4822.734821] Registered led device: ath9k-phy0:tx
[ 4822.734849] Registered led device: ath9k-phy0:rx
[ 4827.135498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
ladi@lado:~$

---

### Post by pytheas22 on 2009-08-19
ladi: I'm guessing the problem has to do with ath_pci controlling your card instead of ath9k, which would have been the default originally.  You can run these commands to force the system to use ath9k and hopefully get back to where you were before following the tutorial above:
```

echo blacklist ath_pci | sudo tee -a /etc/modprobe.d/blacklist.conf
echo ath9k | sudo tee -a /etc/modules
sudo update-initramfs -k all -u
```

Then reboot and let me know if things work better.  If not, please post the output of:
```

dmesg | grep -e wlan -e ath
lsmod | grep ath
sudo iwlist scan
```

---

### Post by ladi on 2009-08-20
thanks! it's working again.
though after a while it stopped working..... then i reboot again and it started working again.

i appreciate your effort.

---

### Post by DamITman on 2009-09-01
Kudos! I just adopted Linux yesterday after 12 years of windows and I was able to do this, very simple and elegant at the same time.

One more reason for my windows disks to start collecting dust. :popcorn:
Off subject, but I really do love Ubuntu, it is making the change from everything down to the filesystems incredibly simple and easy to adapt to.

*edit* This should be stickied.

---

### Post by erictherev on 2009-09-23
Doc -
I've followed all of the above steps, to no avail. here are the results of the commands you listed in your last post:

```
[COLOR="SeaGreen"]root@Myrkr:/home/nomad# dmesg | grep -e wlan -e ath  [/COLOR]                          
[    3.377049] device-mapper: multipath: version 1.0.5 loaded                  
[    3.377059] device-mapper: multipath round-robin: version 1.0.0 loaded      
[   12.843091] ath_pci 0000:03:00.0: enabling device (0004 -> 0006)            
[   12.843113] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.843135] ath_pci 0000:03:00.0: setting latency timer to 64               
[   13.337635] MadWifi: ath_attach: Switching rfkill capability off.           
[   13.387832] ath_pci: wifi0: Atheros 5424/2424: mem=0xd0000000, irq=17       
[   13.613835] ath9k: 0.1                                                      
[   33.732125] ath0: no IPv6 routers present                                   
[COLOR="SeaGreen"]root@Myrkr:/home/nomad# lsmod | grep ath    [/COLOR]                                   
ath9k                 263224  0                                                
mac80211              217208  1 ath9k                                          
ath_rate_sample        20480  1                                                
ath_pci               211640  0                                                
wlan                  239984  4 wlan_scan_sta,ath_rate_sample,ath_pci          
ath_hal               371488  3 ath_rate_sample,ath_pci                        
led_class              12036  2 ath9k,acer_wmi                                 
[COLOR="SeaGreen"]root@Myrkr:/home/nomad# sudo iwlist scan  [/COLOR]                                     
lo        Interface doesn't support scanning.                                  

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:22:6B:66:A2:6D
                    ESSID:"patricia"          
                    Mode:Master               
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on                                       
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s    
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s     
                              12 Mb/s; 48 Mb/s                              
                    Extra:bcn_int=100                                       
                    IE: IEEE 802.11i/WPA2 Version 1                         
                        Group Cipher : TKIP                                 
                        Pairwise Ciphers (2) : CCMP TKIP                    
                        Authentication Suites (1) : PSK                     
                    IE: WPA Version 1                                       
                        Group Cipher : TKIP                                 
                        Pairwise Ciphers (2) : CCMP TKIP                    
                        Authentication Suites (1) : PSK                     
[COLOR="Blue"]          Cell 02 - Address: 00:30:BD:FE:21:EE                              
                    ESSID:"Galactic_Empire"                                 
                    Mode:Master                                             
                    Frequency:2.412 GHz (Channel 1)                         
                    Quality=41/70  Signal level=-54 dBm  Noise level=-95 dBm
                    Encryption key:on                                       
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100[/COLOR]
          Cell 03 - Address: 00:30:BD:FB:B7:73
                    ESSID:"SpechtHome"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:1E:E5:32:33:A4
                    ESSID:"danielhome11"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

pan0      Interface doesn't support scanning.


```

Cell 02 is what I'm attempting to connect to. This is an encrypted connection which I do have the keys for, and I had entered them previously. After updating, I no longer have the option to connect to anything.

Thanks for helping with this issue.

---

### Post by pytheas22 on 2009-09-23
erictherev: you might want to try connecting with wicd, an alternate connection manager that sometimes work better.  To install wicd, type:
```

sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.

(wicd will force you to uninstall NetworkManager.  If you ever want NM back, just type 'sudo apt-get install network-manager-gnome'.)

---

### Post by erictherev on 2009-09-25
I found the solution for the problem with my Acer Aspire One netbook... Reinstall Kubuntu, and NEVER activate the proprietary drivers! :mrgreen:

---

### Post by drpjkurian on 2009-09-29
Hi Erictherev

I think Wicd is a best option for KDE after installing Madwifi.
Well I have both Gnome and KDE for my Ubuntu Jaunty. After the installation of madwifi, my wireless worked only in Gnome and not in KDE.
The issue was solved by installing Wicd in KDE.

With
Regards
Dr Kurian

---

### Post by killians31 on 2009-09-30
> **pytheas22 said:**
> ladi: I'm guessing the problem has to do with ath_pci controlling your card instead of ath9k, which would have been the default originally.  You can run these commands to force the system to use ath9k and hopefully get back to where you were before following the tutorial above:
```

echo blacklist ath_pci | sudo tee -a /etc/modprobe.d/blacklist.conf
echo ath9k | sudo tee -a /etc/modules
sudo update-initramfs -k all -u
```Then reboot and let me know if things work better.  If not, please post the output of:
```

dmesg | grep -e wlan -e ath
lsmod | grep ath
sudo iwlist scan
```


I think i might be having the same issues. When i completed the full steps in the first post, my 'connect to wireless network' section of the network manager went away. After performing the steps you posted above, i got that section back within the network manager post-reboot.

I still however, am having difficulties getting my AR928x to work on my asus G50v.

I installed wicd, but this is reluctant to work as well.

The following output as requested from the commands above:
ben@ubuntu:~$ dmesg | grep -e wlan -e ath
[    3.296836] device-mapper: multipath: version 1.0.5 loaded
[    3.296838] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.100018] ath9k: 0.1
[   11.100062] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.100074] ath9k 0000:03:00.0: setting latency timer to 64
[   11.532250] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.563874] Registered led device: ath9k-phy0:radio
[   11.563890] Registered led device: ath9k-phy0:assoc
[   11.563905] Registered led device: ath9k-phy0:tx
[   11.563919] Registered led device: ath9k-phy0:rx
[   20.920463] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  266.388452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
--------------------------------------------------------------------------------------------------------------------
ben@ubuntu:~$ lsmod | grep ath
ath9k                 263224  0 
mac80211              217208  1 ath9k
ath_pci               211640  0 
wlan                  239984  1 ath_pci
ath_hal               371488  1 ath_pci
led_class              12036  2 ath9k,asus_laptop

--------------------------------------------------------------------------------------------------------------------
ben@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
--------------------------------------------------------------------------------------------------------------------

Any help is greatly appreciated!

Thanks!

---

### Post by pytheas22 on 2009-09-30
killians31: please try running this command to blacklist ath_pci:
```

echo blacklist ath_pci | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Then power down your computer completely and remove the power cord for a minute (and the battery as well if this is a laptop).  Then boot back into Ubuntu.  Does the wireless work?

I suspect that your problem possibly is the result of the wireless card being left in a state that the Linux driver can't control.  Power down completely will cause it to default back to the normal state, which sometimes helps.

---

### Post by killians31 on 2009-10-01
Looks like it worked! Thanks for the GREAT tutorial and help guys, i have been trying to get these card working for a few weeks!

---

### Post by mo0nykit on 2009-10-13
Hi!

This HOWTO also works for Acer Aspire 4520. Maybe we can update the title? Thanks! :D

---

### Post by drpjkurian on 2009-10-14
> **mo0nykit said:**
> Hi!

This HOWTO also works for Acer Aspire 4520. Maybe we can update the title? Thanks! :D

Hi
I am glad to know that it works in Acer Aspire, I will definitely update the title.

With regards
Dr Kurian

---

### Post by anibal.m6gic on 2009-10-31
5 *****
Many Thanks works fine for me.

---

### Post by drpjkurian on 2009-11-01
> **anibal.m6gic said:**
> 5 *****
Many Thanks works fine for me.

Hi

You are most welcome

With regards
Dr Kurian

---

### Post by crgutierrez on 2009-11-09
It works on **_Acer AO 751h_** as well!
Jaunty 9.04 on kernel 15 and after updgrade to kernel 16

MUCHAS GRACIAS!!

---

### Post by drpjkurian on 2009-11-10
> **crgutierrez said:**
> It works on **_Acer AO 751h_** as well!
Jaunty 9.04 on kernel 15 and after updgrade to kernel 16

MUCHAS GRACIAS!!

Hi
Thank you for your information

With regards
Dr Kurian

---

### Post by drskartik on 2009-11-11
Hi!
I had the same problem: [https://answers.launchpad.net/ubuntu/+question/72059](https://answers.launchpad.net/ubuntu/+question/72059).
Now I have upgraded to Karmic, the wifi issue has been sorted out, and i connect effortlessly. With Jaunty , I had to reinstall the driver after every major update.
regards
Kartik

---

### Post by french boy on 2009-12-28
ok, I'm sorry, but it DIDN'T work. I installed madwifi and wicd by following the HOWTO, and wicd say he can't find the IP adress; I have ubuntu 9.10 amd 64, and a wi-fi card ath 5k. does amyone know what I've got to do? :confused::confused::confused:

---

### Post by drpjkurian on 2009-12-28
> **french boy said:**
> ok, I'm sorry, but it DIDN'T work. I installed madwifi and wicd by following the HOWTO, and wicd say he can't find the IP adress; I have ubuntu 9.10 amd 64, and a wi-fi card ath 5k. does amyone know what I've got to do? :confused::confused::confused:

Hi french boy
Please note that these instructions are meant for intel chipsets namely 32 bit

Dr Kurian

---

### Post by drpjkurian on 2009-12-28
> **french boy said:**
> ok, I'm sorry, but it DIDN'T work. I installed madwifi and wicd by following the HOWTO, and wicd say he can't find the IP adress; I have ubuntu 9.10 amd 64, and a wi-fi card ath 5k. does amyone know what I've got to do? :confused::confused::confused:

Hi French boy
I did some meagre googling and found this. Let it be a beginning for you
[http://dir.filewatcher.com/d/Ubuntu/...ib/net.0.0.htm](http://dir.filewatcher.com/d/Ubuntu/...ib/net.0.0.htm)
[http://spacebison.com/files/atheros-...rdy-heron.html](http://spacebison.com/files/atheros-...rdy-heron.html)
Though it is an instruction of Hardy heron, You can give a try.
Best of luck

---

### Post by french boy on 2009-12-29
drpkkurian, I saw on the net that my wi-fi card (ar5001) is not working under linux. Could this be true? I never had wi-fi problems before, on vista. Do I have to buy an other card? Thanks for your help.

---

### Post by drpjkurian on 2009-12-30
> **french boy said:**
> drpkkurian, I saw on the net that my wi-fi card (ar5001) is not working under linux. Could this be true? I never had wi-fi problems before, on vista. Do I have to buy an other card? Thanks for your help.

Hi French boy
If Linux drivers don't work / are not available for your card you might try ndiswrapper. It allows you to use Windows drivers with the Linux kernel (with some limitations).  [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419) has been thanked a lot, so maybe it also helps you.

---

### Post by macho on 2009-12-30
Thanks for the how-to.  It got me a little bit farther with my wireless card.  Previously I wasn't getting any wireless interface, but after installing the madwifi cvs code, I get an ath0:

```
$ iwconfig ath0
ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Unfortunately, it doesn't seem to be able to detect any of the other several wireless networks in the area. Any thoughts on what I can do?

```
$ iwlist ath0 scan
ath0      No scan results
```

Before following this howto I began a [thread about this problem elsewhere]("http://ubuntuforums.org/showthread.php?t=1367021").  I'm running hardy.

---

### Post by drpjkurian on 2009-12-30
> **macho said:**
> Thanks for the how-to.  It got me a little bit farther with my wireless card.  Previously I wasn't getting any wireless interface, but after installing the madwifi cvs code, I get an ath0:

```
$ iwconfig ath0
ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Unfortunately, it doesn't seem to be able to detect any of the other several wireless networks in the area. Any thoughts on what I can do?

```
$ iwlist ath0 scan
ath0      No scan results
```

Before following this howto I began a [thread about this problem elsewhere]("http://ubuntuforums.org/showthread.php?t=1367021").  I'm running hardy.

Hi
Please note that the command line for installing madwifi for Hardy is little different from other releases.
The URL for these instructions is [http://ubuntuforums.org/showthread.php?t=942195](http://ubuntuforums.org/showthread.php?t=942195)

Anyway you are having Pytheas to help you in your case. He is better than me.

Dr Kurian

---

### Post by pytheas22 on 2009-12-31
> Anyway you are having Pytheas to help you in your case. He is better than me.


Thanks for the kind words.  Obviously you've also ably helped many people in this thread.

---

### Post by drpjkurian on 2010-01-01
> **pytheas22 said:**
> Thanks for the kind words.  Obviously you've also ably helped many people in this thread.

Dear Pytheas
:p:p:p

---

### Post by jchute on 2010-02-01
[COLOR=black]drpjkurian you legend! can continue with aircrack-ng now![/COLOR][URL="http://ubuntuforums.org/member.php?u=805294"]
[/URL]

---

### Post by uwe.koch.k on 2010-10-06
Hi. The patch to recompile after each kernel update worked fine for me up to one month ago. I think the upgraded version was 2.6.32 . So I decided to go to maverick (beta), where I get same error after running make & make install:

root@uwe-desktop:~/madwifi-ng# make && make install
./kernelversion.c:13: fatal error: linux/utsrelease.h: No existe el archivo o directorio
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Alto.

Any idea how to work around the problem?

Thanks in advance,

---

### Post by uwe.koch.k on 2010-10-06
> **uwe.koch.k said:**
> Hi. The patch to recompile after each kernel update worked fine for me up to one month ago. I think the upgraded version was 2.6.32 . So I decided to go to maverick (beta), where I get same error after running make & make install:

root@uwe-desktop:~/madwifi-ng# make && make install
./kernelversion.c:13: fatal error: linux/utsrelease.h: No existe el archivo o directorio
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Alto.

Any idea how to work around the problem?

Thanks in advance,

I decided to install from scratch. It worked like a charm again. Hope this helps others.

---

### Post by drpjkurian on 2010-10-07
Hi
Good to know that it worked

---

### Post by Speedwagon on 2010-10-12
replied to the wrong thread I had open.

---

### Post by uwe.koch.k on 2011-05-05
> **drpjkurian said:**
> Hi French boy
I did some meagre googling and found this. Let it be a beginning for you
[http://dir.filewatcher.com/d/Ubuntu/...ib/net.0.0.htm](http://dir.filewatcher.com/d/Ubuntu/...ib/net.0.0.htm)
[http://spacebison.com/files/atheros-...rdy-heron.html](http://spacebison.com/files/atheros-...rdy-heron.html)
Though it is an instruction of Hardy heron, You can give a try.
Best of luck

Hi, could you please write the webpages [I]in-extenso[I], since they are not complete. I also have an Acer Aspire 4520, but run an 64 bit distro on it (natty), and would like to see if I'm capable to see my wifi  work again. It did it up to 2.6.32-*

Anyway, it works like a charm on 32 bit distros, even Natty.

---

