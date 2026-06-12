---
title: "Weak WI-FI signal: HP Pavilion Sleekbook 15-b047, Ralink RT3290 PCI, Ubuntu 13.04 x64"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by Marzian on 2013-04-21
Hello,
The kernel of Ubuntu 13.04 (3.8.0-19-generic x86_64) does recognize this wireless card, but native support is still lacking ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)) and so to get it working I had to download the driver (rt3290.bin) and move it to /lib/firmware. 

(Ubuntu 12.10 did not even recognize the card and - after an unsuccesful attempt just updating the kernel - I decided to install 13.04 before the official relase)

Unfortunately, while other users (see discussion on Launchpad) were able to get it working this way, my connection in the room where I use the laptop has always a poor signal, after a while it disconnects and is often slow, while in Windows 8 it worked fine. Moreover, the WI-FI hotekey (F12) is not working.

So, do I have any way to understand if the problem is due to the driver or the configuration?

Somebody says to just try wicd instead of network-manager, but considering this other unresolved bug ([https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529)), right now it doesn't seem the right solution. And I already tried disabling the power managment of the card, but to no avail.

If the problem is in the driver, I could compile the official one from scatch, but I'm getting errors like this one, and I can't find suggestions about how to solve 'em:

```
DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:71:1: error: &#8216;__mod_pci_device_table&#8217; aliased to undefined symbol &#8216;rt2860_pci_tbl&#8217;
cc1: some warnings being treated as errors
```

The router (Netgear DG834G) is in the floor upstairs, and I already tried putting the antenna horizontal and pointing in the direction of the room. Is it right?

Thank you very much for your time,

-- Carlo

```
$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"OrionSRL"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:C0:C6:BA   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:18  Invalid misc:3   Missed beacon:0
```

```
$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:C0:C6:BA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"OrionSRL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f24e9fa33
                    Extra: Last beacon: 38628ms ago
                    IE: Unknown: 00084F72696F6E53524C
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: a4:17:31:b1:76:2d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-19-generic firmware=0.37 ip=192.168.0.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:52510000-5251ffff
```

```
$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
ext2                   72837  1 
joydev                 17377  0 
arc4                   12615  2 
rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
hp_accel               26012  0 
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
i915                  600351  3 
coretemp               13355  0 
snd_rawmidi            30180  1 snd_seq_midi
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
lis3lv02d              20111  1 hp_accel
input_polldev          13896  1 lis3lv02d
drm_kms_helper         49394  1 i915
wmi                    19070  1 hp_wmi
uvcvideo               80847  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
video                  19390  1 i915
videobuf2_vmalloc      13056  1 uvcvideo
snd_timer              29425  2 snd_pcm,snd_seq
cfg80211              510937  2 mac80211,rt2x00lib
drm                   286313  4 i915,drm_kms_helper
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
mac_hid                13205  0 
eeprom_93cx6           13344  1 rt2800pci
psmouse                95870  0 
lpc_ich                17061  0 
soundcore              12680  1 snd
serio_raw              13215  0 
crc_ccitt              12707  1 rt2800lib
mei                    41158  0 
i2c_algo_bit           13413  1 i915
microcode              22881  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
r8169                  67446  0 
ahci                   25731  3 
libahci                31364  1 ahci
```

---

### Post by Marzian on 2013-04-22
Hello,
I added some more information to the fist post. Any suggestions, at least about the compiling error?

---

### Post by kurt18947 on 2013-04-22
I have a generic USB adapter using a Ralink RT5370 that's kinda slow with mediocre signal strength.  Disabling hardware encryption seems to help this device.  The module in use is rt2800usb.  I created the following file: 
```
/etc/modprobe.d/rt2800usb.conf
```
That file consists of one line:
```
options rt2800usb nohwcrypt=y
```

Save and reboot.  This doubled the test speed on a couple internet speed test sites and the response to clicks seems much quicker.  It's still not great but it seems better.  Worth a try and if it doesn't help you can always delete the file and reboot.

---

### Post by Marzian on 2013-04-22
Thanks for the answer! Just tried (with the rt2800pci module), but I can't see any difference.

---

### Post by kurt18947 on 2013-04-22
> **Marzian said:**
> Thanks for the answer! Just tried (with the rt2800pci module), but I can't see any difference.

Sorry to hear it.  I don't know of any 100% guaranteed-to-work solution.  Disabling power management and hardware encryption are the only things I know to try.   I was thinking about replacing the MiniPCIe card in your HP with one that is more linux friendly. I think (not certain though) that HP and Lenovo are fussy about which WiFi cards they play nice with.  The BIOSs only recognize certain cards.

---

### Post by Marzian on 2013-04-22
After all the money spent on this laptop I'd prefer to avoid it... But if we are in the worst case scenario, then suggestions for almost-guaranteed-to-work miniPICIe or USB cards are welcome.

---

### Post by Marzian on 2013-04-24
One last chance... I forget to add the dmesg. Here it is, in case someone would be so kind to have a look: [http://paste.ubuntu.com/5599059/](http://paste.ubuntu.com/5599059/)

---

### Post by malkdude on 2013-05-01
I am facing similar issues with a RT5390 card. The problems only appeared after I updated from 12.10 to 13.04. More specifically, if the signal strength is week, it fails to connect. If the signal strength is strong, it connects with no problem. Installing the Ralink driver on kernel 3.8.0-19 on ubuntu 13.04 led to errors. Indeed after I entered make, I ran into compilation errors, which after some tracing, were related to __devinit and __devexit, which somehow the new kernel doesn't like. And my knowledge of how drivers work is very poor to try and fix it. I am just hoping that in the next kernel update, the problem will be gone, because it has been reported as a bug. Even buying an external usb Realtek card did not fix the problem.

---

### Post by malkdude on 2013-05-01
Solved for me! NOTE THAT MY CARD IS RT5390 WHILE YOURS IS RT3290. So please be careful that you need to download the right driver, and the right patch too. I am not sure if the patch for your driver is available.

In any case, I followed ukbeast's solution for installing the ralink driver:

[FONT=arial]http://ubuntuforums.org/showthread.php?t=2138302&p=12628115#post12628115

(post #4). After that, all I did was to blacklist the drivers such as rt2800pci which came with the distribution, by doing the following:

[/FONT]sudo gedit /etc/modprobe.d/blacklist.conf

At the end of the file, add these lines:

# Blacklist conflicting kernel modules
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

(I took that from the second half of the solution in
[http://www.upubuntu.com/2012/02/how-to-install-drivers-for-ralink.html](http://www.upubuntu.com/2012/02/how-to-install-drivers-for-ralink.html)
but I did not use his ppa).

After that, I rebooted, and it worked fine for me, and my rt5390. Thank you ukbeast.:guitar:

---

### Post by Marzian on 2013-05-11
Hello,
I upgraded to Kernel 3.9 without noticing any difference (except for an unrelated but important bug-fix affecting the SD Card: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/221489](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/221489)) and... I also spent more money on a N 300 D-Link Mini Adapter, which works even WORSE than the miniPCI. This is so annoying and frustrating... :-(

Anyway, I tried again to compile the proprietary driver, but I'm still getting the errors as in the first post. Do I need a patch like that for rt5390? Where could I find it? Or is it the same?

---

### Post by malkdude on 2013-05-11
Hi Marzian,

Ok I will try to put a complete solution (based on post #4 in [http://ubuntuforums.org/showthread.php?t=2138302&p=12628115#post12628115](http://ubuntuforums.org/showthread.php?t=2138302&p=12628115#post12628115)).

1. download driver [http://www.mediatek.com/_en/07_downl...il.php?sn=5001]("http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001")
2 tar -xvf  /home/ukbeast/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.  bz2.bz2
(of course replace the directory with the directory where you put the driver file)
3 cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
4 download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
5 patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to pci_main_dev.c)
6 make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
7 make
8 sudo make install
9 sudo gedit /etc/modprobe.d/blacklist.conf

At the end of the file, add these lines:

# Blacklist conflicting kernel modules
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta
10 restart

I hope this helps! It worked for me (I am using 64-bit ubuntu 13.04 and rt5390 card).

---

### Post by Marzian on 2013-05-11
Hi malkdude and thanks for your time,
With the patch I was finally able to compile and I had a moment of elation when I saw the signal strength at his peak (never happened), but it lasted only a few seconds before... kernel panic. And kernel panic again after rebooting or shutting down and starting up. I was able to restore everything only blacklisting the newly installed module and de-blacklisting the rt2800pci by using the root prompt shell in the recovery mode :-(

Later, I also tried installing this driver in the kernel 3.8 (I'm using 3.9) but even in that case I got a kernel panic.

---

### Post by malkdude on 2013-05-11
Hi Marzian,

I am so sorry about that. Note that your card is different from mine. You have a RT3290 PCI and I have an RT5390. I did come across this kernel panic bug on the launchpad website, but I did not experience that... I don't know what else to suggest. You did download the right driver for your card, I assume. Maybe the patch for your driver is also different. I see that others had the kernel panic problem with that driver, see for instance

[http://ubuntuforums.org/showthread.php?t=2109571](http://ubuntuforums.org/showthread.php?t=2109571)

I cannot help though because I did not face this problem.

---

### Post by chili555 on 2013-05-12
@Marzian--

May I see:```
lspci -nn | grep 0280
uname -a
```Thanks.

---

### Post by Marzian on 2013-05-12
```
lspci -nn | grep 0280
01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
```

```
uname -a
Linux HP-PS15-PC 3.9.0-030900-generic #201304291257 SMP Mon Apr 29 16:58:15 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
(I'm using this kernel because the previous ones didn't recognize the SD card reader)

---

### Post by chili555 on 2013-05-12
You might download this: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8.3/compat-drivers-3.8.3-2-snpu.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8.3/compat-drivers-3.8.3-2-snpu.tar.bz2)

Get it to your desktop. Right-click it and select 'Extract Here.' Now, with a temporary wired ethernet connection, do:```
sudo apt-get install build-essential linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Since you have a custom kernel, you may need to go to the locaton where you got the linux-image and download and install the headers.```
cd Desktop/compat-drivers-3.8.3-2-snpu
./scripts/driver-select rt2x00
make
```...and if there are no errors:```
sudo make install
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
```Any improvement?

---

### Post by Marzian on 2013-05-12
```
sudo apt-get install build-essential linux-headers-`uname -r
```
build-essential is already the newest version.
linux-headers-3.9.0-030900-generic is already the newest version.

```
cd Desktop/compat-drivers-3.8.3-2-snpu
./scripts/driver-select rt2x00
make
```

I'm getting errors, like:

warning: &#8216;__mesh_path_del&#8217; defined but not used [-Wunused-function]
warning: control reaches end of non-void function [-Wreturn-type]

---

### Post by chili555 on 2013-05-12
Please try this version instead: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2-su.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2-su.tar.bz2)

---

### Post by Marzian on 2013-05-13
OK, I was able to compile, install and give sudo modprobe -r rt2800pci, but... 

"sudo modprobe rt2800pci" only said Invalid Argument and to get the connection again I had to reboot.

Now it looks like the same old signal.

---

### Post by chili555 on 2013-05-13
Let's see:```
lsmod | grep rt2
modinfo rt2800pci | head -n5
nm-tool
```We hope we see something like /lib/modules/3.8.0-19-generic/[COLOR="#FF0000"]updates[/COLOR]/drivers/net/wireless/rt2x00/rt2800pci.ko. If so, that is the newer compiled version you are running.

---

### Post by Marzian on 2013-05-13
```
modinfo rt2800pci | head -n5
filename:       /lib/modules/3.9.0-030900-generic/**updates**/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
```

Then it's running, thanks! 
But... I don't know... maybe it's a bit smoother and more stable, but no great difference as I saw after compiling the RT5390 driver, before the kernel panic. About the kernel panic, dotpc said:

> I started having disconnect issues on KDE, which led me to try many other avenues ... eventually leading to Arch Linux and using netcfg.

    Performance is amazing, and I've had ZERO disconnects over many days. This problem seems to be part of network manager after all. Chiec, if you are brave you should try Arch and netcfg (or **maybe wicd in Ubuntu**).
[http://ubuntuforums.org/showthread.php?t=2109571&page=3](http://ubuntuforums.org/showthread.php?t=2109571&page=3)


Alas, as written earlier in this thread, wicd is not working right now ([https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529)).

Are there any other solutions I could try? Else, Il'll just wait and hope for the future

---

### Post by chili555 on 2013-05-13
> **Marzian said:**
> 

Alas, as written earlier in this thread, wicd is not working right now ([https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529)).

Are there any other solutions I could try? Else, Il'll just wait and hope for the futureIf you are really, *really* brave, you could remove NM altogether and use manual methods; i.e. /etc/network/interfaces. If this is a stay at home computer, it works great. If you want to take it down to the coffee shop, it's pretty un-handy.

What do you think?

---

### Post by malkdude on 2013-05-13
Ooh, Chili555 is clearly an experienced linux user but Marzian, if you have never tried to connect without network-manager, this might be tricky, especially for connecting to various different wireless networks. I would take chili555's warning seriously (the "really brave" part). I once messed up my internet connection really badly, and had to use a livecd with chroot and various steps to be able to reinstall network-manager.

From my experience, these issues with my rt5390 card did not arise previously, before I did the upgrade to ubuntu 13.04. And the bad connectivity with weak signals remained with the latest linux-firmware drivers. If it is really an issue with network-manager itself, then I hope that someone would tell the developers of network-manager that (if no one has done so already).

As a side note, wicd does not work for me now, because of a bug (cannot start wicd-daemon), and in fact, it is after installing it and removing network-manager that I was left without internet (and I had never connected to the internet by manually editing configuration files before), 

If you do want to attempt Chili555's suggestion, you should first learn how to modify the networking configuration files and then, test it by temporarily disabling network-manager (not uninstalling it), via the following command

sudo service network-manager stop

and then to restart it

sudo service network-manager start

(anyway, just some words of caution, if it is not too late)

---

### Post by Marzian on 2013-05-15
Ok, I have been able to both start wicd (using the fix provided here: [https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529/comments/22](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529/comments/22)) and /etc/network/interfaces (which is fine, since I use this laptop almost only at home). But in both cases the rt5390 driver doesn't work at all: it just says something like "no network", while in network-manager works fine, before going in kernel panic.

Bottom line: whether it's wicd, interfaces or network-manager I have to go back to 2800pci. Anyway, let's see if at least this is possible: when it disconnects, I have to manually give "connect to hidden network" and choose the right one. Could it be possible to automatize this process? Thanks again for your time,

(Honestly, I would have already switched back to Windows 8 for the time being, but such was my faith in Linux that I had the brilliant idea of deleting it and for some reason right now I'm not able to load it from USB. I'm stuck with this un-connection that keeps disconnecting: never been so unlucky with a laptop... HP never more!).

---

### Post by malkdude on 2013-05-15
Hi Marzian,

I have a suggestion, if you are still willing to try something out. Looking at:

[http://elrepo.org/bugs/view.php?id=214](http://elrepo.org/bugs/view.php?id=214)

in particular, post 1520 by Marco, gave me this idea, which may or may not work for you. After you apply the patch, and before you type make and make install, you can try to enable HAS_CFG80211_SUPPORT and HAS_RFKILL_HW_SUPPORT, or at least check that they are enabled. This is done by modifying if needed the relevant lines in the file /os/linux/config.mk (relative to the directory of the unzipped ralink driver). Then try to build the ralink driver, just as above. 

I have a feeling that modifying the file config.mk, before building the driver, might help against kernel panic. I am just not sure which lines have to be modified, for this depend on your hardware of course. For some other users, such as Marco in the post linked above, this is what he changed. I hope this helps...

---

### Post by Marzian on 2013-05-19
Thanks for the suggestion, but in my case enabling HAS_CFG80211_SUPPORT only leads to a compiling error, while HAS_RFKILL_HW_SUPPORT compiled good, but it all ended in the usual kernel panic.

I was hoping in a further kernel update, but that doesn't seem possible, since the next one is for saucy, not for oneiric: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I had decided to use wicd in any case, since the connection looked a bit more stable, but after finding out that wicd does not support vpn, I tried Kubuntu and its network utility: even in this case, kernel panic with the rt3290sta driver, thus suggesting that network-manager is not the problem.

I'll try to move the router nearer or use a repeater and see if that works better.

---

### Post by Marzian on 2013-05-29
Little update: for a time I used a WI-FI repeater (plus compact-drivers and disabling hardware encryption/power managment), but even that proved to be unstable. In the end, I opened the laptop and simply replaced the card (with a Ralink RT3090). Works fine now!

By the way, before testing another card I even tried compiling in 12.04 (LTS), but got the usual kernel panic. Anyway, the problem is not fully recognized, since:

Daniel Manrique (roadmr) on 2013-05-25 
Changed in linux-firmware (Ubuntu):
importance: Undecided &#8594; High 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

And hopefully we'll have a real solution some time in the future.

---

