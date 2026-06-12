---
title: "Dual boot 8.0.4 / 10.04 wireless connection"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by sracusin on 2011-09-26
I just installed 10.04 along side 8.04 on my Dell mini. The wireless connection is still functioning on the 8.04 OS but not with the 10.04. 
I have tried on an unsecured connection without luck
Card make is BCM4312 (rev01)
I am concerned that what ever I do on the 10.04 will cause the 8.04 connection to fail so I haven't followed any of the instructions. I also haven't seen an issue in the forum like mine with dual booting, one side works-the other doesn't.

---

### Post by wildmanne39 on 2011-09-26
Hi, you do not need to worry about one install breaking the other they are completely separate.
Please post the results of these commands:
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

### Post by sracusin on 2011-09-26
This is from terminal on 8.04. -nnk is not recognized nor is rfkill list all. I got different results from 10.4 obviously but I don't know how to copy the code (from 10.04) without a network connection! I am not sure if this is helpful. ~Thanks

```
sdr@sdr:~$ lspci -nn | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
sdr@sdr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sms       no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:1  Signal level:173  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sdr@sdr:~$ rfkill list all
bash: rfkill: command not found
sdr@sdr:~$ rfkill
bash: rfkill: command not found

sdr@sdr:~$ lsmod
Module                  Size  Used by
michael_mic             3456  2 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8452  1 ecb
wl                   1278804  0 
parport_pc             36260  0 
ppdev                  10372  0 
parport                37704  2 parport_pc,ppdev
sms1xxx                42116  0 
mbm                     7424  0 
cdc_ether               7168  1 mbm
cdc_acm                18848  0 
uvcvideo               58244  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
rfcomm                 41232  2 
l2cap                  25600  13 rfcomm
hci_usb                16540  0 
bluetooth              60900  5 rfcomm,l2cap,hci_usb
i915                   32640  3 
acpi_cpufreq           10796  1 
cpufreq_conservative     8712  0 
cpufreq_userspace       5156  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
drm                    82324  4 i915
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
snd_seq_midi            9376  0 
snd_seq_oss            35456  0 
snd_seq_dummy           4868  0 
snd_pcm_oss            42144  0 
snd_hda_intel         368176  1 
snd_seq_midi_event      8320  2 snd_seq_midi,snd_seq_oss
snd_rawmidi            25760  1 snd_seq_midi
snd_hwdep              10500  1 snd_hda_intel
snd_pcm                78724  2 snd_pcm_oss,snd_hda_intel
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq                54224  6 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_rawmidi,snd_seq
snd                    56996  13 snd_seq_oss,snd_seq_dummy,snd_pcm_oss,snd_hda_intel,snd_rawmidi,snd_hwdep,snd_pcm,snd_mixer_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ieee80211_crypt_tkip    11520  0 
r8169                  34564  0 
ieee80211_crypt         6912  2 wl,ieee80211_crypt_tkip
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
psmouse                68200  0 
fuse                   50324  3 
ahci                   28548  0 
squashfs               49032  0 
unionfs                78032  0 
ehci_hcd               37900  0 
usbhid                 32256  0 
hid                    38912  1 usbhid
isofs                  36132  0 
zlib_inflate           18176  2 squashfs,isofs
sdr@sdr:~$ 

```

---

### Post by wildmanne39 on 2011-09-26
Hi, yes I really needed the results from 10.04, you can copy then to a jump drive or better known as usb drive then use 8.
04 to post them here, but try this first if it does not work I will need to see the results of those commands from 10.04.
```
sudo modprobe wl
```
Thank you

---

### Post by Megaptera on 2011-09-27
I found this Dell Mini wireless fix also worked in 10.04 too, don't forget the re-boot it mentions. Hope this helps?

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by sracusin on 2011-09-27
Wildmann - flash drive - duh! sorry for being challenged.
sudo modprobe wl did not work. There is no parameter for wl or anything close so those results are not included. ~Thanks sracusin

```
sdr@sdr-laptop:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
sdr@sdr-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
sdr@sdr-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:e8:af:2f:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:56:4f:33:a0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sdr@sdr-laptop:~$ rfkill list all
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
sdr@sdr-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
arc4                    1153  2 
i915                  282354  4 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 36110  0 
b43                   157218  0 
uvcvideo               56990  0 
compal_laptop           2034  0 
drm_kms_helper         29297  1 i915
intel_agp              24177  2 i915
psmouse                63245  0 
mac80211              204922  1 b43
usb_storage            39425  1 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
dcdbas                  5422  0 
soundcore               6620  1 snd
drm                   162471  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
hid                    67032  1 usbhid
serio_raw               3978  0 
cfg80211              126485  2 b43,mac80211
led_class               2864  1 b43
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  33884  0 
mii                     4381  1 r8169
ssb                    37336  1 b43
sdr@sdr-laptop:~$ 

```

---

### Post by wildmanne39 on 2011-09-27
Hi, it is quite possible we will need to use a different driver for your wireless, please post the results of these commands.
```
cat /etc/lsb-release; uname -a
```
```
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm|wlan0'
```
Thank you

---

### Post by sracusin on 2011-09-27
Wildmann- Looks like driver w/firmware? One of the postings had the BCM site but I may need help with download and location ~thanks sdr

```
sdr@sdr-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
Linux sdr-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
sdr@sdr-laptop:~$ sudo iwlist scan
[sudo] password for sdr: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

sdr@sdr-laptop:~$ dmesg | egrep 'b43|firm|wlan0'
[    1.332679] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.332710] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   13.700894] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   14.004039] Registered led device: b43-phy0::tx
[   14.004096] Registered led device: b43-phy0::rx
[   14.004149] Registered led device: b43-phy0::radio
[   14.809303] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   15.009863] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   15.018720] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   15.018903] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   15.019086] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   15.264804] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   15.270827] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   15.284505] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   15.284698] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   15.284892] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   38.962818] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   38.980137] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   39.002427] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   39.002439] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   39.002449] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   39.092322] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   39.110887] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   39.129738] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   39.129752] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   39.129763] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1269.413340] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[ 1269.417419] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[ 1269.429667] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 1269.429680] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 1269.429689] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
sdr@sdr-laptop:~$ 

```

---

### Post by wildmanne39 on 2011-09-27
Hi, that is what I suspected, with the kernel version you are using the b43 driver is not supported for your wireless card

Have you ran any updates since you installed your card?

How did you install the b43 driver?

Do you have a wired connection?
Thank you

---

### Post by sracusin on 2011-09-27
Wildmann- I have a network connection right now on 8.04 Hardy. The Dell mini came with drivers and it worked out of the box. But as I just tried to run the updates (86 total) I recalled that I could NEVER run them. I always go this: An error occured
W: GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release:
The following signatures were invalid: BADSIG 40976EAF437D05B5
Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

repeated a few times. I have read about the BADSIG, but never paid attention since I wanted to upgrade to 10.04.

If the two OSs are separate, I hope that I can update 10.04 and forget the updates on 8.04. I might want to format the disk and start again with 10.04 as long as I have the ability to get the drivers and or firmware. 
Thanks
sdr

---

### Post by wildmanne39 on 2011-09-27
Hi, first 8.04 is no longer supported so you will not be able to get updates for it so it will be at risk for viruses.

If you can not plug it in to update 10.04 then we need to blacklist the b43 driver and ssb so you can use the 10.04 livecd to install the sta driver so we can get this working.
```
sudo su
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
exit
```
Then put your livecd into the cd rom then open synaptic package manager click on settings, repositories, in the window that opens where is says installable from cd/dvd rom put a check mark by cdrom then close that window type broadcom into the search window of synaptic install bcmwl-kernel-source, it will automatically install the required dependencies. 
then remove your livecd and restart your computer and the connection should come a live and you can enter your security key to connect.
Thank you

---

### Post by sracusin on 2011-09-27
Wildmann- 
My only option from the CD is bcmwl-modaliases
installed version 5.60.48.36+bdcom-Oubuntu3  (not a typo)
Latest version (same as above)
Description: Modaliases for the Broadcom 802.11 Linux STA driver

STATUS: INSTALLED. I can't mark it for installation or upgrade

I did a reload and the kernal appeared for installation
there is also a firmware b43-fwcutter that I am not installing but probably should - one thing at a time
of the 11 items about 7 failed (one of them is listed at the bottom)
After rebooting and removing CD I tried to activate the package but it failed because it "failed to fetch from the cdrom:..." - put it back in the drive - still failed
path on cdrom is /pool/main/patch/patch_2.6ubuntu1_i386.deb File not found

I am going to download the package and try a different tack unless you think of something
Thanks~sdr

---

### Post by wildmanne39 on 2011-09-27
Hi, I asked a friend that is our expert to help us out here, so hopefully he will pop in soon.

You can also locate the files under ./pool/restricted/b/bcmwl on the Ubuntu install cd. 
Thank you

---

### Post by wildmanne39 on 2011-09-27
Hi, the livecd you used was for 10.04 correct?
Thank you

---

### Post by sracusin on 2011-09-27
Wildmann- I was there already and tried to install the package directly from the cdrom but it really appears that fetch is going out to the network when I don't have a network connection! 
FAILED TO FETCH [http://archive.ubuntu.com/](http://archive.ubuntu.com/)...
Using the Synaptics packages did the same when the I checked get from cdrom
a konundrum

---

### Post by wildmanne39 on 2011-09-27
Hi, did you put a check mark by cdrom in synaptic before trying to install from the cd?
Thank you

---

### Post by sracusin on 2011-09-27
Yes I did. I kept noticing that it was fetching from the net. It is doing the same thing directly from the package on the cd.
Again, the two OSs are separate so it wouldn't help to do anything on the 8.04 side.
Thanks, many thanks

---

### Post by sracusin on 2011-09-27
Hi, yes also to the query about using the livecd 10.04. I am following directions carefully
Thanks ~sdr

---

### Post by wildmanne39 on 2011-09-27
Hi, I am looking into the possibility of downloading the files and giving them to you in a zip then you could install them from your flash drive, but I am not good at that, so give me a few minutes.
Thank you

---

### Post by wildmanne39 on 2011-09-27
Hi, see if this helps, with your cd in open synaptic then click reload and see if you can install it then.
Thank you

---

### Post by sracusin on 2011-09-27
Wildmann -
You are great! I have been doing this at work and leaving soon and won't be able to communicate until late tonight (east coast) or tomorrow. Will wait patiently for your very excellent help.
Thanks ~sdr

---

### Post by westie457 on 2011-09-27
Hi I have a b4311 chip in my laptop and if I remember correctly to get wireless to work in 10.04 I had to use the bcmwl driver from the cd and b43-fwcutter also from the cd and reboot.

@ wildemanne39 do you think this might work for the OP's 4312 chip.

If not I will step back and learn from one of the people who knows more than me.

---

### Post by wildmanne39 on 2011-09-27
Hi westie457, no because his card with the kernel version he has needs the sta driver, if he was using the updated kernel 2.6.33 or later then he could use it.

Thank you for the suggestion though.

---

### Post by chili555 on 2011-09-27
> **wildmanne39 said:**
> his card with the kernel version he has needs the sta driver, if he was using the updated kernel 2.6.33 or later then he could use it.Do you have a citation or link? You are probably correct, I just haven't seen it before.

---

### Post by wildmanne39 on 2011-09-27
Hi chili555, this is the link.
[http://linuxwireless.org/en/users/Drivers/b43#switch_b43](http://linuxwireless.org/en/users/Drivers/b43#switch_b43)

Do you thank it is worth trying since it says 2.6.33+? he is using 2.6.32
Thank you

---

### Post by chili555 on 2011-09-27
> Do you thank it is worth trying Absolutely! You can do so easily by downloading the b43 firmware installer and simply rmmod wl and modprobe b43. If it works, then remove bcmwl-kernel-source and the b43 blacklist. If not, nothing harmed.

I think it will.

---

### Post by wildmanne39 on 2011-09-27
Hi sracusin, this is what we are going to try since you have no internet on your computer.

Just in case any of the driver or firmware installed run this command please:
```
rmmod -f wl
```

Down load the b43 zip file to your flash drive then drag and drop the file to your 10.04 desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
sudo modprobe ssb
```
Run the commands one at a time and cross your finger's that your wireless comes on.
If this works we will need to unblacklist the ssb and b43 drivers.
Thank you chili555 for your suggestion.

---

### Post by sracusin on 2011-09-28
Wildmann39 and chili555-
from terminal on 10.04 OS ran rmmod -f wl 
result: ERROR: Removing 'wl': Operation not permitted

GETTING CLOSE! list of wireless networks finally appeared but can't connect yet.

...so I assume my next step is to UNblacklist the protocols?

I have the code to blacklist but your help would be appreciated.

Thanks ~sracusin

---

### Post by wildmanne39 on 2011-09-28
Hi, we can go ahead and unblacklist them however since you can see the network then I do not believe that is the issue but lets do it because it will need to be done before you can restart your computer or you will have to enter them again.

Run this command please:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
then remove blacklist b43, blacklist ssb and add blacklist wl then save and close.

Let's see the results of these commands please:
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep b43
```
```
dmesg | egrep 'b43|firm|wlan0'
```

Sorry an over site on my part the command should have been.
```
sudo rmmod -f wl
```
Thank you

---

### Post by sracusin on 2011-09-28
Wildmann39-
I ran into a glitch. I enclosed blacklist.conf.
I believe I have attached .conf file. If not I have content.
After running code to blacklist b43 laptop crashed - had to powerdown and wireless disabled again (exclamation point).

Ran rmmod codes again. When I get to ssb everything comes alive. Still can't make a connection though but promising.

So, I don't think blacklisting is going to work and you are correct, rebooting loses wl

results of code

sdr@sdr-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:AF:2F:18

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [shabob] ------------------------------------------------------(I am not sure how I am connected to this)
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           no
  HW Address:        00:25:56:4F:33:A0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    shabob:          Ad-Hoc, 00:00:00:00:00:00, Freq 2412 MHz, Rate 0 Mb/s, Strength 0 WPA

  IPv4 Settings:
    Address:         10.42.43.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0



sdr@sdr-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"shabob"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
sdr@sdr-laptop:~$ rfkill list all
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

sdr@sdr-laptop:~$ sudo iwlist scan
[sudo] password for sdr: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

sdr@sdr-laptop:~$ lsmod | grep b43
b43                   157218  0 
ssb                    37336  1 b43
mac80211              204922  1 b43
cfg80211              126485  2 b43,mac80211
led_class               2864  1 b43

 
[  899.332396] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  904.849497] b43-phy0: 
[  904.849509] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  904.849531] b43-phy0: Controller RESET (DMA error) ...
[  905.076428] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  910.593431] b43-phy0: Controller restarted
[  910.593727] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  910.593758] b43-phy0: Controller RESET (DMA error) ...
[  910.808404] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  916.321462] b43-phy0: 
[  916.321475] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  916.321497] b43-phy0: Controller RESET (DMA error) ...
[  916.540458] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  922.065434] b43-phy0: Controller restarted
[  922.065730] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  922.065759] b43-phy0: Controller RESET (DMA error) ...
[  922.284351] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  927.797463] b43-phy0: Controller restarted
[  927.797754] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  927.797784] b43-phy0: Controller RESET (DMA error) ...
[  928.012467] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  933.529438] b43-phy0: 
[  933.529452] b43-phy0 ERROR: Controller restarted
[  933.529499] b43-phy0: Controller RESET (DMA error) ...
[  933.744462] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  939.257466] b43-phy0: Controller restarted
[  939.257697] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  939.257728] b43-phy0: Controller RESET (DMA error) ...
[  939.476399] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  944.994388] b43-phy0 ERROR: 
[  944.994399] b43-phy0: Controller restarted
[  944.994444] b43-phy0: Controller RESET (DMA error) ...
[  945.212457] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  950.733474] b43-phy0: Controller restarted
[  950.734185] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  950.734211] b43-phy0: Controller RESET (DMA error) ...
[  950.948408] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  956.461459] b43-phy0: Controller restarted
[  956.461756] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  956.461786] b43-phy0: Controller RESET (DMA error) ...
[  956.676441] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  962.197447] b43-phy0: Controller restarted
[  962.197681] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  962.197712] b43-phy0: Controller RESET (DMA error) ...
[  962.413431] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  967.925429] b43-phy0: Controller restarted
[  967.925447] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  967.925469] b43-phy0: Controller RESET (DMA error) ...
[  968.140401] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  973.653458] b43-phy0: Controller restarted
[  973.653475] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  973.653497] b43-phy0: Controller RESET (DMA error) ...
[  973.872405] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  979.390146] b43-phy0: Controller restarted
[  979.390244] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  979.390259] b43-phy0: Controller RESET (DMA error) ...
[  979.613361] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  985.145453] b43-phy0: Controller restarted
[  985.145486] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  985.145515] b43-phy0: Controller RESET (DMA error) ...
[  985.374556] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  990.909376] b43-phy0: Controller restarted
[  990.910174] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  990.910203] b43-phy0: Controller RESET (DMA error) ...
[  991.124417] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  996.637510] b43-phy0: Controller restarted
[  996.637745] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  996.637776] b43-phy0: Controller RESET (DMA error) ...
[  996.852469] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1002.365467] b43-phy0: Controller restarted
[ 1002.365780] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1002.365809] b43-phy0: Controller RESET (DMA error) ...
[ 1002.585421] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1008.097442] b43-phy0: 
[ 1008.097456] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1008.097478] b43-phy0: Controller RESET (DMA error) ...
[ 1008.316402] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1013.829475] b43-phy0: Controller restarted
[ 1013.830048] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1013.830078] b43-phy0: Controller RESET (DMA error) ...
[ 1014.044412] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1019.557431] b43-phy0: Controller restarted
[ 1019.557454] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1019.557484] b43-phy0: Controller RESET (DMA error) ...
[ 1019.772433] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1025.289432] b43-phy0: Controller restarted
[ 1025.289733] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1025.289762] b43-phy0: Controller RESET (DMA error) ...
[ 1025.504402] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1031.017510] b43-phy0: Controller restarted
[ 1031.017744] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1031.017774] b43-phy0: Controller RESET (DMA error) ...
[ 1031.240373] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1036.785461] b43-phy0: Controller restarted
[ 1036.785871] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1036.785895] b43-phy0: Controller RESET (DMA error) ...
[ 1037.005307] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1042.561878] b43-phy0: Controller restarted
[ 1042.563050] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1042.563070] b43-phy0: Controller RESET (DMA error) ...
[ 1042.784437] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1048.309384] b43-phy0 ERROR: 
[ 1048.309396] b43-phy0: Controller restarted
[ 1048.309441] b43-phy0: Controller RESET (DMA error) ...
[ 1048.532290] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1054.053465] b43-phy0: Controller restarted
[ 1054.053755] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1054.053786] b43-phy0: Controller RESET (DMA error) ...
[ 1054.268377] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1059.781450] b43-phy0: 
[ 1059.781462] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1059.781485] b43-phy0: Controller RESET (DMA error) ...
[ 1059.996513] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1065.509464] b43-phy0: Controller restarted
[ 1065.509486] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1065.509516] b43-phy0: Controller RESET (DMA error) ...
[ 1065.728620] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1071.246387] b43-phy0: 
[ 1071.246398] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1071.246421] b43-phy0: Controller RESET (DMA error) ...
[ 1071.465329] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1076.981428] b43-phy0: Controller restarted
[ 1076.981449] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1076.981477] b43-phy0: Controller RESET (DMA error) ...
[ 1077.204440] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1082.718381] b43-phy0: Controller restarted
[ 1082.718404] b43-phy0 ERROR: 
[ 1082.718448] b43-phy0: Controller RESET (DMA error) ...
[ 1082.936452] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1088.453460] b43-phy0: Controller restarted
[ 1088.453751] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1088.453782] b43-phy0: Controller RESET (DMA error) ...
[ 1088.676400] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1094.189371] b43-phy0: Controller restarted
[ 1094.189665] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1094.189744] b43-phy0: Controller RESET (DMA error) ...
[ 1094.408404] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1099.925462] b43-phy0: Controller restarted
[ 1099.925479] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1099.925501] b43-phy0: Controller RESET (DMA error) ...
[ 1100.144418] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1105.657474] b43-phy0: Controller restarted
[ 1105.657772] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1105.657802] b43-phy0: Controller RESET (DMA error) ...
[ 1105.876448] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1111.389471] b43-phy0: Controller restarted
[ 1111.389762] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1111.389792] b43-phy0: Controller RESET (DMA error) ...
[ 1111.604411] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1117.121442] b43-phy0: Controller restarted
[ 1117.121743] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1117.121774] b43-phy0: Controller RESET (DMA error) ...
[ 1117.340454] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1122.853463] b43-phy0: Controller restarted
[ 1122.853755] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1122.853785] b43-phy0: Controller RESET (DMA error) ...
[ 1123.068441] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1128.581492] b43-phy0: Controller restarted
[ 1128.582246] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1128.582276] b43-phy0: Controller RESET (DMA error) ...
[ 1128.796434] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1134.309383] b43-phy0: Controller restarted
[ 1134.309405] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1134.309435] b43-phy0: Controller RESET (DMA error) ...
[ 1134.528419] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1140.041479] b43-phy0: 
[ 1140.041491] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1140.041513] b43-phy0: Controller RESET (DMA error) ...
[ 1140.268372] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1145.781469] b43-phy0: Controller restarted
[ 1145.781760] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1145.781791] b43-phy0: Controller RESET (DMA error) ...
[ 1145.996333] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1151.509431] b43-phy0: Controller restarted
[ 1151.509455] b43-phy0 ERROR: 
[ 1151.509499] b43-phy0: Controller RESET (DMA error) ...
[ 1151.728456] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1157.241529] b43-phy0: Controller restarted
[ 1157.241821] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1157.241851] b43-phy0: Controller RESET (DMA error) ...
[ 1157.460455] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1162.977410] b43-phy0 ERROR: 
[ 1162.977422] b43-phy0: Controller restarted
[ 1162.977458] b43-phy0: Controller RESET (DMA error) ...
[ 1163.193403] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1168.705457] b43-phy0: Controller restarted
[ 1168.705475] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1168.705497] b43-phy0: Controller RESET (DMA error) ...
[ 1168.921405] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1174.437438] b43-phy0: 
[ 1174.437449] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1174.437471] b43-phy0: Controller RESET (DMA error) ...
[ 1174.653389] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1180.165434] b43-phy0: 
[ 1180.165446] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1180.165468] b43-phy0: Controller RESET (DMA error) ...
[ 1180.384460] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1185.917435] b43-phy0: Controller restarted
[ 1185.917452] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1185.917475] b43-phy0: Controller RESET (DMA error) ...
[ 1186.136409] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1191.665435] b43-phy0: 
[ 1191.665447] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1191.665469] b43-phy0: Controller RESET (DMA error) ...
[ 1191.896411] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1197.409334] b43-phy0: 
[ 1197.409347] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1197.409369] b43-phy0: Controller RESET (DMA error) ...
[ 1197.636346] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1203.153436] b43-phy0: Controller restarted
[ 1203.164420] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1203.164451] b43-phy0: Controller RESET (DMA error) ...
[ 1203.380407] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1208.893445] b43-phy0: 
[ 1208.893457] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1208.893479] b43-phy0: Controller RESET (DMA error) ...
[ 1209.114970] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1214.629532] b43-phy0: Controller restarted
[ 1214.640524] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1214.640561] b43-phy0: Controller RESET (DMA error) ...
[ 1214.857426] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1220.369470] b43-phy0: 
[ 1220.369482] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1220.369504] b43-phy0: Controller RESET (DMA error) ...
[ 1220.588424] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1226.105471] b43-phy0: 
[ 1226.105483] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1226.105505] b43-phy0: Controller RESET (DMA error) ...
[ 1226.336336] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1231.850879] b43-phy0: Controller restarted
[ 1231.851196] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1231.851230] b43-phy0: Controller RESET (DMA error) ...
[ 1232.068417] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1237.581353] b43-phy0: Controller restarted
[ 1237.581374] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1237.581404] b43-phy0: Controller RESET (DMA error) ...
[ 1237.812433] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1243.325438] b43-phy0: 
[ 1243.325449] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1243.325472] b43-phy0: Controller RESET (DMA error) ...
[ 1243.548385] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1249.061436] b43-phy0: Controller restarted
[ 1249.061453] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1249.061475] b43-phy0: Controller RESET (DMA error) ...
[ 1249.292425] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1254.813448] b43-phy0: 
[ 1254.813460] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1254.813483] b43-phy0: Controller RESET (DMA error) ...
[ 1255.028451] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1260.541433] b43-phy0: Controller restarted
[ 1260.552657] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1260.552685] b43-phy0: Controller RESET (DMA error) ...
[ 1260.776397] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1266.289351] b43-phy0: Controller restarted
[ 1266.289626] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1266.289711] b43-phy0: Controller RESET (DMA error) ...
[ 1266.508452] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1272.025435] b43-phy0: 
[ 1272.025448] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1272.025470] b43-phy0: Controller RESET (DMA error) ...
[ 1272.256366] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1277.769441] b43-phy0: 
[ 1277.769452] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1277.769474] b43-phy0: Controller RESET (DMA error) ...
[ 1277.988350] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1283.501451] b43-phy0: 
[ 1283.501462] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1283.501485] b43-phy0: Controller RESET (DMA error) ...
[ 1283.732414] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1289.249450] b43-phy0: 
[ 1289.249461] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1289.249483] b43-phy0: Controller RESET (DMA error) ...
[ 1289.468398] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1294.981436] b43-phy0: Controller restarted
[ 1294.981456] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1294.981485] b43-phy0: Controller RESET (DMA error) ...
[ 1295.212434] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1300.725469] b43-phy0: 
[ 1300.725482] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1300.725504] b43-phy0: Controller RESET (DMA error) ...
[ 1300.944311] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1306.457444] b43-phy0: Controller restarted
[ 1306.458021] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1306.458051] b43-phy0: Controller RESET (DMA error) ...
[ 1306.688434] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1312.201443] b43-phy0: 
[ 1312.201456] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1312.201478] b43-phy0: Controller RESET (DMA error) ...
[ 1312.420356] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1317.941464] b43-phy0: Controller restarted
[ 1317.941514] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1317.941544] b43-phy0: Controller RESET (DMA error) ...
[ 1318.160430] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1323.673466] b43-phy0: Controller restarted
[ 1323.673766] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1323.673797] b43-phy0: Controller RESET (DMA error) ...
[ 1323.888452] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1329.401463] b43-phy0: Controller restarted
[ 1329.401696] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1329.401727] b43-phy0: Controller RESET (DMA error) ...
[ 1329.624403] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1335.137442] b43-phy0: Controller restarted
[ 1335.137753] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1335.137784] b43-phy0: Controller RESET (DMA error) ...
[ 1335.360395] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1340.874410] b43-phy0: 
[ 1340.874421] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1340.874443] b43-phy0: Controller RESET (DMA error) ...
[ 1341.092406] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1346.609442] b43-phy0: Controller restarted
[ 1346.609464] b43-phy0 ERROR: 
[ 1346.609509] b43-phy0: Controller RESET (DMA error) ...
[ 1346.825386] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1352.345476] b43-phy0: 
[ 1352.345488] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1352.345510] b43-phy0: Controller RESET (DMA error) ...
[ 1352.572422] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1358.105299] b43-phy0: Controller restarted
[ 1358.106099] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1358.106155] b43-phy0: Controller RESET (DMA error) ...
[ 1358.324400] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1363.849451] b43-phy0: 
[ 1363.849462] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1363.849484] b43-phy0: Controller RESET (DMA error) ...
[ 1364.076408] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1369.589442] b43-phy0: 
[ 1369.589453] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1369.589475] b43-phy0: Controller RESET (DMA error) ...
[ 1369.808398] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1375.345494] b43-phy0: Controller restarted
[ 1375.345786] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1375.345817] b43-phy0: Controller RESET (DMA error) ...
[ 1375.560436] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1381.082327] b43-phy0: Controller restarted
[ 1381.082487] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1381.082505] b43-phy0: Controller RESET (DMA error) ...
[ 1381.300411] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1386.825461] b43-phy0: 
[ 1386.825473] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1386.825495] b43-phy0: Controller RESET (DMA error) ...
[ 1387.044391] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1392.557466] b43-phy0: Controller restarted
[ 1392.557776] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1392.557808] b43-phy0: Controller RESET (DMA error) ...
[ 1392.777389] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1398.301379] b43-phy0: Controller restarted
[ 1398.301400] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1398.301430] b43-phy0: Controller RESET (DMA error) ...
[ 1398.520433] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1404.037490] b43-phy0: Controller restarted
[ 1404.037786] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1404.037815] b43-phy0: Controller RESET (DMA error) ...
[ 1404.252399] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1409.774429] b43-phy0 ERROR: 
[ 1409.774440] b43-phy0: Controller restarted
[ 1409.774476] b43-phy0: Controller RESET (DMA error) ...
[ 1410.004442] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1415.517367] b43-phy0: 
[ 1415.517379] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1415.517401] b43-phy0: Controller RESET (DMA error) ...
[ 1415.732399] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1421.246257] b43-phy0: Controller restarted
[ 1421.246483] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1421.246501] b43-phy0: Controller RESET (DMA error) ...
[ 1421.465301] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1426.997414] b43-phy0: 
[ 1426.997426] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1426.997448] b43-phy0: Controller RESET (DMA error) ...
[ 1427.212409] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1432.729457] b43-phy0: 
[ 1432.729469] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1432.729491] b43-phy0: Controller RESET (DMA error) ...
[ 1432.953609] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1438.469422] b43-phy0: Controller restarted
[ 1438.469725] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1438.469755] b43-phy0: Controller RESET (DMA error) ...
[ 1438.692455] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1444.205445] b43-phy0: 
[ 1444.205458] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1444.205480] b43-phy0: Controller RESET (DMA error) ...
[ 1444.424438] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1449.938452] b43-phy0 ERROR: 
[ 1449.938463] b43-phy0: Controller restarted
[ 1449.938509] b43-phy0: Controller RESET (DMA error) ...
[ 1450.168390] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1455.681483] b43-phy0: Controller restarted
[ 1455.681509] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1455.681538] b43-phy0: Controller RESET (DMA error) ...
[ 1455.681636] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1455.681661] b43-phy0: Controller RESET (DMA error) ...
[ 1455.900359] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1461.417443] b43-phy0: Controller restarted
[ 1461.417777] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1461.417808] b43-phy0: Controller RESET (DMA error) ...
[ 1461.632437] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1467.145464] b43-phy0: 
[ 1467.145477] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1467.145499] b43-phy0: Controller RESET (DMA error) ...
[ 1467.372413] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1472.889427] b43-phy0 ERROR: 
[ 1472.889438] b43-phy0: Controller restarted
[ 1472.889484] b43-phy0: Controller RESET (DMA error) ...
[ 1473.108389] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1478.625460] b43-phy0: 
[ 1478.625473] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1478.625495] b43-phy0: Controller RESET (DMA error) ...
[ 1478.844416] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1484.357393] b43-phy0: Controller restarted
[ 1484.357416] b43-phy0 ERROR: 
[ 1484.357461] b43-phy0: Controller RESET (DMA error) ...
[ 1484.576389] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1490.101514] b43-phy0: 
[ 1490.101527] b43-phy0 ERROR: Controller restarted
[ 1490.101563] b43-phy0: Controller RESET (DMA error) ...
[ 1490.321341] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1495.841461] b43-phy0: Controller restarted
[ 1495.841762] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1495.841793] b43-phy0: Controller RESET (DMA error) ...
[ 1496.060466] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1501.593438] b43-phy0: Controller restarted
[ 1501.593817] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1501.593849] b43-phy0: Controller RESET (DMA error) ...
[ 1501.813431] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1507.365440] b43-phy0: Controller restarted
[ 1507.366200] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1507.366230] b43-phy0: Controller RESET (DMA error) ...
[ 1507.580435] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1513.097463] b43-phy0: Controller restarted
[ 1513.098009] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1513.098039] b43-phy0: Controller RESET (DMA error) ...
[ 1513.316423] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1518.829453] b43-phy0: 
[ 1518.829464] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1518.829486] b43-phy0: Controller RESET (DMA error) ...
[ 1519.044386] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1524.561761] b43-phy0: Controller restarted
[ 1524.562840] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1524.562873] b43-phy0: Controller RESET (DMA error) ...
[ 1524.780424] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1530.294611] b43-phy0: 
[ 1530.294624] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1530.294646] b43-phy0: Controller RESET (DMA error) ...
[ 1530.512360] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1536.025381] b43-phy0: 
[ 1536.025392] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1536.025414] b43-phy0: Controller RESET (DMA error) ...
[ 1536.244413] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1541.765436] b43-phy0: 
[ 1541.765447] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1541.765469] b43-phy0: Controller RESET (DMA error) ...
[ 1541.984411] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1547.501437] b43-phy0: 
[ 1547.501450] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1547.501472] b43-phy0: Controller RESET (DMA error) ...
[ 1547.720404] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1553.249399] b43-phy0: 
[ 1553.249410] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1553.249433] b43-phy0: Controller RESET (DMA error) ...
[ 1553.468405] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1558.981452] b43-phy0: Controller restarted
[ 1558.981469] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1558.981491] b43-phy0: Controller RESET (DMA error) ...
[ 1559.196432] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1564.709435] b43-phy0: 
[ 1564.709449] b43-phy0 ERROR: Controller restarted
[ 1564.709497] b43-phy0: Controller RESET (DMA error) ...
[ 1564.932366] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1570.461504] b43-phy0: Controller restarted
[ 1570.461796] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1570.461826] b43-phy0: Controller RESET (DMA error) ...
[ 1570.676399] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1576.189439] b43-phy0: 
[ 1576.189451] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1576.189474] b43-phy0: Controller RESET (DMA error) ...
[ 1576.408450] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1581.925464] b43-phy0: 
[ 1581.925478] b43-phy0 ERROR: Controller restarted
[ 1581.925516] b43-phy0: Controller RESET (DMA error) ...
[ 1582.144397] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1587.662393] b43-phy0: Controller restarted
[ 1587.662414] b43-phy0 ERROR: 
[ 1587.662460] b43-phy0: Controller RESET (DMA error) ...
[ 1587.880456] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1593.421443] b43-phy0: 
[ 1593.421456] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1593.421478] b43-phy0: Controller RESET (DMA error) ...
[ 1593.640402] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1599.165452] b43-phy0: Controller restarted
[ 1599.165894] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1599.165924] b43-phy0: Controller RESET (DMA error) ...
[ 1599.380396] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1604.893451] b43-phy0: 
[ 1604.893463] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1604.893486] b43-phy0: Controller RESET (DMA error) ...
[ 1605.108455] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1610.621445] b43-phy0: 
[ 1610.621457] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1610.621479] b43-phy0: Controller RESET (DMA error) ...
[ 1610.837396] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1616.349463] b43-phy0: 
[ 1616.349476] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1616.349499] b43-phy0: Controller RESET (DMA error) ...
[ 1616.568411] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1622.097377] b43-phy0: Controller restarted
[ 1622.097400] b43-phy0 ERROR: 
[ 1622.097445] b43-phy0: Controller RESET (DMA error) ...
[ 1622.327048] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1627.841556] b43-phy0: Controller restarted
[ 1627.842195] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 1627.842228] b43-phy0: Controller RESET (DMA error) ...
[ 1628.068433] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
sdr@sdr-laptop:~$

---

### Post by sracusin on 2011-09-28
> **wildmanne39 said:**
> Hi, we can go ahead and unblacklist them however since you can see the network then I do not believe that is the issue but lets do it because it will need to be done before you can restart your computer or you will have to enter them again.

Run this command please:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```then blacklist b43, blacklist ssb and add blacklist wl then save and close.

Let's see the results of these commands please:
```
nm-tool
``````
iwconfig
``````
rfkill list all
``````
sudo iwlist scan
``````
lsmod | grep b43
``````
dmesg | egrep 'b43|firm|wlan0'
```Sorry an over site on my part the command should have been.
```
sudo rmmod -f wl
```Thank you

wildmann39-
I believe I should UNblacklist the protocols ssb/b43/wl?
Is the blacklist.conf code the way to UNblacklist?

I am beginning to be confused.
Thanks ~sdr

---

### Post by wildmanne39 on 2011-09-28
Hi, I have been research that error, it is nothing we did but it is a bug here is the link to it.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433)
I am not sure of our options since you can to plug it into a wired connection, so I am go to continue to research.

You do not have a friend that you can plug into his internet if needed?

Also when you tried to unblacklist those drivers what exactly happened? You should have had a window open for you to type your password and after you entered it then you should have seen the blacklist file.
Thank you

---

### Post by sracusin on 2011-09-28
wildmann39-
I have a feeling this problem is insurmountable. Have you given up?

Thanks ~sracusin

---

### Post by wildmanne39 on 2011-09-28
Hi, no not yet, I am going to talk with chili555 about it.
Thank you

---

### Post by sracusin on 2011-09-28
> **wildmanne39 said:**
> Hi, I have been research that error, it is nothing we did but it is a bug here is the link to it.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433)
I am not sure of our options since you can to plug it into a wired connection, so I am go to continue to research.

You do not have a friend that you can plug into his internet if needed?

Also when you tried to unblacklist those drivers what exactly happened? You should have had a window open for you to type your password and after you entered it then you should have seen the blacklist file.
Thank you

wildmann39-
I do not know if I actually UNblacklisted the drivers. I ran the blacklist.conf and my question was, is this unblacklisting? Otherwise I need the code. I was unsuccessful in finding the code on my own but I know if I restart ubuntu, I will have to enable the drivers again.
I don't have a wired connection most of the time unfortunately and will be in Australia for a month. This is why I am grateful for the immediate assistance.
Thank you ~sracusin

---

### Post by sracusin on 2011-09-28
wildmann39-
This is the content of the blacklist.conf file. I read your message again and this code does not seem to UNblacklist. It appears to blacklist instead or it is just informational. I thought I had attached this file a few messages ago. I apologize.~sracusin


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
blacklist b43
blacklist ssb

---

### Post by sracusin on 2011-09-28
gksu gedit /etc/modprobe.d/blacklist.conf
Is this supposed to UNBLACKLIST? You suggested running this before rebooting.

---

### Post by wildmanne39 on 2011-09-28
Hi, after you open the file with the command 
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
then remove blacklist b43, and blacklist ssb and add blacklist wl then save and close.

I also believe you can do it this way.
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

---

### Post by chili555 on 2011-09-28
> # ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
[COLOR="Red"]blacklist b43
blacklist ssb[/COLOR]Please remove the highlighted parts. Then do:```
sudo apt-get remove --purge bcmwl-kernel-source
```That's two hyphens, not one, before *purge*. It's a bit hard to read on the forum posts.

Reboot and let us see:```
dmesg | grep b43 | tail -n10
```We are indeed close!

---

### Post by wildmanne39 on 2011-09-28
Hi, please try this:
```
gksudo gedit /etc/modprobe.d/b43.conf
```


add this one line
```
options b43 pio=1 qos=0 nohwcrypt=1
```
Then save and exit, then reboot.
Thank you

---

### Post by chili555 on 2011-09-28
> gksudo gedit /etc/modprobe.d/50-b43.confI wonder if this shouldn't be:```
gksudo gedit /etc/modprobe.d/**b43.conf**
```

---

### Post by wildmanne39 on 2011-09-28
Hi chili555, I am not sure the code was from Suse so it might be a little different, but I can change it.
Thank you

---

### Post by sracusin on 2011-09-28
> **chili555 said:**
> Please remove the highlighted parts. Then do:```
sudo apt-get remove --purge bcmwl-kernel-source
```That's two hyphens, not one, before *purge*. It's a bit hard to read on the forum posts.

Reboot and let us see:```
dmesg | grep b43 | tail -n10
```We are indeed close!

chili555 and wildmann39-
results of dmesg code:
sdr@sdr-laptop:~$ dmesg | grep b43 | tail -n10
[   90.289415] b43-phy0: Controller RESET (DMA error) ...
[   90.512426] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   96.033469] b43-phy0: 
[   96.033481] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   96.033503] b43-phy0: Controller RESET (DMA error) ...
[   96.252357] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  101.777457] b43-phy0: 
[  101.777468] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  101.777490] b43-phy0: Controller RESET (DMA error) ...
[  101.992426] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
sdr@sdr-laptop:~$ ^C
sdr@sdr-laptop:~$ 

still no luck. Prior to rebooting I could see my network listed, wireless icon alive but no connection. Followed wildmann39's instructions and yours to edit .conf files and ran kernel code 
sudo apt-get remove --purge bcmwl-kernel-sourcerebooted and now wireless icon is no longer alive
Thanks ~sracusin

---

### Post by chili555 on 2011-09-29
> rebooted and now wireless icon is no longer aliveLet's take a systematic approach to diagnosis. When you reboot, is the driver b43 loaded?```
lsmod | grep b43
```If not, load it:```
sudo modprobe b43 pio=1 qos=0 nohwcrypt=1
```Any errors or warnings? What does dmesg say?```
dmesg | grep b43
```

---

### Post by sracusin on 2011-09-29
chili555- good idea to do systematic approach. >Last thing I did was remove the code from /etc/modprobe.d/b43.conf but messages from wildmann39 crossed and there was some discussion about the exact name of the file.
[FONT=monospace]Thanks ~sracusin

[/FONT]sdr@sdr-laptop:~$ lsmod | grep b43 (noresult)
sdr@sdr-laptop:~$ lsmod | grep b43 (just in case I made a mistake)

sdr@sdr-laptop:~$ sudo modprobe b43 pio=1 qos=0 nohwcrypt=1
[sudo] password for sdr: 
FATAL: Error inserting b43 (/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

sdr@sdr-laptop:~$ dmesg | grep b43
[    1.355451] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.355479] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   14.038050] b43: Unknown parameter `pio'
[  276.208765] b43: Unknown parameter `pio'

sdr@sdr-laptop:~$

---

### Post by chili555 on 2011-09-29
> Error inserting b43 (/lib/modules/[COLOR="Red"]2.6.32-21[/COLOR]-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)OK, now I think I have it! pio didn't exist as a b43 parameter till later kernels. Please try:```
sudo modprobe b43 qos=0 nohwcrypt=1
```Thanks.

---

### Post by linuxman94 on 2011-09-29
This may have been mentioned, but have you installed firmware-b43-installer?

```
sudo apt-get install firmware-b43-installer
```

---

### Post by sracusin on 2011-09-29
> **chili555 said:**
> OK, now I think I have it! pio didn't exist as a b43 parameter till later kernels. Please try:```
sudo modprobe b43 qos=0 nohwcrypt=1
```Thanks.

Nope! Error inserting b43 (/lib/modules/[COLOR=Red]2.6.32-21[/COLOR]-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg is the same unknown parameter in pio'

Good question from another helpful person about firmware. I have not manually installed firmware and do not have access to cd drive.

I do know that when I run the codes from wildmann39 wireless comes alive but will not connect to the networks.

and I have unblacklisted ssb & b43 as directed. Is there hope? Or is the bug insurmountable?

Thanks ~sracusin

---

### Post by sracusin on 2011-09-29
> **chili555 said:**
> Absolutely! You can do so easily by downloading the b43 firmware installer and simply rmmod wl and modprobe b43. If it works, then remove bcmwl-kernel-source and the b43 blacklist. If not, nothing harmed.

I think it will.

chili555 - I think we need to go back to this tip.  Do you think should I get the bfcutter firmware? 
I think I can find download it from the driver site.

then I would remove the bcmwl-kernel-source from the blacklist??

It could be as simple as this. I did not run the firmware as I was following wildmann39's exact instructions and deliberately ignored installing this when I had the cd drive available.

Thanks ~sracusin

---

### Post by sracusin on 2011-09-29
> **linuxman94 said:**
> This may have been mentioned, but have you installed firmware-b43-installer?

```
sudo apt-get install firmware-b43-installer
```

Have not done that and when I looked in the path /lib/firmware 
Since I I am getting the error:
Error inserting b43 (/lib/modules/[COLOR=Red]2.6.32-21[/COLOR]-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and there is a /lib/firmware/b43 directory with a zip file in it. 

Would it hurt to run this? Does this apt-get command run from withing the file system (simple question for you probably)?

---

### Post by wildmanne39 on 2011-09-29
Hi, I believe it is worth trying:
```
sudo modprobe b43 qos=0
```
Thank you

---

### Post by wildmanne39 on 2011-09-29
Hi, in the b43zip we installed the firmware with it since you said you could not get the packages off the cd to install, you were getting errors.
Thank you

---

### Post by linuxman94 on 2011-09-29
> **sracusin said:**
> Have not done that and when I looked in the path /lib/firmware I noticed that I am getting this 
Error inserting b43 (/lib/modules/[COLOR=Red]2.6.32-21[/COLOR]-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and there is a /lib/firmware/b43 directory with a zip file in it. 

Would it hurt to run this? Does this apt-get command run from withing the file system (simple question for you probably)?

No, it won't hurt it.  It will only affect the installation that you currently have running.

It might fix your firmware issues because the module may be corrupted or missing.

---

### Post by wildmanne39 on 2011-09-29
Hi, here is one fix at this link please refer to post 799.
[http://ubuntuforums.org/showthread.php?t=1266620&page=80](http://ubuntuforums.org/showthread.php?t=1266620&page=80)

The problem is I do not know how to have you do it with out and internet connection, Maybe chli555 has away for you to download it to your usb drive then install it.
Thank you

---

### Post by sracusin on 2011-09-29
wildmann39-
Yes, I wasn't sure the package I downloaded included firmware. Thank you.
Now any modprobe b43 results in
Error inserting b43 (/lib/modules/[COLOR=Red]2.6.32-21[/COLOR]-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I can no longer make the wireless come alive with those original rmmod and modprobe commands. The modprobe b43 gives fatal error. Somewhere along the line it went south.

Also in my research on the BCM chart, it looks as though my STA card does support 2.6.33+
Is it possible to update the kernel? Perhaps my suggestion is going in the wrong direction. ~sracusin

---

### Post by linuxman94 on 2011-09-29
Ahh yes a kernel update would be in order.  You're going to have to download some packages manually from another computer because 2.6.33 isn't in the lucid repos. 

Depending on the architecture (64bit or 32bit), the packages you have to download will change.  Go [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/") and download the appropriate packages.  They should be:

```
linux-headers-2.6.33-02063305-generic_2.6.33-02063305_*.deb 
linux-headers-2.6.33-02063305_2.6.33-02063305_all.deb
linux-image-2.6.33-02063305-generic_2.6.33-02063305_*.deb
(the asterisk is the architecture.  amd64 for 64bit, i386 for 32bit)
```

Once you've got those downloaded, put them on a flash drive and copy them to the home folder of your lucid installation.  Make sure there are no other .deb files in your home. If there are, delete them.

Now for the installation.  Fire up a terminal (Applications -> Accessories -> Terminal).  Next, copy&paste this line into it.

```
sudo dpkg -i *.deb
```

Once you enter your password, you'll have to wait for a little while as the packages are installed.  Once it has returned you to the prompt (hopefully without an error), reboot the computer and make sure to choose the option that has 2.6.33 in the name.  After it starts up, see if your wireless works!

If you get an error on the install, please post it here and we'll take a look.

Good luck!

---

### Post by wildmanne39 on 2011-09-29
Hi, yes that is what I wanted to do from the start but without being able to get on the internet to install it I do not know how to proceed, the link in my last post showed the link to do download it and the directions I believe but I do not know how to put it on an usb drive then install it to ubuntu, I am hoping chilli555 will know how or find a better solution.

Also if you had a wired connection I believe it would be in an update that you could just install using synaptic, that is why I asked in the beginning if you had ever been able to update ubuntu.

I have looked at many web pages on your issue and there are mixed results clear up to ubuntu 11.04, but some many people have got this card to work but some do not have good connections some do.

So let's wait until chili555 is on tomorrow and see what he says and if in doubt always do what he says.

With this card it is a lot of experimenting to try to get it to work, this is a strange beast indeed.

Also I am going to be off most of he day tomorrow, I have to see a couple of different Doctor's.
Thank you

---

### Post by wildmanne39 on 2011-09-29
Hi linuxman94, the problem is he does not have an internet connection on ubuntu, do you know of away to put it on a usb drive, then install to ubuntu?
Thank you

---

### Post by bkratz on 2011-09-30
> **wildmanne39 said:**
> Hi linuxman94, the problem is he does not have an internet connection on ubuntu, do you know of away to put it on a usb drive, then install to ubuntu?
Thank you


@wildmanne-- those files are available for transfer to a thumb drive at 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/)

---

### Post by sracusin on 2011-09-30
> **wildmanne39 said:**
> Hi, yes that is what I wanted to do from the start but without being able to get on the internet to install it I do not know how to proceed, the link in my last post showed the link to do download it and the directions I believe but I do not know how to put it on an usb drive then install it to ubuntu, I am hoping chilli555 will know how or find a better solution.

Also if you had a wired connection I believe it would be in an update that you could just install using synaptic, that is why I asked in the beginning if you had ever been able to update ubuntu.

With this card it is a lot of experimenting to try to get it to work, this is a strange beast indeed.

Thank you

@wildmann39 and @linuxman94
I have a WIRED connection today so I want to use synaptic to upgrade kernel and WIRELESS drivers. This is gonna be a whole lot easier.
I have 48 updates. Given what we have tried so far - which specific packages do I absolutely need to make this wireless thing happen?
Thank you ~sracusin

---

### Post by westie457 on 2011-09-30
Hello sracusin seeing that you now have been able to update to a newer kernel may I refer you to posts #22 and #23 of this thread. The drivers you need are named there. If you prefer to wait for confirmation from either wildemann39 or chili555 by all means do so. They will either agree or say something completely different.

Good luck.

---

### Post by sracusin on 2011-09-30
> **westie457 said:**
> Hello sracusin seeing that you now have been able to update to a newer kernel may I refer you to posts #22 and #23 of this thread. The drivers you need are named there. If you prefer to wait for confirmation from either wildemann39 or chili555 by all means do so. They will either agree or say something completely different.

Good luck.

SUCCESS!
@westie457 is correct. Thank you all. wildmann39 who hung in there with me was also correct about the incompatibility between the STA card and the kernel. linuxman94 gave me the files (I re-read your statement that this kernel 2.6.33 was not in the repository-and followed your directions and the unpack code-took 1 minute)
This is the answer for all Dell minis with the bcm4312 sta card and 10.04.

I am humbled by your knowledge and stamina to stick with the problem for a week.
~sracusin

---

### Post by wildmanne39 on 2011-09-30
Hi, you are very welcome! I am glad it is working, it has been a learning experience, would you please show your support for me becoming an ubuntu member by clicking on the red link in my signature and posting to the thread? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by wildmanne39 on 2011-10-01
Hi bkratz, thank you for the link to upgrade the kernel using a usb drive.

---

