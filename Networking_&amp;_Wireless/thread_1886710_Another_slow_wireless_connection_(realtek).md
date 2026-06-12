---
title: "Another slow wireless connection (realtek)"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by Jeffffrey on 2011-11-25
First of all hello and thanks in advance for any help!
I've been looking around the forums for a while now but haven't been able to find a working
 solution for the wireless download speed. Tried all kind of stuff, disabling ipv6 and RTS, changing to googles DNS and whatnot.. 
But nothing seemed to work, i do must warn you since i'm a total linux noob, but loving it so far :)

It's a shuttle XS35GT v2, with a Realtek RTL8188ce driver which i just updated. 
The connection is stable but very slow: only 0.40 Mbps. 
For comparison: on my imac standing right next to it i get 18.36 Mbps on the same network. 

I've ran some commands i found in the forums, hope they are any use for finding a solution. 

```
lspci -nnk | grep -iA2 net

02:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:2005]
	Kernel driver in use: jme
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176]
	Kernel driver in use: rtl8192ce



lsmod

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
mmc_block              22393  2 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
arc4                   12473  2 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hda_codec_hdmi     31426  4 
nvidia              10390874  53 
sparse_keymap          13658  0 
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
binfmt_misc            17292  1 
rtl8192ce             127398  0 
snd_rawmidi            25241  1 snd_seq_midi
rtlwifi               102641  1 rtl8192ce
snd_hda_codec_idt      60049  1 
mac80211              393459  2 rtl8192ce,rtlwifi
snd_hda_intel          28358  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              172392  2 rtlwifi,mac80211
wmi                    18744  0 
snd_hwdep              13276  1 snd_hda_codec
video                  18908  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
snd                    55902  16 snd_hda_codec_hdmi,snd_rawmidi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_seq,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
jmb38x_ms              17406  0 
memstick               15857  1 jmb38x_ms
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
jme                    40330  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci



iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"KAN-Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 90:84:0D:D8:C9:69   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:111   Missed beacon:0




ifconfig

eth0      Link encap:Ethernet  HWaddr 80:ee:73:1f:be:b7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

wlan0     Link encap:Ethernet  HWaddr e0:91:53:59:47:a8  
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e291:53ff:fe59:47a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10251506 (10.2 MB)  TX bytes:2788608 (2.7 MB)




sudo lshw -C network 

  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 03
       serial: 80:ee:73:1f:be:b7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:feaf4000-feaf7fff ioport:dc00(size=128) ioport:d800(size=256)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: e0:91:53:59:47:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-13-generic-pae firmware=N/A ip=192.168.1.146 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:e800(size=256) memory:febfc000-febfffff
```

Since the computer is at my work i won't be able to run any commands till monday. Hope someone can help me, i just really want to get it working!

Jeffrey

---

### Post by ptrakk on 2011-11-25
have you tried that card in another computer? also some cards don't have very good range due to their antennas..

---

### Post by Jeffffrey on 2011-11-25
It's a build in card so that will be kinda difficult to test ;)
about the range, don't really think that could be it as well since it's only the download speed 
that seems not to be working correctly, upload is working fine. 

Thanks for your help though, any other ideas?

---

### Post by praseodym on 2011-11-25
Hi,

try [this]("http://ubuntuforums.org/showpost.php?p=11489372&postcount=3")

---

### Post by DariusZelvys on 2011-11-26
got the same problems and no success in fixing them

---

### Post by Jeffffrey on 2011-11-28
so,.. this is weird. Started up ubuntu a moment ago and did another speedtest just to check.
I haven't changed any setting or done any update or whatsoever at this stage but now the down & upload speeds are slower than before!:confused: 
Now it really is unusable, last friday it was at 0.40Mbps download / 3.0Mbps upload.. this morning it was 0.10Mbps download / 0.43Mbps upload...

Anyway, i tried the thing with the ISP / google DNS but that didn't affect the down/upload speed at al,
so i tried al possible combinations (if that even helps at all?) with the DNS and the settings in the resolv.conf file. 
but that didn't help either and the rates are still worse than before...

My original resolv.conf file
```
#Generated by NetworkManager
domain telenet.be
search telenet.be
nameserver 192.168.1.1
```

Any other suggestions or ideas? :(

---

### Post by praseodym on 2011-11-28
Please show:
```
sudo iwlist scan
iwlist chan
dmesg | egrep 'rtl8|r8'
cat /etc/network/interfaces
```

---

### Post by Jeffffrey on 2011-11-28
```
sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 90:84:0D:D8:C9:69
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"KAN-Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000ec89642df48
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 000C4B414E2D576972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706424520010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
                    IE: Unknown: DD0700039301720120
                    IE: Unknown: DD070017F203020180



iwlist chan

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.462 GHz (Channel 11)



dmesg | egrep 'rtl8|r8'

[    2.877074] rtl8192ce 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.877094] rtl8192ce 0000:03:00.0: setting latency timer to 64
[ 2412.147040] rtl8192ce 0000:03:00.0: PCI INT A disabled
[ 2413.529869] rtl8192ce 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19



cat /etc/network/interfaces

auto lo
iface lo inet loopback
```

---

### Post by praseodym on 2011-11-28
You can deactivate IPv6 system wide:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
and reboot.

In Firefox you can deactivate it, too. Type in your FF:
```
about:config
```
and change the entry:
```
network.dns.disableIPv6
```
to "true" by double-click. Restart firefox.

---

### Post by Jeffffrey on 2011-11-28
Thanks for responding so fast!

Typed the commands but unfortunately no change in down/upload rates :(
Also disabled the IPv6 in firefox, also no change.. 
not really relevant but i use chrome as standard browser ;)

---

### Post by praseodym on 2011-11-28
Add the mtu-value 1500 to the network-manager instead of "Automatic". Tried to change the channel? IPv6 is "Ignore"d in the NM?

---

### Post by Jeffffrey on 2011-11-28
I've put 1500 as mtu-vallue and IPv6 on ignore in the NetworkManager, in all kinds of on/off 
combinations with the previous suggestions.. but the rates are still the same. :(

I don't know what you meant by 'change the channel', could you explain this to me?

Thanks for ur patience!

---

### Post by praseodym on 2011-11-28
Type in your router IP address via cable connection into the browser and enter the router interface. You should be able to change the channel there to "automatic" or a single channel, e. g. channel one.

---

### Post by Jeffffrey on 2011-11-28
I won't be able to do that since i don't have access to wired internet ór the router :( 
probably should've put that in the startpost.. I just hope this isn't THE thing that should fix the problem cuz that would be quite ](*,)

Is there something/anything else I could try to make it work?

---

### Post by mr_raider on 2011-11-28
I would like to confirm that I have the same card in my laptop (rtl8188ce) and the same issue. Since I have my own home router, I can tell you the card will drop the connection speed to the lowest possible (5.5) on it's own for no reason. Sometimes a reboot of the PC or forcing a reconnection of wireless will solve the issue. This problem appeared in Ubuntu 11.10 onwards, and I think there is an issue with the rtl8192 driver in the kernel. In 10.04, I used to build my own driver from the realtek web site and it worked fine.

If someone can tell me how to disable the built in driver I am willing to retry it.

---

### Post by praseodym on 2011-11-28
The problem is that the Realtek driver(s) dont work properly with kernel 3, most of the time they cant be build.

---

### Post by Jeffffrey on 2011-11-29
So if I understand correctly my wireless probably isn't going to work with 11.10 and with 10.04 for example it should? The version isn't really important to me since i just need wireless to work correctly. 
If this is correct, would you recommend to use 10.04 or maybe an other distro?

Again, thanks for all the help :)

---

### Post by praseodym on 2011-11-29
It should also work with 11.04. I can copy the installation procedure with dkms of the driver if needed (different package!). With that you dont need to compile ever again. Long-Term-Support (LTS) versions are always recommended. 10.04 uses regular GNOME 2

---

### Post by Jeffffrey on 2011-11-29
I suppose this means i need to install some(?) package no matter what to make the wireless work? For the distro I'd like to use a supported version so 10.04 will be the right one for me i guess :). 
If that installation procedure copy is usable with 10.04 i'd really appreciate it if you could help me out there :D

---

### Post by praseodym on 2011-11-29
Here we go:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192ce_dkms_2.6.0006.0321.tar.gz
sudo tar xvf rtl8192ce_dkms_2.6.0006.0321.tar.gz -C /usr/src
sudo dkms add -m rtl8192ce -v 2.6.0006.0321
sudo dkms build -m rtl8192ce -v 2.6.0006.0321
sudo dkms install -m rtl8192ce -v 2.6.0006.0321 
```
The metapackage of the headers should be installed (linux-headers-generic, -generic-pae, whatever you are using)

---

### Post by Jeffffrey on 2011-11-29
Thanks! I'll post again as soon as i have installed 10.04 and used the commands to let you know how it went. :D

---

### Post by mr_raider on 2011-11-29
> **Jeffffrey said:**
> I suppose this means i need to install some(?) package no matter what to make the wireless work? For the distro I'd like to use a supported version so 10.04 will be the right one for me i guess :). 
If that installation procedure copy is usable with 10.04 i'd really appreciate it if you could help me out there :D

I may have found a temporary solution. I set my router wireless G only mode (no b or n), amd security to WPA2 AES. This seems to give me a stable connection for at least 1 day.

---

### Post by Jeffffrey on 2011-12-05
Said i'd post when i had 10.04 installed so here it is.

So i've managed to install Ubuntu 10.04 through a live usb. Was a bit of a hassle since I used the same method on my mac for 10.04 as i used for 11.10 but that didn't seem to work.. 
Finally got it working by following these instructions: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) (method 3)

A new problem has arisen though.. It seems the wireless card isn't recognized because it doesn't even scan for connections. 
Also in the weekend i was able to plug in an ethernet cable, but that did not work as well...

I've looked for other ways to update / install stuff offline and so far i've found Keryx. But that only works on linux and windows, 
and the only thing with a working internet connection i got is a mac #-o 
Now i'm gonna try to use it in combination with virtualbox but i have my doubts if that will work, 

so... i was hoping someone has an awesome tip or anything to help me fix this

Thanks, Jeffrey

---

### Post by praseodym on 2011-12-05
Did you install the driver (again) as descibed in #20? Copy the firmware additionally:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  
```

---

### Post by Jeffffrey on 2011-12-05
I haven't been able to run the commands, it won't complete the first one. (I suppose it needs a working internet connection? ) 

What i am trying now is to get the build-essential.deb package and copy that from the virtualbox to the actual pc and 
install the driver (tar.gz file) from the website. With this i hope to get an internet connection so i can run the commands you provided. 

The shared folder thing between the virtualbox and mac is giving me a headache atm though, but atleast i'm hopeful again :D

---

### Post by praseodym on 2011-12-05
The system in your virtualbox should be the same as your installed version (32/64 bit). Install there

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Then copy all .deb packages from /var/cache/apt/archives to a stick, save them in "Downloads" in your regular system, and install them via
```
sudo dpkg -i ~/Downloads/*.deb
```
build-essential is a metapackage which installs a lot of dependencies.

---

