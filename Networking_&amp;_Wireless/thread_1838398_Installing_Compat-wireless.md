---
title: "Installing Compat-wireless"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by pederbruusgaard on 2011-09-03
Hi,
There is a thread about something pretty similar already, but this is sort of only regarding one specific (and probably the most trivial - I'm very new to Ubuntu (11.04)) aspect of it. That thread can be found here: [http://ubuntuforums.org/showthread.php?t=1739047&page=4](http://ubuntuforums.org/showthread.php?t=1739047&page=4)

So, in short, my Intel Centrino 6205 card doesn't seem to be recognized on my new Lenovo X220. The thread in the link seems to solve that problem, but my problem is that I don't know how to install/run/build it. I've downloaded the file from the link, and extracted it to a folder, and from there I don't know what to do.

Thanks in advance for any help with this!

---

### Post by josephmills on 2011-09-03
hi there to install compat wireless you can go here [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)  and get the daily builds or get the one that fits you, you can find this out by a simple google search  

after Downloading the the the tar you need to unpack it this can be done by right clicking on the  file and exracting it. 

you are then going to need to compile it this is easy to do. You can open up the files and read the READ ME file to tell you how to do this.

or 

open you terminal and cd into the compat file 
then run the command 
```
make
``` 

then 

```
sudo make install
```

then 
```
sudo reboot 
```
and there you go 

I am sure that I am leaving so options out but you can read the README file and learn some more have a good day and enjoy

---

### Post by praseodym on 2011-09-03
Hi,

with 11.04 you can upgrade your drivers from CW via:

```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
But imho its not the newest daily build. Reboot after that.

---

### Post by josephmills on 2011-09-03
> **praseodym said:**
> Hi,

with 11.04 you can upgrade your drivers from CW via:

```
sudo apt-get install linux-backports-modules-cw-[COLOR=Red]2.6.39-natty-generic[/COLOR]
```But imho its not the newest daily build. Reboot after that.


lets make sure that you are using that kernel with the command 
```
uname -a 
```

---

### Post by praseodym on 2011-09-03
Hi,

the red tag shows that these are the modules from kernel 2.6.39 _for_ (the) natty(-kernel) and the common generic architecture. So he/she needs only the **generic** kernel installed, not -pae etc. (Read: you are right in asking "uname -a" in any way ;-) )

---

### Post by pederbruusgaard on 2011-09-03
> **praseodym said:**
> Hi,

with 11.04 you can upgrade your drivers from CW via:

```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
But imho its not the newest daily build. Reboot after that.

Hi!

Thanks for all the help with this issue!
I ran the command you suggested, and something definitely happened, but I still can't see my wireless options. I know there's wifi where I am, but it doesn't detect anything.

Is what I installed with the command the same as compact-wireless? I still don't understand how to do it with the commands in the earlier post. Maybe I'm stupid, but I don't get it :) What does it mean to "cd into the compat file"? The read me file says just about exactly that, but I don't understand what that means...

Thanks!

---

### Post by praseodym on 2011-09-03
Now you upgraded your driver, no need to additionally compile others. Can you show the outputs of:

```
uname -a
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep iwl
lsmod
```

---

### Post by josephmills on 2011-09-03
> **pederbruusgaard said:**
> Hi!

Thanks for all the help with this issue!
I ran the command you suggested, and something definitely happened, but I still can't see my wireless options. I know there's wifi where I am, but it doesn't detect anything.

Is what I installed with the command the same as compact-wireless? I still don't understand how to do it with the commands in the earlier post. Maybe I'm stupid, but I don't get it :) What does it mean to "cd into the compat file"? The read me file says just about exactly that, but I don't understand what that means...

Thanks!
hey there bro you are not stupid but real smart you are starting to use ubuntu and that makes you smart in my book :) 
what I mean by "cd"  change directorys 

so say I am in the terminal and I want to look around

I get something like this 

bob@bob:~$  

if I use the command 
```
ls 
```

that will list all the things in that working directory we can see what directory we are in with the command 
```
pwd
``` which means print working directory 

so lets say that I do a ls and I see the file 
Downloads 

well I want to change directorys into that file called Downloads we use the command 
```
cd /Downloads 
``` 
now if I do a ls then I see a differnt list because I am now in the Downloads directory 

see 
[http://www.youtube.com/watch?v=6kxK8Fqcs5o&feature=related](http://www.youtube.com/watch?v=6kxK8Fqcs5o&feature=related)

---

### Post by pederbruusgaard on 2011-09-03
> **praseodym said:**
> Now you upgraded your driver, no need to additionally compile others. Can you show the outputs of:

```
uname -a
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep iwl
lsmod
```

uname -a:
```
Linux peder-ThinkPad-X220 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 i686 i386 GNU/Linux
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

rfkill list:
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

dmesg | grep iwl:
```
peder@peder-ThinkPad-X220:~$ dmesg grep iwl
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]

```

lsmod:
```
Module                  Size  Used by
hidp                   17993  0 
hid                    77084  1 hidp
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
rfcomm                 38125  8 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
sco                    17827  2 
bnep                   17785  2 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
l2cap                  48656  17 hidp,rfcomm,bnep
thinkpad_acpi          73750  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
i915                  451068  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
binfmt_misc            13213  1 
btusb                  18160  2 
tpm_tis                18089  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              65493  10 hidp,rfcomm,sco,bnep,l2cap,btusb
drm_kms_helper         40745  1 i915
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   184164  4 i915,drm_kms_helper
tpm                    21251  1 tpm_tis
soundcore              12600  1 snd
nvram                  14035  1 thinkpad_acpi
psmouse                59039  0 
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
tpm_bios               13460  1 tpm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
e1000e                138627  0 
ahci                   21591  2 
sdhci_pci              13623  0 
xhci_hcd               72190  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci

```

Again, thank you so much for all the help with this!

---

### Post by pederbruusgaard on 2011-09-03
> **josephmills said:**
> hey there bro you are not stupid but real smart you are starting to use ubuntu and that makes you smart in my book :) 
what I mean by "cd"  change directorys 

so say I am in the terminal and I want to look around

I get something like this 

bob@bob:~$  

if I use the command 
```
ls 
```

that will list all the things in that working directory we can see what directory we are in with the command 
```
pwd
``` which means print working directory 

so lets say that I do a ls and I see the file 
Downloads 

well I want to change directorys into that file called Downloads we use the command 
```
cd /Downloads 
``` 
now if I do a ls then I see a differnt list because I am now in the Downloads directory 

see 
[http://www.youtube.com/watch?v=6kxK8Fqcs5o&feature=related](http://www.youtube.com/watch?v=6kxK8Fqcs5o&feature=related)

Thanks!
This explains a lot of things, actually! :)

---

### Post by josephmills on 2011-09-03
Hi there again 
lets take a look at this out put 
> **pederbruusgaard said:**
> uname -a:
```
Linux peder-ThinkPad-X220 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 i686 i386 GNU/Linux
```

as you can see you are using the 2.6.38-11-generic-pae  kernel so that backport will not work for you. but if you use synaptic to look up the one that pertains to your kernel then it should work 
> 
iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```this is not good this shows that the eth0/ethernet-port  is loaded and so is the loop back or lo. But not the wireless when the wireless is listed you see a wlan0 or ra0 depends on the wireless card  
> 
rfkill list:
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
this is what rfkill list all shows if there is a soft block then there is a software block.
If the hard block says yes then that means that the physical wireless switch is turned off. so it is good that they all say no.  

> Sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```
this shows us that the interfaces do not support scanning I 100% recomend that you NEVER show this to anyone once the wireless is working due to security. But once again we do not see a wireless interface  

> dmesg | grep iwl:
```
peder@peder-ThinkPad-X220:~$ dmesg grep iwl
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]

```
so dmesg or as pronounced dee-message shows all things that the kernel see's on boot grep is a filter so you are asking can I please see all things on boot but please filter it down to iwl . as you can see the kernel dont see anything really for the iwl 


[quote]lsmod:
```
Module                  Size  Used by
hidp                   17993  0 
hid                    77084  1 hidp
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
rfcomm                 38125  8 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
sco                    17827  2 
bnep                   17785  2 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
l2cap                  48656  17 hidp,rfcomm,bnep
thinkpad_acpi          73750  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
i915                  451068  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
binfmt_misc            13213  1 
btusb                  18160  2 
tpm_tis                18089  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              65493  10 hidp,rfcomm,sco,bnep,l2cap,btusb
drm_kms_helper         40745  1 i915
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   184164  4 i915,drm_kms_helper
tpm                    21251  1 tpm_tis
soundcore              12600  1 snd
nvram                  14035  1 thinkpad_acpi
psmouse                59039  0 
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
tpm_bios               13460  1 tpm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
e1000e                138627  0 
ahci                   21591  2 
sdhci_pci              13623  0 
xhci_hcd               72190  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci

```

Again, thank you so much for all the help with this![/quote]so remember how you learned what the command ls does well in linux lingo driver are called mods well sort of . But what this list shows is all mods or moduals that are loaded on the system as of right now. Well bad news I dont see any wireless mods  loaded on the system. 


so this is what we can do. first we need to see some more things from the terminal the first thing is a 
```
lspci -nn
```what this will show is ls like list and pci like all the pci cards that are attached to you motherboard. The -nn is a option that shows the name and the number or product id number 

so lspci -nn means list all pci cards  and please show them by name and number 


also there is a thing called a blacklist file 
what the blacklist.conf file does is make it so that the mods that are in the blacklist.conf file can never ever ever ever ever load. 

so lets take a look at you wireless card and also you blacklist.con file to see you blacklist.conf file do a 
```
cat /etc/modprobe.d/blacklist.conf
```also if this is a usb wifi thingy please let us see a 
```
lsusb
```ls stands for list and usb stands for well usb by default it shows it by name and number so no need for the -nn

---

### Post by pederbruusgaard on 2011-09-03
> **josephmills said:**
> Hi there again 
lets take a look at this out put 


as you can see you are using the 2.6.38-11-generic-pae  kernel so that backport will not work for you. but if you use synaptic to look up the one that pertains to your kernel then it should work 
this is not good this shows that the eth0/ethernet-port  is loaded and so is the loop back or lo. But not the wireless when the wireless is listed you see a wlan0 or ra0 depends on the wireless card  

this is what rfkill list all shows if there is a soft block then there is a software block.
If the hard block says yes then that means that the physical wireless switch is turned off. so it is good that they all say no.  


this shows us that the interfaces do not support scanning I 100% recomend that you NEVER show this to anyone once the wireless is working due to security. But once again we do not see a wireless interface  

so remember how you learned what the command ls does well in linux lingo driver are called mods well sort of . But what this list shows is all mods or moduals that are loaded on the system as of right now. Well bad news I dont see any wireless mods  loaded on the system. 


so this is what we can do. first we need to see some more things from the terminal the first thing is a 
```
lspci -nn
```what this will show is ls like list and pci like all the pci cards that are attached to you motherboard. The -nn is a option that shows the name and the number or product id number 

so lspci -nn means list all pci cards  and please show them by name and number 


also there is a thing called a blacklist file 
what the blacklist.conf file does is make it so that the mods that are in the blacklist.conf file can never ever ever ever ever load. 

so lets take a look at you wireless card and also you blacklist.con file to see you blacklist.conf file do a 
```
cat /etc/modprobe.d/blacklist.conf
```also if this is a usb wifi thingy please let us see a 
```
lsusb
```ls stands for list and usb stands for well usb by default it shows it by name and number so no need for the -nn

Thank you so much for taking the time to help me with this! I really appreciate it!

```
peder@peder-ThinkPad-X220:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:16.3 Serial controller [0700]: Intel Corporation 6 Series Chipset Family KT Controller [8086:1c3d] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b4)
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 6 Series Chipset Family LPC Controller [8086:1c4f] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
0d:00.0 System peripheral [0880]: Ricoh Co Ltd Device [1180:e823] (rev 04)
0e:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
```

```
peder@peder-ThinkPad-X220:~$ cat /etc/modprobe.d/blacklist.conf
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

```

```
peder@peder-ThinkPad-X220:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b217 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Also, that thing with 2.6.38-11-generic-pae kernel and Synaptic - do I just search for something there or how do I go about that?

Thanks a million for all your help!

---

### Post by josephmills on 2011-09-03
Are you sure that you pasted all of the lspci -nn I can not see a wireless device could some one else help out here thanks

---

### Post by pederbruusgaard on 2011-09-03
> **josephmills said:**
> Are you sure that you pasted all of the lspci -nn I can not see a wireless device could some one else help out here thanks

I'm pretty sure I did. Can check again:
```
peder@peder-ThinkPad-X220:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:16.3 Serial controller [0700]: Intel Corporation 6 Series Chipset Family KT Controller [8086:1c3d] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b4)
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 6 Series Chipset Family LPC Controller [8086:1c4f] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
0d:00.0 System peripheral [0880]: Ricoh Co Ltd Device [1180:e823] (rev 04)
0e:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
peder@peder-ThinkPad-X220:~$ 

```

---

### Post by nm_geo on 2011-09-03
> **josephmills said:**
> Are you sure that you pasted all of the lspci -nn I can not see a wireless device could some one else help out here thanks

I looked too Joseph I do not see a mention of wireless.  Usually think pads are Intel correct?

---

### Post by josephmills on 2011-09-03
> **nm_geo said:**
> I looked too Joseph I do not see a mention of wireless.  Usually think pads are Intel correct?
yes I have also seen them with athroes and broadcom in them

---

### Post by nm_geo on 2011-09-04
This is a reach but since it is so new .. Does any other os like windozes work on the computer?  Maybe wireless is turned off by BIOS..

---

### Post by garvinrick4 on 2011-09-04
I cannot see a wireless network card at all.
#Says they come with this installed.
Integrated WiFi wireless LAN adapters[10]("http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/#")ThinkPad b/g/n
##articles say it can be intel or realtek (ThinkPad b/g/n)
#Have read articles about intel 6205 card uses iwlagn a kernel
driver. 
Most just upgraded kernel and solved the firmware problem.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Choose 3.0 or up kernel to install
Need all.deb, headers, image, download the three and just click on and will install thru Ubuntu software center in same order. ( use your 32 or 64 bit)
#First download module-init-tools 3.13 below in .deb (click on built 32 or 64 bit to get .deb file all built for you)
and click on and let install.
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)
Done:
Takes maybe 5 minutes to do and should be resolved. I am using iwlagn driver in Maverick on up with 3.0 and up kernels with upgraded module-init-tools and all installs fine.

---

### Post by garvinrick4 on 2011-09-04
After you do previous post run this and post so we may see. Thanks.
Run This line of code if you would, there is my output below.
```
 lspci -nnk | grep -iA2 network
```02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlagn

---

### Post by pederbruusgaard on 2011-09-04
> **garvinrick4 said:**
> After you do previous post run this and post so we may see. Thanks.
Run This line of code if you would, there is my output below.
```
 lspci -nnk | grep -iA2 network
```02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlagn

Thanks for the advice - I'll update the Kernel as soon as I get back to my computer. Shouldn't be too long :)
Thanks!

---

### Post by garvinrick4 on 2011-09-04
The iwlagn driver from intel only works in "G" in 2.6 kernels so we have been using
a config file to remove "N" from intel cards.
The iwlagn driver will work in "N" with 3.0 and up kernel without a hitch.

For users with "iwlagn" driver and only had a "G" router it never effected them at all
its when most users got "N" routers and set the 2.4 ghz at "N" only it would just slowly
depreciate until it did not work at all. So here is the fix we used below.
Make a config file:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```and then copy this line below in and SAVE then REBOOT.
                               
 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]
 
That above just removes the "N" from the card. When you run"
```
iwconfig
```You will see there is no more "N" in the card.
It will now work in "G" mode at 54Mb/s which is still fine.
#Again for the 2.6 kernels: Intel knew of problem and has been around for a while.
It was not until a lot of "N" routers where sold that was a major problem for intel
"iwlagn" driver.
## I am an owner of a card using this driver so I am practical here and not in theory.
In Maverick and 3 Natty's I upgraded my "module-init-tools" as in earlier post already
in .deb from launchpad and the kernel to 3.0 and up already in .deb and now can set router at "N" only in 2.4 ghz and all is now fine with "iwlagn" driver. Oneiric comes with 3.0 and up kernel
##Always find the already built packages in .deb it is so much easier than compiling.
If you choose just one click and Ubuntu software package installs after you have downloaded package.

---

### Post by pederbruusgaard on 2011-09-04
> **garvinrick4 said:**
> The iwlagn driver from intel only works in "G" in 2.6 kernels so we have been using
a config file to remove "N" from intel cards.
The iwlagn driver will work in "N" with 3.0 and up kernel without a hitch.

For users with "iwlagn" driver and only had a "G" router it never effected them at all
its when most users got "N" routers and set the 2.4 ghz at "N" only it would just slowly
depreciate until it did not work at all. So here is the fix we used below.
Make a config file:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```and then copy this line below in and SAVE then REBOOT.
                               
 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]
 
That above just removes the "N" from the card. When you run"
```
iwconfig
```You will see there is no more "N" in the card.
It will now work in "G" mode at 54Mb/s which is still fine.
#Again for the 2.6 kernels: Intel knew of problem and has been around for a while.
It was not until a lot of "N" routers where sold that was a major problem for intel
"iwlagn" driver.
## I am an owner of a card using this driver so I am practical here and not in theory.
In Maverick and 3 Natty's I upgraded my "module-init-tools" as in earlier post already
in .deb from launchpad and the kernel to 3.0 and up already in .deb and now can set router at "N" only in 2.4 ghz and all is now fine with "iwlagn" driver. Oneiric comes with 3.0 and up kernel
##Always find the already built packages in .deb it is so much easier than compiling.
If you choose just one click and Ubuntu software package installs after you have downloaded package.

Hi,
So I still have to update the kernel to 3.0 +?
I tried it through the Ubuntu Software Center, but every time I try to install the last image, the program freezes...

---

### Post by garvinrick4 on 2011-09-04
> Hi,
So I still have to update the kernel to 3.0 +?
I tried it through the Ubuntu Software Center, but every time I try to install the last image, the program freezes...
If it freezes do it from command line. Put the deb files on Desktop.
```
cd Desktop
```
```
ls
```Above is a lower case L)

```
sudo dpkg -i "copy and paste module-init-tools here hit enter, no quotes.
```
```
sudo dkpg -i "copy and paste .all deb here"
```
```
sudo dpkg -i 'copy and paste headers here'
```
```
sudo dpkg -i "copy and paste image here"
```
```
sudo reboot
```

---

### Post by pederbruusgaard on 2011-09-04
> **garvinrick4 said:**
> The iwlagn driver from intel only works in "G" in 2.6 kernels so we have been using
a config file to remove "N" from intel cards.
The iwlagn driver will work in "N" with 3.0 and up kernel without a hitch.

For users with "iwlagn" driver and only had a "G" router it never effected them at all
its when most users got "N" routers and set the 2.4 ghz at "N" only it would just slowly
depreciate until it did not work at all. So here is the fix we used below.
Make a config file:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```and then copy this line below in and SAVE then REBOOT.
                               
 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]
 
That above just removes the "N" from the card. When you run"
```
iwconfig
```You will see there is no more "N" in the card.
It will now work in "G" mode at 54Mb/s which is still fine.
#Again for the 2.6 kernels: Intel knew of problem and has been around for a while.
It was not until a lot of "N" routers where sold that was a major problem for intel
"iwlagn" driver.
## I am an owner of a card using this driver so I am practical here and not in theory.
In Maverick and 3 Natty's I upgraded my "module-init-tools" as in earlier post already
in .deb from launchpad and the kernel to 3.0 and up already in .deb and now can set router at "N" only in 2.4 ghz and all is now fine with "iwlagn" driver. Oneiric comes with 3.0 and up kernel
##Always find the already built packages in .deb it is so much easier than compiling.
If you choose just one click and Ubuntu software package installs after you have downloaded package.

Ok, so now I upgraded the kernel to 3.0.0, and I also did the commands in the previous post, but it didn't help.
Another, even more strange thing happened, however. In my system monitor, it says I only have 3.4 GB memory, where it used to be 7.8. I have 2 x 4GB memory.

I'm almost starting to freak out about this - I have little experience or knowledge about Linux, and now even more things are starting to disappear from me. Do you think it would help to go back to 10.10?

---

### Post by garvinrick4 on 2011-09-04
what does it say when you do:
```
uname -a
```what kernel:
32 bit will only see up to 3 gig or so of Ram unless you use the pae kernel.
You did those commands fast or either the Ubuntu software center installed them.

---

### Post by pederbruusgaard on 2011-09-04
> **garvinrick4 said:**
> what does it say when you do:
```
uname -a
```
what kernel:
32 bit will only see up to 4 gig of Ram unless you use the pae kernel.
You did those commands fast or either the Ubuntu software center installed them.

```
peder@peder-ThinkPad-X220:~$ uname -a
Linux peder-ThinkPad-X220 3.0.0-0300rc2-generic #201106081532 SMP Wed Jun 8 16:21:54 UTC 2011 i686 i686 i386 GNU/Linux

```

---

### Post by garvinrick4 on 2011-09-04
Ok 32-bit  3.0.0-0300rc2-generic
now reboot and see if picks up your network card. unplug the wired connection.
Have to click on network applet in upper right and find your SSID click on it and
put in your password.

---

### Post by pederbruusgaard on 2011-09-04
> **garvinrick4 said:**
> Ok 32-bit 
3.0.0-0300rc2-generic

Is that ok?
I looked at this older thread [http://ubuntuforums.org/showthread.php?t=1739047&page=3](http://ubuntuforums.org/showthread.php?t=1739047&page=3) , do you think that's a solution?

---

### Post by wildmanne39 on 2011-09-04
Hi, in other words you need to install the 64 bit kernel.
Thank you

---

### Post by garvinrick4 on 2011-09-04
Reboot and run:
> lspci -nnk | grep -iA2 network
Should show your card and driver, does it?

---

### Post by pederbruusgaard on 2011-09-04
> **garvinrick4 said:**
> Reboot and run:

Should show your card and driver, does it?

peder@peder-ThinkPad-X220:~$ lspci -nnk|grep -iA2 network
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21ce]
	Kernel driver in use: e1000e

---

### Post by pederbruusgaard on 2011-09-04
> **wildmanne39 said:**
> Hi, in other words you need to install the 64 bit kernel.
Thank you

Does that mean that I also should have installed 64 bit Ubuntu? Cause I'm pretty sure I chose 32 there as well...

---

### Post by wildmanne39 on 2011-09-04
Hi, if that is the case you can install the pae kernel that is what you must have installed before to use all your memory with a 32 bit system.

In fact that must be the case.
Thank you

---

### Post by garvinrick4 on 2011-09-04
So you are still running the wired connection:
```
lspci -k
```Does it show a network controller and driver? (your wifi card)
Will show a bunch of them look for your network controller and ethernet.

You did take out the wired connection and reboot?
> 
Hi, if that is the case you can install the pae kernelHi wildmane39
Yes they have a 3.0 kernel that is built in pae. Hopefully OP will tell us where he
is at and if he is up and working, he can uninstall a kernel and install a pae in a few minutes time.
Intel Centrino 6205 card and iwlagn driver has worked with 3.0 kernel cannot find out
if being recognized from OP right now. If he even has given it a chance to work. Sometimes
they think it should work without a reboot or a modprobe but will see I imagine. Hope he is up and working.

---

