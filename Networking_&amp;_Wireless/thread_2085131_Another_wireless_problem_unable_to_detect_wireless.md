---
title: "Another wireless problem: unable to detect wireless networks with BCM4306"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by Muiske on 2012-11-17
Hi all,


On my old laptop now runs Xubuntu 10.04. Everything works fine, except for the wireless network. When using the live cd it detected my network card (Broadcom 4306), installed it and I could see all networks including my own. Now that I have Xubuntu installed all of a sudden, after a few days, it does not detect networks anymore. Needless to say, I can't connect to any network whatsoever except for when I plug in my ethernet cable.

I checked everything and there seem to be no problems.... the hardware runs just fine, software is installed through jockey-gtk and I can manually dis- and enable the adapter. I have found no clues in the system diagnostics (lsmod, lspci and the other usual tools report no errors). I am at a loss here, and close to pulling my hair out. 

Minor detail: there does not seem to be any b43 firmware package in the repositories, might that be a problem??

Anyway, I would GREATLY appreciate any help. Thank you.

/ Harm.

---

### Post by carl4926 on 2012-11-17
With a wired connection do:
```
sudo apt-get install firmware-b43-installer
```

If you don't have a wire connection, let me know. But you'll need to be able to download a file I have one way or another.

---

### Post by Muiske on 2012-11-17
Hi Carl,

Thanks for your answer.

That package is not in the repositories for 10.04. So I cannot download it!
Instead, the package v43-cutter is installed by default.

---

### Post by flash63 on 2012-11-17
Hello,
use this command-line with Ubuntu 10.04:
```
sudo apt-get install --reinstall b43-fwcutter 
```

alternative:
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo service network-manager stop
sudo modprobe -rf b43 b43legacy
sudo modprobe b43 b43legacy
dmesg | grep b43 b43legacy
iwconfig
sudo service network-manager start 
```

---

### Post by carl4926 on 2012-11-17
I can't recall what kernel is in 10.04 but I'm sure it's 2.**

Kernel 3> is providing much better wireless support JFI

I'll PM you a link

If you have a folder b43 in /lib/firmware
We need to rename it

```
cd /lib/firmware
```
```
sudo mv b43 old-b43
```

Now copy the the folder b43 I am sending you to 
/lib/firmware

---

### Post by wildmanne39 on 2012-11-17
Hi, that device could use the legacy driver depending what version it is please do:

copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Muiske on 2012-11-17
Hello all,

@flash63: I have tried re-installing the b43 drivers already, but with no succes. I will try your alternative suggestion later on!

@carl4926: Thanks for the files you sent me. I have installed them - but with no succes either. :( Still no networks will pop up..

@Wild Man: That program comes in handy! These are the results in netinfo.txt:

```
                                                                    
                                                                     
                                                                     
                                             

*************** info trace ****************



**** uname -a ****


Linux HPlaptop 2.6.32-45-generic #99-Ubuntu SMP Tue Oct 16 16:31:11 UTC 2012 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"


**** lspci ****


02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb


**** lsusb ****


Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
dm_crypt               11331  0 
snd_intel8x0           25652  6 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  3 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
b43                   163556  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205434  1 b43
joydev                  8740  0 
cfg80211              126528  2 b43,mac80211
snd                    54244  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  2 
ppdev                   5259  0 
rsrc_nonstatic         10015  1 yenta_socket
psmouse                63677  0 
nvidia               4701243  22 
led_class               2864  1 b43
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               3978  0 
k8temp                  3152  0 
lp                      7028  0 
soundcore               6620  3 snd
parport_pc             25962  1 
shpchp                 28835  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
i2c_nforce2             5199  0 
parport                32635  3 ppdev,lp,parport_pc
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
8139too                18545  0 
softcursor              1189  1 bitblit
8139cp                 16186  0 
amd64_agp               7165  1 
video                  17375  0 
ssb                    38934  1 b43
vga16fb                11385  1 
vgastate                8961  1 vga16fb
mii                     4381  2 8139too,8139cp
pata_amd                8766  3 
output                  1871  1 video
agpgart                31724  2 nvidia,amd64_agp


**** nm-tool ****



NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****




**** NetworkManager.conf-10.04 ****


# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false



**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     No scan results



**** resolv ****


# Generated by NetworkManager
nameserver 192.168.1.1


**** blacklist.conf ****


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


**** dmesg ****


[    1.191923] device-mapper: multipath: version 1.1.0 loaded
[    1.191931] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.720602] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[    2.733980] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[   18.697317] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   18.931849] Registered led device: b43-phy0::tx
[   18.945548] Registered led device: b43-phy0::rx
[   18.945864] Registered led device: b43-phy0::radio
[   19.022745] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   19.072855] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   19.090521] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   19.109301] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   19.476306] b43-phy0: Loading firmware version 508.154 (2009-08-18 00:58:22)
[   19.591547] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************
```

---

### Post by wildmanne39 on 2012-11-17
Hi, I will make this easy just follow this link post 4.
[http://ubuntuforums.org/showthread.php?p=12359625#post12359625](http://ubuntuforums.org/showthread.php?p=12359625#post12359625)
Thanks

---

### Post by flash63 on 2012-11-17
Hello,
for this device ...
```
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```
...  you need the **ucode4.fw** firmware-file.

check it out:
```

dmesg | egrep 'b43|Firm'

```


Follow my second instructions  ... ;-)
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
... and restart.

---

### Post by Muiske on 2012-11-18
@Wild Man: Thank you for your reply. However, after following the instructions in that link you posted, still no networks are detected by the adapter... do you have any other suggestions?

@flash63: I have (finally :D) followed your instructions now. But I am sorry to say without any succes yet. There is no difference in the output of the dmesg command; after installing the firmware you provided still the 'wrong' firmware is being used:

```
dmesg | egrep 'b43|Firm'[    2.702427] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   18.297889] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   18.614909] Registered led device: b43-phy0::tx
[   18.615026] Registered led device: b43-phy0::rx
[   18.615221] Registered led device: b43-phy0::radio
[   18.617217] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   18.825963] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.851639] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   18.870919] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   18.883835] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   19.065385] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```

Is there anything else I have to do? For example replace the ucode5.fw file by the ucode4.fw file manually??

---

### Post by rsavage on 2012-11-18
I think you need to look for a simple solution:
 

Right click on the network applet icon and toggle(turn off and on) 'Enable Networking', 'Enable Wireless' and 'Enable Notifications'.  Make sure you have them all ticked.  If you've had a failed suspend then they can untick themselves.
 
Still no wifi?
 Check you have the correct user settings: Go to System -> Administration -> Users and Groups -> Advanced Settings -> User Privileges 
Make sure "Connect to wireless and ethernet networks" is ticked. This will add your user to the netdev group. You will need to reboot for this to take effect. Note, it is not always necessary to join the netdev group.

---

### Post by carl4926 on 2012-11-18
Did you try the 'wl' proprietary driver?

---

### Post by wildmanne39 on 2012-11-18
Hi, was there any errors when you ran the commands I gave you? It should have worked but I figure there is a conflict because of all the other methods you have tried.

Please do:
```
sudo apt-get purge --remove firmware-b43-installer firmware-b43legacy-installer firmware-b43-lpphy-installer
```
Then:

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if it still does not come on then delete the text info file in your home folder and run the script again and attach the file here so we can see what condition your wireless is in after the changes.
Thanks

---

### Post by Muiske on 2012-11-18
Hello all,

This is incredible: the problem is solved, thanks to the solution rsavage posted. It was just that - the right privileges in my account settings were not enabled. All I had to do was tick the box right next to 'connect to wireless and ethernet networks', reboot and it worked. Thank you rsavage!!

But, besides that I feel incredibly stupid right now for not knowing these options could be changed at all, I wonder what caused this privileged to be revoked in the first place. Because when I installed Xubuntu 10.04, I had access to wireless networking. Something must have disabled it, probably during updating of the software, but why and how? All the effort I put in fixing this is unbelievable, while in the end it was just a matter of a few clicks here and there.... Let's hope it continues to work now.

It is solved now, anyway. I wish to convey my gratitude to Wild Man, carl4926 and flash63 for providing me with helpful suggestions and putting so much effort in helping me on the way. Thank you all!

/ Harm.

PS: @Wild Man; no, there were no errors after entering the commands. That is because I made sure that after installing new firmware, I removed the old version consequently.

---

### Post by wildmanne39 on 2012-11-18
Hi, good the hear, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

