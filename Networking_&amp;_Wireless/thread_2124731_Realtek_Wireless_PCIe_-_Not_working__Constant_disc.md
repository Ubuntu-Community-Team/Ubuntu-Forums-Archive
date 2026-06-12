---
title: "Realtek Wireless PCIe - Not working / Constant disconnects"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by meebix on 2013-03-11
Hi Everyone,

I am trying to get my Realtek wireless card up and running but I am having some issues.  I have done quite a bit of research via the internet and in Ubuntu and other forums and keep coming up short on getting my card to work :| (as it would in Windows, without any problems).  So I am seeking your expertise!

The problem:  With a clean install of the Linux OS, the wireless works well for about 10 minutes.  After that, it disconnects frequently or cannot connect at all.  A lot of times when it is connected, I cannot load a webpage.

Here is the output from some commands I have run for you:

```
* I. scanning WIFI PCI devices...
  -- Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
      ==> PCI ID = 10ec:8178 (rev 01)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Friedman"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 80:ee:73:53:f8:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 68:1c:a2:16:14:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 68:1c:a2:16:14:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:d000(size=256) memory:f7c00000-f7c03fff


```

One strange thing I noticed is that it says this is a Realtek RTL8188CE that is installed, but the driver is RTL8192CE?

As I have mentioned, I have tried a bunch of things, but I am very eager to hear what you all have to suggest.  I am excited to get started with Linux and this is holding me back quite a bit!  Please let me know if you need anymore information.

Thank you!

---

### Post by cortman on 2013-03-11
Just check to make sure the firmware is installed, run

```
sudo apt-get install firmware-realtek
```

---

### Post by meebix on 2013-03-11
Thanks cortman - something I have not tried, but probably should have.

When I run the code, I get "Unable to located package firmware-realtek"

I am assuming this is bad, or maybe I just need to grab the .bz2 firmware package online and try the code again?

---

### Post by cortman on 2013-03-12
My mistake- I forgot that I was writing/testing that on my Crunchbang (Debian) machine last night.
For Ubuntu there indeed is not any such package as firmware-realtek.
You may need to install a different driver- see [here]("http://ubuntuforums.org/showthread.php?t=1580036") and [here]("http://ubuntuforums.org/showthread.php?t=1604101") for info on that- the first link includes a link to the driver download.

---

### Post by varunendra on 2013-03-12
> **meebix said:**
> ```
* I. scanning WIFI PCI devices...
  -- Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
      ==> PCI ID = **[COLOR="#000080"]10ec[/COLOR]:[COLOR="#800000"]8178[/COLOR]** (rev 01)
```

One strange thing I noticed is that it says this is a Realtek RTL8188CE that is installed, but the driver is RTL8192CE?

First of all, welcome to the forums meebix !:)

The driver is correct for your card. The proper way to find that out is to make sure the **[COLOR="#000080"]VID[/COLOR]** (Vendor ID, highlighted in Blue above) and [COLOR="#800000"]**PID**[/COLOR] (Product ID, highlighted in brown) combination is supported by it.

This information (+ a lot more) about a driver can be extracted with modinfo command. For example, modinfo rtl8192ce yields following -
```
~$ modinfo rtl8192ce
filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     DA52BF758B7683607AFCB85
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#000080"]**10EC**[/COLOR]d0000**[COLOR="#800000"]8178[/COLOR]**sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.2.0-36-generic SMP mod_unload modversions 
**parm:           swenc:Set to 1 for software crypto (default 0)**
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
```
Note that the VID and PID are included in its 'alias' list, meaning it is meant to support that device, besides three others that are listed.

At the bottom of the output are some parameters (parm) that can be used withe this driver. Let's try one of these to stabilize your connection.
In a terminal, do -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=Y
```
.. then retry connecting and see if it helps.
The above parameter is temporary and will be reset to default on restart, so don't restart after the above two commands. If it helps, we can make it permanent.

---

### Post by meebix on 2013-03-12
Varun,

Thanks for the welcome!  I ran both of the codes you suggested and then opened up my browser.  It was running quicker than ever.  I was watching youtube and surfing.  I started to try and break it, and unfortunately I did :/

(I am using WICD by the way).

Same story, worked really well for about 8 minutes, and then stopped connecting altogether.  It did not "disconnect" though.  Just stopped working.  Wouldn't connect to webpages anymore.  When I went into WICD, it wouldn't even find any networks.


What should we do now?

---

### Post by varunendra on 2013-03-12
> **meebix said:**
> What should we do now?

Let's try another available parameter now -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=Y fwlps=N
```

Even if that doesn't help, please follow the Wireless Script link in my signature and do what the linked post asks to do. Run the script when wireless is connected.

---

### Post by meebix on 2013-03-12
Varun,

You did it!  Those last two codes you posted have been working for the last 25 minutes, and trust me I am trying to break it :p !

How can I make this change permanent?

Thanks!

---

### Post by varunendra on 2013-03-13
> **meebix said:**
> Varun,

You did it! :???:
/me wonders how to respond :-k

> Those last two codes you posted have been working for the last 25 minutes, and trust me I am trying to break it :p !
A word of wisdom - 25 minutes or even 2.5 hours are too soon to become excited. I can't explain in a few words, but I highly doubt its consistency. But if you think it even slightly improves the situation, then -
> How can I make this change permanent?
Do the following -
```
echo "options rtl8192ce swenc=Y fwlps=N" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
It will create a file named "rtl8192ce.conf" in /etc/modprobe.d/ directory that will contain a single line - **options rtl8192ce swenc=Y fwlps=N**
This file will ensure that on next reboot, the rtl8192ce driver is pre-loaded with these parameters.

I suggest you wait for at least 2 days (with at least 2-3 hours usage cycle) to see if it remains stable. If it starts acting funny again, post back (not that I have many ideas in that case ;)).
If it does remain stable, then give us your - *[COLOR="#808080"](I wish, I hope, I pray..)[/COLOR]* **Final** feedback at the end of testing period !

> Thanks!
You're welcome, but you should have reserved it until your final feedback :P

Feel free to break my heart as soon as you can, I've become used to it.

---

### Post by meebix on 2013-03-13
All valid points!  This better work otherwise this is me ---> ](*,) 

I will test for the next couple days, and post some final thoughts.

Much appreciate the help thus far!
-Meebix

---

### Post by meebix on 2013-03-18
Varun,

Excellent work - Wireless is still running smooth!  Appreciate the help!

Moving this to solved.

-Meeibx

---

### Post by varunendra on 2013-03-18
> **meebix said:**
> This better work otherwise this is me ---> ](*,) 
I'm really glad your head is intact...
> **meebix said:**
> Excellent work - Wireless is still running smooth!
:P

..And I found a new parameter to play with \\:D/

---

### Post by meebix on 2013-04-14
Hi All,

I am sad to report that I am starting to have stability issues again :/.  The internet definitely works well, when it's working, but the stability is poor.  It doesn't ever disconnect from the network, but I can tell a lot of times it just pauses or has a mental lapse where it forgets to work.  I usually then have to manually disconnect and reconnect using WICD.

If I still use my Windows machine as a comparison, Linux is no where close :S

Does anyone have additional ideas to improve the stability?

Thanks!
Meebix

---

### Post by varunendra on 2013-04-15
> **meebix said:**
> 
Does anyone have additional ideas to improve the stability?
Let's do some diagnostics. Please post outputs of :
```
uname -mr
ifconfig
iwconfig
grep -R [0-9a-zA-Z] /sys/module/rtl8192ce/parameters/
dmesg | grep 8192
```

---

### Post by zrdc28 on 2013-04-15
Switching from wicd to networkmanager solved this same problem for me. an easy way to do it is go to "/etc/"  "chmod -x wicd" the -x will make wicd
non executable. You might have a wicd folder, if so go into that folder and chmod -x wicd . now go into /etc/NetworkManager and chmod +x networkmanager
that will make networkmanager executable. It will be executed the next time you reboot.

---

### Post by meebix on 2013-04-24
I did try switching back to NetworkManager and it is not any better.

Very sorry for the delay - should have waited to post until after my vacation, but here are the command outputs:

```
 ~ $ uname -mr
3.5.0-17-generic x86_64
 ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 80:ee:73:53:f8:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:576 (576.0 B)  TX bytes:576 (576.0 B)

wlan0     Link encap:Ethernet  HWaddr 68:1c:a2:16:14:25  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6a1c:a2ff:fe16:1425/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14450172 (14.4 MB)  TX bytes:1495350 (1.4 MB)

 ~ $ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BLANK"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:01:5A:80   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:278   Missed beacon:0

 ~ $ grep -R [0-9a-zA-Z] /sys/module/rtl8192ce/parameters/
/sys/module/rtl8192ce/parameters/ips:Y
/sys/module/rtl8192ce/parameters/debug:0
/sys/module/rtl8192ce/parameters/fwlps:N
/sys/module/rtl8192ce/parameters/swenc:Y
/sys/module/rtl8192ce/parameters/swlps:N
 ~ $ dmesg | grep 8192
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021f200000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    9.217812] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[    9.217820] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin


```

Again, it feels like the wireless adapter just forgets that it should be on.  Seems like it goes to sleep or something.

Thanks very much for your help,
Meebix

---

### Post by varunendra on 2013-04-25
Hello meebix,
Right now I'm super busy and can't focus with my tired mind. So just as a blind attempt, maybe even a stupid one, please try -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce ips=N
```
I am assuming the previous configuration file we created is already effective. The above new parameter will also ensure that the adapter will not use "Link power save", thus offering a better and steady link, hopefully.. :|

As earlier, this change will be temporary and will be lost on reboot. If it works, we can make it permanent as earlier.

However, if it doesn't work, please follow the "wireless script" link in my signature, follow the instructions in the linked post and post back the contents of result file (or its pastebin link).

---

### Post by meebix on 2013-05-11
Hi Varun,

Thanks again for the suggestion.  I've been trying it out and it does seem to make the connection better at times, but for instance, right now my Linux connection is hanging really bad, while I am typing this message perfectly fine on my Windows laptop.

Something is really wrong with the Linux connection.  It has its brief moments of greatness, where at times it seems faster than the Windows connection.  However, 90% of the time the Linux connection is unusable.  It is really horrible and frustrating :(

Might there be anything else I could try?

Thanks,
Meebix

---

### Post by varunendra on 2013-05-11
> **meebix said:**
> Might there be anything else I could try?

Yup! Indeed there is something entirely different we may try. The proprietary driver from realtek. While you are connected to internet -

[LIST=1]
[*]Download it from here : [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
[*]Copy the downloaded .tar.bz2 file to your desktop
[*]Right-click the file > "Extract here". This will create a folder and extract all the source files in it.
[*]Open a terminal and do -
[/LIST]

(TIP : type a few initial characters, then press 'Tab' key to auto-complete the name.)
```
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
sudo su
apt-get install build-essential linux-headers-generic
make
make install
exit
```
Reboot and try to connect. Post back how it behaves.

---

### Post by meebix on 2013-05-11
Thanks Varun!

I made the changes.  It constantly disconnects from the internet.  However, I think we are on the right track, because while it IS connected to the internet, the signal strength is much more representative of what it actually should be (given the location I am to the router).  Before, it kept telling me I was at 98%, which isn't even possible.

If we can get it to stay connected, this may work.

Thanks,
Meebix

---

### Post by varunendra on 2013-05-11
Then let's take a closer look at current situation. Please follow the "Wireless Script" link in my signature, follow the instructions and post back the contents of the diagnostics report it creates (or its pastebin link).

---

### Post by meebix on 2013-05-11
Sure thing.

```



*************** info trace ****************



**** uname -a ****


Linux mike-SH67H 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=14
DISTRIB_CODENAME=nadia
DISTRIB_DESCRIPTION="Linux Mint 14 Nadia"


**** lspci ****


05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:0123]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178]
    Kernel driver in use: rtl8192ce


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 002: ID 0a5c:21e8 Broadcom Corp. 
Bus 006 Device 002: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 004: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"Friedman"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-90 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0



**** rfkill ****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               287189  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
arc4                   12529  2 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
aesni_intel            51037  1 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
rtl8192ce             141948  0 
joydev                 17457  0 
rtlwifi               123275  1 rtl8192ce
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
btusb                  18334  0 
bluetooth             209199  22 rfcomm,bnep,btusb
microcode              22803  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13205  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  520519  3 
mac80211              539908  2 rtl8192ce,rtlwifi
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46784  1 i915
lpc_ich                17061  0 
drm                   275528  4 i915,drm_kms_helper
cfg80211              206566  2 rtlwifi,mac80211
i2c_algo_bit           13413  1 i915
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
video                  19335  1 i915
mei                    40690  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_microsoft          12798  0 
ses                    17363  0 
enclosure              15165  1 ses
hid_generic            12493  0 
r8169                  61650  0 
usbhid                 46947  0 
hid                   100366  3 hid_microsoft,hid_generic,usbhid
usb_storage            48838  1 


**** nm-tool ****




**** NetworkManager.state ****




**** NetworkManager.conf ****




**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ATT112"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016768c2055
                    Extra: Last beacon: 936ms ago
                    IE: Unknown: 0006415454313132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Our House"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000089ca2236e0
                    Extra: Last beacon: 864ms ago
                    IE: Unknown: 00094F757220486F757365
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160405190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340405010000000F000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010ABB0F65A35373B26BABCC5E9B11DF2FD1021000E442D4C696E6B2053797374656D73102300074449522D363535102400024134104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020084
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Friedman"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025734199186
                    Extra: Last beacon: 9572ms ago
                    IE: Unknown: 000846726965646D616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B000103104700106CCDA5F1FA80D2B1525023E34A6CD96D10210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"Friedman-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025734a95a0e
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 000E46726965646D616E2D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"842016"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000036f50c97c2
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 0006383432303136
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7E0050F204104A00011010440001011041000100103B00010310470010E484977B182C86C044602D2B8E99DFC61021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"TANIA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000288ab6d7f
                    Extra: Last beacon: 144ms ago
                    IE: Unknown: 000554414E4941
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051900000000000000000000000000000000000000
                    IE: Unknown: 3D1606051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD820050F204104A0001101044000102103B0001031047001000000000000010000000204E7F4680941021000D4E6574676561722C20496E632E1023000757504E3832344E1024000456324831104200046E6F6E651054000800060050F20400011011001457504E3832344E28576972656C65737320415029100800020086103C000103
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"SAMIRWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ade82fc307
                    Extra: Last beacon: 416ms ago
                    IE: Unknown: 000953414D495257494649
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"GandCNetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001506ddf46
                    Extra: Last beacon: 416ms ago
                    IE: Unknown: 000C47616E64434E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001900000000000000000000000000000000000000
                    IE: Unknown: 3D160B001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD890050F204104A0001101044000102103B0001031047001000000000000010000000C03F0E84B3BC1021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F20400011011001A574E44523337303028576972656C6573732041502D322E344729100800020086103C000103
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"CableWiFi"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005b0b41279c9
                    Extra: Last beacon: 18496ms ago
                    IE: Unknown: 00094361626C6557694669
                    IE: Unknown: 01080B8C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100668D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3202606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E02008F000F00FF0359033531483031325F5730303500000000000100003E
                    IE: Unknown: 9606004096001900
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 167.206.251.129
nameserver 167.206.251.130

# OpenDNS Fallback (configured by Linux Mint in /etc/resolvconf/resolv.conf.d/tail).
nameserver 208.67.222.222
nameserver 208.67.220.220


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


[   11.633973] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.816117] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.864831] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.148338] wlan0: authenticate with <MAC address removed>
[   25.158678] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.170052] wlan0: authenticated
[   25.183688] wlan0: associate with <MAC address removed> (try 1/3)
[   25.186783] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   25.186919] wlan0: associated
[   25.187263] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.831540] wlan0: Connection to AP <MAC address removed> lost.
[   31.797195] wlan0: authenticate with <MAC address removed>
[   31.817494] wlan0: send auth to <MAC address removed> (try 1/3)
[   32.020129] wlan0: send auth to <MAC address removed> (try 2/3)
[   32.028071] wlan0: authenticated
[   32.040090] wlan0: associate with <MAC address removed> (try 1/3)
[   32.124564] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   32.124700] wlan0: associated
[   39.801979] wlan0: Connection to AP <MAC address removed> lost.
[   41.090582] wlan0: authenticate with <MAC address removed>
[   41.110909] wlan0: send auth to <MAC address removed> (try 1/3)
[   41.112589] wlan0: authenticated
[   41.126108] wlan0: associate with <MAC address removed> (try 1/3)
[   41.129207] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   41.129360] wlan0: associated
[   55.760344] wlan0: Connection to AP <MAC address removed> lost.
[   57.048941] wlan0: authenticate with <MAC address removed>
[   57.069546] wlan0: send auth to <MAC address removed> (try 1/3)
[   57.071914] wlan0: authenticated
[   57.084463] wlan0: associate with <MAC address removed> (try 1/3)
[   57.087461] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   57.087593] wlan0: associated
[   61.743236] wlan0: Connection to AP <MAC address removed> lost.
[   63.023855] wlan0: authenticate with <MAC address removed>
[   63.044188] wlan0: send auth to <MAC address removed> (try 1/3)
[   63.045850] wlan0: authenticated
[   63.059388] wlan0: associate with <MAC address removed> (try 1/3)
[   63.067271] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   63.067506] wlan0: associated
[   65.197469] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   65.575795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   66.086732] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.861331] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   68.792540] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   71.224426] wlan0: authenticate with <MAC address removed>
[   71.234625] wlan0: send auth to <MAC address removed> (try 1/3)
[   71.236296] wlan0: authenticated
[   71.247976] wlan0: associate with <MAC address removed> (try 1/3)
[   71.251450] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   71.251599] wlan0: associated
[   71.251956] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   84.676155] wlan0: Connection to AP <MAC address removed> lost.
[   85.960251] wlan0: authenticate with <MAC address removed>
[   85.980458] wlan0: send auth to <MAC address removed> (try 1/3)
[   85.987309] wlan0: authenticated
[   85.999670] wlan0: associate with <MAC address removed> (try 1/3)
[   86.002768] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   86.002868] wlan0: associated
[   94.654624] wlan0: Connection to AP <MAC address removed> lost.
[   95.938731] wlan0: authenticate with <MAC address removed>
[   95.959106] wlan0: send auth to <MAC address removed> (try 1/3)
[   95.960757] wlan0: authenticated
[   95.974165] wlan0: associate with <MAC address removed> (try 1/3)
[   95.980014] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[   95.980205] wlan0: associated
[  105.601824] wlan0: Connection to AP <MAC address removed> lost.
[  106.889908] wlan0: authenticate with <MAC address removed>
[  106.910125] wlan0: send auth to <MAC address removed> (try 1/3)
[  106.920484] wlan0: authenticated
[  106.933313] wlan0: associate with <MAC address removed> (try 1/3)
[  106.936311] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  106.936446] wlan0: associated
[  110.577096] wlan0: Connection to AP <MAC address removed> lost.
[  111.861189] wlan0: authenticate with <MAC address removed>
[  111.881407] wlan0: send auth to <MAC address removed> (try 1/3)
[  111.894563] wlan0: authenticated
[  111.908619] wlan0: associate with <MAC address removed> (try 1/3)
[  111.911662] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  111.911805] wlan0: associated
[  152.472299] wlan0: Connection to AP <MAC address removed> lost.
[  153.760336] wlan0: authenticate with <MAC address removed>
[  153.780491] wlan0: send auth to <MAC address removed> (try 1/3)
[  153.784915] wlan0: authenticated
[  153.795840] wlan0: associate with <MAC address removed> (try 1/3)
[  153.798924] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  153.799067] wlan0: associated
[  154.920147] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  155.300451] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  159.001618] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  160.844840] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  161.844638] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  164.277113] wlan0: authenticate with <MAC address removed>
[  164.287339] wlan0: send auth to <MAC address removed> (try 1/3)
[  164.290651] wlan0: authenticated
[  164.304492] wlan0: associate with <MAC address removed> (try 1/3)
[  164.310208] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  164.310350] wlan0: associated
[  164.311093] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  172.365470] wlan0: Connection to AP <MAC address removed> lost.
[  173.645576] wlan0: authenticate with <MAC address removed>
[  173.665784] wlan0: send auth to <MAC address removed> (try 1/3)
[  173.729667] wlan0: authenticated
[  173.740805] wlan0: associate with <MAC address removed> (try 1/3)
[  173.743912] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  173.744054] wlan0: associated
[  175.359378] wlan0: Connection to AP <MAC address removed> lost.
[  176.639461] wlan0: authenticate with <MAC address removed>
[  176.659702] wlan0: send auth to <MAC address removed> (try 1/3)
[  176.661346] wlan0: authenticated
[  176.674935] wlan0: associate with <MAC address removed> (try 1/3)
[  176.678031] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  176.678137] wlan0: associated
[  179.015018] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  179.396013] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  179.962180] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  181.772181] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  182.752275] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  185.174729] wlan0: authenticate with <MAC address removed>
[  185.185024] wlan0: send auth to <MAC address removed> (try 1/3)
[  185.186891] wlan0: authenticated
[  185.198296] wlan0: associate with <MAC address removed> (try 1/3)
[  185.205430] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  185.205572] wlan0: associated
[  185.206323] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  283.994280] wlan0: Connection to AP <MAC address removed> lost.
[  285.948036] wlan0: authenticate with <MAC address removed>
[  285.968325] wlan0: send auth to <MAC address removed> (try 1/3)
[  285.969984] wlan0: authenticated
[  285.983563] wlan0: associate with <MAC address removed> (try 1/3)
[  285.993543] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  285.993696] wlan0: associated
[  291.349117] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  291.748901] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  528.107318] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  528.470368] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  529.477359] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  534.022327] wlan0: authenticate with <MAC address removed>
[  534.042504] wlan0: send auth to <MAC address removed> (try 1/3)
[  534.044131] wlan0: authenticated
[  534.057800] wlan0: associate with <MAC address removed> (try 1/3)
[  534.060807] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  534.060965] wlan0: associated
[  534.061711] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  549.123173] wlan0: Connection to AP <MAC address removed> lost.
[  550.411253] wlan0: authenticate with <MAC address removed>
[  550.431670] wlan0: send auth to <MAC address removed> (try 1/3)
[  550.437080] wlan0: authenticated
[  550.450699] wlan0: associate with <MAC address removed> (try 1/3)
[  550.454542] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  550.454649] wlan0: associated
[  556.099826] wlan0: Connection to AP <MAC address removed> lost.
[  557.387803] wlan0: authenticate with <MAC address removed>
[  557.408008] wlan0: send auth to <MAC address removed> (try 1/3)
[  557.409667] wlan0: authenticated
[  557.423265] wlan0: associate with <MAC address removed> (try 1/3)
[  557.426332] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  557.426474] wlan0: associated
[  561.086965] wlan0: Connection to AP <MAC address removed> lost.
[  562.367054] wlan0: authenticate with <MAC address removed>
[  562.387297] wlan0: send auth to <MAC address removed> (try 1/3)
[  562.392445] wlan0: authenticated
[  562.406490] wlan0: associate with <MAC address removed> (try 1/3)
[  562.411945] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=11)
[  562.412088] wlan0: associated
[  568.756975] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  569.142068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2420.569300] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2423.044136] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2426.573279] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2427.611853] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2430.045469] wlan0: authenticate with <MAC address removed>
[ 2430.055693] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2430.068563] wlan0: authenticated
[ 2430.080967] wlan0: associate with <MAC address removed> (try 1/3)
[ 2430.084091] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[ 2430.084233] wlan0: associated
[ 2430.084993] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


**************** done ********************







```

---

### Post by varunendra on 2013-05-11
> **meebix said:**
> ```

**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"Friedman"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          **Link Quality=[COLOR="#FF0000"]20[/COLOR]/70  Signal level=[COLOR="#FF0000"]-90 dBm[/COLOR]  **
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

```
With that kind of link quality, I am amazed that you can even connect! What is the distance of the router/access-point from the notebook? Is it the same access-point that connects fine in windows? What is the signal strength in windows when connected to the same access-point?

Please also post -
```
modinfo rtl8192ce
```

---

### Post by meebix on 2013-05-11
I am pretty much at the furthest point from the router in the house :-&

But, again, the Windows machine surfs the web without a problem - and that is really all I need.  The windows machine is in the same exact location as the Linux machine.  Yes, they both connect to the same access point.

The windows machine from this location gets about 80% at all times.

```

filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8371CA3A9E899B11125FFDE
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.5.0-17-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)



```

---

### Post by varunendra on 2013-05-11
We created a config file earlier. I'm wondering if it is needed anymore. Let's remove it for now and see if defaults can deliver any better connectivity -
```
sudo rm /etc/modprobe.d/rtl8192ce.conf
```

Then do -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

If that doesn't help, or even worsens the situation, please post -
```
grep -iR [0-9a-z] /sys/module/rtl8192ce/parameters/
```

With this, I'm off to bed now. It's already 12:12 am here, and I'm too tired to continue. See you tomorrow! :)

---

### Post by meebix on 2013-05-11
Unfortunately, that didn't help.

Here is the results from the command:

/sys/module/rtl8192ce/parameters/ips:Y
/sys/module/rtl8192ce/parameters/fwlps:Y
/sys/module/rtl8192ce/parameters/swenc:N
/sys/module/rtl8192ce/parameters/swlps:N


Thanks for your continued help!  Talk to you tomorrow.

---

### Post by meebix on 2013-05-12
Any way I can use the Windows drivers in Linux?

---

### Post by meebix on 2013-05-12
Went with a clean install of the system.

Downloaded the latest Realtek driver from here:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
In my case that happens to be:  RTL8192CE-VA4 for the Rosewill Wireless RNX-N250PCe 

Put the file in my Home directory. 

Followed the instructions from the ReadMe file and what Varun laid out.

1.  Right click TAR file and "Extract Here" (in Home directory)
2.  Go to terminal and CD into that newly created folder
3.  sudo su
4.  make
5.  make install
6.  reboot

*Worth noting, I ditched WICD (due to issues last time I tried the Realtek driver) and am sticking with the NetworkManager.*

My wireless signal is representative of what I think it should be.   Wireless is working well at the moment.  I am hopeful I am on the right  track this time with the Realtek driver from OEM.

I will post back in a week or so.

---

### Post by meebix on 2013-05-14
Don't even have to wait a week.  I can't believe it took me this long to use the OEM driver.  Working like a charm.

Solved.

---

### Post by varunendra on 2013-05-15
> **meebix said:**
> Don't even have to wait a week.  I can't believe it took me this long to use the OEM driver.
Maybe because you were stuck with someone trying to do 'experiments' with the native driver (hoping an easier, permanent fix) :P

But anyway, -
> Working like a charm.

Solved.
..so sweet to the ears!

Just be aware, you will have to rebuild and reinstall the driver with every kernel upgrade. Assuming newer kernel headers will get installed by default, then-
[INDENT]extract the files (to start fresh) > 'cd' to the extracted directory > sudo su > make > make install > exit[/INDENT]
..followed by a reboot if necessary should be all that should be needed.

Another note - the path to the extracted files should 'never' contain spaces, else the build will fail. Just an extra tip :)

---

### Post by meebix on 2013-05-18
Thanks for all your help Varun!!

---

### Post by varunendra on 2013-05-18
> **meebix said:**
> Thanks for all your help Varun!!

You're welcome ! I'm glad I could :)

I hope you're posting this with a relatively pleasant experience with your wireless now. :)

---

