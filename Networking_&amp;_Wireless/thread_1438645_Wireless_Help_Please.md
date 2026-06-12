---
title: "Wireless Help Please"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by banksj17 on 2010-03-25
I am unable to connect to my wireless network. When I click on Network manager it says under wireless "device not managed" Please help me. [IMG]http://img638.imageshack.us/img638/2489/83585262.jpg[/IMG]

---

### Post by chili555 on 2010-03-25
Disabled? I wonder why it's disabled. Please post:```
rfkill list
dmesg | grep wlan0
```You don't have to do a cumbersome screenshot. You can copy and paste out of the terminal into a text editor, such as gedit, and copy and paste out of the text editor into your reply.

---

### Post by banksj17 on 2010-03-26
Sorry it took me so long. I was at work all day. Also sorry about the picture, I was not sure how you guys did things around here. The comands you gave me are not giving any output.

---

### Post by chili555 on 2010-03-26
Let's take a look at:```
dmesg | grep rtl
```Thanks.

---

### Post by banksj17 on 2010-03-26
Looks like fail. I have no idea whats going on. Ohh some extra info. The driver I am using is from Realtek support. 
```
    joshua@joshua-laptop:~$ dmesg | grep rtl
  
  [   12.436997] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  
  [   12.437004] rtl819xE 0000:03:00.0: setting latency timer to 64
  
  [   12.777633] rtllib_crypt: registered algorithm 'NULL'
  
  [   12.777638] rtllib_crypt: registered algorithm 'TKIP'
  
  [   12.777639] rtllib_crypt: registered algorithm 'CCMP'
  
  [   12.777641] rtllib_crypt: registered algorithm 'WEP'
  
  [   12.777660] proc_dir_entry 'net/rtl819xE' already registered
  
  [   12.777733]  [<ffffffffa02e3000>] ? rtl8192_pci_module_init+0x0/0x124 [r8192e_pci]
  
  [   12.777741]  [<ffffffffa02e3000>] ? rtl8192_pci_module_init+0x0/0x124 [r8192e_pci]
  
  [   12.777757]  [<ffffffffa029467a>] rtl8192_proc_module_init+0x2a/0x50 [r8192e_pci]
  
  [   12.777765]  [<ffffffffa02e30fa>] rtl8192_pci_module_init+0xfa/0x124 [r8192e_pci]
  
  [   12.777791] Error: Driver 'rtl819xE' is already registered, aborting...
  
  [   13.707394] rtl819xE: PlatformInitFirmware()==>
  
  [   13.707431] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/boot.img
  
  [   13.776884] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/main.img
  
  [   13.991313] rtl819xE:Download Firmware: Put code fail!
  
  [   13.991318] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
  
  [   13.991321] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
  
  [   13.991323] rtl819xE:ERR in init_firmware()
  
  [   13.991326] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
```

---

### Post by chili555 on 2010-03-26
> The driver I am using is from Realtek support.It appears that you have two drivers loading and you may not have the needed firmware. A driver from Realtek's website should not be required in Lucid, as far as I know. Let's do some more troubleshooting. Please post:```
lsmod | grep rtl
lspci -nn
```The second command will produce a fair amount of output; feel free to strip away everything that's clearly not your Realtek. Also, open up Synaptic and assure you have installed *linux-firmware.*

---

### Post by banksj17 on 2010-03-26
```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01) 
 07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) 
```

---

### Post by chili555 on 2010-03-26
> I am not seeing Linux-firmware in synaptic.In Synaptic, open Settings > Repositories and enable as attached. Press Reload and then find and install *linux-firmware.*

---

### Post by banksj17 on 2010-03-26
I am not sure if this helps but its not showing any networks around me. When I click connect to a hidden network, enter my network info and click join it just says Wireless Disconnected.

---

### Post by banksj17 on 2010-03-26
> **chili555 said:**
> In Synaptic, open Settings > Repositories and enable as attached. Press Reload and then find and install *linux-firmware.*
It has an explanation mark. 

EDIT: I updated it and its now green

---

### Post by chili555 on 2010-03-26
Is the ethernet cable attached all this time?

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themCan you connect or do you see networks if you detach the cable, wait a few moments and click the Network Manager icon?

May I see:```
lsmod | grep -e r819 -e rtl
```Thanks.

---

### Post by banksj17 on 2010-03-26
yea I knew about the wired. I unconnected the wire when trying wireless and it does not change. it shows no networks and will not connect to any when my info is enter manually 

```
[COLOR=Red] r819[/COLOR]2_pci             269306  0 
```

---

### Post by chili555 on 2010-03-26
Sorry, I took a few moments to boot the live CD of Lucid in order to better diagnose this. Let's see what the kernel says:```
dmesg | grep -e 819 -e wlan
rfkill list
```

---

### Post by banksj17 on 2010-03-26
> **chili555 said:**
> Sorry, I took a few moments to boot the live CD of Lucid in order to better diagnose this. Let's see what the kernel says:```
dmesg | grep -e 819 -e wlan
rfkill list
```

rfkill list gives no feedback. 
```
joshua@joshua-laptop:~$ dmesg | grep -e 819 -e wlan
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91480 r8192 d23208 u524288
[    0.000000] pcpu-alloc: s91480 r8192 d23208 u524288 alloc=1*2097152
[    0.494819] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.498199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP4_._PRT]
[   11.042819] Registered led device: mmc0::
[   11.453472] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   11.457175] Linux kernel driver for RTL8192 based WLAN cards
[   11.457222] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.457230] rtl819xE 0000:03:00.0: setting latency timer to 64
[   15.855856] rtl819xE: PlatformInitFirmware()==>
[   15.855887] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/boot.img
[   16.212396] rtl819xE:request firmware fail!
[   16.212400] rtl819xE:ERR in init_firmware()
[   16.212404] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!


```

---

### Post by chili555 on 2010-03-26
Please check here:  [http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-761714/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-761714/)

The file referred to in post #13 contains, among other things, boot.img. I suggest you download it and extract it and I will be back in a few moments to help get it in place.

---

### Post by banksj17 on 2010-03-26
Ok I got it but I will have to wait for you because I do not know where to go from here.

---

### Post by chili555 on 2010-03-26
Hey, look at my avatar. I had to flip over the record!

By default, Lucid downloads to a folder called Downloads; let's check:```
ls Downloads
```You should see the zip file you downloaded and, if you right-clicked and selected Extract Here, a folder called *rtl8192efirmware*. Let's make a directory and then move the files:```
sudo mkdir /lib/firmware/RTL8192E
sudo cp Downloads/rtl8192efirmware/* /lib/firmware/RTL8192E
```Now, let's make sure the ownership and permissions are correct:```
sudo chown root:root /lib/firmware/RTL8192E/*
sudo chmod 644 /lib/firmware/RTL8192E/*
```Now, detach the cable, reboot and enjoy the wireless...or post:```
dmesg | grep -e 819 -e wlan

```

---

### Post by banksj17 on 2010-03-26
Ok I am going to try this but I have an unrelated question. I am dual booting with Windows 7 64bit. I am using ubuntu 64 bit but is it better to use the 32? I am not sure if one is better than the other or if it does not matter.

---

### Post by banksj17 on 2010-03-26
```
joshua@joshua-laptop:~$ dmesg | grep -e 819 -e wlan
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91480 r8192 d23208 u524288
[    0.000000] pcpu-alloc: s91480 r8192 d23208 u524288 alloc=1*2097152
[   14.692078] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   14.698674] Linux kernel driver for RTL8192 based WLAN cards
[   14.698720] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.698728] rtl819xE 0000:03:00.0: setting latency timer to 64
[   16.300869] rtl819xE: PlatformInitFirmware()==>
[   16.300901] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/boot.img
[   16.396974] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/main.img
[   16.610332] rtl819xE:Download Firmware: Put code fail!
[   16.610339] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   16.610342] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
[   16.610344] rtl819xE:ERR in init_firmware()
[   16.610348] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
```

---

### Post by chili555 on 2010-03-26
The compiled from Realtek may not work with 64-bit. However, we can always uninstall it. The dual-boot should be irrelevant.

---

### Post by banksj17 on 2010-03-26
> **chili555 said:**
> The compiled from Realtek may not work with 64-bit. However, we can always uninstall it. The dual-boot should be irrelevant.
The driver they gave me and I have put on  here worked on 64bit 9.10
EDIT: I am not sure if you saw my output back on page 2.

---

### Post by chili555 on 2010-03-26
I am wondering if the file you downloaded indicated in any way that is was 64-bit. If not, it probably wasn't. What was the symptom that suggested you needed to download and compile a driver instead of using the built-in?

---

### Post by banksj17 on 2010-03-26
9.10 did not have a built in driver for my card. I emailed Realtek and they sent me a file and said that it was the correct driver.

---

### Post by banksj17 on 2010-03-26
Here is the file they emailed me if it helps
[http://www.mediafire.com/?jfnmnmnnjnd](http://www.mediafire.com/?jfnmnmnnjnd)

---

### Post by chili555 on 2010-03-26
I'm confused. Your avatar says 'Development Release' which is, as far as I know, is Lucid, also known as 10.04, which does include rtl8192e:> /lib/modules/2.6.32-16-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-16-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-16-generic/kernel/ubuntu/rtl8192se/r8192se_pci.koNo wonder I am struggling!

What do you have?```
uname -r
```

---

### Post by banksj17 on 2010-03-26
> **chili555 said:**
> I'm confused. Your avatar says 'Development Release' which is, as far as I know, is Lucid, also known as 10.04, which does include rtl8192e:No wonder I am struggling!

What do you have?```
uname -r
```
I am running 10.04 now coming from 9.10 This is why I am having problems. I know it is supposed to have rtl8192e and I dont know why its not working. I am going to do a clean install of 10.04 and see what I get. I will not install the driver they emailed me and let the default load.

---

### Post by chili555 on 2010-03-26
Good. Hop on here and let's get you going!

---

### Post by banksj17 on 2010-03-26
> **chili555 said:**
> Good. Hop on here and let's get you going!

Ok I have a new install. What do you want to see first?

---

### Post by chili555 on 2010-03-26
Let's see:```
lspci -nn
lsmod | grep 819
iwconfig
```Thanks.

---

### Post by banksj17 on 2010-03-26
> **chili555 said:**
> Let's see:```
lspci -nn
lsmod | grep 819
iwconfig
```Thanks.

```
jsohua@jsohua-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
02:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
02:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
02:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
```

```
jsohua@jsohua-laptop:~$ lsmod | grep 819
r8192_pci             269306  0 
```

```
jsohua@jsohua-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chili555 on 2010-03-26
> wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0You have an interface and the driver is loaded. Can you detach the ethernet cable, wait a few moments for Network Manager to see the change of state and click on the icon, see networks and connect?

---

### Post by banksj17 on 2010-03-26
I just get a disconnected and it show no networks.

---

### Post by chili555 on 2010-03-26
Please do:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Any improvement?

---

### Post by banksj17 on 2010-03-26
> **chili555 said:**
> Please do:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Any improvement?

```
joshua@joshua-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for joshua: 
SIOCSIFFLAGS: Operation not permitted

joshua@joshua-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by chili555 on 2010-03-26
What kind of laptop is it? Please post:```
lsmod
dmesg | grep 819
```

---

### Post by banksj17 on 2010-03-27
Day 3: Thanks for all your help so far. Its looking like that boot.img again so I am going to fix that and see where that takes us. 
```
joshua@joshua-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10834  1 
fat                    55286  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   278794  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5779  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12693  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25453  2 
snd_hda_codec          85855  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41362  0 
snd_mixer_oss          16267  1 snd_pcm_oss
snd_pcm                87978  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31187  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23521  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62339  0 
snd                    71010  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  319868  3 
drm_kms_helper         30742  1 i915
sdhci_pci               6700  0 
joydev                 11072  0 
intel_agp              29165  1 
psmouse                64288  0 
serio_raw               4886  0 
videodev               40422  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
soundcore               8052  1 snd
v4l2_compat_ioctl32    12020  1 videodev
snd_page_alloc          8660  2 snd_hda_intel,snd_pcm
r8192_pci             269306  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  1 sdhci
drm                   198930  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            48969  1 
usbhid                 40860  0 
hid                    83312  1 usbhid
r8169                  40002  0 
mii                     5205  1 r8169
joshua@joshua-laptop:~$ 

```

```
joshua@joshua-laptop:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91352 r8192 d23336 u524288
[    0.000000] pcpu-alloc: s91352 r8192 d23336 u524288 alloc=1*2097152
[    8.058190] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[   12.571980] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   12.575769] Linux kernel driver for RTL8192 based WLAN cards
[   12.575824] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.575831] rtl819xE 0000:03:00.0: setting latency timer to 64
[   14.411605] rtl819xE: PlatformInitFirmware()==>
[   14.411664] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/boot.img
[   14.456906] rtl819xE:request firmware fail!
[   14.456909] rtl819xE:ERR in init_firmware()
[   14.456912] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!

```

---

### Post by banksj17 on 2010-03-27
Its a Toshiba Satellite M505-S4940 
```
joshua@joshua-laptop:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91352 r8192 d23336 u524288
[    0.000000] pcpu-alloc: s91352 r8192 d23336 u524288 alloc=1*2097152
[   12.321728] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   12.326996] Linux kernel driver for RTL8192 based WLAN cards
[   12.327047] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.327054] rtl819xE 0000:03:00.0: setting latency timer to 64
[   13.896736] rtl819xE: PlatformInitFirmware()==>
[   13.896766] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/boot.img
[   13.956994] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/main.img
[   14.020052] rtl819xE:Download Firmware: Put code fail!
[   14.020058] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   14.020060] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
[   14.020062] rtl819xE:ERR in init_firmware()
[   14.020065] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!

```

---

### Post by chili555 on 2010-03-27
Oh, boy! A Realtek with a firmware problem. Let me just get a horse tranquilizer. Please do:```
sudo updatedb
locate 8192 | grep -e firmware -e img
```updatedb will take a few moments, please be patient. Thanks, I think.

---

### Post by banksj17 on 2010-03-27
Im sorry. Hope I am not being too much trouble
 [code]joshua@joshua-laptop:~$ locate 8192 | grep -e firmware -e img
/home/joshua/Downloads/rtl8192efirmware
/home/joshua/Downloads/rtl8192efirmware.zip
/home/joshua/Downloads/rtl8192efirmware/boot.img
/home/joshua/Downloads/rtl8192efirmware/data.img
/home/joshua/Downloads/rtl8192efirmware/main.img
/lib/firmware/RTL8192E
/lib/firmware/RTL8192SE
/lib/firmware/RTL8192E/boot.img
/lib/firmware/RTL8192E/data.img
/lib/firmware/RTL8192E/main.img
/lib/firmware/RTL8192SE/rtl8192sfw.bin
/lib/firmware/RTL8192SE/rtl8192sfw492.bin
/lib/firmware/RTL8192SE/rtl8192sfw74.bin

---

### Post by chili555 on 2010-03-27
I might have the permissions wrong. Please do:```
sudo chmod 755 /lib/firmware/RTL8192E/*
```Reboot and run:```
dmesg | grep 819

```Pray; pray hard!

---

### Post by banksj17 on 2010-03-27
> **chili555 said:**
> I might have the permissions wrong. Please do:```
sudo chmod 755 /lib/firmware/RTL8192E/*
```Reboot and run:```
dmesg | grep 819

```Pray; pray hard!


```
joshua@joshua-laptop:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91352 r8192 d23336 u524288
[    0.000000] pcpu-alloc: s91352 r8192 d23336 u524288 alloc=1*2097152
[   12.488712] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   12.501108] Linux kernel driver for RTL8192 based WLAN cards
[   12.501169] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.501177] rtl819xE 0000:03:00.0: setting latency timer to 64
[   14.046298] rtl819xE: PlatformInitFirmware()==>
[   14.046341] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/boot.img
[   14.073235] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/main.img
[   14.380118] rtl819xE:Download Firmware: Put code fail!
[   14.380122] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   14.380125] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
[   14.380127] rtl819xE:ERR in init_firmware()
[   14.380130] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!

```

---

### Post by chili555 on 2010-03-27
I'm probably grasping at straws here, but let's try:
```
sudo mkdir /lib/firmware/`uname -r`/RTL8192E
```Those tickmarks are on the upper left of my US keyboard on the same key with ~.
```
sudo cp /lib/firmware/RTL8192E/*  /lib/firmware/`uname -r`/RTL8192E
sudo rmmod -f r8192_pci
sudo modprobe r8192_pci
dmesg | grep 819
```Please post what happens after [  14.38..]

---

### Post by banksj17 on 2010-03-27
sudo modprobe r8192_pci has been working for a few minutes is that normal?

---

### Post by chili555 on 2010-03-27
No. Please open a terminal and do:```
sudo tail -f /var/log/messages
```See what's going on. You might be able to kill modprobe with Ctrl-C.

---

### Post by banksj17 on 2010-03-27
```
joshua@joshua-laptop:~$ sudo tail -f /var/log/messages
[sudo] password for joshua: 
Mar 27 18:47:33 joshua-laptop kernel: [  728.241827]  [<ffffffff81364218>] driver_detach+0xc8/0xd0
Mar 27 18:47:33 joshua-laptop kernel: [  728.241834]  [<ffffffff81363135>] bus_remove_driver+0x85/0xe0
Mar 27 18:47:33 joshua-laptop kernel: [  728.241841]  [<ffffffff81364872>] driver_unregister+0x62/0xa0
Mar 27 18:47:33 joshua-laptop kernel: [  728.241848]  [<ffffffff812caf65>] pci_unregister_driver+0x45/0xc0
Mar 27 18:47:33 joshua-laptop kernel: [  728.241862]  [<ffffffffa0097571>] rtl8192_pci_module_exit+0x15/0x46 [r8192_pci]
Mar 27 18:47:33 joshua-laptop kernel: [  728.241869]  [<ffffffff8109cf28>] sys_delete_module+0x1a8/0x270
Mar 27 18:47:33 joshua-laptop kernel: [  728.241876]  [<ffffffff81087b9e>] ? up_read+0xe/0x10
Mar 27 18:47:33 joshua-laptop kernel: [  728.241884]  [<ffffffff810131f2>] system_call_fastpath+0x16/0x1b
Mar 27 18:47:33 joshua-laptop kernel: [  728.241950]  RSP <ffff880118613cd0>
Mar 27 18:47:33 joshua-laptop kernel: [  728.241957] ---[ end trace 1ea90eb1e0de0a19 ]---


```

---

### Post by chili555 on 2010-03-27
I have no idea, but it looks serious! Googling. What does this tell us?```
dmesg | grep 819
```

---

### Post by banksj17 on 2010-03-27
```
joshua@joshua-laptop:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91352 r8192 d23336 u524288
[    0.000000] pcpu-alloc: s91352 r8192 d23336 u524288 alloc=1*2097152
[   12.723773] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   12.745750] Linux kernel driver for RTL8192 based WLAN cards
[   12.746344] rtl819xE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.746353] rtl819xE 0000:03:00.0: setting latency timer to 64
[   13.726495] rtl819xE: PlatformInitFirmware()==>
[   13.726527] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/boot.img
[   13.826894] rtl819xE 0000:03:00.0: firmware: requesting RTL8192E/main.img
[   14.212001] rtl819xE:Download Firmware: Put code fail!
[   14.212007] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   14.212009] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
[   14.212011] rtl819xE:ERR in init_firmware()
[   14.212015] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[  728.241603] Modules linked in: binfmt_misc ppdev snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd sdhci_pci uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 joydev psmouse sdhci serio_raw led_class i915 drm_kms_helper intel_agp drm i2c_algo_bit r8192_pci(C-) soundcore snd_page_alloc video output lp parport usbhid hid r8169 mii
[  728.241791]  [<ffffffffa0072009>] rtl8192_free_rx_ring+0x69/0x150 [r8192_pci]
[  728.241805]  [<ffffffffa00977a9>] rtl8192_pci_disconnect+0xf6/0x1ab [r8192_pci]
[  728.241862]  [<ffffffffa0097571>] rtl8192_pci_module_exit+0x15/0x46 [r8192_pci]
joshua@joshua-laptop:~$ 

```

---

### Post by chili555 on 2010-03-27
I'm baffled. If you reboot and it springs a kernel panic, it will be hard to get repaired without a lot of tinkering with a live CD; not for the faint-hearted. I don't quite know how to fix it. It was already not working!

We could easily blacklist it and get it going, but why? The point was, I think, to get the wireless going. If you want to blacklist r8192_pci, do:```
sudo su
echo "blacklist r8192_pci" >> /etc/modprobe.d/blacklist.conf
exit
```

We certainly ought to report it to the developers so they can fix this before Lucid's final release.

May I hear your thoughts?

---

### Post by banksj17 on 2010-03-27
I agree they should know about this.

---

### Post by chili555 on 2010-03-27
[https://bugs.launchpad.net/ubuntu/lucid/+bugs](https://bugs.launchpad.net/ubuntu/lucid/+bugs)

---

### Post by banksj17 on 2010-03-27
I am not really sure what to put. Any ideas?

---

### Post by chili555 on 2010-03-27
Upper right: [COLOR="DarkOrange"]Report a bug[/COLOR]. You will probably have to register.

I think the bug ought to report that the module r8192_pci asks for firmware that doesn't exist and that all attempts to add it have failed. Include *dmesg | grep 819* showing such.

---

### Post by moaoci on 2010-03-28
The dmesg messages from post #19 show the same errors as with the drivers prior to version 13 that you posted in #24.  I verified the posted driver and it is the same as the one I use ( 64bit 9.10 Karmic) and that you also used in the same configuration.

It makes me wonder if the realtek driver gets precedence over the Lucid Lynx driver.  Command  lshw -C network  should show what driver is actually used:

```
....
       configuration: broadcast=yes driver=rtl819xE driverversion=0013.0127.2010 ip=192.168.1.103 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:5000(size=256) memory:d5100000-d5103fff
....
```
If the  configuration line DOES NOT shows 0013.0127.2010, it means that somehow, the kernel driver is taking over.  Did you do a make clean before the make install ?   In that case, Chili555 may be a better help to point to the right Realtek driver first.

But if the configuration line shows 0013.0127.2010 , I would really appreciate that you also contact [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL] to verify what's going on with the driver in Lucid Lynx. ( I am sticking to 9.10 until someone reports that RTL8192E is functionnal under Lucid )

I hope you find the problem soon !

---

