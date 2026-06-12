---
title: "Accidentally turned off Wi-Fi adapter"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by MichaelMale on 2012-08-10
Hello (again...),

Whilst I was trying to fix a problem, I managed to create another one. I have now seemingly turned my wi-fi adapter off, when I do lsusb it's not there.

Is there any way to turn it on again?

---

### Post by praseodym on 2012-08-10
Re-plugged it?

---

### Post by sffvba[e0rt on 2012-08-10
> Try this:

Install rfkill -> sudo apt-get install rfkill

Give this command in terminal -> rfkill unblock all

Your wireless will work instantly, I hope. I guess you have a Intel wireless card and an Hp laptop, one of them at least.

[http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working](http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working)



404

---

### Post by MichaelMale on 2012-08-10
> **praseodym said:**
> Re-plugged it?

Tried that, but to no avail.

> **not found said:**
> [http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working](http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working)



404

Didn't work either, which is quite a pain. If it helps:

```

michael@Bonoahx:~$ sudo apt-get install rfkill
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rfkill is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 338 not upgraded.
michael@Bonoahx:~$ rfkill unblock all
michael@Bonoahx:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c31b Logitech, Inc. Compact Keyboard K300
Bus 003 Device 003: ID 046d:0824 Logitech, Inc. 
Bus 005 Device 002: ID 044f:b108 ThrustMaster, Inc. 
Bus 007 Device 002: ID 046d:c062 Logitech, Inc. LS1 Laser Mouse, corded

```

My device is a Netgear N600 USB, uses WNDA3100v2. I'm using the bcmn43xx32 driver, which worked at one point but now says the hardware isn't present. I'll try the stuff on AskUbuntu.

UPDATE: Didn't work :(

---

### Post by praseodym on 2012-08-10
This means, you are using ndiswrapper? Installed anything?

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
sudo depmod -a
sudo modprobe ndiswrapper
```
Re-plug again.

---

### Post by MichaelMale on 2012-08-10
> **praseodym said:**
> This means, you are using ndiswrapper? Installed anything?

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
sudo depmod -a
sudo modprobe ndiswrapper
```
Re-plug again.

I am using ndiswrapper, yes. The only driver I have is for the adapter. Only other applications I've installed are things like Teamspeak and Skype, I can't see why that would do anything to it.

Anyway, it didn't work. Here's the output:

```

michael@Bonoahx:~$ sudo apt-get install linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
[sudo] password for michael: 
Sorry, try again.
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dkms is already the newest version.
ndisgtk is already the newest version.
ndiswrapper-dkms is already the newest version.
linux-headers-3.2.0-29-generic-pae is already the newest version.
linux-headers-3.2.0-29-generic-pae set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 338 not upgraded.
michael@Bonoahx:~$ sudo depmod -a
sudo modprobe ndiswrmichael@Bonoahx:~$ ^C
michael@Bonoahx:~$ sudo depmod -a
michael@Bonoahx:~$ sudo modprobe ndiswrapper
michael@Bonoahx:~$ 

```

---

### Post by praseodym on 2012-08-10
Ok, please show:
```
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
lsmod
dmesg | grep ndis
rfkill list
sudo iwlist scan
```
IMHO Kernel -29 is not the regular one. Did you activate the backport or proposed archives? Tried an earlier kernel?

---

### Post by MichaelMale on 2012-08-10
> **praseodym said:**
> Ok, please show:
```
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
lsmod
dmesg | grep ndis
rfkill list
sudo iwlist scan
```
IMHO Kernel -29 is not the regular one. Did you activate the backport or proposed archives? Tried an earlier kernel?

```
michael@Bonoahx:~$ ndiswrapper -l
bcmn43xx32 : driver installed
michael@Bonoahx:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias wlan0 ndiswrapper
michael@Bonoahx:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
udf                    84466  1 
crc_itu_t              12627  1 udf
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
vesafb                 13516  1 
binfmt_misc            17292  1 
snd_hda_codec_realtek   174222  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         101566  1 
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
fglrx                2909855  106 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
snd                    62064  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
psmouse                72919  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
k10temp                12990  0 
wmi                    18744  1 asus_wmi
serio_raw              13027  0 
ndiswrapper           192268  0 
joydev                 17393  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
lp                     17455  0 
mac_hid                13077  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
r8169                  56321  0 
pata_atiixp            12999  0 
michael@Bonoahx:~$ dmesg | grep ndis
[   25.330086] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   25.418132] usbcore: registered new interface driver ndiswrapper
michael@Bonoahx:~$ rfkill list
michael@Bonoahx:~$ sudo iwlist scan
[sudo] password for michael: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

To be honest I'm very new to Linux and only have a vague idea of what a kernel is, and have no clue what you mean by backport. Apologies.

---

### Post by praseodym on 2012-08-11
How much RAM do you have?

Please reboot, press the SHIFT-button during boot, choose "earlier ubuntu versions", and choose kernel 3.2.0.27 there. Try it again

---

### Post by MichaelMale on 2012-08-11
> **praseodym said:**
> How much RAM do you have?

Please reboot, press the SHIFT-button during boot, choose "earlier ubuntu versions", and choose kernel 3.2.0.27 there. Try it again

I have 4GB of RAM installed, but I've been told the drivers for the adapter only work on 32-bit so I guess I have 3GB of RAM. There isn't an option for 3.2.0.27 on the boot screen, only 3.2.0.29 and 3.2.0.23. I booted up into 3.2.0.23 and nothing changed.

---

### Post by praseodym on 2012-08-11
Did you (re-)install the kernel headers for the -23?

---

### Post by MichaelMale on 2012-08-11
> **praseodym said:**
> Did you (re-)install the kernel headers for the -23?

No - I don't think I've changed anything to do with the kernels.

---

### Post by praseodym on 2012-08-11
Try with this kernel:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms ndiswrapper-utils-1.9 ndiswrapper-common
sudo depmod -a
sudo modprobe ndiswrapper
```
From where did you get the driver? Alternatively, try the one attached or reinstall the one in use from terminal:

```
sudo modprobe -rfv ndiswrapper #unload
sudo ndiswrapper -i /path/to/driver/bcmn43xx32.inf
sudo modprobe -v ndiswrapper
```
and replug the stick.

---

### Post by MichaelMale on 2012-08-11
> **praseodym said:**
> Try with this kernel:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms ndiswrapper-utils-1.9 ndiswrapper-common
sudo depmod -a
sudo modprobe ndiswrapper
```
From where did you get the driver? Alternatively, try the one attached or reinstall the one in use from terminal:

```
sudo modprobe -rfv ndiswrapper #unload
sudo ndiswrapper -i /path/to/driver/bcmn43xx32.inf
sudo modprobe -v ndiswrapper
```
and replug the stick.

I'll try them step by step on both.
```

michael@Bonoahx:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms ndiswrapper-utils-1.9 ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 7 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,289 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 181711 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using .../build-essential_11.5ubuntu2_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1ubuntu3 (using .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.2.0-29-generic-pae 3.2.0-29.46 (using .../linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-29-generic-pae ...
Preparing to replace ndisgtk 0.8.5-1 (using .../ndisgtk_0.8.5-1_i386.deb) ...
Unpacking replacement ndisgtk ...
Preparing to replace ndiswrapper-common 1.57-1ubuntu1 (using .../ndiswrapper-common_1.57-1ubuntu1_all.deb) ...
Unpacking replacement ndiswrapper-common ...
Preparing to replace ndiswrapper-dkms 1.57-1ubuntu1 (using .../ndiswrapper-dkms_1.57-1ubuntu1_all.deb) ...

-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.57
Kernel:  3.2.0-29-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-29-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement ndiswrapper-dkms ...
Preparing to replace ndiswrapper-utils-1.9 1.57-1ubuntu1 (using .../ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb) ...
Unpacking replacement ndiswrapper-utils-1.9 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up build-essential (11.5ubuntu2) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up linux-headers-3.2.0-29-generic-pae (3.2.0-29.46) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-29-generic-pae /boot/vmlinuz-3.2.0-29-generic-pae
Setting up ndiswrapper-common (1.57-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.57-1ubuntu1) ...
Setting up ndisgtk (0.8.5-1) ...
Setting up ndiswrapper-dkms (1.57-1ubuntu1) ...
Loading new ndiswrapper-1.57 DKMS files...
Building only for 3.2.0-29-generic-pae
Building initial module for 3.2.0-29-generic-pae
Done.

ndiswrapper:
Running module version sanity check.

Good news! Module version 1.57 for ndiswrapper.ko
exactly matches what is already found in kernel 3.2.0-29-generic-pae.
DKMS will not replace this module.
You may override by specifying --force.

depmod....

DKMS: install completed.
michael@Bonoahx:~$ sudo modprobe -rfv ndiswrapper #unload
rmmod /lib/modules/3.2.0-29-generic-pae/misc/ndiswrapper.ko
michael@Bonoahx:~$ sudo ndiswrapper -i /desktop/bcmn43xx32.inf
driver bcmn43xx32 is already installed
michael@Bonoahx:~$ sudo modprobe -v ndiswrapper
insmod /lib/modules/3.2.0-29-generic-pae/misc/ndiswrapper.ko 

```

And the old kernel...

```


michael@Bonoahx:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms ndiswrapper-utils-1.9 ndiswrapper-common
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 7 reinstalled, 0 to remove and 0 not upgraded.
Need to get 944 kB/1,247 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise/main linux-headers-3.2.0-23-generic-pae i386 3.2.0-23.36 [944 kB]
Fetched 944 kB in 2s (446 kB/s)                             
(Reading database ... 181711 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using .../build-essential_11.5ubuntu2_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1ubuntu3 (using .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.2.0-23-generic-pae 3.2.0-23.36 (using .../linux-headers-3.2.0-23-generic-pae_3.2.0-23.36_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-23-generic-pae ...
Preparing to replace ndisgtk 0.8.5-1 (using .../ndisgtk_0.8.5-1_i386.deb) ...
Unpacking replacement ndisgtk ...
Preparing to replace ndiswrapper-common 1.57-1ubuntu1 (using .../ndiswrapper-common_1.57-1ubuntu1_all.deb) ...
Unpacking replacement ndiswrapper-common ...
Preparing to replace ndiswrapper-dkms 1.57-1ubuntu1 (using .../ndiswrapper-dkms_1.57-1ubuntu1_all.deb) ...

-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.57
Kernel:  3.2.0-29-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-29-generic-pae/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement ndiswrapper-dkms ...
Preparing to replace ndiswrapper-utils-1.9 1.57-1ubuntu1 (using .../ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb) ...
Unpacking replacement ndiswrapper-utils-1.9 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up build-essential (11.5ubuntu2) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up linux-headers-3.2.0-23-generic-pae (3.2.0-23.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
Setting up ndiswrapper-common (1.57-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.57-1ubuntu1) ...
Setting up ndisgtk (0.8.5-1) ...
Setting up ndiswrapper-dkms (1.57-1ubuntu1) ...
Loading new ndiswrapper-1.57 DKMS files...
Building for 3.2.0-23-generic-pae and 3.2.0-29-generic-pae
Building initial module for 3.2.0-23-generic-pae
Done.

ndiswrapper:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
Building initial module for 3.2.0-29-generic-pae
Done.

ndiswrapper:
Running module version sanity check.

Good news! Module version 1.57 for ndiswrapper.ko
exactly matches what is already found in kernel 3.2.0-29-generic-pae.
DKMS will not replace this module.
You may override by specifying --force.

depmod....

DKMS: install completed.
michael@Bonoahx:~$ sudo depmod -a
michael@Bonoahx:~$ sudo modprobe ndiswrapper
michael@Bonoahx:~$ sudo modprobe -rfv ndiswrapper #unload
rmmod /lib/modules/3.2.0-23-generic-pae/updates/dkms/ndiswrapper.ko
michael@Bonoahx:~$ sudo ndiswrapper -i /desktop/bcmn43xx32.inf
driver bcmn43xx32 is already installed
michael@Bonoahx:~$ sudo modprobe -v ndiswrapper
insmod /lib/modules/3.2.0-23-generic-pae/updates/dkms/ndiswrapper.ko 
michael@Bonoahx:~$ 

```

No change :(

---

### Post by coldraven on 2012-08-11
After having installed the OS with the wifi switched off I  got my wifi back by booting into the BIOS Setup and selecting "Restore Defaults".
But then I had to do a fresh install because if I let the laptop boot into the existing installation it would switch it back off again :(
This was a real Catch22 situation.
Mine is a Broadcom BCM43xx and it works fine with the STA proprietary  driver

---

### Post by MichaelMale on 2012-08-13
I've resorted to buying an ethernet cable which is about 10 metres too long and making a physical connection. It works perfectly!

[IMG]http://www.speedtest.net/result/2117176824.png[/IMG]

Thanks a lot for your help, anyway :), is there a way to close this thread without marking it as solved?

---

