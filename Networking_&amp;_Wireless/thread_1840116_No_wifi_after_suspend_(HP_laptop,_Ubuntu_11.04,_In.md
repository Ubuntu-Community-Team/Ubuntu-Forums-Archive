---
title: "No wifi after suspend (HP laptop, Ubuntu 11.04, Intel wireless)"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by psycho_killer on 2011-09-07
I've searched around a bunch but haven't found a solution to my problem yet.  My laptop won't connect to wireless internet upon waking from suspend.  Networks are found, but the connection indicator just keeps flashing when it goes to connect to mine.  Eventually it will ask for the network wpa password but won't connect even when it's provided.  This is a bit of a dealbreaker because my laptop runs too hot to leave it on continuously and I keep too many programs open to turn it off and on all the time.  (Hibernate does not work at all, incidentally.)

**Machine:**
HP dv7t quad edition laptop
Intel quad core i7-2630QM 2.0 GHz
8GB RAM

**Running:**
Ubuntu 11.04 64-bit in Classic Mode
3.0.0-9-lowlatency (you may note below there's an audio interface connected)

Sorry if there's too much info below; I'm not sure what to grep in all cases...

**lspci:**

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
19:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```**lsusb:**

```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 17cc:0815 Native Instruments Audio Kontrol 1
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:e258 Suyin Corp. 
Bus 001 Device 003: ID 138a:0018 DigitalPersona, Inc 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```**ifconfig:**

```
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:ad:33:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1790604 (1.7 MB)  TX bytes:1790604 (1.7 MB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:97:69:00  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8ea9:82ff:fe97:6900/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1807555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1066172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2672565091 (2.6 GB)  TX bytes:100649721 (100.6 MB)
```**iwconfig:**

```
wlan0     IEEE 802.11bgn  ESSID:"flux capacitor"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:1C:67:9F   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:116  Invalid misc:8446   Missed beacon:0
```**lsmod:**

```
Module                  Size  Used by
parport_pc             34915  0 
ppdev                  16865  0 
dm_crypt               22529  1 
binfmt_misc            17083  1 
vboxnetadp             13113  0 
vboxnetflt             28052  0 
vboxdrv               203938  2 vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     30621  1 
snd_hda_codec_idt      62044  1 
arc4                   12458  2 
joydev                 17257  0 
snd_usb_caiaq          39534  2 
snd_hda_intel          30380  2 
snd_hda_codec          85031  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               70617  0 
snd_hwdep              13150  1 snd_hda_codec
videodev               78630  1 uvcvideo
v4l2_compat_ioctl32    16842  1 videodev
snd_pcm                83789  5 snd_hda_codec_hdmi,snd_usb_caiaq,snd_hda_intel,snd_hda_codec
hp_wmi                 17390  0 
sparse_keymap          12768  1 hp_wmi
snd_seq_midi           12848  0 
snd_rawmidi            27063  2 snd_usb_caiaq,snd_seq_midi
snd_seq_midi_event     13316  1 snd_seq_midi
snd_seq                57024  2 snd_seq_midi,snd_seq_midi_event
snd_timer              26838  2 snd_pcm,snd_seq
snd_seq_device         13097  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55939  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_usb_caiaq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                68222  0 
serio_raw              12806  0 
iwlagn                300211  0 
mac80211              292050  1 iwlagn
cfg80211              178156  2 iwlagn,mac80211
rts_pstor             436265  0 
soundcore              12432  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
mei                    39963  0 
hp_accel               21104  0 
lis3lv02d              17855  1 hp_accel
input_polldev          12906  1 lis3lv02d
lp                     17104  0 
parport                35862  3 parport_pc,ppdev,lp
i915                  544029  2 
radeon                997834  0 
ttm                    60883  1 radeon
drm_kms_helper         35393  2 i915,radeon
drm                   195759  5 i915,radeon,ttm,drm_kms_helper
ahci                   25186  3 
r8169                  54531  0 
libahci                26865  1 ahci
xhci_hcd               81237  0 
i2c_algo_bit           12879  2 i915,radeon
wmi                    17410  1 hp_wmi
video                  17969  1 i915
```**dmesg | grep "iwlagn":**

```
[   25.986476] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   25.986479] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   25.986538] iwlagn 0000:0d:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.986548] iwlagn 0000:0d:00.0: setting latency timer to 64
[   25.986580] iwlagn 0000:0d:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   26.017599] iwlagn 0000:0d:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   26.017603] iwlagn 0000:0d:00.0: Device SKU: 0X9
[   26.017606] iwlagn 0000:0d:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   26.017616] iwlagn 0000:0d:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   26.017713] iwlagn 0000:0d:00.0: irq 53 for MSI/MSI-X
[   26.054254] iwlagn 0000:0d:00.0: loaded firmware version 39.31.5.1 build 35138
```**sudo lshw -C network:**

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:ad:33:49
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:97:69:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-9-lowlatency firmware=39.31.5.1 build 35138 ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:c4500000-c4501fff
```**iwlist scan:**

```
wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:1C:67:9F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"flux capacitor"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005978742dc3
                    Extra: Last beacon: 63225ms ago
                    IE: Unknown: 000E666C757820636170616369746F72
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```**sudo /etc/init.d/networking restart**:

```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          
Ignoring unknown interface wlan0=wlan0.
```

---

### Post by psycho_killer on 2011-09-09
Bump.  Anybody got anything for me?

---

### Post by psycho_killer on 2011-10-14
I've tried everything I can find on the web to fix this problem and nothing has worked.  I was hoping it might magically get solved by 11.10 but no such luck.  

I'm going to try a couple of other distributions and see if that fixes it.  If not, I guess it's back to Windows.  I can't run a laptop without a suspend function, end of story.

---

### Post by nah40 on 2011-10-15
> **psycho_killer said:**
> I've tried everything I can find on the web to fix this problem and nothing has worked.  I was hoping it might magically get solved by 11.10 but no such luck.  

I'm going to try a couple of other distributions and see if that fixes it.  If not, I guess it's back to Windows.  I can't run a laptop without a suspend function, end of story.

I have the same problem, same Intel wireless.
I have spend many hours on this with no solution.
It is no longer worth the effort, back to Windows after five years with Ubuntu.

---

### Post by rommer on 2011-11-01
Let's see...
No support for the fingerprint reader.
No resume after suspend for the intel wireless 1000
If screen is turned off by power system the screen won't turn back on.
Can't use the ATI graphics card without the system locking up.

I'm really regretting buying this new HP laptop. 

I REALLY hate to say I may have to join the windows crowd on this one and I've been exclusive Linux since 1993!!!!!!!

Seems Ubuntu 11.10 is very prematurely release. I've found WAY too many show stoppers. Sighhhhhh....

---

### Post by psycho_killer on 2011-11-01
> **rommer said:**
> 
No support for the fingerprint reader.
No resume after suspend for the intel wireless 1000
If screen is turned off by power system the screen won't turn back on.
Can't use the ATI graphics card without the system locking up.

I'm really regretting buying this new HP laptop. 


Yup, I've had every single one of those problems.  I still like the laptop, though...

---

### Post by sgtguthrie on 2011-12-03
Anyone found a solution for the suspend thing? That's the only issue I have with hp dv6t with basically the same specs. I'm going to try the zen kernel, compiling now. I've had 2 distros where it's worked, and they were both old kernels with barely any sandy bridge support. I'm really thinking it's kernel related...

---

### Post by mattzab on 2011-12-22
Did anyone try this solution?
I have the same problem and don't have the time to try this out but it doesnt look like a bad workaround. I'm linking to the article and quoting it as well to save you the hassle of having to click the link if you don't want to.

Link: [http://fooninja.net/2010/09/02/how-to-fix-wifi-after-suspendresume-in-ubuntu/](http://fooninja.net/2010/09/02/how-to-fix-wifi-after-suspendresume-in-ubuntu/)

Quoted:
> Problem: After suspending and then resuming my Thinkpad X61s running Ubuntu 10.04 (Lucid), the wireless would no longer work. Networks were detected but I couldn't connect - nothing happened. The wifi card is an "Intel PRO/Wireless 4965 AG or AGN", according to lspci. (I had the same problem with Ubuntu 9.10 (Karmic)).

Solution: I still don't know the cause, but restarting networking and unloading/reloading the module for the wireless interface fixed the problem.

```
#!/bin/sh
# Stop networking and network-manager
stop network-manager
service networking stop

# Remove and reload the module for the wifi card
# (replace iwlagn with your own if you have a different one)
modprobe -r -f iwlagn
modprobe iwlagn

# Start networking and network-manager again
service networking start
start network-manager
```
Save the file as fixwifi.sh, run chmod +x fixwifi.sh and run it as root. Voila! (Hopefully.)

To make things smoother, if you always have this problem after resuming, you can have the script run automatically after resume. In earlier versions of Ubuntu you would put the script in /etc/acpi/resume.d. This has changed with 10.04 Lucid. You now have to put the script in /etc/pm/sleep.d, but you will have to make some modifications. After looking at the scripts in /usr/lib/pm-utils/sleep.d for guidance, I came up with the following:

```
#!/bin/sh

. "${PM_FUNCTIONS}"

resume_wifi()
{
        # Stop networking and network-manager
        stop network-manager
        service networking stop

        # Remove and reload the module for the wifi card
        modprobe -r -f iwlagn
        modprobe iwlagn

        # Start networking and network-manager again
        service networking start
        start network-manager
}

case "$1" in
        thaw|resume)
                resume_wifi
                ;;
        *) exit $NA
                ;;
esac
```
Save the file as 99fixwifi.sh, put it in /etc/pm/sleep.d and make it executable (chmod +x 99fixwifi.sh). Crude? Yes, but it works for me. If you have a nicer solution, let me know!

---

### Post by psycho_killer on 2011-12-22
> **mattzab said:**
> Did anyone try this solution?
I have the same problem and don't have the time to try this out but it doesnt look like a bad workaround. I'm linking to the article and quoting it as well to save you the hassle of having to click the link if you don't want to.

Link: [http://fooninja.net/2010/09/02/how-to-fix-wifi-after-suspendresume-in-ubuntu/](http://fooninja.net/2010/09/02/how-to-fix-wifi-after-suspendresume-in-ubuntu/)

Quoted:

Yeah, that never worked for me.  Actually, with the latest kernels, Ubuntu doesn't even suspend at all on my computer.  An older kernel ameliorates the wifi problem but causes a bunch of new ones, so I don't think there's a good fix yet.

---

### Post by sgtguthrie on 2012-01-05
> **psycho_killer said:**
> Yeah, that never worked for me.  Actually, with the latest kernels, Ubuntu doesn't even suspend at all on my computer.  An older kernel ameliorates the wifi problem but causes a bunch of new ones, so I don't think there's a good fix yet.

EXACTLY!!!  And it's killing me!  All I want to be able to do is shut my lid to suspend, open it, and have wireless networking work!  I'm growing tired of this issue not being fixed.  I've tried zen kernel, I'm currently on kernel 3.2 rc7 and still no dice :(

Not quite sure where to go from here...

---

### Post by nah40 on 2012-01-05
I will wait until 12.04.
Hopefully this will be fixed.
Until then I have no choice but to use Windows.

---

### Post by sgtguthrie on 2012-02-16
Anyone get this figured out or have a viable work around?  Hibernate works fine if your swap is larger than your ram (ie: 8GB Ram you need a little over 8GB of swap).  It still takes a lot longer than waking from suspend.  I'm currently on 11.10 with the 3.3rc3 kernel and I've tried 12.04 Alpha 2 just to see if the issue was still present...go figure, it is ](*,)

---

### Post by chili555 on 2012-02-16
Please try this:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="iwlagn"
```Substitute your wireless driver if it's not iwlagn. Proofread, save and close gedit. Let us and the searchers have your report, please.

---

### Post by psycho_killer on 2012-02-16
> **chili555 said:**
> Please try this:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="iwlagn"
```Substitute your wireless driver if it's not iwlagn. Proofread, save and close gedit. Let us and the searchers have your report, please.

Thanks, but I tried that ages ago without success.  Currently my laptop won't suspend at all (just hangs on a blankish screen) and trying that solution again doesn't fix it.

---

### Post by garvinrick4 on 2012-02-16
Here are 3.0 and up kernels to use if you are using 2.6 kernel in 11.04.
I have iwlagn driver and 1000 card and it works for me. 
Take the 3 - headers, all.deb and image of 32 or 64 bit kernel and download to desktop.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1.4-oneiric/")
Now take the module-init-tools below in .deb of 64 or 32 bit whatever is yours. Click on 32 or 64 bit build .deb will be in lower left corner download to desktop.
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)
So now you have 4 .deb's on your Desktop, make sure only .deb on desktop is those 4 then:
```
cd Desktop
``````
sudo dpkg -i *.deb
```Type in password and the 4 .debs will install.
Then
reboot into new kernel 3.1.4 and all with iwlagn driver should work fine in 11.04 Natty

---

### Post by psycho_killer on 2012-02-16
> **garvinrick4 said:**
> Here are 3.0 and up kernels to use if you are using 2.6 kernel in 11.04.
I have iwlagn driver and 1000 card and it works for me. 
Take the 3 - headers, all.deb and image of 32 or 64 bit kernel and download to desktop.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1.4-oneiric/")
Now take the module-init-tools below in .deb of 64 or 32 bit whatever is yours. Click on 32 or 64 bit build .deb will be in lower left corner download to desktop.
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)
So now you have 4 .deb's on your Desktop, make sure only .deb on desktop is those 4 then:
```
cd Desktop
``````
sudo dpkg -i *.deb
```Type in password and the 4 .debs will install.
Then
reboot into new kernel 3.1.4 and all with iwlagn driver should work fine in 11.04 Natty

Thanks, but my machine still refuses to suspend with the new kernel (I was on 3.0.0-16 before).  It just hangs on a tty1 screen.

---

### Post by garvinrick4 on 2012-02-16
If post above does not do it for some here is a older iwlagn link worth a try.

[http://ubuntuforums.org/showthread.php?t=1862484&page=8](http://ubuntuforums.org/showthread.php?t=1862484&page=8)

---

### Post by nah40 on 2012-03-02
Just updated to 12.04.
Power usage much better.
Still unable to reconnect to wireless after suspending.
Still a deal killer for me.
I will continue to use Windows until there is a fix.

---

### Post by Nesbitt on 2012-04-28
Upgraded to 12.04 and still have this annoying problem !

---

### Post by sgtguthrie on 2012-04-28
Upgraded to a 15" Macbook Pro and no more issues ;-) 

Screw HP... LOL!

---

### Post by nah40 on 2012-04-28
Yes, still the same problems with 12.04.
Keeps me using Windows.

---

### Post by Kelketek on 2012-06-03
Create /etc/modprobe.d/iwlwifi.conf and put in:

options iwlwifi bt_coex_active=0

Older versions might need to use 'iwlagn' instead of 'iwlwifi'.

---

### Post by nah40 on 2012-06-04
Tried it, still does not work.
Thanks anyway.
Maybe someday I will get it fixed or this laptop will crap out and get replaced.

---

### Post by prarobo on 2012-08-22
I have the same issues with wifi on Ubuntu (11.04 / 11.10 / 12.04). It does not connect after suspend or closing the lid. My laptop is a HP dv6t, similiar configuration to a lot of posts in this thread.

The work around for me is to put the computer to "do nothing" when the lid is closed. This might not be a perfect solution but works for me.

Hope it helps someone. If you are a person on the go and are concerned with draining your battery, this is not for you.

---

### Post by psycho_killer on 2012-10-01
After more than a year I finally seem to have gotten this solved.  I have a hodgepodge of solutions implemented and I'm not sure which of them is actually doing the trick; at some point I may try to disassociate them to figure it out but right now I'm just basking in the warmth of a working suspend function.  Here's everything I have in place.  Note that I use Arch and not Ubuntu now, but hopefully that doesn't matter.

/etc/modprobe.d/iwlwifi.conf
```
options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1
```/etc/pm/config.d/config
```
SUSPEND_MODULES="iwlwifi"
```/etc/pm/config.d/modules
```
SUSPEND_MODULES="ehci_hcd xhci_hcd iwlwifi hp_wmi wmi mac80211 cfg80211 sparse_keymap rfkill"
```/etc/pm/sleep.d/wifi
```
case "${1}" in
    resume|thaw)
        rmmod iwlwifi
    modprobe iwlwifi bt_coex_active=0
;;
esac
```Thanks to everyone who has provided suggestions, especially Kelketek.

---

### Post by mclewell on 2012-10-02
> **psycho_killer said:**
> After more than a year I finally seem to have gotten this solved.  I have a hodgepodge of solutions implemented and I'm not sure which of them is actually doing the trick; at some point I may try to disassociate them to figure it out but right now I'm just basking in the warmth of a working suspend function.  Here's everything I have in place.  Note that I use Arch and not Ubuntu now, but hopefully that doesn't matter.

/etc/modprobe.d/iwlwifi.conf
```
options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1
```/etc/pm/config.d/config
```
SUSPEND_MODULES="iwlwifi"
```/etc/pm/config.d/modules
```
SUSPEND_MODULES="ehci_hcd xhci_hcd iwlwifi hp_wmi wmi mac80211 cfg80211 sparse_keymap rfkill"
```/etc/pm/sleep.d/wifi
```
case "${1}" in
    resume|thaw)
        rmmod iwlwifi
    modprobe iwlwifi bt_coex_active=0
;;
esac
```Thanks to everyone who has provided suggestions, especially Kelketek.

This worked! I only added the following to /etc/modprobe.d/iwlwifi.conf:

```
options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1
```

and everything is well again after a resume from suspend. (Running Linux Mint 13, aka 12.04)

---

### Post by robbyrob on 2013-01-13
glad to see that you guys got this going. I am a total linux noob as I just made the switch from windows about a week ago and not really sure on how to do much on linux. Ive been jaded by just double clicking a .exe for over 10 years and letting the system do the rest.

I'm a little confused on how to apply this fix. Can someone with some time care to at lease describe how I would apply the first one and ill just do the same for the rest.

ps. is there a good guide to get the basics of linux around you guys recommend?

---

### Post by chili555 on 2013-01-13
> **robbyrob said:**
> glad to see that you guys got this going. I am a total linux noob as I just made the switch from windows about a week ago and not really sure on how to do much on linux. Ive been jaded by just double clicking a .exe for over 10 years and letting the system do the rest.

I'm a little confused on how to apply this fix. Can someone with some time care to at lease describe how I would apply the first one and ill just do the same for the rest.

ps. is there a good guide to get the basics of linux around you guys recommend?Do you have an iwlagn or an iwlwifi device, or as I suspect, something different altogether? Please open a terminal and run and post:```
sudo lshw -C network
```Gathering and listing all that data takes a few moments, please be patient.

---

### Post by supermannow on 2013-06-11
I'm a long time linux user 10+ years at least but still consider myself a noob,
Just ran into this "suspend wifi" problem after an update to 12.? Anyway as chili555 suggested ran in terminal ```

sudo lshw -C network
```
Towards the bottom of the generated info. saw I was using "iwlwifi" for the driver on my hp Pavillion dv6 Laptop
Then I ran in terminal```
sudo gedit /etc/modprobe.d/iwlwifi.conf/
```
This will open text editor for this config file and pasted the following from psycho_killer's post```

options iwlwifi bt_coex_active=0 
options iwlwifi 11n_disable=1
```
Hit save and closed everything, rebooted and all is good now.
Thanks to everyone who posted on this thread, made it easy to fix. 
Hope this helps someone

---

### Post by nah40 on 2013-06-11
Still does not work.
Thanks anyway.

---

### Post by cbaxley on 2013-06-22
worked for my dv6 on raring ringtail too.

---

### Post by cbaxley on 2013-06-22
Worked with my dv6 on raring ringtail.



> **supermannow said:**
> I'm a long time linux user 10+ years at least but still consider myself a noob,
Just ran into this "suspend wifi" problem after an update to 12.? Anyway as chili555 suggested ran in terminal ```

sudo lshw -C network
```
Towards the bottom of the generated info. saw I was using "iwlwifi" for the driver on my hp Pavillion dv6 Laptop
Then I ran in terminal```
sudo gedit /etc/modprobe.d/iwlwifi.conf/
```
This will open text editor for this config file and pasted the following from psycho_killer's post```

options iwlwifi bt_coex_active=0 
options iwlwifi 11n_disable=1
```
Hit save and closed everything, rebooted and all is good now.
Thanks to everyone who posted on this thread, made it easy to fix. 
Hope this helps someone

---

### Post by jtzero on 2013-09-23
Im a little late, but adding this worked for me as well! thanks!

---

### Post by ideler.dennis on 2014-08-26
> **mclewell said:**
> This worked! I only added the following to /etc/modprobe.d/iwlwifi.conf:

```
options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1
```

and everything is well again after a resume from suspend. (Running Linux Mint 13, aka 12.04)

My /etc/modprobe.d/iwlwifi.conf file contains the line

```

remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

The above may have some errors since I wrote it out on my phone (couldn't copy paste from my laptop, can't connect to Wi-Fi from it).

Do I remove this line? I put the two "options" lines above it, restarted the machine, but still couldn't connect to the Wi-Fi.

---

### Post by wildmanne39 on 2014-08-26
Thread closed. Please do not post in old threads. Start a new thread in networking with a descriptive title please.
Thanks

---

