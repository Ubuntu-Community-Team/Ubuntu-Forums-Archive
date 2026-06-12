---
title: "Can't get my wireless card to work. Help"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by SCTPenguin on 2010-01-26
I have been messing around with ubuntu for a few hours now trying to get my wireless driver to work, but I am having no luck. It seems like I installed the driver right, and network-admin use to show the wireless, but I couldn't unlock it to mess with properties. Now it doesn't even show wireless, and I still can't unlock it, so I'm unable to get my wireless card to work.

---

### Post by bkratz on 2010-01-26
Please go to the terminal  (Applications>>Accessories>>terminal) and copy/paste the output of:

lspci (that is LSPCI in lowercase) back here. It will tell what wireless card you have.

---

### Post by SCTPenguin on 2010-01-26
```
collin@collin-ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
collin@collin-ubuntu:~$ 


```

---

### Post by MaindotC on 2010-01-26
> **bkratz said:**
> Please go to the terminal  (Applications>>Accessories>>terminal) and copy/paste the output of:

lspci (that is LSPCI in lowercase) back here. It will tell what wireless card you have.

Let me save you some forum posts:  OP, check out the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  Please follow the steps and let us know at what point you are having difficulty.

---

### Post by bkratz on 2010-01-26
Check out this thread especially post 9

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by SCTPenguin on 2010-01-26
I was following this tutorial last night. 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and ran this code. 

```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```

Did that do anything? When I go into System > Admin > network, it doesn't show wireless anymore. (Sorry guys, I'm still very new to linux).

---

### Post by SCTPenguin on 2010-01-26
> **strAlan said:**
> Let me save you some forum posts:  OP, check out the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  Please follow the steps and let us know at what point you are having difficulty.

I'm stuck on step 4.2.3 - Not sure what I did wrong, or what step to do so that the card shows when I run sudo iwconfig

lshw -C network
```

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:16 memory:f9ffe000-f9ffffff
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:24:8c:23:0c:15
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:28 memory:f9e7c000-f9e7cfff ioport:c880(size=8) memory:f9e7f400-f9e7f4ff memory:f9e7f000-f9e7f00f
```

lsmod
```

Module                  Size  Used by
ndiswrapper           245248  0 
usb_storage            65952  1 
snd_hda_codec_nvhdmi     6048  1 
binfmt_misc            10220  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
x_tables               25832  1 ip_tables
psmouse                57124  0 
serio_raw               6596  0 
amd64_edac_mod         26688  0 
ppdev                   8232  0 
lp                     11908  0 
edac_core              48876  1 amd64_edac_mod
joydev                 13088  0 
i2c_nforce2             8168  0 
parport_pc             37352  1 
parport                40528  3 ppdev,lp,parport_pc
asus_atk0110            9472  0 
hid_logitech           10112  0 
ff_memless              6504  1 hid_logitech
usbhid                 43968  1 hid_logitech
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
ssb                    40944  0 
video                  23612  0 
output                  3680  1 video
floppy                 65192  0 
forcedeth              61292  0

```

sudo iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by Fivezero on 2010-01-26
i am also havng the same problem :(

---

### Post by bkratz on 2010-01-26
> **SCTPenguin said:**
> I'm stuck on step 4.2.3 - Not sure what I did wrong, or what step to do so that the card shows when I run sudo iwconfig



I was just looking at that listing and can't find 4.2.3.  Can you list out what the heading shows?

did you ever actually install the .inf file?

---

### Post by SCTPenguin on 2010-01-26
> **bkratz said:**
> I was just looking at that listing and can't find 4.2.3.  Can you list out what the heading shows?

did you ever actually install the .inf file?

Yeah, I installed the .inf with the .sys.
> 4.2.3. Check driver

    *

      If you ran lshw -C network and saw a driver bound to the device then let's test to make sure it's communicating to the kernel.
         1.

          run the command lsmod to see if driver is loaded. (look for the driver name that was listed in the output of lshw, "configuration" line). If you did not see the driver module in the list then use the modprobe command to load it.
         2.

            run the command sudo iwconfig. If you see output like in the example in the command section then the driver is at least identifying the device as a wireless device to the kernel.
               1.

                  Opening networking in system>administration> and seeing the device in the list is how to identify through gui if driver is at least communicating to the kernel at a basic level. 
         3.

            run the command sudo iwlist scan to scan for a router. If an access point is identified this is a second identifier which shows the driver as communicating and shows that it's probably working as it can complete a wireless interface task. (note not all cards support scanning so this may not work for you) 

---

### Post by bkratz on 2010-01-26
OK it was in the wireless troubleshooting guide not what you did last night and where your link pointed. Now I will read it and be back!

---

### Post by bkratz on 2010-01-26
While reading I went to the terminal and copied out mine (just the wireless)

 link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:11:f3:3b:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Marvell,11/27/2006,1.0.4.9 link=no multicast=yes wireless=IEEE 802.11g



As you will see it shows the driver as being ndiswrapper + something. Yours doesn't

---

### Post by SCTPenguin on 2010-01-26
Okay can you help me figure out why mine isn't showing that, and how to fix it? I'm completely confused on this whole situation now.

---

### Post by bkratz on 2010-01-26
try

 sudo modprobe ndiswrapper

then 

sudo lshw -C network

and see if it shows up then

---

### Post by SCTPenguin on 2010-01-26
> **bkratz said:**
> try

 sudo modprobe ndiswrapper

then 

sudo lshw -C network

and see if it shows up then

I tried that and this is the result. 

```
collin@collin-ubuntu:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
collin@collin-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:16 memory:f9ffe000-f9ffffff
  *-network DISABLED
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:24:8c:23:0c:15
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:22 memory:f9e7c000-f9e7cfff ioport:c880(size=8) memory:f9e7f400-f9e7f4ff memory:f9e7f000-f9e7f00f
collin@collin-ubuntu:~$ 


```

Also, nothing is even showing 'wireless anymore.' These both use to at least have something that said wireless, so don't know why that's gone. 

[IMG]http://i47.tinypic.com/2925lie.png[/IMG]

---

### Post by bkratz on 2010-01-26
OK all we did was tell it to load in ndiswrapper.  Let's take a giant step backwards.

Go to system>>administration>>synaptic package manager

hit reload and search for ndis, by the time you type it should find several. Mark ndisgtk for installation. It will automatically select the two ndiswapper files for installation also (if not already installed).

Go ahead and load it in. You will then have an entry under system>>administration>>windows wireless drivers.
Start that file, it will ask you for the .inf file. Point it wherever you originally placed it. It will then say something like device not found--ignore it and it will say something along the lines of network setup something not found--ignore it too.
Go to system>>preferences>>network connections.. Fill all that stuff in.
You should now have a wireless selection under the icon at the top of the screen. Use it.

---

### Post by SCTPenguin on 2010-01-26
Nothing for me to fill in? Frustrating.

---

### Post by bkratz on 2010-01-26
does it now look more like mine, or does it still say the b43-pci-bridge
stuff.

By the way here is the link to the thread that I have been using
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)


The next step if it still shows the b43-pci-bridge is

sudo gedit /etc/modprobe.d/blacklist.conf
blacklist b43-pci-bridge
sudo update-initramfs -k all -u


Now reboot

If it still doesn't work you might go through this thread it has a few user in exactly the same condition (mostly they succeeded) 
[http://ubuntuforums.org/showthread.php?t=1188702&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1188702&highlight=BCM4318)

If no success is found with this thread the next step would be to 
sudo rmmod b43-pci-bridge
which could be kinda severe so I would wait and see if the thread helps first.

---

### Post by SCTPenguin on 2010-01-26
Okay so I just kind of said F it, and did a fresh install of ubuntu so I could start from the beginning. I can at least see the wireless in network-admin, but everything is grayed out, and I don't know what to do anymore. iwconfig (or whatever that command is) shows the wlan0, and the driver is installed. 

[IMG]http://i47.tinypic.com/oi6idv.png[/IMG]

---

### Post by SCTPenguin on 2010-01-26
> **alexevans said:**
> Ur solution is NdisWrapper which comes with Ubuntu. If you can get ur hands on Windows drivers for your WLAN card then u should be able to get it to work with ndiswrapper. I recon u checkout the ndiswrapper documentation.

I'm using ndiswrapper, in fact I've been following this tutorial. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), and it's not working for me. If I blacklist the crap it tells me, than my wireless disappears all together, the rest of the tutorial I have followed exactly.

---

### Post by bkratz on 2010-01-27
> **SCTPenguin said:**
> I'm using ndiswrapper, in fact I've been following this tutorial. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), and it's not working for me. If I blacklist the crap it tells me, than my wireless disappears all together, the rest of the tutorial I have followed exactly.

Here is a link to another person using the BCM4318 with ndiswrapper, perhaps a PM will help discover what went wrong.

[http://ubuntuforums.org/showthread.php?t=1381808](http://ubuntuforums.org/showthread.php?t=1381808)

---

### Post by Cabs21 on 2010-01-27
If you have the wireless card I think you have then you might have selected the wrong driver thinking it was the correct one.  I did this with my brothers computer spending almost 2 hours trying to get the wireless driver to work only to realize that even thou the driver I chose had the correct numbers BCM43xx the other driver had the correct number as well but without the xx's.  once I changed the driver I instantly got wireless connection prompt for my home router.  If you have more then one driver present when updating try the other one and see if it works.  If not then you will be stuck with ndiswrapper.

---

### Post by MaindotC on 2010-01-27
Here are some replies to your answers:

> **SCTPenguin said:**
> I was following this tutorial last night. 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and ran this code. 

```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```

Did that do anything? When I go into System > Admin > network, it doesn't show wireless anymore. (Sorry guys, I'm still very new to linux).

It does do something.  Just to refresh here's the following from the documentation:
> Sometimes ndiswrapper is used prematurely. There may be a native driver that comes with Ubuntu which is taking the primary driver position and conflicting with ndiswrapper. In such cases, if the native driver does not work properly with your card you want to use ndiswrapper, you can blacklist the native driver, by adding a file to /etc/modprobe.d/ 

I'm sure you understand what a blacklist is in historical terms and it applies the same way here, just without discrimination.  So that's the REASON why you have a blacklist.  Here's a breakdown of that command you typed:

```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```

You can check the man pages for the commands echo, tee, and their options.  What this is doing is echoing the text inside the quotes, and placing that into the /etc/modprobe.d/blacklist file.  There are many ways to do this, but the author decided to use the tee command.  I know this wasn't in the documentation but it's good practise to always make a backup of any system files you are editing.  If you had, you could compare the current blacklist file with the old blacklist file - but the only difference you would see is that the following lines are added to the blacklist file (in 9.04 and above this is the "blacklist.conf" file):
```

blacklist bcm43xx
blacklist b43legacy
blacklist ssb

```
The "/n" is something called a newline character.  It's like pressing return after entering text so each of those "blacklist" commands are on separate lines.

> **SCTPenguin said:**
> I'm stuck on step 4.2.3 - Not sure what I did wrong, or what step to do so that the card shows when I run sudo iwconfig

lshw -C network
```

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:16 memory:f9ffe000-f9ffffff
  *
```

I'm not really sure how you got to the above portion using ndiswrapper.  It seems to me you have the option of using the b43 driver.

> lsmod
```

Module                  Size  Used by
ndiswrapper           245248  0 

```

As you can see, the ndiswrapper module (that's the open-source term for a driver) is loaded but nothing is using it.  I think this may because either the device won't use ndiswrapper.

[quote]
sudo iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```
Ok this is a little confusing because in lshw you can see that the wired interface is assigned the name eth0:
```

logical name: eth0

```
But it shows the wireless interface using the b43 driver but didn't assign it an interface.  We'll re-visit this.

Can you start over using the b43 driver?  It looks like your card is using a supported chipset.  I found a great, cross-platform tutorial here: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/)

---

### Post by SCTPenguin on 2010-01-27
Okay I tried that link you sent me and immediately ran into this. 

```
rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
collin@collin-desktop:~$
```

I was doing some more googling and found someone who said run dmesg or something.. This is the result I got.

```
[    8.430065] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input5
[    9.503779] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[    9.558297] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[    9.560046] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    9.560048] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    9.560050] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[    9.632721]   alloc irq_desc for 28 on node 0
[    9.632723]   alloc kstat_irqs on node 0
[    9.632729] forcedeth 0000:00:0a.0: irq 28 for MSI/MSI-X
[    9.632917] eth0: no link during initialization.
[    9.633546] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.933783] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[    9.935407] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[    9.937007] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    9.937009] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    9.937011] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   11.491074] usplash:440 freeing invalid memtype fffffffffb000000-fffffffffbe00000
[  211.169168] end_request: I/O error, dev fd0, sector 0
[  223.239256] end_request: I/O error, dev fd0, sector 0
[  223.239266] Buffer I/O error on device fd0, logical block 0
[  235.318990] end_request: I/O error, dev fd0, sector 0
[  235.319001] Buffer I/O error on device fd0, logical block 0
[  247.398513] end_request: I/O error, dev fd0, sector 0
[  364.474771] Disabling lock debugging due to kernel taint
[  364.483014] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  364.537824] usbcore: registered new interface driver ndiswrapper
collin@collin-desktop:~$ 
```

I'm guessing that those error's might be part of the issue.

---

### Post by MaindotC on 2010-01-27
> **SCTPenguin said:**
> ```
rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
collin@collin-desktop:~$
```

Ok so bcm43xx isn't loaded - that's perfectly fine because I believe you want to use the b43 module, not the bcm43xx.
> 
I was doing some more googling and found someone who said run dmesg or something.. This is the result I got.

```
[    8.430065] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input5
[    9.503779] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[    9.558297] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[    9.560046] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    9.560048] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    9.560050] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website

```

Did you follow these directions, although I believe b43 should be installed by default.  You can find it like this:
```

xk@xk:~/Desktop$ modprobe -l b43
kernel/drivers/net/wireless/b43/b43.ko

```
And you should be able to load it with:
```

xk@xk:~/Desktop$ lsmod | grep b43
# module not loaded so no output

xk@xk:~/Desktop$ sudo modprobe -a b43
[sudo] password for xk: 
xk@xk:~/Desktop$ lsmod | grep b43
b43                   174085  0 
ssb                    39073  1 b43
mac80211              192432  1 b43
cfg80211              142860  2 b43,mac80211
led_class               3666  1 b43

```

Try that.

---

### Post by SCTPenguin on 2010-01-27
> **strAlan said:**
> Ok so bcm43xx isn't loaded - that's perfectly fine because I believe you want to use the b43 module, not the bcm43xx.


Did you follow these directions, although I believe b43 should be installed by default.  You can find it like this:
```

xk@xk:~/Desktop$ modprobe -l b43
kernel/drivers/net/wireless/b43/b43.ko

```
And you should be able to load it with:
```

xk@xk:~/Desktop$ lsmod | grep b43
# module not loaded so no output

xk@xk:~/Desktop$ sudo modprobe -a b43
[sudo] password for xk: 
xk@xk:~/Desktop$ lsmod | grep b43
b43                   174085  0 
ssb                    39073  1 b43
mac80211              192432  1 b43
cfg80211              142860  2 b43,mac80211
led_class               3666  1 b43

```

Try that.

I got those results, but nothing works still? I'm kind of lost on what I should be doing. The System>Admin>Netowrk still wont let me unlock it, or choose the 'wireless' selection. I just did iwlist scan and it said network is down.

---

### Post by MaindotC on 2010-01-27
Post the output of your /etc/modprobe.d/blacklist file (or blacklist.conf depending on your version of Ubuntu).  Actually just look in any of those files and see if there's a mention of b43 and if so post it here.

---

### Post by SCTPenguin on 2010-01-27
```
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

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
#broadcom native driver
blacklist bcm43xx
```

---

### Post by MaindotC on 2010-01-27
Can you check [this list](http://hardware4linux.info/module/b43-pci-bridge/) to see if the type of card you have is listed and what (if any) modifications were prescribed?  You're card is using the b43-pci-bridge module.  I know it's listed in your output of lspci but I just want to verify - is this on-bard wireless or a pci card you installed?

---

### Post by SCTPenguin on 2010-01-27
> **strAlan said:**
> Can you check [this list](http://hardware4linux.info/module/b43-pci-bridge/) to see if the type of card you have is listed and what (if any) modifications were prescribed?  You're card is using the b43-pci-bridge module.  I know it's listed in your output of lspci but I just want to verify - is this on-bard wireless or a pci card you installed?

PCI - Linksys WMP54GS is my card.

---

