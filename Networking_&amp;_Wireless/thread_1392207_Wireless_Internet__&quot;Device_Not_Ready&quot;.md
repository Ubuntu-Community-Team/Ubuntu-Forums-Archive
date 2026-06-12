---
title: "Wireless Internet  &quot;Device Not Ready&quot;"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by ronubunt on 2010-01-27
I just recently installed ubuntu, my first experience with linux. I don't know if it isn't recognizing my wireless card or if it is another issue, but I am unable to view any wireless networks/connect to any. When I click on the network icon it says "wireless" with Device Not Ready underneath. I apologize for the length of the feedback I'm posting, but I was unsure what was/wasn't pertinent so I'm posting all of it. I also understand you fellows here deal with this type of thread a thousand times over so I greatly appreciate those of you who take time to help us lost folk! Thanks in advance.



1. HP Pav. dv6000 -Ubuntu 9.10 i686

2. lspci

05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

lsusb

Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


3. ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:b7:d6:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4. lsmod
Module                  Size  Used by
ipw2200               140292  0 
libipw                 43148  1 ipw2200
lib80211                6432  2 ipw2200,libipw
arc4                    1660  2 
ecb                     2524  2 
b43                   122136  0 
binfmt_misc             8356  1 
mac80211              181236  1 b43
snd_hda_codec_conexant    20060  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
joydev                 10272  0 
snd_seq_oss            28576  0 
ppdev                   6688  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                      8964  0 
parport                35340  2 ppdev,lp
cfg80211               93052  2 b43,mac80211
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
led_class               4096  2 b43,sdhci
ricoh_mmc               3676  0 
psmouse                56180  0 
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
i915                  221064  3 
ohci1394               29900  0 
e100                   32452  0 
mii                     5212  1 e100
ieee1394               86596  1 ohci1394
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35300  1 b43
video                  19380  1 i915
intel_agp              27484  2 i915
output                  2780  1 video
agpgart                34988  2 drm,intel_agp



sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:b7:d6:72
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:db:1a:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

---

### Post by chili555 on 2010-01-27
> *-network DISABLEDWonder why it's disabled. Do you have a little switch on your laptop that got nudged over to off by the cat? Please let us see:```
rfkill list
```Thanks.

---

### Post by ronubunt on 2010-01-27
> **chili555 said:**
> Wonder why it's disabled. Do you have a little switch on your laptop that got nudged over to off by the cat? Please let us see:```
rfkill list
```Thanks.
I do have that switch, but I made sure it was in the "on" position. As soon as I boot up though the light next to the switch shows the "disabled" color, and I can switch it back and forth with no affect. I'll be back momentarily with the results of the command you posted, thanks for the quick response!

---

### Post by ronubunt on 2010-01-27
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2010-01-27
Well, that looks entirely normal. Let's see if the kernel has any clues:```
dmesg | grep b43
dmesg | grep wlan
```Thanks.

---

### Post by ronubunt on 2010-01-27
$ dmesg | grep b43
[    1.513714] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.513733] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    8.928661] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   16.468124] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   16.912406] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   16.915619] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   16.915624] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   16.915628] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   17.188112] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   17.192041] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   17.196678] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   17.196684] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   17.196687] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

dmesg | grep wlan

gave a blank response.

---

### Post by chili555 on 2010-01-27
> ERROR: Firmware file "b43/ucode5.fw" not foundThere ya go! Here is the procedure from the referenced website. You will need internet connectivity, i.e. ethernet to do so.> in latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package:

    ```
sudo apt-get install b43-fwcutter
```
          when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter) 

---

### Post by ronubunt on 2010-01-27
Hm...question. Is there anyway I can obtain the firmware outside of the ubuntu installation (other partition or computer) and transfer it there? My only available internet is my wireless router, so I'm stuck in a sort of catch22 wherein I need this software to get internet but need internet to get the software :shock:

---

### Post by chili555 on 2010-01-27
I don't know of a way, but I'm searching. I suggest you do also.> requesting b43/[COLOR="Blue"]ucode5.fw[/COLOR]Is the firmware on the other partition??? Can you copy it to a thumbdrive and then to your Ubuntu partition? Drag and drop it to your Home folder and then do:```
sudo cp <firmware_files_you_found> /lib/firmware
sudo chmod +r /lib/firmware/*
sudo rmmod -f b43
sudo modprobe b43
```Does your wireless now work?

---

### Post by chili555 on 2010-01-27
This might do it!

[http://www.omattos.com/node/6](http://www.omattos.com/node/6)

---

### Post by ronubunt on 2010-01-27
Hey Chili, once again thank you very much for all this help.

Where I'm at now is I connected my computer directly to the router with a "firewire" cord or whatever, sorry don't know the proper terms. From there I was able to connect to the internet with my wired ethernet connection. I tried the sudo

sudo apt-get install b43-fwcutter


and got this

sudo apt-get install b43-fwcutter

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter


I then followed your link to that alternate firmware package, and after struggling for a while to figure out how to get the "permissions" to be able to extract the files into lib\firmware I got the files in there, but haven't seen any change in my wireless. Still says "device not ready"

I appreciate all your patients and help, any idea of where I can go from here?

---

### Post by ronubunt on 2010-01-27
update!


Not sure what made the difference since my last post, I refreshed the network and didn't see any changes. But just now I took a look and it is working! So I'm guessing it was the firmware download you linked me to. Thank you very much for all your help, I am EXTREMELY greatful.

---

### Post by chili555 on 2010-01-28
Glad it's working! Enjoy!

---

### Post by vzybilly on 2010-11-01
i'm having the same issue, i did what y'all did here and it still didn't work

```
vzybilly@VZYServ:~$ dmesg | grep b43
[    1.394579] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.869749] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    9.051700] Registered led device: b43-phy0::tx
[    9.051720] Registered led device: b43-phy0::rx
[    9.051742] Registered led device: b43-phy0::radio
[   22.852369] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   22.852375] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   22.852379] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[343377.517230] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[343377.517237] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[343377.517241] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
vzybilly@VZYServ:~$ sudo apt-get install b43-fwcutter
[sudo] password for vzybilly: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.3kB of archives.
After this operation, 81.9kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main b43-fwcutter i386 1:013-2 [16.3kB]
Fetched 16.3kB in 0s (31.6kB/s)       
Selecting previously deselected package b43-fwcutter.
(Reading database ... 124238 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-2_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-2) ...
vzybilly@VZYServ:~$ dmesg | grep b43
[    1.394579] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.869749] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    9.051700] Registered led device: b43-phy0::tx
[    9.051720] Registered led device: b43-phy0::rx
[    9.051742] Registered led device: b43-phy0::radio
[   22.852369] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   22.852375] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   22.852379] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[343377.517230] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[343377.517237] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[343377.517241] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
vzybilly@VZYServ:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
vzybilly@VZYServ:~$ dmesg | grep wlan
vzybilly@VZYServ:~$ 

```i restarted and got this

```
vzybilly@VZYServ:~$ dmesg | grep b43
[    1.396367] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.397177] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   27.892903] Registered led device: b43-phy0::tx
[   27.892924] Registered led device: b43-phy0::rx
[   27.892944] Registered led device: b43-phy0::radio
[   30.307648] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   30.307654] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   30.307658] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
vzybilly@VZYServ:~$ 

```

thanks for all of your help, it would be awesome if the wireless would work on this computer

---

