---
title: "New ubuntu install, wireless does not work"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by lukew101 on 2013-07-14
Hi, I just installed ubuntu on my new laptop to dual boot with windows.  I'm using the 64 bit version of precise pangolin and my computer is a dell inspiron 3521.  After looking up a similar thread I ran the following command and got the following out put:

lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)

I then put the following command in the terminal

rfkill list all

There was no output, it just gave me a new command line.

Any help would be greatly appreciated

Thanks,
Luke

---

### Post by Yellow Pasque on 2013-07-14
It's an AR9565 chipset. You need a kernel >= 3.7 (or you could try one of those wireless backports packages, like 'linux-backports-modules-cw-3.8-precise-generic-pae'

---

### Post by lukew101 on 2013-07-15
OK, how do I get kernel >=3.7 ?

Also, is there a drawback to the wireless backport packages?

---

### Post by lukew101 on 2013-07-15
I used the instructions from this site to upgrade my kernel to 3.7, still using 12.04.2:

[http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html](http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html)

Now when I go to the networking menu at the top right of the screen it gives the option to enable wireless network.  When I do that it finds my wireless network and automatically connects, but when I try to open firefox it still tells me that it cannot find the server.  Any ideas on what to do to fix that?

Thanks.
Luke

---

### Post by wildmanne39 on 2013-07-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by praseodym on 2013-07-15
I recommend using kernel 3.9 which is also flagged as stable

---

### Post by lukew101 on 2013-07-15
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

I ran the command. It didn't create a tar.gz file, just a txt file.  Here is the text from that:


```
*************** info trace ***************

***** uname -a *****

Linux luke-Inspiron-3521 3.7.0-030700-generic #201212102335 SMP Tue Dec 11 04:36:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0c45:649a Microdia 

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

***** lsmod *****

ath9k                 147526  0 
mac80211              573649  1 ath9k
ath9k_common           14054  1 ath9k
ath9k_hw              417643  2 ath9k,ath9k_common
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
cfg80211              217913  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12
    DNS:             192.168.1.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search at.cox.net

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[   13.146376] ath: phy0: ASPM enabled: 0x43
[   13.146377] ath: EEPROM regdomain: 0x60
[   13.146378] ath: EEPROM indicates we should expect a direct regpair map
[   13.146379] ath: Country alpha2 being used: 00
[   13.146380] ath: Regpair used: 0x60
[   13.197481] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.197782] Registered led device: ath9k-phy0

****************** done ******************
```

---

### Post by praseodym on 2013-07-15
Switch on your wireless ;)

---

### Post by lukew101 on 2013-07-15
> **praseodym said:**
> Switch on your wireless ;)

To the best of my knowledge I have it switched on.  I rebooted to windows to make sure that it was on there and toggled it on/off/on with Fn F2.  There is no hard switch.  I then rebooted in ubuntu.  Once I checked enable wireless on the network menu (top right of screen) it appeared to be on and connected, except that it won't connect to any website.  I also checked the networking section in the systems menu on the lower left side of the screen.  Under the wireless section there is a virtual slider switch that is also set to on, but still won't connect to any website.

---

### Post by praseodym on 2013-07-15
Then try```


sudo rfkill unblock all
rfkill list  #check
iwconfig  #check
```

---

### Post by wildmanne39 on 2013-07-15
If that does not work please post the output of:
```
lsmod
```
Thanks

---

### Post by lukew101 on 2013-07-15
It did not work.  Here is the output from those commands:


```
luke@luke-Inspiron-3521:~$ sudo rfkill unblock all
[sudo] password for luke: 
luke@luke-Inspiron-3521:~$ rfkill list  #check
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
luke@luke-Inspiron-3521:~$ iwconfig  #check
eth0      no wireless lions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
luke@luke-Inspiron-3521:~$ 


And here is the output from the lsmod:

luke@luke-Inspiron-3521:~$ lsmod
Module                  Size  Used by
parport_pc             32867  0 
rfcomm                 47923  12 
bnep                   18400  2 
ppdev                  17114  0 
arc4                   12574  2 
ath9k                 147526  0 
mac80211              573649  1 ath9k
joydev                 17614  0 
snd_hda_codec_hdmi     37116  1 
coretemp               13555  0 
snd_hda_codec_realtek    79808  1 
ath9k_common           14054  1 ath9k
i915                  588292  3 
snd_hda_intel          38522  3 
snd_hda_codec         140413  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
uvcvideo               82215  0 
ath9k_hw              417643  2 ath9k,ath9k_common
kvm_intel             137787  0 
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
btusb                  18292  0 
videobuf2_core         36138  1 uvcvideo
kvm                   441559  1 kvm_intel
videodev              130085  2 uvcvideo,videobuf2_core
snd_hwdep              17765  1 snd_hda_codec
snd_pcm               102478  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm_kms_helper         46934  1 i915
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
drm                   286536  4 i915,drm_kms_helper
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts5139               350620  0 
bluetooth             219394  24 rfcomm,bnep,btusb
cfg80211              217913  3 ath9k,mac80211,ath
mei                    41468  0 
ghash_clmulni_intel    13260  0 
dell_laptop            17426  0 
cryptd                 20531  1 ghash_clmulni_intel
dell_wmi               12682  0 
soundcore              15092  1 snd
sparse_keymap          13891  1 dell_wmi
microcode              23076  0 
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
dcdbas                 14491  1 dell_laptop
lp                     17800  0 
snd_page_alloc         18799  2 snd_hda_intel,snd_pcm
wmi                    19257  1 dell_wmi
mac_hid                13254  0 
i2c_algo_bit           13565  1 i915
lpc_ich                17145  0 
psmouse                92405  0 
parport                46563  3 parport_pc,ppdev,lp
serio_raw              13216  0 
video                  19413  1 i915
r8169                  68841  0 
luke@luke-Inspiron-3521:~$
```

---

### Post by Yellow Pasque on 2013-07-15
Did you try to connect to the router after that?

---

### Post by lukew101 on 2013-07-15
I just tried to connect again after running lsmod.  This time it could find websites but was extremely slow.  The speed is fine when I'm connected with a cable though.

---

### Post by wildmanne39 on 2013-07-15
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
if you have anymore trouble with softblocks do:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by lukew101 on 2013-07-15
Thanks, that last one worked.  I'm going to try rebooting and see if it still is ok.  If it's fine after reboot I'll mark the thread solved.  In case it is helpful, here is the output:

luke@luke-Inspiron-3521:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for luke: 
options ath9k nohwcrypt=1
luke@luke-Inspiron-3521:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.7.0-030700-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.7.0-030700-generic/kernel/net/wireless/cfg80211.ko
luke@luke-Inspiron-3521:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.7.0-030700-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.7.0-030700-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.7.0-030700-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
luke@luke-Inspiron-3521:~$ echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist dell_laptop
luke@luke-Inspiron-3521:~$

---

### Post by lukew101 on 2013-07-15
Thanks for the help everyone, the internet works fine after reboot, I'm going to mark the thread solved.  On another note, my fan seems to run more after the fix, but I'm fine with that.

---

### Post by wildmanne39 on 2013-07-15
Glad it is working! You should have not effected the fan speed at all. things like upgrading the kernel or installing a new video card driver can do that.
Thanks

---

### Post by wildmanne39 on 2013-07-15
*Thread moved to **Networking & Wireless**.*

---

### Post by Gurmel on 2013-09-15
Hello, please find the info gather below from my machine...

I have Dell Inspiron 15 - 3521

As i am new to ubuntu world.. please help to solve this problem..

Problem: Wifi not working


*************** info trace ***************

***** uname -a *****

Linux khalsa-Inspiron-3521 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0c45:64ad Microdia 

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: asleep

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address  removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth0"

***** dmesg *****


****************** done ******************

---

### Post by praseodym on 2013-09-15
Hi,

please update the kernel via cable connection. obviously, this device is not part of kernel 3.5:

```
sudo apt-get install --reinstall linux-headers-generic-lts-raring linux-image-generic-lts-raring build-essential dkms 
```
Reboot and check
```
iwconfig
cat /var/lib/NetworkManager/NetworkManager.state
modinfo ath9k
uname -a
```

---

### Post by Carlos_Dunick on 2013-09-15
for me it says that there are no wireless extensions

---

### Post by Yellow Pasque on 2013-09-15
@Gurmel and Carlos_Dunick:
You need Ubuntu >= 13.04 (or Ubuntu 12.04.3) because you need a 3.8 kernel for the wireless to work. If you're trying to use an older Ubuntu release and don't have a wired interent connection available to update the kernel, then you're SOL.

---

### Post by praseodym on 2013-09-15
Open the file
```

gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
change "false" to "true" and restart the network
```

sudo service networkmanager restart
```

---

### Post by Carlos_Dunick on 2013-09-15
@teüjin.   i have Ubuntu 13.04 lts with a wired connection.

@praseodym    this is something new i have seen,   unfortunately everyone is set to True

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

---

### Post by Carlos_Dunick on 2013-09-15
even with the restart which i tried before the wired connection disables and wifi starts flashing and then gives up.   then the wired connection estahblishes again.

One thing to note is that on the drop down internet icon on the top right there is no possibility for a wireless connection... hmmm

---

### Post by praseodym on 2013-09-15
Deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Check:
```

modinfo ath9k
dmesg | grep ath9k
iwlist chan
sudo iwlist scan
iwconfig wlan0
rfkill list
lsmod
```

---

### Post by Gurmel on 2013-09-18
Thanks a lot Temujin... it (version upgrade) worked for me..

---

