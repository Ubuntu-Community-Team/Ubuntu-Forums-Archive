---
title: "BCM4321 not working after upgrade to 11.10"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2011-10-15
First, I have read all of the threads that appear related and attempted those solutions. No joy.

lspci -v provides the following:

06:01.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
	Subsystem: Linksys Device 0060
	Flags: bus master, fast devsel, latency 32, IRQ 11
	Memory at ea300000 (32-bit, non-prefetchable) [size=16K]
	Kernel modules: ssb

Network manager shows no wireless. If I attempt to use jockey-gtk to load the STA driver it fails and tells me to read the jockey log. I have done that but don't find any information that points me to a solution. If I 'sudo modprobe b43' I do have entries for wireless in network manager, but it does not see any networks and can't connect.

I expect to have the same problem with my SO's machine, so I would like to sort it out. Before I hose anything up further I am asking for help. I am connected via ethernet from the machine in question. Thanks.

*** SOLUTION IS IN THE LAST POST ***

---

### Post by wildmanne39 on 2011-10-15
Hi, please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
Thank you

---

### Post by lingenfr on 2011-10-15
$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
--
06:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Linksys Device [1737:0060]
	Kernel driver in use: b43-pci-bridge


$ lsmod
Module                  Size  Used by
arc4                   12473  2 
b43                   318816  0 
ssb                    50682  1 b43
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
des_generic            21191  0 
md4                    12523  0 
nls_utf8               12493  0 
cifs                  248817  0 
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vboxnetadp             13328  0 
vboxnetflt             27840  0 
vboxdrv               230133  2 vboxnetadp,vboxnetflt
kvm_intel              55857  0 
kvm                   336964  1 kvm_intel
binfmt_misc            17292  1 
nvidia              10390874  40 
snd_usb_audio         100880  2 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
usbhid                 41905  0 
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80468  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_usbmidi_lib        24558  1 snd_usb_audio
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
parport_pc             32114  1 
snd                    55902  20 snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63474  0 
serio_raw              12990  0 
firewire_sbp2          22510  0 
firewire_core          56937  1 firewire_sbp2
crc_itu_t              12627  1 firewire_core
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
floppy                 60310  0 
r8169                  47200  0 
pata_jmicron           12651  0 
ahci                   21634  0 
libahci                25761  1 ahci


I had tried some instructions from other posts. I think they were intended to use the kernel driver. If it will work, I would prefer to use the STA driver from Broadcom. However, at this point, I will take whatever works. Thanks for the help.

---

### Post by wildmanne39 on 2011-10-15
Hi, let&#347; do this please:
```
sudo apt-get --purge remove b43-fwcutter firmware-b43-installer
```
Then restart your computer and do this.
```
sudo apt-get update
```
```
sudo apt-get install bcmwl-kernel-source
```
Then go to Additional Drivers, the STA driver activate it. 

Then
```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```
Then restart your computer after you unplug your wired connection.
Thank you

---

### Post by lingenfr on 2011-10-16
> **wildmanne39 said:**
> Hi, let&#347; do this please:
```
sudo apt-get --purge remove b43-fwcutter firmware-b43-installer
```
Then restart your computer and do this.
```
sudo apt-get update
```
```
sudo apt-get install bcmwl-kernel-source
```


Ok, I did this but bcmwl-kernel-source was already installed. When I went to Additional Drivers to activate STA, jockey-gtk crapped out again. So, I did:

```
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
```

but I didn't need to execute the following instruction:

> **wildmanne39 said:**
> Then go to Additional Drivers, the STA driver activate it. 

Then
```
sudo echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
```
Then restart your computer after you unplug your wired connection.
Thank you

as I had already blacklisted bcma from some following instructions in other posts. Others attempting to following these instructions should:

> more /etc/modprobe.d/blacklist.conf|grep -i bcma

to see if bcma is blacklisted. If not, then execute wildmanne39's instruction above. Once I activated the STA driver, jockey-gtk told me to restart to activate the driver and when I did, my wireless was working. Thanks very much for your help.

Also, FWIW, these same (approximate) instructions worked on my SO's machine.

---

### Post by wildmanne39 on 2011-10-16
Hi, I am glad it it working!
Enjoy

---

### Post by mmelgaco on 2011-10-28
Hi, how are you?
I have this wifi adapter:
01:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

I try this solution, but did not work for me.
The adapter is recognized, shows on iwconfig and gnome network manager, but no networks are listed.

Thanks for the help.

---

### Post by wildmanne39 on 2011-10-28
Hi, welcome to the forum! please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mmelgaco on 2011-10-28
```


# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux OptiPlex380 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

# lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
    Kernel driver in use: wl
--
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Dell Device [1028:0400]
    Kernel driver in use: tg3


# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"rumo-pm"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:54:F4:52   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:538   Missed beacon:0

eth2      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


# rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

# lsmod
Module                  Size  Used by
wl                   2568210  0 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17540  1 
arc4                   12529  2 
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
mac80211              310872  2 rt2x00usb,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
v4l2_compat_ioctl32    17083  1 videodev
lib80211_crypt_tkip    17390  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
dcdbas                 14490  0 
wmi                    19256  1 dell_wmi
parport_pc             36962  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  566711  2 
lib80211               14991  2 wl,lib80211_crypt_tkip
psmouse                73882  0 
drm_kms_helper         42558  1 i915
serio_raw              13166  0 
drm                   236330  3 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
tg3                   147729  0


```

---

### Post by wildmanne39 on 2011-10-28
Hi, first I would take the dash mark out of your ESSID that could cause connection problems.

Then please post the results of these commands:
```
nm-tool
```
```
sudo iwlist scan
```

Please disconnect your usb adapter before you run this last command and any wired connection you might have, remember that the wireless can not connect as long as you have a wired or usb adapter plug in.
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan | tail -n35
```
Thank you

---

### Post by mmelgaco on 2011-10-28
Hello, 
i can't change the essid right now, i'm at work and we have many stations working.
I will try to change tomorrow.

I unplugged my dlink usb wifi dongle, restart the pc and run the commands:

```

# nm-tool

NetworkManager Tool

State: disconnected

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        C4:17:FE:48:0B:3F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        A4:BA:DB:07:79:74

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      No scan results

# cat /var/log/syslog | grep -e wl -e firmware -e wlan | tail -n35
Oct 28 17:00:20 OptiPlex380 dhclient: Listening on LPF/wlan1/00:19:5b:7b:8a:79
Oct 28 17:00:20 OptiPlex380 dhclient: Sending on   LPF/wlan1/00:19:5b:7b:8a:79
Oct 28 17:00:20 OptiPlex380 dhclient: DHCPREQUEST of 192.168.0.114 on wlan1 to 255.255.255.255 port 67
Oct 28 17:00:22 OptiPlex380 dhclient: DHCPREQUEST of 192.168.0.114 on wlan1 to 255.255.255.255 port 67
Oct 28 17:00:23 OptiPlex380 NetworkManager[911]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
Oct 28 17:00:23 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 28 17:00:23 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) started...
Oct 28 17:00:23 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started...
Oct 28 17:00:24 OptiPlex380 NetworkManager[911]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 28 17:00:24 OptiPlex380 NetworkManager[911]: <info> Policy set 'rumo-pm' (wlan1) as default for IPv4 routing and DNS.
Oct 28 17:00:24 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) successful, device activated.
Oct 28 17:00:24 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
Oct 28 17:00:24 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 28 17:00:31 OptiPlex380 kernel: [   52.312005] wlan1: no IPv6 routers present
Oct 28 17:00:41 OptiPlex380 NetworkManager[911]: <info> (wlan1): IP6 addrconf timed out or failed.
Oct 28 17:00:41 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Oct 28 17:00:41 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 4 of 5 (IP6 Configure Timeout) started...
Oct 28 17:00:41 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started...
Oct 28 17:00:41 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
Oct 28 17:00:41 OptiPlex380 NetworkManager[911]: <info> Activation (wlan1) Stage 4 of 5 (IP6 Configure Timeout) complete.
Oct 28 17:01:56 OptiPlex380 kernel: [  137.120185] wlan1: deauthenticating from 1c:af:f7:54:f4:52 by local choice (reason=3)
Oct 28 17:01:56 OptiPlex380 dhclient: receive_packet failed on wlan1: Network is down
Oct 28 17:01:56 OptiPlex380 NetworkManager[911]: <info> (wlan1): now unmanaged
Oct 28 17:01:56 OptiPlex380 NetworkManager[911]: <info> (wlan1): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Oct 28 17:01:56 OptiPlex380 NetworkManager[911]: <info> (wlan1): deactivating device (reason 'removed') [36]
Oct 28 17:01:56 OptiPlex380 NetworkManager[911]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 1819
Oct 28 17:01:56 OptiPlex380 NetworkManager[911]: <info> (wlan1): cleaning up...
Oct 28 17:01:56 OptiPlex380 NetworkManager[911]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/net/wlan1, iface: wlan1)
Oct 28 17:01:56 OptiPlex380 wpa_supplicant[1019]: Could not read interface wlan1 flags: No such device
Oct 28 17:03:31 OptiPlex380 kernel: [   12.758340] intel_rng: don't want to disable this in firmware setup, and if
Oct 28 17:03:31 OptiPlex380 kernel: [   12.915465] wl: module license 'MIXED/Proprietary' taints kernel.
Oct 28 17:03:31 OptiPlex380 kernel: [   13.040380] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 28 17:03:31 OptiPlex380 kernel: [   13.040386] wl 0000:01:00.0: setting latency timer to 64
Oct 28 17:03:32 OptiPlex380 NetworkManager[865]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 28 17:03:32 OptiPlex380 NetworkManager[865]: <info> (eth2): new 802.11 WiFi device (driver: 'wl' ifindex: 3)


```

---

### Post by wildmanne39 on 2011-10-28
Ok, change the ESSID in your router and wireless settings, then we will go from there.
Thank you

---

### Post by mmelgaco on 2011-10-28
I'll try and report here.

Thanks for all the help !

[]'s

---

### Post by mmelgaco on 2011-11-09
Hi, sorry for the long time.
I changed the ESSID today, removing the "-".
But still not works.


thanks

---

### Post by wildmanne39 on 2011-11-10
Hi, did you remove the dash from network manger in the upper right of the screen, then type 192.168.0.1 into your web browser while connected to the router by a hard wire?

To connect with internal card you will have to have your computer off and unplug your usb adapter then turn your computer on.
Thank you

---

### Post by mmelgaco on 2011-11-11
I accessed my router using my usb wifi adapter, changed the essid in the wireless configuration removing the "-".
Then, i remove all wifi networks from my network manager.
Then i shutdown the computer, remove the usb adapter and starts it again.
The network manager don't show any adapter or network.
Then, i plug my usb wifi adapter. Now, the network manager shows the 2 adapters, but only my dlink usb list my network. I connected using it and post this message.

The commands that i run when start the computer without the usb adapter:

```


$iwconfig
eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

$ iwlist eth2 scanning
eth2      Interface doesn't support scanning.


```

---

### Post by wildmanne39 on 2011-11-11
Hi, let's try this please:
```
sudo apt-get purge bcmwl-kernel-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
After the second command is done installing shut down your computer and unplug your usb adapter then boot up.
Thank you

---

### Post by mmelgaco on 2011-11-11
now there is no wireless adapter:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

Thanks

---

### Post by wildmanne39 on 2011-11-11
Hi, did you run that command with the usb adapter unplugged because with the driver I am trying to use it will be wlan and not eht0?

Please post the results of:
```
iwconfig
rfkill list all
lsmod
nm-tool
```
Thank you

---

### Post by mmelgaco on 2011-11-11
I run the command without the wireless usb dongle.
The eth0 is the ethernet (wired).

I will run and post here, wait.

---

### Post by mmelgaco on 2011-11-11
mar@OptiPlex380:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mar@OptiPlex380:~$ sudo rfkill list all
mar@OptiPlex380:~$

mar@OptiPlex380:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
snd_hda_codec_realtek   330769  1 
v4l2_compat_ioctl32    17083  1 videodev
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
binfmt_misc            17540  1 
dcdbas                 14490  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
wmi                    19256  1 dell_wmi
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  566711  2 
parport_pc             36962  1 
drm_kms_helper         42558  1 i915
soundcore              12680  1 snd
drm                   236330  3 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
tg3                   147729  0 

mar@OptiPlex380:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        A4:BA:DB:07:79:74

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

---

### Post by mmelgaco on 2011-11-11
```


mar@OptiPlex380:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mar@OptiPlex380:~$ sudo rfkill list all
mar@OptiPlex380:~$

mar@OptiPlex380:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
snd_hda_codec_realtek   330769  1 
v4l2_compat_ioctl32    17083  1 videodev
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
binfmt_misc            17540  1 
dcdbas                 14490  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
wmi                    19256  1 dell_wmi
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  566711  2 
parport_pc             36962  1 
drm_kms_helper         42558  1 i915
soundcore              12680  1 snd
drm                   236330  3 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
tg3                   147729  0 

mar@OptiPlex380:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        A4:BA:DB:07:79:74

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


```

---

### Post by wildmanne39 on 2011-11-11
Hi, did you have errors when you ran this command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
The driver is not loaded.

Did you have internet connection when you ran that command?

Please run it again and watch for errors then shutdown and unplug usb then bootup if it does not come on so you can enter your password then run this command if you did not have errors.
```
sudo modprobe b43
```
Thank you

---

### Post by mmelgaco on 2011-11-11
This broadcom worked fine in my old Ubuntu 10.04 in this same machine.
It stops to work when i installed the 11.10.
Do you know what is happening?
I dind'nt like the unity manager and i considering downgrade to the 10.04.

Thanks!

---

### Post by wildmanne39 on 2011-11-11
Hi, they are using different drivers but I think we can get it to work we just need to find the right combination, and 10.04 will 0nly be supported until April.
Thank you

---

### Post by mmelgaco on 2011-11-11
No, the two apt-get commands runs succesfully. 
I was connected to the internet using my usb wifi adapter.

I will boot up without the wifi adapter and try the modprobe.

thanks

---

### Post by wildmanne39 on 2011-11-11
Hi, ok I think the b43 driver is blacklisted by default in this version so do what you said then modprobe and it should come on if it does we will unblacklist the b43 driver.
Thank you

---

### Post by mmelgaco on 2011-11-11
Hi, 

i shutdown, unplug the wifi adapter.
Then i run modprobe.
The driver get up, but no networks are show.
Yes, the driver is blacklisted, as show the last command
here is the commands:
Thanks.

```


mar@OptiPlex380:/etc/modprobe.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mar@OptiPlex380:/etc/modprobe.d$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
mar@OptiPlex380:/etc/modprobe.d$ lsmod
Module                  Size  Used by
arc4                   12529  2 
b43                   341198  0 
ssb                    52752  1 b43
mac80211              310872  1 b43
cfg80211              199587  2 b43,mac80211
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
dcdbas                 14490  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
parport_pc             36962  1 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 dell_wmi
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
i915                  566711  2 
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
tg3                   147729  0 
mar@OptiPlex380:/etc/modprobe.d$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        A4:BA:DB:07:79:74

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        C4:17:FE:48:0B:3F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


mar@OptiPlex380:/etc/modprobe.d$ iwlist wlan0 scanning
wlan0     No scan results

mar@OptiPlex380:/etc/modprobe.d$ grep b43 *
blacklist.conf:# replaced by b43 and ssb.
broadcom-sta-common.conf:blacklist b43legacy
broadcom-sta-common.conf:blacklist b43


```

---

### Post by wildmanne39 on 2011-11-11
Hi, give me a few minutes so I can do some more research and see if I can find a solution.
This particular card is having issues in 11.10 there is different 4321 cards and one is working great and this one is having issues.
Thank you

---

### Post by wildmanne39 on 2011-11-11
Hi, please post the results of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e wpa -e etwork | tail -n55
```
You will need to have usb unplugged.
```
lsmod | grep b43
```

Thank you

---

### Post by mmelgaco on 2011-11-16
Hi, how are you?
Here is the output of the commands.
I startup the computer without the usb wifi adapter and run the commands.
Thanks!

```


mar@OptiPlex380:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e wpa -e etwork | tail -n55
[sudo] password for mar: 
Nov 16 14:16:47 OptiPlex380 kernel: [   15.762909] Registered led device: b43-phy0::rx
Nov 16 14:16:47 OptiPlex380 kernel: [   15.762923] Registered led device: b43-phy0::radio
Nov 16 14:16:47 OptiPlex380 kernel: [   15.897459] type=1400 audit(1321460207.615:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=908 comm="apparmor_parser"
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: init!
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: update_system_hostname
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPluginIfupdown: management mode: unmanaged
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/ssb0:0/net/wlan0, iface: wlan0)
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: end _init.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    Ifupdown: get unmanaged devices count: 0
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: (18769712) ... get_connections.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    SCPlugin-Ifupdown: (18769712) ... get_connections (managed=false): return empty list.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    keyfile: parsing rumo ... 
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    keyfile:     read connection 'rumo'
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]:    Ifupdown: get unmanaged devices count: 0
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> modem-manager is now available
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver (unknown))
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> Networking is enabled by state file
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> (wlan0): now managed
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 16 14:16:47 OptiPlex380 NetworkManager[876]: <info> (wlan0): bringing up device.
Nov 16 14:16:48 OptiPlex380 kernel: [   16.456016] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (wlan0): preparing device.
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov 16 14:16:48 OptiPlex380 kernel: [   16.578337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 16 14:16:48 OptiPlex380 dbus[864]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): carrier is OFF
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): now managed
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): bringing up device.
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): preparing device.
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (eth0): deactivating device (reason 'managed') [2]
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0
Nov 16 14:16:48 OptiPlex380 dbus[864]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> wpa_supplicant started
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <warn> bluez error getting default adapter: No such adapter
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (wlan0): supplicant interface state: starting -> ready
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov 16 14:16:48 OptiPlex380 NetworkManager[876]: <info> (wlan0): supplicant interface state: ready -> inactive

mar@OptiPlex380:~$ lsmod | grep b43
b43                   341198  0 
mac80211              310872  1 b43
cfg80211              199587  2 b43,mac80211
ssb                    52752  1 b43
mar@OptiPlex380:~$ 



```

---

### Post by northd_tech on 2011-11-16
> **wildmanne39 said:**
> , and 10.04 will 0nly be supported until April.


Hi wildmanne,

Are you sure about that April date?  My understanding is that 10.04.3 LTS means "Long Term Support" (a HUGE portion of the reason(s) why I prefer it).  Well that and the fact that I CAN'T STAND Unity (and Win7/8 or Macintoshes- but that's mostly because of that old single button mouse thing from years ago ;) ).

Anyway- this looks like a Desktop ~2013.3 - Server ~2015.4 to me:
                                **  [LTS]("https://wiki.ubuntu.com/LTS")**


[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

[https://wiki.ubuntu.com/LTS?action=AttachFile&do=get&target=ubuntu-release-cycle-2.png](https://wiki.ubuntu.com/LTS?action=AttachFile&do=get&target=ubuntu-release-cycle-2.png)

> $ **cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 [COLOR=Red]**LTS**[/COLOR]"

Please advise- this concerns me greatly (in fact I had a little bit of a long distance phone 'argument' with my step-brother about what "LTS" means in an Ubuntu context), but he likes that "bleeding edge" [read **broken** IMHO] stuff so whaddya do? ;)

Also, if you have lots of spare time and want to scratch the hair off your head a little bit, I'm having a bit of a Broadcom 4318, 4321, "wl" firmware mystery here:

[http://ubuntuforums.org/showpost.php?p=11462308&postcount=10](http://ubuntuforums.org/showpost.php?p=11462308&postcount=10)

I'm wondering if those Ubuntu 11.xx kernels have been changed considerably in their Broadcom driver regions...

---

### Post by wildmanne39 on 2011-11-16
Hi northd_tech, you are correct, I thought 10.04 support was ending in April 2012 but it looks like it is 2013 and server support is 2015.
Here is a link.
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

It looks like you got your wireless issue resolved, Good Work!!!

I am not on much right now I am writing a guide for ubuntu.

---

### Post by bkratz on 2011-11-16
Here is a chart showing the support dates

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Responded a little slow!

---

### Post by gopo on 2011-11-21
*[deleted]*

---

