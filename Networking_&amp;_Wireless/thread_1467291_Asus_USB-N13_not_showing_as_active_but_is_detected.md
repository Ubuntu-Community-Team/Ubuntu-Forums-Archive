---
title: "Asus USB-N13 not showing as active but is detected"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Thomazian on 2010-04-30
Hi Everyone,

I recently purchased an Asus USB-N13 and am having some trouble getting it setup.  I have followed this post [http://ubuntuforums.org/showpost.php?p=8958958&postcount=35]("http://ubuntuforums.org/showpost.php?p=8958958&postcount=35") including downloading the driver version, but I am now a little stuck.

This is a laptop which used to have a Netgear Wg111v2 wireless USB adapter (laptop does not have internal wireless).  That adapter died so I purchased the Asus.  The day I purchased the Asus adapter they were both plugged in at the same time for a short period - not sure if that is relevant or not but just thought I should let you know.

Here is some output from various commands which may be helpful:

lspci
```
ron@ron-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0b.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
02:0b.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
02:0b.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator

```

lsusb - the device shows up here
```
ron@ron-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

ifconfig / iwconfig - it shows up here too
```
ron@ron-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:26:e9:87  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe26:e987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1169 errors:4 dropped:6 overruns:4 frame:0
          TX packets:1127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1148114 (1.1 MB)  TX bytes:199266 (199.2 KB)
          Interrupt:9 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ron@ron-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod
```
ron@ron-laptop:~$ lsmod
Module                  Size  Used by
rt3070sta             512015  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
binfmt_misc             6587  1 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
radeon                674135  3 
joydev                  8708  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
snd_timer              19098  2 snd_pcm,snd_seq
ttm                    49943  1 radeon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
drm_kms_helper         29297  1 radeon
yenta_socket           20408  2 
intel_agp              24177  1 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  5 radeon,ttm,drm_kms_helper
rsrc_nonstatic         10015  1 yenta_socket
agpgart                31724  3 ttm,intel_agp,drm
soundcore               6620  1 snd
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_algo_bit            5028  1 radeon
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
psmouse                63245  0 
shpchp                 28820  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
ieee1394               81181  1 ohci1394

```

dmesg | grep usb - I think the last line is for the wireless adapter

```
ron@ron-laptop:~$ dmesg | grep usb
[    0.082042] usbcore: registered new interface driver usbfs
[    0.082056] usbcore: registered new interface driver hub
[    0.082084] usbcore: registered new device driver usb
[    0.256396] usb usb1: configuration #1 chosen from 1 choice
[    0.257101] usb usb2: configuration #1 chosen from 1 choice
[    0.257567] usb usb3: configuration #1 chosen from 1 choice
[    0.257834] usb usb4: configuration #1 chosen from 1 choice
[  360.516059] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  360.692717] usb 2-1: configuration #1 chosen from 1 choice
[  360.802920] usbcore: registered new interface driver hiddev
[  360.816976] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8
[  360.817209] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[  360.817244] usbcore: registered new interface driver usbhid
[  360.817918] usbhid: v2.6:USB HID core driver
[  370.200079] usb 1-4: new high speed USB device using ehci_hcd and address 3
[  370.350230] usb 1-4: configuration #1 chosen from 1 choice
[  370.452516] rtusb init --->
[  370.452547] usbcore: registered new interface driver rt2870

```

sudo -C network (says its disabled)
```
ron@ron-laptop:~$ sudo lshw -C network
[sudo] password for ron: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:26:e9:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.103 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:9 ioport:c800(size=256) memory:ffdff400-ffdff4ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.1.2.0 multicast=yes wireless=RT2870 Wireless

```

iwlist scan
```
ron@ron-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

ron@ron-laptop:~$ 

```

```
ron@ron-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS

```

```
ron@ron-laptop:~$ uname -mr
2.6.32-21-generic i686

```

```
ron@ron-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                       Ignoring unknown interface eth0=eth0.

```

Finally I renamed the Wireless folder to "/etc/Wireless/RT2870STA" once I saw RT2870STA was re-occuring.  According to this post.. [http://ubuntuforums.org/showpost.php?p=9136604&postcount=47]("http://ubuntuforums.org/showpost.php?p=9136604&postcount=47")

I have restarted a couple of times with it plugged in and with it not plugged.  At no time does it show in the Network Manager aplet.

What should I do as the next step?

---

### Post by chili555 on 2010-04-30
Please show us what the kernel has to report:```
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by Thomazian on 2010-04-30
Hi chili, thanks for your quick reply

```
ron@ron-laptop:/etc/Wireless$ dmesg | grep -e rt2 -e rt3
[  370.452547] usbcore: registered new interface driver rt2870

```

---

### Post by chili555 on 2010-04-30
Please detach the ethernet cable and do:```
sudo ifconfig eth0 down
sudo ifconfig ra0 up
sudo iwlist ra0 scan
```Did you modify the .dat file as outlined in the README?

---

### Post by Thomazian on 2010-04-30
I had not yet modified the .dat file..

I changed it to this:
```
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2870STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=sonicwall-1C98
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
```

The light on the device has come on and it is detecting the wireless signals around, here is the output:

```
ron@ron-laptop:/etc/Wireless/RT2870STA$ sudo ifconfig eth0 down
ron@ron-laptop:/etc/Wireless/RT2870STA$ sudo ifconfig ra0 up
ron@ron-laptop:/etc/Wireless/RT2870STA$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:24:01:75:93:BD
                    Protocol:802.11b/g/n
                    ESSID:"house"
                    Mode:Managed
                    Channel:9
                    Quality:37/100  Signal level:-75 dBm  Noise level:-63 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
          Cell 02 - Address: 00:1C:F0:43:8F:90
                    Protocol:802.11b/g
                    ESSID:"MM Meatshops"
                    Mode:Managed
                    Channel:2
                    Quality:100/100  Signal level:-47 dBm  Noise level:-63 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:21:04:74:04:BC
                    Protocol:802.11b/g
                    ESSID:"Hammerhead"
                    Mode:Managed
                    Channel:11
                    Quality:7/100  Signal level:-87 dBm  Noise level:-63 dBm
                    Encryption key:on
                    Bit Rates:22 Mb/s
          Cell 04 - Address: 00:17:C5:2E:1C:98
                    Protocol:802.11g
                    ESSID:"sonicwall-1C98"
                    Mode:Managed
                    Channel:1
                    Quality:100/100  Signal level:-49 dBm  Noise level:-63 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

Nothing has shown up in Network Manager, and I have not been prompted to enter the wireless password.

---

### Post by chili555 on 2010-04-30
> WPAPSK=I think you'll need to add the key here.

Don't quote it here; obscure it for the snoopy hackers.> Nothing has shown up in Network ManagerIs Enable Networking and Enable Wireless checked?

---

### Post by Thomazian on 2010-04-30
I have entered the password to the .dat file, brought the ra0 interface down then up again, no change.

If I right click Network Manager - Enable Networking is enabled, there is no option for Enable Wireless.

---

### Post by chili555 on 2010-04-30
Does */etc/network/interfaces* contain anything more than the lo stanzas?

---

### Post by Thomazian on 2010-04-30
Here is the contents of /etc/network/interfaces

```
auto lo
iface lo inet loopback

```

---

### Post by chili555 on 2010-05-01
Let's try to find out why it fails. Please click the Network Manager icon to try to connect and then do: ```
sudo cat /var/log/syslog | grep -i network
```See what the kernel has to say and post some relevant lines.

---

### Post by Thomazian on 2010-05-05
Thanks for your help chili555, this is now working and below is the complete procedure to get this installed.

I ended up wiping the PC and starting with a fresh 10.04 installation.  

Based off one of your previous posts [http://swiss.ubuntuforums.org/showpost.php?p=8916939&postcount=17]("http://swiss.ubuntuforums.org/showpost.php?p=8916939&postcount=17"), and another post (which is also based on your post) [http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html]("http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html"), here is the simplest method to get this to work.

1) Download the attached .bz2 file
2) Extract to ~/Desktop/2009)  
3) Open a terminal and cd ~/Desktop/2009)
4) sudo gedit os/linux/config.mk
Find these lines:    
-------------------------------------
HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
-------------------------------------
Change them to =y 

5) Save and close gedit
6) sudo gedit os/linux/usb_main_dev.c
7) Add a new line:
-------------------------------------
{USB_DEVICE(0x0B05,0x1784)}, /* Asus 3070 */
-------------------------------------

8) Save and close gedit
9) sudo make
10) sudo make install
11) sudo mkdir /etc/Wireless/RT2870STA
12) sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
13) sudo gedit /etc/modules    
Add these two lines to the end of the file
-------------------------------------    
rt2870sta    
rt3070sta    
-------------------------------------   

14) Save and close gedit 
15) reboot

After doing this procedure the wireless was detected and working properly and also showed up correctly in the Network Manager applet.

---

### Post by itsnpc on 2010-05-17
Hello,
 
I install the LTS 10.04, and followed the steps. The usb-n13 works smoothly.
 
However, after the network is up and running, I updated the LTS through the update manager as suggested. Then the usb-n13 is gone in the updated system.
 
The whole procedure is redone, but it did not work.
 
Does anyone has the similar issue?
 
Thanks for your feedback.

---

### Post by chili555 on 2010-05-17
If you did the steps in the post above, you compiled the driver against a prior kernel. The update brought, among many other things, a newer kernel. Please repeat these steps:```
cd ~/Desktop/2009
[COLOR="Red"]sudo make clean[/COLOR]
sudo make
sudo make install
```Now load the driver:```
sudo modprobe rt3070sta
```You should be all set.

Every time a newer kernel, or linux-image is installed, you will need to repeat the process I described.

---

### Post by itsnpc on 2010-05-17
Thanks a lot! 
Currently, I cannot access my linux box.
 
Update the result later. Appreicate your response :)

---

### Post by itsnpc on 2010-05-17
hello,

after "sudo modprobe rt3070sta"

FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt3070sta.ko): Device or resource busy

no matter the usb-N13 is inserted or not. This fatal error always shows up.

Any idea?

Thanks,

---

### Post by chili555 on 2010-05-17
How about letting me see:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by itsnpc on 2010-05-17
lsmod | grep -e rt2 -e rt3
response:
rt2870sta     525366   0

dmesg | grep -e rt2 -e rt3
response:
rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
Error: Driver 'rt2870' is already registered, aborting...

I can only type these errors. There are some other lines but for the same messages.

Thanks,

---

### Post by chili555 on 2010-05-17
Did you by chance already try ndiswrapper?```
dmesg | grep ndis
iwconfig
```Thanks.

---

### Post by itsnpc on 2010-05-17
no. This is a newly installed LTS, and the wireless installation is the first thing I tried to do. 

dmesg | grep ndis
did not give me any response.

iwconfig
did not show any wireless extensions.

:(

---

### Post by itsnpc on 2010-05-17
I did try:
sudo modprobe rt2870sta

it did not response anything. no error.

but the usb-n13 does not work, neither.

---

### Post by Thomazian on 2010-05-18
I marked this thread as solved when it worked but I have since had the same problem and it no longer works.

Marking the thread as unsloved...

---

### Post by chili555 on 2010-05-18
Please remove the device and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules 
```Since you followed the howto here [http://ubuntuforums.org/showpost.php?p=8958958&postcount=35](http://ubuntuforums.org/showpost.php?p=8958958&postcount=35)  I assume you already have the file, but we are going to make a change:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba [COLOR="Red"]rt2870sta[/COLOR]"
```Proofread carefully, save and close gedit. Now do:```
gedit /etc/modprobe.d/network_drivers.conf 
```Make the highlighted changes:```
install [COLOR="Red"]rt2870sta[/COLOR] /sbin/modprobe --ignore-install [COLOR="Red"]rt2870sta[/COLOR] $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Now reinsert the device and do:```
iwconfig
```Do you have a wireless interface? Can you connect?

---

### Post by Thomazian on 2010-05-23
I've had some time to play with this again and below is the full procedure I used to get this device to work form a clean installation of 10.04.  I had the device connected throughout this entire procedure.  Thanks to everyone who has helped along the way, in particular chili555.

1) Download the file file from earlier in this thread: "2009_1110_RT3070_Linux_STA_v2.1.2.0"
2) Extract it to the Desktop.  Double clicking it to open and dragging the folder inside to the Desktop works just fine.
3) Open a command prompt and go to the newly created folder
```
cd Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/
```
4) Create the make file.  As I understand it, this will create a 'makefile' which has the installation procedure required, according to the configuration of your system.
```
sudo make
```
5) Run the installation.  This runs the installation according to settings made in the step above.
```
sudo make install
```
6) Create a 'network_drivers.rules' file,
```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```
Enter this code:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta" 
```
Save and exit gedit

7) Create a 'network_drivers.conf' file,
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
Enter this code:
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```
Save and exit gedit

8) Restart your system

The device should come on after the restart and you can connect to your wireless network via the NetworkManager applet.  In my tests, the device continues to work after applying updates.

---

### Post by Thomazian on 2010-05-23
Now that this is working, I have some questions as to **why** what we have done works.  I still have a lot to learn about Linux and often find myself blindly typing comands.. I want to understand what I am doing, so here goes..

Step 6)
Why is the file called "network_drivers.rules"?
Why does it have to be in this folder "/etc/udev/rules.d/"?
What does the code within the file actually do?

How did you know it had to be called that particular file name and placed in that particular folder and with that exact code?  I don't see that in the readme file, where did you come accross that information..

Step 7)
The same respective questions...

Another interesting observation; when I could not get the device to work, it was called 'ra0' when I typed 'iwconfig'.  Now that it is working device is called 'wlan0'.  Does that mean anything? Can anyone explain why that would be?

---

### Post by chili555 on 2010-05-23
> How did you know it had to be called that particular file name and placed in that particular folder and with that exact code? I don't see that in the readme file, where did you come accross that information..I just stole it from someone else on this forum. I have no idea why it works, I just know by observation that it does.

It's not in the README file because it is intended to get the native driver working; it's not intended for the compiled from Ralink version.> when I could not get the device to work, it was called 'ra0' when I typed 'iwconfig'. Now that it is working device is called 'wlan0'. Does that mean anything? Can anyone explain why that would be? The native built in the kernel version uses wlan0; the compiled from Ralink version uses ra0. Despite your efforts to compile the downloaded version, your system is using the native driver. When you run:```
modinfo rt2870sta
```Does it come from kernel/drivers/net (for compiled) or from kernel/drivers/staging (for native)?

Hey, if I find something that works, I don't apologize; I use it.

---

### Post by Thomazian on 2010-05-23
Hi chili555,

Here is the code:
```
modinfo rt2870sta
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
alias:          rt3070sta
version:        2.0.1.0
license:        GPL
description:    RTxx70 Wireless LAN Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     169A56F8E0E6AA9C2B2FD02
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
staging:        Y
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)
```

Finally, I had some connection problems connecting to one particular router (D-Link DIR-628), and some specific settings had to be set.

The adapter would not connect if the Encryption on the router was set to "TKIP and AES", I had to choose one or the other.  I went with AES.

Also the adapter would not connect to this router if I set the router to "N only" mode.

The router does have the latest firmware and is an 'N' router, so I'm not sure at this stage if this is an adapter problem or this specific router that has the problem.

For now I am happy to be connecting even if it is at 'G' speeds, and know where to look if for some reason I can't connect to a router.

---

### Post by chili555 on 2010-05-23
> /lib/modules/2.6.32-22-generic/kernel/drivers/[COLOR="Red"]staging[/COLOR]/rt2870/rt2870sta.ko
alias:          rt3070sta
version:        [COLOR="Red"]2.0.1.0[/COLOR]
This is the built in to the kernel driver. What you tried to build is:> 2009_1110_RT3070_Linux_STA_v[COLOR="Red"]2.1.2.0[/COLOR]Hey, if it works, it works!

---

### Post by Thomazian on 2010-05-24
So I reinstalled Ubuntu again...

This time, I only did steps 6 and 7 of post#23, so as not to use the downloaded driver at all, and it works just the same.

I did some reading around these two directories:
/etc/udev/rules.d/
/etc/modprobe.d/

They seem to play a key part it forcing modules to load, but I need to do more research around the linux kernel and how modules work to fully understand it.

Another question comes to mind though, how does one know if there is already a present GPL driver for a given piece of hardware?  

I would never have known unless you told me I was using that driver, I would have kept trying to make the external driver work...

---

### Post by Thomazian on 2010-05-24
So I reinstalled Ubuntu again...

This time, I only did steps 6 and 7 of post#23, so as not to use the downloaded driver at all, and it works just the same.

I did some reading around these two directories:
/etc/udev/rules.d/
/etc/modprobe.d/

They seem to play a key part it forcing modules to load, but I need to do more research around the linux kernel and how modules work to fully understand it.

Another question comes to mind though, how does one know if there is already a present GPL driver for a given piece of hardware?  

I would never have known unless you told me I was using that driver, I would have kept trying to make the external driver work...

---

### Post by chili555 on 2010-05-24
> Another question comes to mind though, how does one know if there is already a present GPL driver for a given piece of hardware? And here I thought I was going to keep my secrets forever. Oh, well, nothing lasts forever.

Iowan and bkratz, among others, will be interested in this.

Either lspci -nn, if it's a PCI device or lsusb, if it's USB, will give the device ID. Here is an example:```
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [[COLOR="Red"]8086:4227[/COLOR]] (rev 02)
```If you google the ID, you can find clues as to what the driver is: [http://webcache.googleusercontent.com/search?q=cache:ecisGkpGXsYJ:cateee.net/lkddb/web-lkddb/IWL3945.html+8086:4227&cd=6&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:ecisGkpGXsYJ:cateee.net/lkddb/web-lkddb/IWL3945.html+8086:4227&cd=6&hl=en&ct=clnk&gl=us)

In this example, we can see that iwl3945 drives the device. We can check:```
$ modinfo iwl3945 | grep 4227
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]4227[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
```The real trick is knowing when two conflicting drivers both claim a device. That is just a matter of experience.

---

### Post by Dhruv94 on 2010-10-12
i have the exact same problem as the original poster.

i have the same usb  but im running 10.10 x64

i too am a complete noob... any help would be greatly appreciated.

---

### Post by WarmonkeyUK on 2010-10-13
Just upgraded to Maverick, and and having problems. I'd been fine following the solution listed by Thomazi/chili555, but on Maverick running the 'make' command crashes out with make errors. A bit of googling lead me to believe that this might mean gcc was not installed, but I think it is, and trying apt-get install gcc informs you that this is an obsoleted package anyway. I realise Maverick is only very new, but it looks like for the moment that the solution that has been posted in several threads is only valid up toLucid.

---

### Post by thenickrulz on 2011-05-01
> **Thomazian said:**
> Thanks for your help chili555, this is now working and below is the complete procedure to get this installed.

I ended up wiping the PC and starting with a fresh 10.04 installation.  

Based off one of your previous posts [http://swiss.ubuntuforums.org/showpost.php?p=8916939&postcount=17](http://swiss.ubuntuforums.org/showpost.php?p=8916939&postcount=17), and another post (which is also based on your post) [http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html](http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html), here is the simplest method to get this to work.

1) Download the attached .bz2 file
2) Extract to ~/Desktop/2009)  
3) Open a terminal and cd ~/Desktop/2009)
4) sudo gedit os/linux/config.mk
Find these lines:    
-------------------------------------
HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
-------------------------------------
Change them to =y 

5) Save and close gedit
6) sudo gedit os/linux/usb_main_dev.c
7) Add a new line:
-------------------------------------
{USB_DEVICE(0x0B05,0x1784)}, /* Asus 3070 */
-------------------------------------

8) Save and close gedit
9) sudo make
10) sudo make install
11) sudo mkdir /etc/Wireless/RT2870STA
12) sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
13) sudo gedit /etc/modules    
Add these two lines to the end of the file
-------------------------------------    
rt2870sta    
rt3070sta    
-------------------------------------   

14) Save and close gedit 
15) reboot

After doing this procedure the wireless was detected and working properly and also showed up correctly in the Network Manager applet.

Have benn having a bit of trouble with my adapter recently with trying to get it to work with Ubuntu 11.04. After i read a did these things it worked streight way... THANKS!

---

### Post by WantSomethingNew on 2011-06-03
Nick, I see you've posted this to several threads.  I'm glad its working for you!  Are you getting speeds faster than 54?  My N13 gets and keeps a connection, but won't perform faster than 54...

---

