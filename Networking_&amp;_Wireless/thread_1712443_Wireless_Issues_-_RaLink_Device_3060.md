---
title: "Wireless Issues - RaLink Device 3060"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by bnor82 on 2011-03-22
Hi I can see there are a number of posts about this however I have been going through them for hours now and still having problems!

desktop:~$ lspci  
 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate  
 00:01.0 PCI bridge: ASRock Incorporation Device 9602  
 00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)  
 00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)  
 00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]  
 00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller  
 00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller  
 00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)  
 00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller  
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)  
 00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller  
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge  
 00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control  
 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control  
 01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]  
 02:00.0 USB Controller: Device 1b73:1000 (rev 01)  
 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)  
 04:06.0 Network controller: RaLink Device 3060  
 
  desktop:~$ ifconfig  
 eth1      Link encap:Ethernet  HWaddr 00:25:22:8e:d5:97   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:42 Base address:0xc000  
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)  
 
 wlan0     Link encap:Ethernet  HWaddr 00:06:4f:98:fd:e1   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  

 desktop:~$ lsmod  
 Module                  Size  Used by  
 binfmt_misc             7984  1  
 parport_pc             30086  0  
 ppdev                   6804  0  
 arc4                    1497  2  
 rt2800pci              10528  0  
 rt2800lib              32002  1 rt2800pci  
 rt2x00usb              11316  1 rt2800lib  
 rt2x00pci               6993  1 rt2800pci  
 crc_ccitt               1699  1 rt2800pci  
 rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci  
 led_class               3393  1 rt2x00lib  
 mac80211              267099  3 rt2x00usb,rt2x00pci,rt2x00lib  
 cfg80211              170485  2 rt2x00lib,mac80211  
 eeprom_93cx6            1789  1 rt2800pci  
 snd_hda_codec_realtek   300173  1  
 snd_hda_intel          26147  2  
 snd_hda_codec         100951  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               6660  1 snd_hda_codec  
 snd_pcm                89104  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi            5932  0  
 snd_rawmidi            22207  1 snd_seq_midi  
 fglrx                2523725  34  
 snd_seq_midi_event      7291  1 snd_seq_midi  
 snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              23850  2 snd_pcm,snd_seq  
 snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq  
 joydev                 11395  0  
 snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                62080  0  
 serio_raw               4910  0  
 edac_core              46822  0  
 edac_mce_amd            9387  0  
 i2c_piix4              10047  0  
 k10temp                 3535  0  
 xhci_hcd               60496  0  
 soundcore               1240  1 snd  
 snd_page_alloc          8588  2 snd_hda_intel,snd_pcm  
 shpchp                 34910  0  
 lp                     10201  0  
 parport                37032  3 parport_pc,ppdev,lp  
 usbhid                 42030  0  
 hid                    84710  1 usbhid  
 r8169                  42254  0  
 mii                     5261  1 r8169  
 ahci                   22210  0  
 pata_atiixp             4405  2  
 libahci                26148  1 ahci  

 desktop:~$ sudo lshw -C network  
   *-network                
        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth1  
        version: 03  
        serial: 00:25:22:8e:d5:97  
        size: 10MB/s  
        capacity: 1GB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s  
        resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feae0000-feafffff  
   *-network  
        description: Wireless interface  
        product: RaLink  
        vendor: RaLink  
        physical id: 6  
        bus info: pci@0000:04:06.0  
        logical name: wlan0  
        version: 00  
        serial: 00:06:4f:98:fd:e1  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-28-generic firmware=N/A latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn  
        resources: irq:21 memory:febf0000-febfffff  

 desktop:~$ uname -mr  
 2.6.35-28-generic x86_64
 
desktop:~$ iwconfig
lo        no wireless extensions.
eth1      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
desktop:~$ iwlist scan
lo        Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
wlan0     No scan results

I have also tried blacklisting the following but to no avail.

blacklist rt2800lib              
blacklist rt2x00usb              
blacklist rt2x00pci
blacklist mac80211              
blacklist cfg80211

If anyone has any suggestions on how I can get this working please get in contact or post.

Many thanks in advance!

---

### Post by RedSingularity on 2011-03-22
Run the command:

lspci -v

And only paste the output under "04:06.0 Network controller: RaLink Device 3060"

---

### Post by bnor82 on 2011-03-22
RedSingularity, thanks for the reply! Below is the output


04:06.0 Network controller: RaLink Device 3060
    Subsystem: RaLink Device 3060
    Flags: bus master, slow devsel, latency 32, IRQ 21
    Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

---

### Post by RedSingularity on 2011-03-22
Run:

sudo ifconfig wlan0 up

Then run ifconfig again and post the output of the wlan0 section.

---

### Post by MooPi on 2011-03-23
If all else fails this is my tutorial on the rt3060 chip
This is an amended version from the original due to the change in driver status in this link
[http://ubuntuforums.org/showthread.php?t=1608095]("http://ubuntuforums.org/showthread.php?t=1608095")
Download the Ralink driver from this location: [http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")
Unpack the archive and navigate to the driver folder.
```
sudo apt-get install build-essential
```
I then followed the instructions in the README file.
Navigate to downloaded_driver_folder/os/linux and open config.mk in a text editor.
Find and set
HAS_WPA_SUPPLICANT=y
and also set
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
Open a terminal in the driver folder and type
```
sudo make
``````
sudo make install
```
Now you'll need to load the driver
```
sudo modprobe rt3562sta
```
```
sudo ifconfig ra0 inet up
```
After you successfully connect add the driver to /etc/modules so it it would load at startup. This is a copy of mine

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rt3562sta.ko
```
It may also be necessary to copy RT2860STA.dat to /etc/Wireless/RT2860STA/RT2860STA.dat
```
cp RT2860STA.dat /etc/Wireless/RT2860STA/
```
You may want to edit and proofread your /etc/modprobe.d/blacklist.conf to include all the modules that are loading erroneously. This may or may not be necessary as I just loaded this driver and none of these modules are showing in lsmod. Add at the end of blacklist.conf
```
blacklist_rt2800pci
blacklist_rt2800lib
blacklist_rt2800usb
blacklist_rt2x00pci
blacklist_rt2x00lib
blacklist_rt2x00usb
```
Good luck and post back your results and mark solved if this works.

---

### Post by bnor82 on 2011-03-23
Moopi, Thanks for you response I will try this later when i get back from work.

RedSingularity, Again thanks for the response. Here is the output


desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:06:4f:98:fd:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by bnor82 on 2011-03-23
Have tried re-doing all of this but now i get the following 

desktop:~/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make
make -C tools
make[1]: Entering directory `/home/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
desktop:~/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make install
make: Nothing to be done for `install'.

Any ideas???

---

### Post by MooPi on 2011-03-23
I'm not certain what has transpired before so lets start with a clean slate. Open a terminal in the driver folder.
Make certain you have "build-essential" installed

```
sudo make clean
sudo make
sudo make install
sudo modprobe rt3562sta
sudo ifconfig ra0 inet up
```Each of these seperately. Complete the rest of the instructions in order.

---

### Post by shalinmangar on 2011-03-26
Thanks MooPi! I was able to make it work with your instructions.

---

### Post by RedSingularity on 2011-03-26
> **shalinmangar said:**
> Thanks MooPi! I was able to make it work with your instructions.

If you get the chance, mark the thread as solved for other users.  Thanks :)

---

### Post by bnor82 on 2011-04-01
Right I have tried this again but am still having problems. To be fair it is probably me just being a muppet but I really want to get this working so would really appreciate a hand in getting this resolved.
So far I have rebuilt my computer so it was a fresh install.

1. sudo apt-get install build-essential -FINE
2. Downloaded driver file and modified as per instructions **(I think)** please see attached files.
3. sudo make - FINE
4. sudo make install - FINE
5. sudo modprobe rt3562sta - FINE
6. desktop:~/Downloads/ralink$ sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device 
**(NOT SURE IF THIS IS A PROBLEM AS I HAVE A INTERFACE CALLED WLAN0)**
so
7. desktop:~/Downloads/ralink$ sudo ifconfig wlan0 inet up - FINE
8. lsmod 

Module                  Size  Used by
rt3562sta             922687  0 

I am still unable to see any wireless networks, wireless interface does not show in System, Preferences, Network Connections, Wireless Tab. 
Wireless icon in top right hand corner just has a big red exclamation mark on it.

lspci -v

04:06.0 Network controller: RaLink Device 3060
    Subsystem: RaLink Device 3060
    Flags: bus master, slow devsel, latency 32, IRQ 21
    Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt3562sta, rt2800pci

Have added the following to the blacklist

blacklist_rt2800pci
blacklist_rt2800lib
blacklist_rt2800usb
blacklist_rt2x00pci
blacklist_rt2x00lib
blacklist_rt2x00usb

Have added the following to /etc/modules 

rt3562sta.ko

Reboot still no joy. Please can some one help get this sorted or I am just going to have to buy another card :(

Many thanks in advance for you assistance!!!!

---

### Post by MooPi on 2011-04-01
Can you attach your [COLOR="Blue"]downloaded_driver_folder/os/linux/config.mk[/COLOR]
 So we can take a look ?

---

### Post by bnor82 on 2011-04-02
The config.mk file is located in the attached file.

Many thanks

---

### Post by MooPi on 2011-04-02
I don't mean to pester but on your description of steps there is a missing step for a clean install. At the beginning of the process to clear out old info you must make clean.You don't need to re-download any info just use the existing folder for the driver.So can we start all over again ?
```
[COLOR="Teal"]sudo make clean[/COLOR]
sudo make
sudo make install
sudo modprobe rt3562sta
sudo ifconfig ra0 inet up
```
The text in teal color is the important step. You may need to reboot to finalize these steps to initialize the device.

---

### Post by leojm77 on 2012-05-28
> **bnor82 said:**
> Right I have tried this again but am still having problems. To be fair it is probably me just being a muppet but I really want to get this working so would really appreciate a hand in getting this resolved.
So far I have rebuilt my computer so it was a fresh install.

1. sudo apt-get install build-essential -FINE
2. Downloaded driver file and modified as per instructions **(I think)** please see attached files.
3. sudo make - FINE
4. sudo make install - FINE
5. sudo modprobe rt3562sta - FINE
6. desktop:~/Downloads/ralink$ sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device 
**(NOT SURE IF THIS IS A PROBLEM AS I HAVE A INTERFACE CALLED WLAN0)**
so
7. desktop:~/Downloads/ralink$ sudo ifconfig wlan0 inet up - FINE
8. lsmod 

Module                  Size  Used by
rt3562sta             922687  0 

I am still unable to see any wireless networks, wireless interface does not show in System, Preferences, Network Connections, Wireless Tab. 
Wireless icon in top right hand corner just has a big red exclamation mark on it.

lspci -v

04:06.0 Network controller: RaLink Device 3060
    Subsystem: RaLink Device 3060
    Flags: bus master, slow devsel, latency 32, IRQ 21
    Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt3562sta, rt2800pci

Have added the following to the blacklist

blacklist_rt2800pci
blacklist_rt2800lib
blacklist_rt2800usb
blacklist_rt2x00pci
blacklist_rt2x00lib
blacklist_rt2x00usb

Have added the following to /etc/modules 

rt3562sta.ko

Reboot still no joy. Please can some one help get this sorted or I am just going to have to buy another card :(

Many thanks in advance for you assistance!!!!

**********************************************************

Hi, the procedure described by Moopi is correct except for underscores in the blacklist, it must be written like this:

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2800usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2x00usb

Regards!

---

### Post by branchi on 2012-06-17
MooPi, this worked for me as well - thank you!
However, I noticed that after upgrade to 12.04 wireless was gone.
I retraced all your steps and got it working.
Today I did some updates as suggested by Update Manager.
Noting special, usual routine.
It asked for restart and once again wireless vanished.
Once again, I retraced all your steps and got it working :-)
Is there an antidote for this?

---

### Post by MooPi on 2012-06-17
This driver is not part of the ubuntu repository, so the system will try to us the default when an updated kernel is installed.  When you upgrade each time you will need to follow these steps listed to get your wireless back. Sorry for not responding sooner as I don't visit the forums much lately. I've not done this but you could write a script to streamline the process.

---

### Post by branchi on 2012-06-17
MooPi, for a limo driver, your reply was very fast :-)
I've seen an option to use windows drivers for this card with tool called ndiswrapper.
Would this help?
Would you recommend this approach?

---

### Post by MooPi on 2012-06-18
Negative on the ndiswrapper. Always use the native linux driver when it is available and especially since the Ralink diver works so well.

---

