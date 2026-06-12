---
title: "Installed B43 Wireless Drivers, wlan doesn't show up"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by steindor2 on 2010-07-03
Hey guys, I have a Broadcom B4312(I believe) wireless card and installed the drivers for it, but under the Wireless tab in Network Connections, it doesn't show "wlan0" or anything similar to "eth0"(which it shows under "Wired"). I ran iwconfig and this is what I got:
 
juddcaster@judd-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


Any idea what's wrong?
[IMG]http://img192.imageshack.us/img192/205/screenshot3la.png[/IMG]

---

### Post by roosh on 2010-07-03
Could you please run these commands in a terminal and post their outputs:
```
lsusb
``` ```
lspci
``` ```
lsmod
```

---

### Post by steindor2 on 2010-07-03
> **roosh said:**
> Could you please run these commands in a terminal and post their outputs:
```
lsusb
``` ```
lspci
``` ```
lsmod
```
juddcaster@judd-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:030c Quanta Computer, Inc. HP Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


juddcaster@judd-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

juddcaster@judd-laptop:~$ lsmod
Module                  Size  Used by
b43                   157218  0 
ssb                    37336  1 b43
mac80211              204922  1 b43
cfg80211              126485  2 b43,mac80211
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_atiixp_modem        9103  0 
snd_via82xx_modem       8486  0 
snd_intel8x0m          10751  0 
snd_ac97_codec        100646  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus                1002  1 snd_ac97_codec
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  21 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               56990  0 
i915                  282354  3 
drm_kms_helper         29297  1 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
psmouse                63245  0 
serio_raw               3978  0 
joydev                  8708  0 
ricoh_mmc               2923  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  2 b43,sdhci
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
snd_page_alloc          7076  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
intel_agp              24177  2 i915
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
hid_microsoft           2647  0 
usbhid                 36110  0 
hid                    67032  2 hid_microsoft,usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32008  2 
r8169                  33884  0 
mii                     4381  1 r8169

---

### Post by roosh on 2010-07-03
It seems that you have the BCM4312 chip. Keep that in mind and try this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by khuttger on 2010-07-03
Did you do...

```
sudo iwconfig wlan0 up
```

That should do you just good :)

---

### Post by steindor2 on 2010-07-03
Okay, thanks Roosh, I'll check that out. 

EDIT: I've already done this and nothing seemed to happen.
> **khuttger said:**
> Did you do...

```
sudo iwconfig wlan0 up
```That should do you just good :)
juddcaster@judd-laptop:~$ sudo iwconfig wlan0 up
[sudo] password for juddcaster: 
iwconfig: unknown command "up"

---

### Post by khuttger on 2010-07-03
Sorry my mistake try...

```
sudo ifconfig wlan0 up
```

Thats the one I used.

---

### Post by steindor2 on 2010-07-03
> **khuttger said:**
> Sorry my mistake try...

```
sudo ifconfig wlan0 up
```Thats the one I used.
juddcaster@judd-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

Weird, cause that first command I pasted in the opening post seems to recognize something.

---

### Post by khuttger on 2010-07-03
Can you give me the output of

```
ifconfig
```

Thanks

---

### Post by steindor2 on 2010-07-03
eth0      Link encap:Ethernet  HWaddr 00:1b:24:fe:fa:78  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fefe:fa78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6973381 (6.9 MB)  TX bytes:2399149 (2.3 MB)
          Interrupt:28 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:ee:82:38  
          inet6 addr: fe80::21a:73ff:feee:8238/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

---

### Post by khuttger on 2010-07-03
SO it appears you dont even have a wireless interface =/

That would be a problem. Heres what I did for my debian box (kinda the same right?) 
```
sudo aptitude install b43-fwcutter wireless-tools
modprobe b43
iwconfig
sudo ifconfig wlan0 up
```

I had to add the repository for it and it extracted and installed the firmware for me. Try those

---

### Post by /b/rotard on 2010-07-03
I had the exact same problem as you. Go onto broadcom's site and download the appropriate tarball.
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Follow the instructions in the readme (aka remove conflicting drivers), and then install. Now it works like a charm :)

---

### Post by steindor2 on 2010-07-03
> **khuttger said:**
> SO it appears you dont even have a wireless interface =/

That would be a problem. Heres what I did for my debian box (kinda the same right?) 
```
sudo aptitude install b43-fwcutter wireless-tools
modprobe b43
iwconfig
sudo ifconfig wlan0 up
```I had to add the repository for it and it extracted and installed the firmware for me. Try those

Should I uninstall the STA wireless driver first?

---

### Post by /b/rotard on 2010-07-03
> **steindor2 said:**
> Should I uninstall the STA wireless driver first?

Yea, it also mentions some other things you might wanna do in the readme from broadcom.

One weird thing though is now my wireless show up on the interface eth1....but it doesn't interrupt anything for me lol.

---

### Post by khuttger on 2010-07-03
> **/b/rotard said:**
> Yea, it also mentions some other things you might wanna do in the readme from broadcom.

One weird thing though is now my wireless show up on the interface eth1....but it doesn't interrupt anything for me lol.

Yes, i believe eth1 can be used as a wireless interface along with some others.

---

### Post by steindor2 on 2010-07-03
> **/b/rotard said:**
> I had the exact same problem as you. Go onto broadcom's site and download the appropriate tarball.
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Follow the instructions in the readme (aka remove conflicting drivers), and then install. Now it works like a charm :)
I can't remove "wl", it says permission denied. I tried adding "sudo" before teh command, but it didn't work either.

juddcaster@judd-laptop:~$ lsmod | grep "b43\|ssb\|wl"
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
juddcaster@judd-laptop:~$ echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
juddcaster@judd-laptop:~$ sudo echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
juddcaster@judd-laptop:~$

---

### Post by khuttger on 2010-07-03
Just hilight the STA one by clicking remove under Hardware Drivers.

---

### Post by steindor2 on 2010-07-03
> **khuttger said:**
> SO it appears you dont even have a wireless interface =/

That would be a problem. Heres what I did for my debian box (kinda the same right?) 
```
sudo aptitude install b43-fwcutter wireless-tools
modprobe b43
iwconfig
sudo ifconfig wlan0 up
```I had to add the repository for it and it extracted and installed the firmware for me. Try those
The first command seemed to be successful and a few prompts to download stuff came up, but when I tried the second command, I got errors:
juddcaster@judd-laptop:~$ modprobe b43
WARNING: Error inserting mac80211 (/lib/modules/2.6.32-21-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
WARNING: Error inserting ssb (/lib/modules/2.6.32-21-generic/kernel/drivers/ssb/ssb.ko): Operation not permitted
FATAL: Error inserting b43 (/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted

---

### Post by /b/rotard on 2010-07-03
> **steindor2 said:**
> The first command seemed to be successful and a few prompts to download stuff came up, but when I tried the second command, I got errors:
juddcaster@judd-laptop:~$ modprobe b43
WARNING: Error inserting mac80211 (/lib/modules/2.6.32-21-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
WARNING: Error inserting ssb (/lib/modules/2.6.32-21-generic/kernel/drivers/ssb/ssb.ko): Operation not permitted
FATAL: Error inserting b43 (/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted

You did not use sudo.

I can't remove "wl", it says permission denied. I tried adding "sudo" before teh command, but it didn't work either.

juddcaster@judd-laptop:~$ lsmod | grep "b43\|ssb\|wl"
wl 1959598 0 
lib80211 5046 2 lib80211_crypt_tkip,wl
juddcaster@judd-laptop:~$ echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
juddcaster@judd-laptop:~$ sudo echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
juddcaster@judd-laptop:~$

Try opening (with sudo) the file with a text editor. ex sudo nano /etc/modprobe.d/blacklist.conf
 
btw, i never blacklisted, it is not a necessary step, but a convenience. I have had no problems not blacklisting.

---

### Post by steindor2 on 2010-07-03
> **/b/rotard said:**
> You did not use sudo.

juddcaster@judd-laptop:~$ sudo modprobe b43
juddcaster@judd-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
juddcaster@judd-laptop:~$ sudo ifconfig wlan0 up
juddcaster@judd-laptop:~$ 


I'm gonna go try to restart. Not sure if it worked or not, nothing shows up under the Wireless tab still.

---

### Post by steindor2 on 2010-07-03
> **/b/rotard said:**
> 
Try opening (with sudo) the file with a text editor. ex sudo nano /etc/modprobe.d/blacklist.conf
 
btw, i never blacklisted, it is not a necessary step, but a convenience. I have had no problems not blacklisting.
EDIT: Okay, I managed to blacklist it. Now I need to try and follow the rest of the instructions.

EDIT: Also, nothing happened after that last restart, the contents of " lsmod  | grep "b43\|ssb\|wl" are different, but there's still nothing under the Wireless tab of Network Connections.

Another EDIT: I'm actually pretty confused now. I'm trying to do this:
> **/b/rotard said:**
> I had the exact same problem as you. Go onto  broadcom's site and download the appropriate tarball.
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Follow the instructions in the readme (aka remove conflicting drivers),  and then install. Now it works like a charm :)

But I'm kind of lost in the instructions of the readme. I've already installed the proper packages:
> On Ubuntu, you will need headers and tools.  Try these commands:
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux

To check to see if you have this directory do this:

# ls /lib/modules/`uname -r`/build

And now it tells me this:> 
1. Setup the directory by untarring the proper tarball:

For 32 bit:     hybrid-portsrc.tar.gz
For 64 bit:     hybrid-portsrc-x86_64.tar.gz

# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

But when I try that it says:
juddcaster@judd-laptop:~/hybrid_wl$ tar xzf <path>/hybrid-portsrc.tar
bash: path: No such file or directory
juddcaster@judd-laptop:~/hybrid_wl$

---

### Post by khuttger on 2010-07-03
Nothing will show up under the wireless tab. Maybe your Essid is hidden too. so manualy add that.

---

### Post by steindor2 on 2010-07-03
> **khuttger said:**
> Nothing will show up under the wireless tab. Maybe your Essid is hidden too. so manualy add that.
I don't understand, like this?
[IMG]http://img15.imageshack.us/img15/6216/screenshot6ba.png[/IMG]

---

### Post by khuttger on 2010-07-03
yup thats the way now just edit the name to the essid of your router :) and go from there :)

---

### Post by steindor2 on 2010-07-03
> **khuttger said:**
> yup thats the way now just edit the name to the essid of your router :) and go from there :)
Okay I filled out the network name and password and disconnected my wired connection and it didnt' work.

EDIT: Please keep replying, I might not be able to respond though, because I need to get off my wired connection for now. I'll try to check back when I can.

---

### Post by /b/rotard on 2010-07-04
Lol did you do tar.gz or just .tar?

I can not tonight (its 1 am here...), but if this problem persists into tomorrow, I can teamview you.

EDIT: the other guy is different, wireless works as advertised if you follow the steps in the readme.... Some steps are not necessary, just do the essential ones.

---

### Post by Praveen30 on 2010-07-04
> **steindor2 said:**
> Okay I filled out the network name and password and disconnected my wired connection and it didnt' work.

EDIT: Please keep replying, I might not be able to respond though, because I need to get off my wired connection for now. I'll try to check back when I can.

I also had the same problem.i have found the solution just by running the update command...may be it works in yours problem..
[http://ubuntuforums.org/showthread.php?t=1510778]("http://http//ubuntuforums.org/showthread.php?t=1510778")

---

### Post by steindor2 on 2010-07-06
Okay guys, thanks for the help. All I had to do was re-install the drivers through the Hardware Drivers utility and then set up the connection manually. Last time I set it up manually, I didn't know which information I had to put, but I followed a video and got it working. Thanks to everyone that helped me.

---

