---
title: "ASUS PCE-N15 Installation"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by ZombeApocalips on 2012-05-27
Good evening, folks.  I have looked around quite a bit and tried to use the readme.txt that came with the drivers I downloaded but the commands don't work and I'm just plain lost here.

I've got a box running Ubuntu 10.04.  I know it's not the newest version, but it's the newest version that does what I need it do do.  I've been all over here the last few days trying to get all of the bugs worked out because I'm tired of Windows running slow and constantly failing me.  By bugs, I suppose one could infer that the real problem lies with the fact that I don't know what the crap I'm doing.

So... I've downloaded the drivers for Linux from the ASUS page, specifically the package named Linux_PCE_N15_1008.zip.  I have no idea what to do after extracting the archive.  I have read another thread about installing this card in Ubuntu 11.04 but the commands return error messages along the lines of missing syntax or unknown commands.  I read the manual of which I downloaded a .pdf but the only instructions I have seen are for Windows.  Please help! I need a line-by-line on this one.  Thanks in advance.

---

### Post by ZombeApocalips on 2012-05-27
Oh, some additional information:

lspci output:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
20:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8178 (rev 01)
3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express (rev 02)

iwconfig output:

lo        no wireless extensions.

eth0      no wireless extensions.

lsmod output:

Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_intel          22069  0 
snd_hda_codec          74297  2 snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  11  snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
parport_pc             25962  1 
ati_agp                 5094  0 
soundcore               6620  1 snd
fglrx                2092908  35 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
psmouse                63677  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
k8temp                  3152  0 
agpgart                31724  2 ati_agp,fglrx
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
floppy                 53016  0 
pata_atiixp             3148  0 
tg3                   109324  0 
ahci                   32680  2 
[FONT=monospace]sudo lshw -C network output:

[/FONT] *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:20:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:1100(size=256) memory:d0a00000-d0a03fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:29:db:5a:f1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.102 duplex=full firmware=5755-v3.29 ip=192.168.1.8  latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:19 memory:d0500000-d050ffff

---

### Post by DavesDogSirius on 2012-05-27
Hey, I'm in a similar situation. Just put together a custom built PC with the ASUS PCE-N15, though i've installed Ubuntu 12.04. I'm also new to Linux and working my way through this.

I managed to get the hardware recognized by following the steps in the readme file. I did get error outputs when i ran the Make and Make Install commands, but after rebooting the system the hardware showed up as recognized. You said you tried these steps right?

In any case, I'm still having difficulty connecting to my wireless network. It's detecting the SSID but won't let me connect for some reason.

---

### Post by ZombeApocalips on 2012-05-28
Yes, I downloaded the driver (latest version for Linux) and did everything in the readme.  No dice.  The make and make install returned errors and after a reboot, the OS doesn't seem to recognize the wireless card.

---

### Post by chili555 on 2012-05-28
In order to compile, you'll need linux-headers-generic and build-essential. Can you check in Synaptic or Software Center to see if they are installed? What was in the file you unzipped? What is the name of the package? After you have installed the prerequisites, please try again:```
cd Desktop/RTL8whatever  <--or wherever you extracted the files
sudo su
make clean
make 
make install
exit
```Any improvement?

I found it. How did you know which or what to compile? May we see:```
lspci -nn | grep 0280
```

---

### Post by ZombeApocalips on 2012-06-05
Solved.  Kind of.  So, here's the deal:

I assumed that the most recent version of the driver was the way to go.  The readme.txt instructions for this driver were a no-go.  I downloaded the FIRST version of the driver, followed the instructions and good to go.  Kind of.  The only problem now is that it appears to be not running so fast.  On my windows box the same card was performing at 300mbps.  It appears significantly slower than that now.  Going to keep trying some things.

---

### Post by yabbadabado on 2012-06-12
I just installed my new ASUS PCE-N15 Wireless-N PCI-E card and I have Ubuntu 12.04 installed. When I booted up the card was working and it picked up my wireless network. I ran the update installer to install some updates and the connection must have dropped as it failed to install the updates. They installed OK with the ethernet connection. I then tried to install the driver from here ([http://uk.asus.com/Networks/Wireless_Adapters/PCEN15/#download](http://uk.asus.com/Networks/Wireless_Adapters/PCEN15/#download)) and it failed with the following error:
```

make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
gcc: error: /lib/modules/3.2.0-24-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/tmp/Linux_PCE_N15_1006/HAL/rtl8192/Makefile". Fix it to use ccflags-y. Stop.
make[1]: *** [_module_/tmp/Linux_PCE_N15_1006/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [all] Error 2

```I verified that the file "/lib/modules/3.2.0-24-generic/build/include/linux/autoconf.h" is not there.  

Anybody know how to get this working?

Thanks,
-Fred

---

### Post by yabbadabado on 2012-06-12
Here is the wireless card info:
```

  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: c8:60:00:d3:f5:e1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-24-generic firmware=N/A ip=<my ip> latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:e000(size=256) memory:fe400000-fe403fff

```It looks like a generic driver is already installed with Ubuntu 12.04 but it does not work well with the wireless card and the new one from the ASUS site will not install for the file not found reason.. anybody know how to update to the correct driver?

Thanks,
-Fred

---

### Post by chili555 on 2012-06-12
> gcc: error:Are you sure you have the package *build-essential* installed? Did you run make after sudo su?

However, rtl8192ce, de and se are included by default in Ubuntu 12.04. Why are you building a different, not-optimized-for-Ubuntu one? Please post:```
lspci -nn | grep 0280
dmesg | grep 8192
```> it does not work well with the wireless cardIn what way?

Thanks.

---

### Post by yabbadabado on 2012-06-12
Here is the output for lspci:
```


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)


```and for dmesg:
```


[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023fa00000 s83072 r8192 d23424 u524288
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
[   16.767238] rtl8192ce 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.767246] rtl8192ce 0000:03:00.0: setting latency timer to 64
[   17.750822] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   18.662493] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   39.147605] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   69.139803] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  109.124963] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  159.108796] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  206.309718] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2603.365556] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2698.332744] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2738.317463] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2788.303816] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2848.284501] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2908.265854] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2968.246426] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3028.227873] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3088.207899] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3148.189674] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3208.170341] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3268.150994] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3328.132333] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3388.112615] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3448.094176] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3508.073321] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3568.055416] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3628.036028] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3688.017650] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3747.998668] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3807.979025] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3867.960584] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3927.941522] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3987.922342] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4047.898657] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4107.884556] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4167.864653] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4227.845898] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4287.827049] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4347.807980] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4407.788557] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4467.765381] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4527.750380] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4587.731587] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4647.712542] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4707.693431] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4767.673794] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4827.652299] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4887.631473] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4947.617248] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5007.598452] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5067.578488] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5127.560184] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5187.540690] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5247.518474] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5307.502540] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5367.482472] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5427.458910] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5487.445829] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5547.421513] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5607.407378] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5667.386715] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5727.367698] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5787.350217] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5847.329388] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5907.311996] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5967.292557] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6027.272137] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6087.254320] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6147.235079] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6207.216043] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6267.197768] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6327.177928] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6387.158424] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6447.139674] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6507.116776] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6567.101560] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6627.079028] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6687.063918] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6747.043834] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6807.025476] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6867.006626] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6926.987721] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6986.968794] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7046.945323] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7106.929043] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7166.911269] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7226.892404] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7286.871432] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7346.853577] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7381.033790] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin


```I couldn't use the Update Manager over the wireless connection and the Desktop is a couple of feet from the router. I have build essential installed and I ran make as root. 

After some searching online I think I found the issue in a customer review.

> 
I did a little bit more research into the control module. Apparently N15  uses Realtek  RL8192CE chip. It is not actually a adapter. The realtek  chip only provides minimum level of networking trafficing. All the major  work is on software layer. To make it simple, this card is VERY  dependent on your PC's CPU computing power. This explains why its  performance varies so much from driver to driver. Sadly, ASUS only has  horrible driver for this adapter. The newest 1.0.0.8 will actually  reduce your connecting rates. Bad signal, bad control chip and above  all: horrible driver. 


Thanks,
-Fred

---

### Post by chili555 on 2012-06-12
> After some searching online I think I found the issue in a customer review.So do you want to replace the device or would you like to try to compile? I downloaded it and it makes without drama for me. I don't have the device, so I can't vouch that it actually performs as expected.

If it were me, I'd replace.

---

### Post by Troy^ on 2013-04-06
I too have had this card for a very long time and to no avail have I ever got this card to work properly under ubuntu 12.04 or 12.10. I had it recognized and the ability to connect to the wireless network but it disconnects and fails miserably. Also very slow speeds compared to in Windows.

---

### Post by chili555 on 2013-04-06
> **Troy^ said:**
> I too have had this card for a very long time and to no avail have I ever got this card to work properly under ubuntu 12.04 or 12.10. I had it recognized and the ability to connect to the wireless network but it disconnects and fails miserably. Also very slow speeds compared to in Windows.Is this a comment that the card is not very good in Ubuntu or a request for assistance? If the latter, please post:```
dmesg | grep rtl
lsmod | grep rtl
```

---

### Post by erikmolstad on 2013-05-26
Hi

I have a PCE-N15 card and have followed the instructions below to install drivers, but I simply don't get it to wok properly, I loose connection after 5sec or so.

I tried to remove the card and put back my old SWEEX LW052, but it is simply not recognized at all anymore. 

So, my request is help to remove the PCE-N15 drivers to allow my old card to work (if I remember correctly it was working automatically when I installed Ubuntu) 

This is my fist post in this forum so I hope I post in the right place...
Thankful for support

[   29.539012] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   29.539020] rtl8192ce 0000:02:00.0: setting latency timer to 64
[   29.716450] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   30.207478] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   30.208172] rtlwifi: wireless switch is on

rtl8192ce              52800  0 
rtl8192c_common        46721  1 rtl8192ce
rtlwifi                64122  1 rtl8192ce
mac80211              474641  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              188155  2 rtlwifi,mac80211
compat                 19507  4 rtl8192ce,rtlwifi,mac80211,cfg80211

---

### Post by chili555 on 2013-05-26
Let's start by blacklisting the Asus driver:```
gksuso gedit /etc/modules
```If rtl8192ce is in there, remove it, proofread, save and close gedit. Next:```
gksuso gedit /etc/modprobe.d/blacklist.conf
```Add a line at the end:```
blacklist rtl8192ce
```Now, with the SWEEX inserted, reboot and show us:```
lspci -nn | grep 0280
iwconfig
```Thanks.

---

### Post by erikmolstad on 2013-05-26
Thanks
I guess you ment gksudo, that seemed to work anyway.
I removed the Asus card and put in my sweex

Now, however I have no network, so I cannot really paste.
 
lspci -nn | grep 0280 iwconfig
Returns no data

iwconfig
lo & eth0 no wireless extensions

Is the conclusion that the card is broken?

---

### Post by chili555 on 2013-05-26
> lspci -nn | grep 0280 iwconfig
Returns no dataThat's two separate commands:```
lspci -nn | grep 0280
```And then, separately:```
iwconfig
```If the lspci returns no data, then we assume the SWEEX is inoperative; it is a PCI device, correct?

If it is inoperative, let's try to troubleshoot the Asus. I emphasize 'try.'

---

### Post by erikmolstad on 2013-05-26
Yes, it is a pci device.
Well, then the sweex is dead :-(

I stop blacklisting the Asus device and put it back.

The issue is that it starts fine but stops working after a few sec. It still show a network connection icon, but it is false. 
However, by disconnecting and connecting again I can get network again, for a few more sec at least....

Any suggestions?

---

### Post by chili555 on 2013-05-26
Let's see if there are any clues here:```
dmesg | grep -e wlan -e rtl -e cfg8
```

---

### Post by erikmolstad on 2013-05-27
[   25.954680] cfg80211: Calling CRDA to update world regulatory domain
[   26.182104] cfg80211: World regulatory domain updated:
[   26.182108] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.182111] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.182114] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.182116] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.182118] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.182121] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.219161] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.219170] rtl8192ce 0000:02:00.0: setting latency timer to 64
[   26.229305] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   26.229308] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229310] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   26.229313] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229315] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   26.229318] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229320] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   26.229322] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229324] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   26.229327] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229329] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   26.229332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229334] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   26.229336] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229338] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   26.229341] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229343] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   26.229345] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229348] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   26.229350] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229352] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   26.229355] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229357] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   26.229360] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229362] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   26.229364] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   26.229367] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   26.229558] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   26.760617] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   26.766852] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   26.767451] rtlwifi: wireless switch is on
[   26.799366] udevd[409]: renamed network interface wlan0 to wlan1
[   27.339659] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   27.347114] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   30.368437] wlan1: authenticate with 10:bf:48:80:ab:e8


I could also mention that I use my laptop on the same WLAN network at the same time, so it is up and functional.

---

### Post by chili555 on 2013-05-27
Hmmm. We don't see it drop and reconnect. Can you wait until it does a few times and try again? We'll look for timestamps later than 30.368.> cfg80211: World regulatory domain updated: [COLOR="#FF0000"]blank[/COLOR]What is your domain? US? DK? GB? or...what? Maybe we need to force it.```
iw reg get
```If you temporarily turn off N speeds in the router, is there any change? Is encryption AES or the dreaded TKIP?

---

### Post by erikmolstad on 2013-05-28
Hi

It never did reconnect by itself, just drop.



iw reg get:[COLOR=#222222][FONT=Verdana]Country GB:[/FONT][/COLOR]	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS

Encryption is AES

What do you mean n-speed? Wireless mode? I can select "auto", "legacy" or "n-only". I also have a b/g protection feature.

I will play around a bit with the different settings. I unchecked b/g protection and set bw to 20MHz (before it was 20/40) and now it has been working for quite a while... so it looks promising. Still I don't understand why... 

What annoys me bigtime is that it is an ASUS router I have (DSL-N55U) and I bought them at the same time from the same place, so I just assumed they would be compatible...

---

### Post by chili555 on 2013-05-28
I'm sure they are compatible. However, the driver in question, rtl8192ce, is pretty tricky and I doubt it has been tested and refined to the extent that the Windows driver has. I am encouraged by the fact that the device seems to be working better with 40 mHz turned off. That's obviously not the best solution, but it at least gets you working until a better driver comes along.> iw reg get:Country [COLOR="#FF0000"]GB[/COLOR]:	(2402 - 2482 @ 40), (N/A, 20)
(5170 - 5250 @ 40), (N/A, 20)
(5250 - 5330 @ 40), (N/A, 20), DFS
(5490 - 5710 @ 40), (N/A, 27), DFSIt appears a proper country code is being set.

---

### Post by forestlake-au on 2014-05-12
well i have this wireless adapter and i have had no luck.... unfortunately i have had no luck understanding anything you guys have written either :{ i am guessing there is no other way of doing this then without going into the terminal ?

---

### Post by chili555 on 2014-05-12
> **forestlake-au said:**
> well i have this wireless adapter and i have had no luck.... unfortunately i have had no luck understanding anything you guys have written either :{ i am guessing there is no other way of doing this then without going into the terminal ?There isn't a better way, unfortunately. I have been hoping for a graphical tool called 'fix my wireless,' but so far, the subject is too complex and too fast moving to be able to figure out that tool! It seems like new devices and newer versions of old devices come out every day! 

If you'd like to proceed, let's gather some information. I will explain every step carefully as we go along. First, open a terminal with Ctrl+Alt+t. We want to list all the PCI devices and get some numerical details:```
lspci -nn
```Pick out your wireless device and post the result here. It may identify itself as a Realtek wireless adapter, since they supply the chips to Asus. Post what you found here.

Next we need to know which Ubuntu version you have installed:```
lsb_release -d
```Finally, 'i have had no luck' covers a lot of ground. What, exactly, are your symptoms?

---

### Post by chili555 on 2014-05-12
Deleted double-post.

---

### Post by forestlake-au on 2014-05-18
hi [**[COLOR=#000000]chili555[/COLOR]**]("http://ubuntuforums.org/member.php?u=35909") and thanks for getting back to me :) By me having no luck i meant that everything i have found online has been of no help to me or it's just over my head and i can't understand it anyways ;p

after imputing lspci -nn i got this...
30:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)

i am running Ubuntu 14.04 LTS.... this network adapter worked in everything from 13.04 backwards, but not in 13.10 or 14.04

symptoms are that it shows it's connected but there is no actual connection

sorry for the late reply and cheers,
Forest

---

### Post by chili555 on 2014-05-18
> Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)I assume the driver being loaded is *rtl8192ce*; confirm:```
lsmod | grep rtl8
```Is an actual wireless interface created, ideally wlan0?```
iwconfig
```When Network Manager confirms that you are connected, do you get an IP address?```
nm-tool
```Can you ping?```
ping -c3 8.8.8.8
```Thanks.

---

### Post by forestlake-au on 2014-05-18
driver >>>

rtl8192ce              53550  0  

 rtl_pci                26690  1 rtl8192ce  
 rtlwifi                63475  2 rtl_pci,rtl8192ce  

 rtl8192c_common        53172  1 rtl8192ce  

 mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce

wlan0 >>>


eth0      no wireless extensions.  

   
 lo        no wireless extensions.  

 

 wlan0     IEEE 802.11bgn  ESSID:off/any   

           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    

           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off  

           Power Management:off

Network Manager/IP address >>>


NetworkManager Tool  

 

 State: connected (global)  

 

 - Device: wlan0  [The Matrix] --------------------------------------------------  

   Type:              802.11 WiFi  

   Driver:            rtl8192ce  

   State:             connected  

   Default:           yes  

   HW Address:        AC:22:0B:93:9F:AF  

 

   Capabilities:  

     Speed:           1 Mb/s  

 

   Wireless Properties  

     WEP Encryption:  yes  
     WPA Encryption:  yes  

     WPA2 Encryption: yes  

 

   Wireless Access Points (* = current AP)  

     BigPondF0FC42:   Infra, A4:B1:E9:F0:FC:42, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA2  

     Optus E586 ee59: Infra, 80:B6:86:6E:EE:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA  

     BigPond5354:     Infra, 00:1E:C7:A1:37:69, Freq 2442 MHz, Rate 54 Mb/s, Strength 37 WPA  

     NETGEAR:         Infra, 00:18:4D:8F:12:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP  

     adam:            Infra, 30:46:9A:A2:FE:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2  

     *The Matrix:     Infra, 54:A5:1B:D8:2B:19, Freq 2412 MHz, Rate 54 Mb/s, Strength 48 WPA2  

 

   IPv4 Settings:  

     Address:         192.168.1.100  

     Prefix:          24 (255.255.255.0)  

     Gateway:         192.168.1.1  

 

     DNS:             192.168.1.1  

 

 

 - Device: eth0 -----------------------------------------------------------------  

   Type:              Wired  

   Driver:            e1000e  

   State:             unavailable  

   Default:           no  

   HW Address:        00:0F:FE:C7:3E:A2  

 

   Capabilities:  

     Carrier Detect:  yes  

 

   Wired Properties  

     Carrier:         off  

Ping >>>


PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.  

 

 --- 8.8.8.8 ping statistics ---  

 3 packets transmitted, 0 received, 100% packet loss, time 2016ms

---

### Post by chili555 on 2014-05-18
Wow! Everything looks wonderful right up to the ping! How about the router?```
ping -c3 192.168.1.1
```

---

### Post by forestlake-au on 2014-05-18
> **chili555 said:**
> Wow! Everything looks wonderful right up to the ping! How about the router?```
ping -c3 192.168.1.1
```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.  
 

 --- 192.168.1.1 ping statistics ---  
 3 packets transmitted, 0 received, 100% packet loss, time 1999ms

---

### Post by chili555 on 2014-05-19
What is happening behind the scenes as it's trying to connect; or, more likely, connecting and dropping?```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n25 
```

---

### Post by forestlake-au on 2014-05-19
just wanted to say thank you for efforts in helping me :)

ok, here is the output for this...

May 19 23:43:35 forest-HP-Elite avahi-daemon[827]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::ae22:bff:fe93:9faf.  
 May 19 23:43:35 forest-HP-Elite avahi-daemon[827]: New relevant interface wlan0.IPv6 for mDNS.  
 May 19 23:43:35 forest-HP-Elite avahi-daemon[827]: Registering new address record for fe80::ae22:bff:fe93:9faf on wlan0.*.  
 May 19 23:43:37 forest-HP-Elite dhclient: DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67 (xid=0x7da0f4ab)  
 May 19 23:43:37 forest-HP-Elite NetworkManager[833]: <info> (wlan0): DHCPv4 state changed preinit -> expire  
 May 19 23:43:37 forest-HP-Elite dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x783508e7)  
 May 19 23:43:37 forest-HP-Elite NetworkManager[833]: <info> (wlan0): DHCPv4 state changed expire -> preinit  
 May 19 23:43:40 forest-HP-Elite dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x783508e7)  
 May 19 23:43:41 forest-HP-Elite dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67 (xid=0x783508e7)  
 May 19 23:43:43 forest-HP-Elite NetworkManager[833]: <info> (wlan0): DHCPv4 state changed preinit -> bound  
 May 19 23:43:43 forest-HP-Elite NetworkManager[833]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...  
 May 19 23:43:43 forest-HP-Elite NetworkManager[833]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...  
 May 19 23:43:43 forest-HP-Elite avahi-daemon[827]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.  
 May 19 23:43:43 forest-HP-Elite avahi-daemon[827]: New relevant interface wlan0.IPv4 for mDNS.  
 May 19 23:43:43 forest-HP-Elite avahi-daemon[827]: Registering new address record for 192.168.1.101 on wlan0.IPv4.  
 May 19 23:43:44 forest-HP-Elite NetworkManager[833]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]  
 May 19 23:43:44 forest-HP-Elite NetworkManager[833]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.  
 May 19 23:43:44 forest-HP-Elite NetworkManager[833]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]  
 May 19 23:43:44 forest-HP-Elite NetworkManager[833]: <info> Policy set 'The Matrix' (wlan0) as default for IPv4 routing and DNS.  
 May 19 23:43:56 forest-HP-Elite NetworkManager[833]: <info> Activation (wlan0) successful, device activated.  
 May 19 23:43:56 forest-HP-Elite wpa_supplicant[1074]: wlan0: CTRL-EVENT-SCAN-STARTED  
 May 19 23:43:56 forest-HP-Elite NetworkManager[833]: <info> (wlan0): IP6 addrconf timed out or failed.  
 May 19 23:43:56 forest-HP-Elite NetworkManager[833]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...  
 May 19 23:44:06 forest-HP-Elite NetworkManager[833]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...  
 May 19 23:44:06 forest-HP-Elite NetworkManager[833]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

---

### Post by chili555 on 2014-05-20
The log looks perfect! The device requested an IP address from the router and got one. We do not see a drop at all.> Registering new address record for 192.168.1.101 on wlan0.IPv4. Do you now have that address?```
ifconfig
```Is this router one for which you have administrative privileges? If so, you may have better luck with a network name without a space; that is TheMatrix instead of The Matrix. Second, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit. 

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Any improvement? If not, we need to try to see the log after it drops; what you posted is perfect.

---

### Post by forestlake-au on 2014-05-20
hey ! yes, i have admin privledges but just wanted to ask before i tried this, will this affect my connection for Windows or for other users on the network as i share my connection with a neighbour 2 doors down ?

---

### Post by chili555 on 2014-05-20
> **forestlake-au said:**
> hey ! yes, i have admin privledges but just wanted to ask before i tried this, will this affect my connection for Windows or for other users on the network as i share my connection with a neighbour 2 doors down ?Probably not, unless they are using a really old computer that doesn't do WPA2. They will drop and reconnect as you reboot the router. I usually do such things late at night or early in the morning so that few or none are on line.

---

