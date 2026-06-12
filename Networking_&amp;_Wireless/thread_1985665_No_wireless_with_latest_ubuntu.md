---
title: "No wireless with latest ubuntu"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by dannodan2008 on 2012-05-23
Hi People,
I am praying that some can help me here. Since i have upgraded to 12.04 my wireless has just dissapeared. I have had a few very helpfull people try to solve this for me but it seems i was asking in the wrong forum. I was told to post the thread in this "networking" forum.
[http://ubuntuforums.org/showthread.php?p=11959899#post11959899](http://ubuntuforums.org/showthread.php?p=11959899#post11959899)

Its a large thread but if there is any more data you need just ask. I do feel like i need to make clear to you guys as everyone here seems to be a ubuntu pro lol :-) and that is my ubuntu knowledge is literally copy and paste the commands you guys give me and i post the outcome. I absolutely hate windows and love ubuntu. Please be patient with me guys and thank you for taking the time to read this.
Regards
A very frustrated Danno

---

### Post by chili555 on 2012-05-24
Patience R Us!

Please post the outcome of these two terminal commands:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by dannodan2008 on 2012-05-24
> **chili555 said:**
> Patience R Us!

Please post the outcome of these two terminal commands:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Wow Chilli555 ive heard lots about you, You have been recomended by alot of people. Thank you. Unfortunately it looks like i will be stuck at work tonight so i will not be able to respond untill tomorrow evening with the results. And thanks again.
Talk Tomorrow 
Danno

---

### Post by chili555 on 2012-05-24
Was anything you heard about me good? I guess you didn't hear from my ex-wife's lawyer!

I look forward to your report. Have a good day and night at work!

---

### Post by dannodan2008 on 2012-05-24
Hi Westie and Chilli, 
                                       I managed to get home from work so here are your commands that you requested. Ill do westies 1st. so ..

```
danno@danno-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux danno-laptop 3.0.0-19-generic-pae #33-Ubuntu SMP Thu Apr 19 20:59:10 UTC 2012 i686 i686 i386 GNU/Linux
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145e]
    Kernel modules: brcmsmac
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:365c]
    Kernel driver in use: r8169
danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 064e:c107 Suyin Corp. HP webcam [dv6-1190en]
Bus 002 Device 004: ID 03f0:231d Hewlett-Packard 
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
udf                    83826  1 
dm_crypt               22565  0 
bnep                   17923  2 
rfcomm                 38408  12 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  4 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
btusb                  18160  2 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  3 
snd_hda_codec          91888  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                63474  0 
serio_raw              12990  0 
intel_ips              17753  0 
uvcvideo               67271  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
bluetooth             148869  23 bnep,rfcomm,btusb
ir_nec_decoder         12490  0 
rc_rc6_mce             12454  0 
ene_ir                 18214  0 
rc_core                25797  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
snd_rawmidi            25241  1 snd_seq_midi
wmi                    18744  1 hp_wmi
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
snd_seq_midi_event     14475  1 snd_seq_midi
jmb38x_ms              17406  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
memstick               15857  1 jmb38x_ms
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
r8169                  47200  0 
ahci                   21634  3 
libahci                25761  1 ahci
firewire_ohci          35846  0 
sdhci_pci              13658  0 
firewire_core          56937  1 firewire_ohci
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  2 udf,firewire_core
video                  19069  0 
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:9E:CE:EB:6C

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.78
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ sudo iwlist scan
[sudo] password for danno: 
Sorry, try again.
[sudo] password for danno: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ dmesg | grep wl
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv7 Notebook PC/365C, BIOS F.13 12/03/2009
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ lsmod | grep wl
danno@danno-laptop:~$ lsmod | grep wl
danno@danno-laptop:~$ lsmod | grep wl
danno@danno-laptop:~$ 

```

I think thats all westie although as you can see the lsmod | grep wl didnt return anything.
 And Chilli, 
                     Lol yes it was all good i heard about you.  Here are the commands you requested,

```
danno@danno-laptop:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
danno@danno-laptop:~$ 

```

and the rfkill list all i have posted just aboove, should be near the comp tonight so youll get a quick reply to anything else you need. Cheers for looking guys :-)
Danno

---

### Post by dannodan2008 on 2012-05-24
I thought the update we just recieved from ubuntu might be the key when i saw all the networking goodies inside but as you can see in the pic. Same error. Unable to activate

---

### Post by chili555 on 2012-05-24
Please make sure the ethernet is hooked up and connected and, in a terminal, do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Now detach the ethernet and use your wireless to tell us how it's working.

---

### Post by dannodan2008 on 2012-05-24
> **chili555 said:**
> Please make sure the ethernet is hooked up and connected and, in a terminal, do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Now detach the ethernet and use your wireless to tell us how it's working.

Hi Chilli,
```
danno@danno-laptop:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2
  liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf
  libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,202 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 254266 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 3.0.0-19-generic-pae and 3.2.0-24-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ sudo modprobe wl
[sudo] password for danno: 
FATAL: Module wl not found.
danno@danno-laptop:~$ 


```

---

### Post by dannodan2008 on 2012-05-24
Also still no wireless option in menu and cannot activate driver :-(

---

### Post by km3952 on 2012-05-24
I'm looking on here, what computer & model do you have?

[http://drivers.downloadatoz.com/download/212,broadcom-wireless-lan-driver.html](http://drivers.downloadatoz.com/download/212,broadcom-wireless-lan-driver.html)

---

### Post by km3952 on 2012-05-24
> Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 3.0.0-19-generic-pae and 3.2.0-24-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-24-generic
Done.

This looks, to me, like you are attempting to build the module from source code without having the kernel headers or source code on your machine. Am I right?

---

### Post by dannodan2008 on 2012-05-24
> **km3952 said:**
> I'm looking on here, what computer & model do you have?

[http://drivers.downloadatoz.com/download/212,broadcom-wireless-lan-driver.html](http://drivers.downloadatoz.com/download/212,broadcom-wireless-lan-driver.html)

I have a HP Pavillion DV7 3111ea . Thanks ill take a look.Most of it looks as if its about 11.10 and my wireless was fine then.But i think we have covered most of the error fixes allready  but i will read into it more :-)

---

### Post by chili555 on 2012-05-24
Well! What a stubborn little module! Please try:```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install linux-headers-generic-pae
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```I suspect some of the confusion is that you have kernels for pae and non-pae and headers for some but evidently not both.> Building for 3.0.0-19-generic-pae and 3.2.0-24-generic Once we conquer the present task, you might correct that by removing those you don't really want to use. If you have more than 2 Gb of RAM, I think you'd want all pae. If so, be sure you have and are running the most current pae before you start amputating kernels. If in doubt, *STOP* and ask.

You can also safely do:```
sudo apt-get autoremove
```

---

### Post by dannodan2008 on 2012-05-24
> **km3952 said:**
> This looks, to me, like you are attempting to build the module from source code without having the kernel headers or source code on your machine. Am I right? 
 I dont know mate. Its embarrasing. Im totally numb to this, I was lost when you got to source code...If a command can give you anymore info chuck it at me  please..

---

### Post by km3952 on 2012-05-24
Logging off now;

You may find something here,

[http://wiki.debian.org/Broadcom](http://wiki.debian.org/Broadcom)

---

### Post by dannodan2008 on 2012-05-24
> **chili555 said:**
> Well! What a stubborn little module! Please try:```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install linux-headers-generic-pae
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```I suspect some of the confusion is that you have kernels for pae and non-pae and headers for some but evidently not both. Once we conquer the present task, you might correct that by removing those you don't really want to use. If you have more than 2 Gb of RAM, I think you'd want all pae. If so, be sure you have and are running the most current pae before you start amputating kernels. If in doubt, *STOP* and ask.

You can also safely do:```
sudo apt-get autoremove
```


Here ya go chilli, Still no joy im afraid 
```
danno@danno-laptop:~$ sudo apt-get remove bcmwl-kernel-source
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2
  liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf
  libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,252 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 254265 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ sudo apt-get install linux-headers-generic-pae
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic-pae is already the newest version.
The following packages were automatically installed and are no longer required:
  libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2
  liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf
  libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ sudo apt-get install linux-headers-generic
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2
  liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf
  libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libindicator6 libapt-pkg4.11 libglew1.5 libglewmx1.5 libgssdp-1.0-2
  liblwres60 libept1 gir1.2-dee-0.5 zeitgeist-extension-fts libblas3gf
  libquvi0 libattica0 libdb4.8 python-wnck libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,202 kB of archives.
After this operation, 3,252 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 254216 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 3.0.0-19-generic-pae and 3.2.0-24-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ sudo modprobe wl
[sudo] password for danno: 
FATAL: Module wl not found.
danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ sudo apt-get autoremove
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gir1.2-dee-0.5 libapt-pkg4.11 libattica0 libblas3gf libdb4.8 libept1
  libglew1.5 libglewmx1.5 libgnome-desktop-2-17 libgssdp-1.0-2 libindicator6
  liblwres60 libquvi0 python-wnck zeitgeist-extension-fts
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
After this operation, 6,855 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 254265 files and directories currently installed.)
Removing gir1.2-dee-0.5 ...
dpkg: warning: while removing gir1.2-dee-0.5, directory '/usr/lib/pymodules/python2.7' not empty so not removed.
Removing libept1 ...
Removing libapt-pkg4.11 ...
Removing libattica0 ...
Removing libblas3gf ...
Removing libdb4.8 ...
Removing libglew1.5 ...
Removing libglewmx1.5 ...
Removing libgnome-desktop-2-17 ...
Removing libgssdp-1.0-2 ...
Removing libindicator6 ...
Removing liblwres60 ...
Removing libquvi0 ...
Removing python-wnck ...
Removing zeitgeist-extension-fts ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
danno@danno-laptop:~$ 

```

---

### Post by chili555 on 2012-05-24
Please post:```
uname -r
sudo dpkg -s linux-headers-`uname -r` | head -n3
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

---

### Post by dannodan2008 on 2012-05-24
> **chili555 said:**
> Please post:```
uname -r
sudo dpkg -s linux-headers-`uname -r` | head -n3
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

```
danno@danno-laptop:~$ uname -r
3.0.0-19-generic-pae
danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ sudo dpkg -s linux-headers-`uname -r` | head -n3
[sudo] password for danno: 
Package `linux-headers-3.0.0-19-generic-pae' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
danno@danno-laptop:~$ 
```

---

### Post by chili555 on 2012-05-24
> Package `linux-headers-3.0.0-19-generic-pae' is not installed Weird. As I said before, let's get the wireless working and clean up later. Please do:```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```We hope for a more harmonious result.

---

### Post by irv on 2012-05-24
I don't know if your problem was the same as mine, but if it is, Post #25 at this link did the trick for me. I keep this link handy because anytime I install any flavor of Ubuntu I need to do this.
[http://ubuntuforums.org/showthread.php?t=1742147&page=3]("http://ubuntuforums.org/showthread.php?t=1742147&page=3")

---

### Post by dannodan2008 on 2012-05-24
> **chili555 said:**
> Weird. As I said before, let's get the wireless working and clean up later. Please do:```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```We hope for a more harmonious result.

```
danno@danno-laptop:~$ sudo apt-get install linux-headers-`uname -r`
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.0.0-19-generic-pae
E: Couldn't find any package by regex 'linux-headers-3.0.0-19-generic-pae'
danno@danno-laptop:~$ 


```

```
danno@danno-laptop:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,202 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 254114 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 3.0.0-19-generic-pae and 3.2.0-24-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
danno@danno-laptop:~$ 

```

```
danno@danno-laptop:~$ sudo modprobe wl
[sudo] password for danno: 
FATAL: Module wl not found.
danno@danno-laptop:~$ 

```
I dont understand any of this code but im guessing "FATAL" isnt good lol

---

### Post by chili555 on 2012-05-24
> **irv said:**
> I don't know if your problem was the same as mine, but if it is, Post #25 at this link did the trick for me. I keep this link handy because anytime I install any flavor of Ubuntu I need to do this.
[http://ubuntuforums.org/showthread.php?t=1742147&page=3]("http://ubuntuforums.org/showthread.php?t=1742147&page=3")Thank you, Irv but you have a different device, a 4311. Danno has:> Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

---

### Post by praseodym on 2012-05-24
Hi,

if I see it right, you have booted into the "old" kernel 3.0 from 11.10, right? Therefore the kernel-headers are not available anymore, because you upgraded to 12.04, kernel 3.2:
> Module build for the [COLOR="Red"]currently[/COLOR] running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-24-generic
Did you install Startupmanager? Still 3.0 the default kernel to boot?

Reboot, press the SHIFT button and choose the kernel 3.2. After that it should work with Chili555's tip. The following modules need to be blacklisted first:
```
echo -e "blacklist bcma\nblacklist brcm80211\nblacklist brcmsmac" | sudo tee /etc/modprobe.d/blacklist-bcm.conf 
```This is one line, you better copy/paste it.

Show after that:
```

lsmod
iwconfig
rfkill list
```

---

### Post by chili555 on 2012-05-24
> **dannodan2008 said:**
> 
I dont understand any of this code but im guessing "FATAL" isnt good lolIt means you are causing old Chili to curse and take up strong drink. It also means you are running a kernel, also known as linux-image that came and went and is no longer available for installation and also for which there are no available headers. The current latest linux-image is 3.2.0-24-generic-pae, so you are a bit behind. Please try:```
sudo apt-get update && sudo apt-get upgrade
```Among the several packages that will be updated are linux-image and linux-headers. Reboot and boot into the latest kernel. Then, *finally*, you should be able to:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Pouring another one...

---

### Post by dannodan2008 on 2012-05-24
> **chili555 said:**
> It means you are causing old Chili to curse and take up strong drink. It also means you are running a kernel, also known as linux-image that came and went and is no longer available for installation and also for which there are no available headers. The current latest linux-image is 3.2.0-24-generic-pae, so you are a bit behind. Please try:```
sudo apt-get update && sudo apt-get upgrade
```Among the several packages that will be updated are linux-image and linux-headers. Reboot and boot into the latest kernel. Then, *finally*, you should be able to:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Pouring another one...

Ok, im so sorry. i should of said sooner, When i select 3.2.0-24-generic-pae at the dual boot screen it black screens and does nothing. So i have always selected 3.0.0-19-generic-pae thinking i was ending up in the same place.I appologise for wasting your time guys :-( Is this an easy fix ? but please bear in mind im just lost when were talking about kernals, kernal headers
Danno

---

### Post by dannodan2008 on 2012-05-24
So am i right in guessing the second number in that chain is the kernal your using ? and im using the very 1st one . just guessing really. And is it a problem that i cant access 3.2.0-24-generic-pae

---

### Post by darkod on 2012-05-24
Have you tried using nomodeset? If running nvidia that usually helps.

In the grub boot menu, highlight the ubuntu entry (the 3.2.0 one), and hit 'e' for edit. That will show the boot lines.

With the arrows move the cursor towards the end of the line starting with linux. Before 'quiet splash' add nomodeset.
Press Ctrl + X to boot.

Does that load the desktop correctly?

If it does, you might wanna activate the video driver offered in Additional Drivers (if there is such). Once you have this video problem sorted, continue booting 3.2.0 and look into the wi-fi problem.
Who knows, the STA driver might activate without problems when you have 3.2.0 booted.

---

### Post by dannodan2008 on 2012-05-24
back to the point. Do you guys still want the commands even tho im in 3.0.0-19-generic-pae ?

---

### Post by dannodan2008 on 2012-05-24
> **darkod said:**
> Have you tried using nomodeset? If running nvidia that usually helps.

In the grub boot menu, highlight the ubuntu entry (the 3.2.0 one), and hit 'e' for edit. That will show the boot lines.

With the arrows move the cursor towards the end of the line starting with linux. Before 'quiet splash' add nomodeset.
Press Ctrl + X to boot.

Does that load the desktop correctly?

If it does, you might wanna activate the video driver offered in Additional Drivers (if there is such). Once you have this video problem sorted, continue booting 3.2.0 and look into the wi-fi problem.
Who knows, the STA driver might activate without problems when you have 3.2.0 booted.

Hi again Darko,
                              Wow, right ill write this down and do what you ask (after a much needed cigarette). If it doesnt boot will i still be able to boot this one ?. Also yes i have NVidia Geforce card that has always needed drivers. It has never ever in ubuntu worked i dont think. So ill post the outcome soon providing i have not made my laptop go bang .

---

### Post by darkod on 2012-05-24
Don't worry, nothing can get broken by that try. When you edit like that it's a one time thing, nothing stays permanent. That's why you would still need to activate the driver if it boots OK once.

Adding the nomodeset parameter like that is temporary, just for that boot.

You can still boot the 3.0.0 the next time if nomodeset doesn't work.

But now with the new info it seems it will.

---

### Post by chili555 on 2012-05-24
I'm going to stand by; it seems that darkod can help you get the latest kernel going. Once done, I'm sure the wireless driver will install with no problems.

---

### Post by dannodan2008 on 2012-05-24
> **darkod said:**
> Don't worry, nothing can get broken by that try. When you edit like that it's a one time thing, nothing stays permanent. That's why you would still need to activate the driver if it boots OK once.

Adding the nomodeset parameter like that is temporary, just for that boot.

You can still boot the 3.0.0 the next time if nomodeset doesn't work.

But now with the new info it seems it will.

Ok so i just added nomodeset and there was a difference but it wasnt successfull. Now the Ubuntu startup logo appears for approx 30-40sc (alot longer than norm) then goes black screen. I can hear ubuntu loading -login sounds etc. :-(

---

### Post by dannodan2008 on 2012-05-24
> **chili555 said:**
> I'm going to stand by; it seems that darkod can help you get the latest kernel going. Once done, I'm sure the wireless driver will install with no problems.

Thanks for your time chilli. I may call on you if the wireless is still messed up after i manage to get the new kernal :-)
Cheers Chilli

---

### Post by chili555 on 2012-05-24
> **dannodan2008 said:**
> Thanks for your time chilli. I may call on you if the wireless is still messed up after i manage to get the new kernal :-)
Cheers ChilliNo problem. I'll be watching and I'll jump in when the kernel issue is solved.

---

### Post by darkod on 2012-05-24
> **dannodan2008 said:**
> Ok so i just added nomodeset and there was a difference but it wasnt successfull. Now the Ubuntu startup logo appears for approx 30-40sc (alot longer than norm) then goes black screen. I can hear ubuntu loading -login sounds etc. :-(

Oh man. That should usually do it.

OK, thos time add nomodeset again but delete 'quiet splash', both of them. In that case instead of the ubuntu screen, there will be text scrolling by while trying to boot. At the moment it stops/blocks, watch out about any specific error messages. That could give as a lead.

Try to write them or remember them, and post them if there is anything specific.

---

### Post by jkorten on 2012-05-26
As an FYI - I have an eeepc net top and I disabled my wireless adaptor while trying to get network traffic low in my house (testing a blue ray connection to wlan) and in 12.04 it turns out there is no way to get back your wirless adapter through the GUI.

What I ended up doing was issueing the "rfkill list all" command in a terminal window - saw that it said the following:

0: eeepc-wlan Wireless LAN
    Soft blocked: yes
    Hard blocked: no

I then typed (using wisdom gained from rfkill --help)

rfkill unblock 0

and I am now up and running again.

Probably the lack of a way to re-enable the wireless adaptor should be listed as a bug?

Regards,


Jerry

---

### Post by chili555 on 2012-05-26
> **jkorten said:**
> As an FYI - I have an eeepc net top and I disabled my wireless adaptor while trying to get network traffic low in my house (testing a blue ray connection to wlan) and in 12.04 it turns out there is no way to get back your wirless adapter through the GUI.

What I ended up doing was issueing the "rfkill list all" command in a terminal window - saw that it said the following:

0: eeepc-wlan Wireless LAN
    Soft blocked: yes
    Hard blocked: no

I then typed (using wisdom gained from rfkill --help)

rfkill unblock 0

and I am now up and running again.

Probably the lack of a way to re-enable the wireless adaptor should be listed as a bug?

Regards,


JerryI'm fairly confident it's a bug in the module acer-wmi. I suggest you file a bug: [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

