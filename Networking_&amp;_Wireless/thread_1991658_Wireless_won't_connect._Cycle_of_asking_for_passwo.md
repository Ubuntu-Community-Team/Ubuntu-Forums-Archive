---
title: "Wireless won't connect. Cycle of asking for password."
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by heylovie on 2012-05-30
First off, followed all instructions here:
[http://ubuntuforums.org/showthread.php?t=1898644](http://ubuntuforums.org/showthread.php?t=1898644)
And after executing the command by wildmanne39 : 
> gksu gedit /etc/modprobe.d/options.confand then
> 
options iw14965 11n_disable=1I have now have no wireless to control. However, here's the problem before that.

Just for clarity, I've got the right password saved in the network connections. I've tried deleting the connection and then re-creating it.

I'm able to see the wireless connections, I can select one, but when it asks for the password, it takes about 20-30 seconds attempting to connect, but ends up popping back up asking for the password again. Endless cycle. Not sure what to do.

cat /etc/lsb-release; uname -a
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Lindaslaptop 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:51:22 UTC 2012 i686 athlon i386 GNU/Linuxlspci -nnk | grep -iA2 net
> 00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
    Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network [103c:0024]
    Kernel driver in use: natsemiiwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.lsmod
> Module                  Size  Used by
dm_crypt               22528  0
joydev                 17393  0
snd_ali5451            23459  2
snd_ac97_codec        106082  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                87213  0
serio_raw              13027  0
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39791  0
snd                    62064  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0
i2c_ali15x3            12878  0
pcmcia_rsrc            18367  1 yenta_socket
rfcomm                 38139  0
bnep                   17830  2
i2c_ali1535            12777  0
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32114  1
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0
shpchp                 32325  0
snd_page_alloc         14115  1 snd_pcm
binfmt_misc            17292  1
mac_hid                13077  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
radeon                729591  2
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
pata_ali               13562  2
floppy                 60310  0
natsemi                31943  0
video                  19068  0
i2c_algo_bit           13199  1 radeon
usbhid                 41906  0
ati_agp                13242  1
hid                    77367  1 usbhidLet me know what other info I should be providing. I know that my internal wireless card is a broadom 4306.


Thanks

---

### Post by wildmanne39 on 2012-05-31
Hi, first options iw14965 11n_disable=1 when you typed that line where you have the one it should have been a small l, so always copy and paste for accuracy.

Second if you have a 4306 then that will not work even if the command did not have a typo because that is for an intel card.

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by heylovie on 2012-05-31
Thanks for the reply!
```

linda@Lindaslaptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Lindaslaptop 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:51:22 UTC 2012 i686 athlon i386 GNU/Linux
linda@Lindaslaptop:~$ lspci -nnk | grep -iA2 net
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
    Subsystem: Compaq Computer Corporation Device [0e11:00e7]
    Kernel modules: ssb
--
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
    Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network [103c:0024]
    Kernel driver in use: natsemi
    Kernel modules: natsemi
linda@Lindaslaptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
linda@Lindaslaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

linda@Lindaslaptop:~$ rfkill list all
linda@Lindaslaptop:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_ali5451            23459  2 
snd_ac97_codec        106082  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
pcmcia                 39791  0 
joydev                 17393  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
i2c_ali1535            12777  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ppdev                  12849  0 
shpchp                 32325  0 
binfmt_misc            17292  1 
psmouse                87213  0 
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
radeon                729591  2 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
usbhid                 41906  0 
hid                    77367  1 usbhid
natsemi                31943  0 
i2c_algo_bit           13199  1 radeon
pata_ali               13562  2 
floppy                 60310  0 
video                  19068  0 
ati_agp                13242  1 

```

---

### Post by wildmanne39 on 2012-05-31
Hi, let's try the simple thing first:
```
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```
```
sudo modprobe b43
```
Does it come to life?
Thanks

---

### Post by heylovie on 2012-05-31
Did this:
```
linda@Lindaslaptop:~$ sudo apt-get install b43-fwcutter firmware-b43legacy-installer
[sudo] password for linda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  libunity6 language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  libdee-1.0-1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  firmware-b43legacy-installer
0 upgraded, 1 newly installed, 0 to remove and 49 not upgraded.
Need to get 0 B/3,000 B of archives.
After this operation, 33.8 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package firmware-b43legacy-installer.
(Reading database ... 203121 files and directories currently installed.)
Unpacking firmware-b43legacy-installer (from .../firmware-b43legacy-installer_1%3a015-9_all.deb) ...
Setting up firmware-b43legacy-installer (1:015-9) ...
No chroot environment found. Starting normal installation
--2012-05-31 15:17:26--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org (downloads.openwrt.org)... 78.24.191.177
Connecting to downloads.openwrt.org (downloads.openwrt.org)|78.24.191.177|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652866 (638K) [text/plain]
Saving to: `wl_apsta-3.130.20.0.o'

100%[======================================>] 652,866      239K/s   in 2.7s    

2012-05-31 15:17:29 (239 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

Deleting old extracted firmware...
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
linda@Lindaslaptop:~$ sudo modprobe b43

```

But nothing showing up yet. Under the menu item on the top right it lists the wired network connection but no wireless yet.

---

### Post by heylovie on 2012-05-31
Here's what I mean

[IMG]https://dl.dropbox.com/u/82370429/Selection_005.png[/IMG]

---

### Post by wildmanne39 on 2012-05-31
Hi, please post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e radio -e switch -e wpa -e wlan -e etork | tail -n75
```
```
lsmod | grep b43
```
install rkfill then post output of:
```
rfkill list all
```
```
nm-tool
ls /lib/firmware/b43
```
Thanks

---

### Post by heylovie on 2012-06-01
```
linda@Lindaslaptop:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e radio -e switch -e wpa -e wlan -e etork | tail -n75
[sudo] password for linda: 
May 31 15:17:31 Lindaslaptop NetworkManager[1025]: <info> kernel firmware directory '/lib/firmware' changed
May 31 15:17:44 Lindaslaptop kernel: [ 5375.042452] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
May 31 15:50:55 Lindaslaptop kernel: [    0.000000] APIC: switched to apic NOOP
May 31 15:50:55 Lindaslaptop kernel: [    0.008509] SMP alternatives: switching to UP code
May 31 15:50:55 Lindaslaptop kernel: [    2.513675] Console: switching to colour frame buffer device 128x48
May 31 15:50:55 Lindaslaptop NetworkManager[576]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 31 15:50:55 Lindaslaptop NetworkManager[576]: <info> WiFi enabled by radio killswitch; enabled by state file
May 31 15:50:55 Lindaslaptop NetworkManager[576]: <info> WWAN enabled by radio killswitch; enabled by state file
May 31 15:50:55 Lindaslaptop NetworkManager[576]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  1 00:11:26 Lindaslaptop kernel: [    0.000000] APIC: switched to apic NOOP
Jun  1 00:11:26 Lindaslaptop kernel: [    0.012704] SMP alternatives: switching to UP code
Jun  1 00:11:26 Lindaslaptop kernel: [    2.503811] Console: switching to colour frame buffer device 128x48
Jun  1 00:11:26 Lindaslaptop NetworkManager[563]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  1 00:11:26 Lindaslaptop NetworkManager[563]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  1 00:11:26 Lindaslaptop NetworkManager[563]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  1 00:11:26 Lindaslaptop NetworkManager[563]: <info> WiMAX enabled by radio killswitch; enabled by state file
```

```
linda@Lindaslaptop:~$ rfkill list all
linda@Lindaslaptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            natsemi
  State:             connected
  Default:           yes
  HW Address:        00:0F:20:21:32:2E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             24.205.224.36


linda@Lindaslaptop:~$ ls /lib/firmware/b43

```

---

### Post by wildmanne39 on 2012-06-01
Hi, please show:
```
ls /lib/firmware
```
Thanks

---

### Post by heylovie on 2012-06-01
```
linda@Lindaslaptop:~$ ls /lib/firmware
2.6.38-15-generic            libertas
3.0.0-20-generic             matrox
3.2.0-24-generic             mrvl
3com                         mts_cdma.fw
acenic                       mts_edge.fw
adaptec                      mts_gsm.fw
advansys                     mts_mt9234mu.fw
agere_ap_fw.bin              mts_mt9234zba.fw
agere_sta_fw.bin             mwl8335_duplex.fw
aic94xx-seq.fw               mwl8k
ar3k                         myri10ge_ethp_z8e.dat
ar7010_1_1.fw                myri10ge_eth_z8e.dat
ar7010.fw                    myri10ge_rss_ethp_z8e.dat
ar9170-1.fw                  myri10ge_rss_eth_z8e.dat
ar9170-2.fw                  myricom
ar9170.fw                    NPE-B
ar9271.fw                    NPE-C
asihpi                       ositech
ath3k-1.fw                   phanfw.bin
ath6k                        ql2100_fw.bin
atmel_at76c502_3com.bin      ql2200_fw.bin
atmel_at76c502.bin           ql2300_fw.bin
atmel_at76c502d.bin          ql2322_fw.bin
atmel_at76c502e.bin          ql2400_fw.bin
atmel_at76c504_2958.bin      ql2500_fw.bin
atmel_at76c504a_2958.bin     qlogic
atmel_at76c504.bin           r128
atmel_at76c506.bin           radeon
atmsar11.fw                  rt2561.bin
av7110                       rt2561s.bin
b43legacy                    rt2661.bin
bnx2                         rt2860.bin
bnx2x                        rt2870.bin
brcm                         rt3070.bin
carl9170-1.fw                rt3071.bin
cis                          rt3090.bin
cpia2                        rt73.bin
cxgb3                        RTL8192E
cxgb4                        RTL8192SE
dabusb                       rtl_nic
dsp56k                       rtlwifi
dvb-fe-xc5000-1.6.114.fw     s2250.fw
dvb-usb-dib0700-1.20.fw      s2250_loader.fw
dvb-usb-terratec-h5-drxk.fw  sb16
e100                         scripts
ea                           slicoss
edgeport                     sun
emi26                        sxg
emi62                        TDA7706_OM_v2.5.1_boot.txt
ene-ub6250                   TDA7706_OM_v3.0.2_boot.txt
ess                          tehuti
f2255usb.bin                 ti_3410.fw
GPL-3                        ti_5052.fw
hp                           ti-connectivity
htc_7010.fw                  tigon
htc_9271.fw                  tlg2300_firmware.bin
i2400m-fw-usb-1.4.sbcf       tr_smctr.bin
i2400m-fw-usb-1.5.sbcf       ttusb-budget
i6050-fw-usb-1.5.sbcf        ueagle-atm
intelliport2.bin             usbdux
ipw2100-1.3.fw               usbduxfast_firmware.bin
ipw2100-1.3-i.fw             usbdux_firmware.bin
ipw2100-1.3-p.fw             usbduxsigma_firmware.bin
ipw2200-bss.fw               v4l-cx231xx-avcore-01.fw
ipw2200-ibss.fw              v4l-cx23418-apu.fw
ipw2200-sniffer.fw           v4l-cx23418-cpu.fw
isci                         v4l-cx23418-dig.fw
iwlwifi-1000-5.ucode         v4l-cx2341x-dec.fw
iwlwifi-100-5.ucode          v4l-cx2341x-enc.fw
iwlwifi-105-6.ucode          v4l-cx2341x-init.mpg
iwlwifi-135-6.ucode          v4l-cx23885-avcore-01.fw
iwlwifi-2000-6.ucode         v4l-cx23885-enc.fw
iwlwifi-2030-6.ucode         v4l-cx25840.fw
iwlwifi-3945-2.ucode         v4l-pvrusb2-24xxx-01.fw
iwlwifi-4965-2.ucode         v4l-pvrusb2-29xxx-01.fw
iwlwifi-5000-5.ucode         vicam
iwlwifi-5150-2.ucode         vntwusb.fw
iwlwifi-6000-4.ucode         vxge
iwlwifi-6000g2a-5.ucode      WHENCE.ubuntu
iwlwifi-6000g2b-6.ucode      whiteheat.fw
iwlwifi-6050-5.ucode         whiteheat_loader.fw
kaweth                       yam
keyspan                      yamaha
keyspan_pda                  zd1201-ap.fw
korg                         zd1201.fw
lbtf_usb.bin                 zd1211
lgs8g75.fw

```

---

### Post by wildmanne39 on 2012-06-01
Hi, let's do this:

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
That should do it.
Thanks

---

### Post by heylovie on 2012-06-01
Not sure if I'm doing this right.

Here's what I've done. The first command doesn't seem to be working. At the beginning there I hadn't unpacked the zip file yet, but then I did and re-ran the commands. So...

```
linda@Lindaslaptop:~$ sudo mkdir /lib/firmware/b43
[sudo] password for linda: 
Sorry, try again.
[sudo] password for linda: 
linda@Lindaslaptop:~$ sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
linda@Lindaslaptop:~$ sudo cp Desktop/b43/* /lib/firmware/b43
cp: cannot stat `Desktop/b43/*': No such file or directory
linda@Lindaslaptop:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
linda@Lindaslaptop:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
linda@Lindaslaptop:~$ sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
linda@Lindaslaptop:~$ sudo cp Desktop/b43/* /lib/firmware/b43
linda@Lindaslaptop:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
linda@Lindaslaptop:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
linda@Lindaslaptop:~$ sudo modprobe b43
linda@Lindaslaptop:~$ sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
linda@Lindaslaptop:~$ sudo cp Desktop/b43/* /lib/firmware/b43
linda@Lindaslaptop:~$ sudo rmmod -f b43
linda@Lindaslaptop:~$ sudo rmmod -f ssb
linda@Lindaslaptop:~$ sudo modprobe b43
linda@Lindaslaptop:~$ 

```

---

### Post by wildmanne39 on 2012-06-01
Hi, if you extracted it to the desktop then reboot and try this please:
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by heylovie on 2012-06-01
Did it.

Weird that it asked for my password again. I know it was correct when I entered it.

```
linda@Lindaslaptop:~$ cd Desktop
linda@Lindaslaptop:~/Desktop$ sudo mv b43/* /lib/firmware
[sudo] password for linda: 
Sorry, try again.
[sudo] password for linda: 
linda@Lindaslaptop:~/Desktop$ sudo rmmod -f b43
linda@Lindaslaptop:~/Desktop$ sudo rmmod -f ssb
linda@Lindaslaptop:~/Desktop$ sudo modprobe b43
linda@Lindaslaptop:~/Desktop$ 

```

---

### Post by wildmanne39 on 2012-06-01
Hi, did your wireless come on? is it working now?
Thanks

---

### Post by heylovie on 2012-06-01
I got nothing.

Here's a screen shot of the network connections only letting me add vpn but no wireless, and now in the menu bar there's only "enable" it but no "wired" or others.

[IMG]https://dl.dropbox.com/u/82370429/Selection_001.png[/IMG]

[IMG]https://dl.dropbox.com/u/82370429/Selection_003.png[/IMG]

---

### Post by wildmanne39 on 2012-06-01
Hi, post a screenshot of what it shows after you click on edit connections.
Please post:
```
lsmod | grep b43
dmesg | egrep 'b43|firm'
```
Thanks

---

### Post by heylovie on 2012-06-01
[IMG]https://dl.dropbox.com/u/82370429/2/Selection_003.png[/IMG]

[IMG]https://dl.dropbox.com/u/82370429/2/Selection_005.png[/IMG]

---

### Post by wildmanne39 on 2012-06-01
Hi, please do:
```
rm /etc/modprobe.d/options.conf 
```
Take out the spaces in your network name and reboot.
Edit:
After reboot:
Please do:
```
sudo modprobe b43
```
Please post after the reboot:
```
ls /lib/firmware/b43
dmesg | grep b43
```
Thanks

---

### Post by heylovie on 2012-06-02
```
linda@Lindaslaptop:~$ ls /lib/firmware/b43
a0g0bsinitvals5.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  n0initvals11.fw
a0g0bsinitvals9.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  pcm5.fw
a0g0initvals5.fw     b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode11.fw
a0g0initvals9.fw     b0g0bsinitvals5.fw   lp0initvals13.fw    ucode13.fw
a0g1bsinitvals13.fw  b0g0bsinitvals9.fw   lp0initvals14.fw    ucode14.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw    lp0initvals15.fw    ucode15.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw     n0absinitvals11.fw  ucode5.fw
a0g1initvals13.fw    b0g0initvals9.fw     n0bsinitvals11.fw   ucode9.fw
linda@Lindaslaptop:~$ dmesg | grep b43
[  115.706857] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10

```

---

### Post by wildmanne39 on 2012-06-02
Hi, please install pastebin then run the following commands:
```
sudo apt-get install pastebinit
dmesg > lovie.txt
lsmod >> lovie.txt
ls /etc/modprobe.d >> lovie.txt
cat /etc/modues >> lovie.txt 
```
one line at a time, this will create text files,  after you have run all the commands open the text files and copy and paste the contents at this link [http://paste.ubuntu.com/](http://paste.ubuntu.com/) so we can see them, then post the link in this thread.
Thanks

---

### Post by heylovie on 2012-06-04
Problem with last command. (The Report a Problem app came up and says somehing about the get-apt program not working or something, it's kind of frozen now...):

```
linda@Lindaslaptop:~$ sudo apt-get install pastebinit
[sudo] password for linda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunity6 libdee-1.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-configobj
The following NEW packages will be installed:
  pastebinit python-configobj
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 249 kB of archives.
After this operation, 1,740 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main python-configobj all 4.7.2+ds-3build1 [233 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/universe pastebinit all 1.3-2ubuntu2 [16.0 kB]
Fetched 249 kB in 2s (111 kB/s)  
Selecting previously unselected package python-configobj.
(Reading database ... 207459 files and directories currently installed.)
Unpacking python-configobj (from .../python-configobj_4.7.2+ds-3build1_all.deb) ...
Selecting previously unselected package pastebinit.
Unpacking pastebinit (from .../pastebinit_1.3-2ubuntu2_all.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up python-configobj (4.7.2+ds-3build1) ...
Setting up pastebinit (1.3-2ubuntu2) ...
linda@Lindaslaptop:~$ dmesg > lovie.txt
linda@Lindaslaptop:~$ lsmod >> lovie.txt
linda@Lindaslaptop:~$ ls /etc/modprobe.d >> lovie.txt
linda@Lindaslaptop:~$ cat /etc/modues >> lovie.txt
cat: /etc/modues: No such file or directory
linda@Lindaslaptop:~$ cat /etc/modues >> lovie.txt
cat: /etc/modues: No such file or directory
linda@Lindaslaptop:~$ dmesg > lovie.txt
linda@Lindaslaptop:~$ lsmod >> lovie.txt
linda@Lindaslaptop:~$ ls /etc/modprobe.d >> lovie.txt
linda@Lindaslaptop:~$ cat /etc/modues >> lovie.txt
cat: /etc/modues: No such file or directory
linda@Lindaslaptop:~$ 

```

---

### Post by heylovie on 2012-06-04
Here's the only file I found:

[http://paste.ubuntu.com/1022521/](http://paste.ubuntu.com/1022521/)

---

### Post by chili555 on 2012-06-04
Wild Man-

I see the following that are alarming:> [    0.077751] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[    0.077918] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[    0.078092] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) [COLOR="Red"]*0, disabled.[/COLOR]
[    0.078240] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *9
[    0.078402] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) [COLOR="Red"]*0, disabled.[/COLOR]
[    0.078565] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 11) [COLOR="Red"]*0, disabled.[/COLOR]
[    0.078711] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[    0.078873] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[    0.079017] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9I suggest that the BIOS be examined and all available IRQs be enabled. I have the best luck with IRQs on 'Auto Select.'> [    2.167725] powernow: No PST tables match this cpuid (0x7a0)
[    2.167727] powernow: [COLOR="Red"]This is indicative of a broken BIOS.[/COLOR]
[    2.167730] powernow: Trying ACPI perflibI suggest the BIOS be updated.> [    0.856643] tun: Universal TUN/TAP device driver, 1.6
[    0.856645] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>Is this a virtual machine?

Back to our regularly scheduled guru!

---

### Post by wildmanne39 on 2012-06-04
Hi heylovie, please do what chili555 suggests he is the wireless expert and my mentor.

Thank you chili555.

---

### Post by heylovie on 2012-06-04
Sounds great.

How do I update the BIOS and enable Auto IRQs?

Also, this is not a virtual machine.

---

### Post by wildmanne39 on 2012-06-04
Hi, here is a link to update bios in ubuntu.
[http://www.ehow.com/how_7256759_update-bios-ubuntu.html](http://www.ehow.com/how_7256759_update-bios-ubuntu.html)
if you have windows you can use it.

If you need anymore help with upgrading the bios I recommend that you start a thread just for the bios in installation and upgrades or the general section.
Thanks

---

