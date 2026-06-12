---
title: "No wireless on Dell N5110 with any driver"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by robawalsh on 2013-02-20
I've tried installing b43, STA, wl, ndiswrapper, none have worked, so now I'm trying brcmsmac

Problem is, I have this problem when trying to **modprobe** ANY module: 

    ```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

    FATAL: Error inserting brcmsmac (/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko): Invalid argument

```Apparently I have bcma and ssb running each time I boot, from **lsmod**: 
[URL="http://pastebin.com/vBwMmuYB"]http://pastebin.com/vBwMmuYB
[/URL] 
**iwconfig** gives: 

    ```
robawalsh@Dell-Inspiron-N5110:~$ iwconfig

    lo        no wireless extensions.

    eth0      no wireless extensions.

```And here is the output of **lspci**: [http://pastebin.com/eLHXwYaC](http://pastebin.com/eLHXwYaC)

I have run [B]sudo apt-get update && sudo apt-get upgrade


[/B]I have had wireless working before, but since updating, the wireless stopped working again. This has happened a few times, so I made backups of the contents of */lib/modules/< KERNEL>/kernel/net/wireless* so that I could easily replace them after an update, which worked a few times, but not any more.

I'm on the verge of giving up with Linux entirely. I love it, but I've spent far too long trying to fix these damned wireless drivers. :mad:

PLEASE HELP ME FIX THIS

---

### Post by westie457 on 2013-02-20
Which version are running, 12.04 or 12.10?

---

### Post by robawalsh on 2013-02-20
> **westie457 said:**
> which version are running, 12.04 or 12.10?

12.04

---

### Post by chili555 on 2013-02-20
Did you also ask on askubuntu.com? Please see my answer there.

---

### Post by westie457 on 2013-02-20
Lets gather as much info as we can quite quickly.

Follow what is in this post please. [http://ubuntuforums.org/showpost.php?p=12519073&postcount=21](http://ubuntuforums.org/showpost.php?p=12519073&postcount=21)

In the meantime I will be researching something.

---

### Post by robawalsh on 2013-02-20
Done...

---

### Post by robawalsh on 2013-02-20
> **chili555 said:**
> Did you also ask on askubuntu.com? Please see my answer there.

Yes I did. 

I tried your suggestions and rebooted, but still there is no Wireless option
Backports was not installed, btw

---

### Post by chili555 on 2013-02-20
> **robawalsh said:**
> Yes I did. 

I tried your suggestions and rebooted, but still there is no Wireless option
Backports was not installed, btwDid the reinstallation of bcmwl-kernel-source, which is correct for your device, go without error?

---

### Post by westie457 on 2013-02-20
Did chill555's answer on Askubuntu help?

---

### Post by robawalsh on 2013-02-20
> **chili555 said:**
> Did the reinstallation of bcmwl-kernel-source, which is correct for your device, go without error?

Ah, didn't notice that - no, there is an error: 

```
robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of bcmwl-kernel-source is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by robawalsh on 2013-02-20
> **westie457 said:**
> Did chill555's answer on Askubuntu help?

No...

---

### Post by chili555 on 2013-02-20
> Reinstallation of bcmwl-kernel-source is not possible, it cannot be downloaded.Can you get a temporary wired ethernet connection and try again?

---

### Post by robawalsh on 2013-02-20
> **chili555 said:**
> Can you get a temporary wired ethernet connection and try again?

I'm on wired ethernet on the same laptop now

---

### Post by chili555 on 2013-02-20
> **robawalsh said:**
> I'm on wired ethernet on the same laptop nowPlease check Software Sources and be sure everything is enabled as attached. Then do:```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modpobe wl
```The server selection should match your location if not US as in the example.

---

### Post by robawalsh on 2013-02-20
> **chili555 said:**
> Please check Software Sources and be sure everything is enabled as attached. Then do:```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modpobe wl
```The server selection should match your location if not US as in the example.

The server selection was on "Server for United Kingdom", I switched it to US (Main Server) and it downloaded, but there were errors reinstalling: 

```
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-38-generic
Building for architecture x86_64
Building initial module for 3.2.0-38-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-38-generic/updates/dkms/

depmod....

DKMS: install completed.
FATAL: Error inserting wl (/lib/modules/3.2.0-38-generic/updates/dkms/wl.ko): Invalid argument
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
robawalsh@Dell-Inspiron-N5110:~$ 

```

sudo modprobe wl gave the same: 

```
FATAL: Error inserting wl (/lib/modules/3.2.0-38-generic/updates/dkms/wl.ko): Invalid argument

```

---

### Post by chili555 on 2013-02-20
> FATAL: Error inserting wl (/lib/modules/3.2.0-38-generic/updates/dkms/wl.ko): Invalid argumentVerrrry interesting. Let's have a look at:```
sudo dpkg -s linux-backports-modules-cw-3.6-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~. Also:```
sudo apt-cache search linux-backports-modules-cw*
```

---

### Post by robawalsh on 2013-02-20
For the first command: 

```
robawalsh@Dell-Inspiron-N5110:~$ sudo dpkg -s linux-backports-modules-cw-3.6-`uname -r`
[sudo] password for robawalsh: 
Package `linux-backports-modules-cw-3.6-3.2.0-38-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
robawalsh@Dell-Inspiron-N5110:~$ 
```And the second: 

```
robawalsh@Dell-Inspiron-N5110:~$ sudo apt-cache search linux-backports-modules-cw*
linux-backports-modules-cw-3.3-3.2.0-23-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-precise-generic - Backported wireless drivers for generic kernel image
linux-backports-modules-cw-3.3-3.2.0-23-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-precise-generic-pae - Backported wireless drivers for generic-pae kernel image
linux-backports-modules-cw-3.3-3.2.0-24-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-25-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-26-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-27-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-29-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-30-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-31-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-32-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-33-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-34-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-35-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-35-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-36-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-36-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-37-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-37-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-38-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.2.0-38-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-29-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-30-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-31-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-32-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-33-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-34-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-35-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-35-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-36-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-36-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-37-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-37-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-38-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-3.2.0-38-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.4-precise-generic - Backported wireless drivers for generic kernel image
linux-backports-modules-cw-3.5-3.2.0-33-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-34-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-35-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-35-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-36-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-36-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-37-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-37-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-38-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-3.2.0-38-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.5-precise-generic - Backported wireless drivers for generic kernel image
linux-backports-modules-cw-3.6-3.2.0-33-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-34-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-35-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-35-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-36-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-36-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-37-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-37-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-38-generic - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-3.2.0-38-virtual - compat-wireless Linux modules for version 3.2.0 on x86/x86_64
linux-backports-modules-cw-3.6-precise-generic - Backported wireless drivers for generic kernel image
linux-backports-modules-cw-3.3-3.2.0-24-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-25-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-26-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-27-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-29-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-30-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-31-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-32-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-33-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-34-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-35-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-36-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-37-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.3-3.2.0-38-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-29-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-30-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-31-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-32-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-33-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-34-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-35-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-36-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-37-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-3.2.0-38-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.4-precise-generic-pae - Backported wireless drivers for generic-pae kernel image
linux-backports-modules-cw-3.5-3.2.0-33-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.5-3.2.0-34-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.5-3.2.0-35-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.5-3.2.0-36-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.5-3.2.0-37-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.5-3.2.0-38-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.5-precise-generic-pae - Backported wireless drivers for generic-pae kernel image
linux-backports-modules-cw-3.6-3.2.0-33-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.6-3.2.0-34-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.6-3.2.0-35-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.6-3.2.0-36-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.6-3.2.0-37-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.6-3.2.0-38-generic-pae - compat-wireless Linux modules for version 3.2.0 on x86
linux-backports-modules-cw-3.6-precise-generic-pae - Backported wireless drivers for generic-pae kernel image

```

I'm not sure what this means. I assume these shouldn't have been installed? 
I don't remember installing them...

---

### Post by chili555 on 2013-02-20
Hmmm, everything looks as it should so far, nothing to fix here. These aren't the droids we're looking for. Let's dig deeper; reboot so we have a clean slate and show us:```
lsmod
```

---

### Post by robawalsh on 2013-02-20
> **chili555 said:**
> Hmmm, everything looks as it should so far, nothing to fix here. These aren't the droids we're looking for. Let's dig deeper; reboot so we have a clean slate and show us:```
lsmod
```

```
robawalsh@Dell-Inspiron-N5110:~$ lsmod
Module                  Size  Used by
bbswitch               13396  0 
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  4 
snd_hda_codec_idt      70795  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
mxm_wmi                13021  0 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
psmouse                97485  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
serio_raw              13211  0 
joydev                 17693  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  3 
mei                    41616  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
btusb                  18332  2 
snd_hwdep              17764  1 snd_hda_codec
bluetooth             180153  23 rfcomm,bnep,btusb
wmi                    19256  2 dell_wmi,mxm_wmi
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac_hid                13253  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29990  2 snd_seq,snd_pcm
i915                  477611  3 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
bcma                   26696  0 
ssb                    52752  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0 
usbhid                 47238  0 
hid                    99636  1 usbhid
lzo                    12597  0 

```

---

### Post by chili555 on 2013-02-20
The installation of bcmwl-kernel-source is supposed to blacklist ssb and bcma; they are still loading and wl is not. Please do:```
gksudo gedit /etc/modules
```If bcma and ssb are in there, remove them and add wl. Proofread, save and close gedit. Now do:```
sudo su
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
modprobe -r bcma
modprobe -r ssb
modprobe wl
exit
```Any improvement?

---

### Post by robawalsh on 2013-02-20
> **chili555 said:**
> The installation of bcmwl-kernel-source is  supposed to blacklist ssb and bcma; they are still loading and wl is  not. Please do:```
gksudo gedit /etc/modules
```If bcma and ssb are  in there, remove them and add wl. Proofread, save and close gedit.  

**bcma** and **ssb** weren't in there, but **b43** was, so I added **wl** and removed **b43** - correct?

> **chili555 said:**
> Now do:```
sudo su
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
modprobe -r bcma
modprobe -r ssb
modprobe wl
exit
```Any improvement?

All successful up to **modprobe wl**, but then the same error again: 

```
FATAL: Error inserting wl (/lib/modules/3.2.0-38-generic/updates/dkms/wl.ko): Invalid argument
```:?

---

### Post by chili555 on 2013-02-20
Now that we have done some housekeeping, please run again:```

sudo apt-get install --reinstall bcmwl-kernel-source
```Reference: [http://ubuntuforums.org/showthread.php?t=1610246](http://ubuntuforums.org/showthread.php?t=1610246)

---

### Post by robawalsh on 2013-02-20
> **chili555 said:**
> Now that we have done some housekeeping, please run again:```
sudo dpkg --force-all -P
sudo apt-get install --reinstall bcmwl-kernel-source
```Reference: [http://ubuntuforums.org/showthread.php?t=1610246](http://ubuntuforums.org/showthread.php?t=1610246)

Again, exactly the same as before, resulting in: 

```
FATAL: Error inserting wl (/lib/modules/3.2.0-38-generic/updates/dkms/wl.ko): Invalid argument
```

---

### Post by robawalsh on 2013-02-21
After a reboot, I'm still getting the same: 

```
robawalsh@Dell-Inspiron-N5110:~$ sudo modprobe brcmsmac
WARNING: Error inserting brcmutil (/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko): Invalid argument
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-38-generic/kernel/net/mac80211/mac80211.ko): Invalid argument
FATAL: Error inserting brcmsmac (/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko): Invalid argument

```

I can't find anything on this on Google...

---

### Post by chili555 on 2013-02-21
Please show me:```
sudo apt-get remove --purge linux-backports-modules-cw*
```Thanks.

---

### Post by robawalsh on 2013-02-21
> **chili555 said:**
> Please show me:```
sudo apt-get remove --purge linux-backports-modules-cw*
```Thanks.


robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get remove --purge linux-backports-modules-cw*
[sudo] password for robawalsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-34-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-29-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-36-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-33-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-38-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-38-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-35-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-37-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-36-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-34-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-32-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-37-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-precise-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-36-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-35-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-precise-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-33-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-38-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-24-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-37-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-36-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-32-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-27-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-30-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-35-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-precise-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-33-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-32-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-27-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-24-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-36-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-36-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-33-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-35-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-38-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-35-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-37-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-37-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-34-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-33-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-36-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-36-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-38-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-35-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-34-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-30-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-38-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-37-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-37-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-33-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-30-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-25-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-38-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-34-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-precise-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-30-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-25-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-31-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-37-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-36-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-33-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-35-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-38-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-37-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-34-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-29-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-34-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-29-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-36-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-33-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-37-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-36-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-38-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-35-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-precise-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-35-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-31-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-37-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-38-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-23-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.6-3.2.0-36-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-34-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-29-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-38-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-precise-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-3.2.0-35-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-31-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-26-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-31-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-26-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-38-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.5-precise-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-35-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-32-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-23-generic-pae' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-precise-generic' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.3-3.2.0-37-virtual' for regex 'linux-backports-modules-cw*'
Note, selecting 'linux-backports-modules-cw-3.4-3.2.0-35-generic-pae' for regex 'linux-backports-modules-cw*'
Package linux-backports-modules-cw-3.3-3.2.0-23-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-24-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-25-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-26-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-27-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-29-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-30-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-31-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-32-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.3-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.3-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-29-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-30-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-31-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-32-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.4-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.4-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.5-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.5-precise-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-33-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-34-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-35-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-35-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-36-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-36-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-37-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-37-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-38-generic is not installed, so not removed
Package linux-backports-modules-cw-3.6-3.2.0-38-virtual is not installed, so not removed
Package linux-backports-modules-cw-3.6-precise-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
robawalsh@Dell-Inspiron-N5110:~$

---

### Post by chili555 on 2013-02-21
> Problem is, I have this problem when trying to modprobe ANY module:And that, of course, is the real problem. Please reboot. In the first second or two of the boot process, press the Shift key to bring up the GRUB menu. Use the arrow keys to select any kernel version earlier than 3.2.0-[COLOR="Red"]38[/COLOR]-generic. Press Enter and boot into the earlier version. In that version can you successfully modprobe any module?```
sudo modprobe brcmsmac
```If so, let's try to reinstall -38:```
sudo apt-get install --reinstall linux-image-3.2.0-[COLOR="Red"]38[/COLOR]-generic
```Then reboot into -38 and try modprobe again. If it works, now do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Please see attached.

Fingers crossed!

---

### Post by robawalsh on 2013-02-21
> **chili555 said:**
> And that, of course, is the real problem. Please reboot. In the first second or two of the boot process, press the Shift key to bring up the GRUB menu. Use the arrow keys to select any kernel version earlier than 3.2.0-[COLOR=Red]38[/COLOR]-generic. Press Enter and boot into the earlier version. In that version can you successfully modprobe any module?```
sudo modprobe brcmsmac
```If so, let's try to reinstall -38:```
sudo apt-get install --reinstall linux-image-3.2.0-[COLOR=Red]38[/COLOR]-generic
```Then reboot into -38 and try modprobe again. If it works, now do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Please see attached.

Fingers crossed!

Hmm, I did think to try that, which didn't work in kernel 3.2.0-[COLOR=Red]37 [COLOR=black]either, but I'll try an earlier kernel and report back - shortly. 

Boot into recovery mode or not?

Also, do I want to modprobe brcmsmac or wl?
[/COLOR][/COLOR]

---

### Post by chili555 on 2013-02-21
> Boot into recovery mode or not?Either. Recovery mode, if I remember correctly, is text mode only, so Gnome, Compiz, and, by the way, Network Manager, etc. aren't in the way. You can do everything above from there.

---

### Post by robawalsh on 2013-02-21
Currently in kernel 3.2.0.34, and the wireless worked straight away at boot. 

The first thing I did was **sudo modprobe brcmsmac**, and this appeared successful. 

So then I tried **lsmod**:

```
robawalsh@Dell-Inspiron-N5110:~$ sudo modprobe brcmsmac
[sudo] password for robawalsh: 
robawalsh@Dell-Inspiron-N5110:~$ lsmod
Module                  Size  Used by
bbswitch               13396  0 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  4 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
brcmsmac              570874  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
i915                  477438  3 
cfg80211              205544  2 brcmsmac,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
crc8                   12893  1 brcmsmac
drm_kms_helper         46978  1 i915
drm                   241921  4 i915,drm_kms_helper
uvcvideo               72627  0 
cordic                 12535  1 brcmsmac
i2c_algo_bit           13423  1 i915
dell_laptop            18119  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               98259  1 uvcvideo
btusb                  18332  2 
dcdbas                 14490  1 dell_laptop
psmouse                97443  0 
joydev                 17693  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi               12681  0 
v4l2_compat_ioctl32    17128  1 videodev
sparse_keymap          13890  1 dell_wmi
serio_raw              13211  0 
mxm_wmi                12979  0 
video                  19596  1 i915
wmi                    19256  2 dell_wmi,mxm_wmi
lp                     17799  0 
soundcore              15091  1 snd
mei                    41616  0 
mac_hid                13253  0 
bluetooth             180104  23 rfcomm,bnep,btusb
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18248  0 
uas                    18180  0 
usb_storage            49198  1 ums_realtek
usbhid                 47199  0 
hid                    99592  1 usbhid
r8169                  62099  0 
lzo                    12597  0 
robawalsh@Dell-Inspiron-N5110:~$ 

```Since I can't see any other wireless module, I assume this kernel is using brcmsmac and has blacklisted the other drivers/modules. This is what I want.

**sudo apt-get install --reinstall linux-image-3.2.0-38-generic** appeared mostly successful, but with a dkms error: 
```

robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install --reinstall linux-image-3.2.0-38-generic
[sudo] password for robawalsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/38.5 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 604225 files and directories currently installed.)
Preparing to replace linux-image-3.2.0-38-generic 3.2.0-38.60 (using .../linux-image-3.2.0-38-generic_3.2.0-38.60_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.2.0-38-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Setting up linux-image-3.2.0-38-generic (3.2.0-38.60) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-38.60 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-38.60 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
[B]ERROR (dkms apport): kernel package linux-headers-3.2.0-38-generic is not supported
Error! Bad return status for module build on kernel: 3.2.0-38-generic (x86_64)
Consult /var/lib/dkms/psmouse-alps/0.10/build/make.log for more information.[/B]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Generating grub.cfg ...
using custom appearance settings
Found background image: /media/DATA/Wallpapers/Black_Texture.jpg
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done
robawalsh@Dell-Inspiron-N5110:~$ 
```This package, ** linux-headers-3.2.0-38-generic**, is what seems to be causing problems when I try to build/compile anything. 
[I]
/var/lib/dkms/psmouse-alps/0.10/build/make.log [/I]contains: 

```
DKMS make.log for psmouse-alps-0.10 for kernel 3.2.0-38-generic (x86_64)
Thu Feb 21 16:53:22 GMT 2013
make: Entering directory `/usr/src/linux-headers-3.2.0-38-generic'
  LD      /var/lib/dkms/psmouse-alps/0.10/build/src/built-in.o
  CC [M]  /var/lib/dkms/psmouse-alps/0.10/build/src/psmouse-base.o
  CC [M]  /var/lib/dkms/psmouse-alps/0.10/build/src/synaptics.o
  CC [M]  /var/lib/dkms/psmouse-alps/0.10/build/src/alps.o
/var/lib/dkms/psmouse-alps/0.10/build/src/alps.c:135:33: error: expected &#8216;)&#8217; before &#8216;int&#8217;
make[2]: *** [/var/lib/dkms/psmouse-alps/0.10/build/src/alps.o] Error 1
make[1]: *** [/var/lib/dkms/psmouse-alps/0.10/build/src] Error 2
make: *** [_module_/var/lib/dkms/psmouse-alps/0.10/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic'
```I'll boot into 3.2.0-38 to try modprobe and see if the error(s) still occur.

---

### Post by robawalsh on 2013-02-21
So I booted into 3.2.0-38, and the wireless *just worked*. Not sure how or why, but it's working :D

**lsmod**: 
```
robawalsh@Dell-Inspiron-N5110:~$ uname -r
3.2.0-38-generic
robawalsh@Dell-Inspiron-N5110:~$ lsmod
Module                  Size  Used by
michael_mic            12612  4 
arc4                   12529  2 
bbswitch               13396  0 
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  4 
snd_hda_codec_idt      70795  1 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
mxm_wmi                13021  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33773  3 
snd_seq_midi           13324  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
joydev                 17693  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                97485  0 
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13211  0 
lib80211_crypt_tkip    17390  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
v4l2_compat_ioctl32    17128  1 videodev
wmi                    19256  2 mxm_wmi,dell_wmi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
btusb                  18332  2 
mac_hid                13253  0 
bluetooth             180153  23 rfcomm,bnep,btusb
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29990  2 snd_pcm,snd_seq
wl                   3074895  0 
i915                  477611  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
cfg80211              205774  3 brcmsmac,mac80211,wl
lib80211               14381  2 lib80211_crypt_tkip,wl
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 
lzo                    12597  0 
```Looks like wl *and* brcmsmac are loaded. Is this correct? Will they conflict or are they the same thing?
  
**modprobe** appears to be working. It was an error with the kernel?
 
Also, I tried compiling the hybrid-portsrc_x86_64-v5_100_82_112 driver (to test) - but with an error. What gives? 
```

robawalsh@Dell-Inspiron-N5110:/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112$ make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-38-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic'
robawalsh@Dell-Inspiron-N5110:/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-38-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/built-in.o
  CC [M]  /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/shared/linux_osl.o
  CC [M]  /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o
/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: error: unknown field ‘ndo_set_multicast_list’ specified in initialiser
/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: warning: initialisation from incompatible pointer type [enabled by default]
/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: warning: (near initialisation for ‘wl_netdev_ops.ndo_validate_addr’) [enabled by default]
make[2]: *** [/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic'
make: *** [all] Error 2
robawalsh@Dell-Inspiron-N5110:/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112$ 

```Again, this "/usr/src/linux-headers-3.2.0-38-generic". Why won't it **make**?

P.S. Thanks for your help. The Ubuntu community is part of what makes Ubuntu so great =D>

---

### Post by chili555 on 2013-02-21
They are not the same and will likely conflict. I'd remove one and see if the wireless works as expected:```
sudo modprobe -r wl
```If all is well, use brcmsmac and remove wl:```
sudo apt-get remove --purge bcmwl-kernel-source
```If you unload wl and the wireless conks out, then wl is preferred and blacklist brcmsmac:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
```Find out by testing as above and apply whichever solution gives the best result; don't blindly apply either fix.> Again, this "/usr/src/linux-headers-3.2.0-38-generic". Why won't it make?
I suggest you reinstall the headers. ```
sudo apt-get install --reinstall linux-headers-3.2.0-38-generic
```Then make clean and make again. Any improvement?

The package in the repositories, bcmwl-kernel-source, should work perfectly. There is really no reason to build from source.

---

### Post by xSCCMx on 2013-02-21
Broadcom really does suck, I am typing this from a Dell Inspiron 1520 that used to have the Broadcom Wi-fi chip.

I recomend getting another wireless card that has an open source driver, I personally recommend Intel cards because they have boosted my wifi preformance.

---

### Post by chili555 on 2013-02-21
> **xSCCMx said:**
> Broadcom really does suck, I am typing this from a Dell Inspiron 1520 that used to have the Broadcom Wi-fi chip.

I recomend getting another wireless card that has an open source driver, I personally recommend Intel cards because they have boosted my wifi preformance.With the correct driver and no conflicts, Broadcoms work well.

---

### Post by robawalsh on 2013-02-21
> **chili555 said:**
> They are not the same and will likely conflict. I'd remove one and see if the wireless works as expected:```
sudo modprobe -r wl
```If all is well, use brcmsmac and remove wl:```
sudo apt-get remove --purge bcmwl-kernel-source
```If you unload wl and the wireless conks out, then wl is preferred and blacklist brcmsmac:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
```Find out by testing as above and apply whichever solution gives the best result; don't blindly apply either fix.

If I modprobe -r wl, the wifi cuts out, and comes back when I modprobe wl

But when I modprobe -r brcmsmac, the wifi doesn't cut out

Both wl and brcmsmac are in /etc/modules
brcmsmac is blacklisted (by the method you gave), but it seems to load anyway

I understand wl is the older, more generic and more reliable driver, and brcmsmac is newer and open-source, maybe better driver, but less reliable?

---

### Post by robawalsh on 2013-02-21
> **chili555 said:**
> I suggest you reinstall the headers. ```
sudo apt-get install --reinstall linux-headers-3.2.0-38-generic
```Then make clean and make again. Any improvement?


The reinstall failed. I am connected to the internet: 

```
robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install --reinstall linux-headers-3.2.0-38-generic
[sudo] password for robawalsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Reinstallation of linux-headers-3.2.0-38-generic is not possible, it cannot be downloaded.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
robawalsh@Dell-Inspiron-N5110:~$ 

```Something's wrong with my headers...

---

### Post by chili555 on 2013-02-21
> Both wl and brcmsmac are in /etc/modules
brcmsmac is blacklisted (by the method you gave), but it seems to load anywayIt loads anyway because its in /etc/modules. Please remove it. Reboot and see if your wireless works as expected. 

You might try:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

---

### Post by robawalsh on 2013-02-21
> **chili555 said:**
> It loads anyway because its in /etc/modules. Please remove it. Reboot and see if your wireless works as expected. 

You might try:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

OK, I removed brcmsmac from /etc/modules and rebooted, and all is working well. 

**sudo apt-get install --reinstall linux-headers-generic** was successful, it reinstalled

**sudo apt-get install --reinstall linux-headers-`uname -r`** , however, still doesn't download: 

```
robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install --reinstall linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-headers-3.2.0-38-generic is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by westie457 on 2013-02-21
@ chili555

Earlier Wild Man posted to a thread concerning another enquiry about the B4313 chip. In it he posted this link, not sure if it has any relevance to the issue in this current thread.

[http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)

---

### Post by chili555 on 2013-02-22
> Reinstallation of linux-headers-3.2.0-38-generic is not possible, it cannot be downloaded.What a stubborn little problem! I wonder if it is a locale issue; that is, if it isn't available on the Ubuntu servers selected in Software Sources. Please see attached. I suggest you try the USA servers and then run:```
sudo apt-get update
sudo apt-get install --reinstall linux-headers-`uname -r`
```If that doesn't do it, then let's try here: [http://packages.ubuntu.com/precise/linux-headers-3.2.0-38-generic](http://packages.ubuntu.com/precise/linux-headers-3.2.0-38-generic)

I believe yours is a 64-bit system, so be sure to get the amd64 package.

Download the package to your desktop. Then do:```
cd Desktop
sudo dpkg -i linux-headers*.deb
```Fingers crossed.

@ westie457-- I think we have the wireless part working now; again, fingers crossed, but that's excellent information and I'm glad to have it. Thanks!

---

### Post by robawalsh on 2013-02-23
> **chili555 said:**
> What a stubborn little problem! I wonder if it is a locale issue; that is, if it isn't available on the Ubuntu servers selected in Software Sources. Please see attached. I suggest you try the USA servers and then run:```
sudo apt-get update
sudo apt-get install --reinstall linux-headers-`uname -r`
```

This seems to have worked - I switched the server by selecting "Other" and then "Choose best server". The headers seemed to reinstall: 
```

robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get update
[sudo] password for robawalsh: 
Ign http://mirror.sov.uk.goscomb.net precise InRelease
Ign http://mirror.sov.uk.goscomb.net precise-updates InRelease                 
Ign http://mirror.sov.uk.goscomb.net precise-security InRelease                
Hit http://repository.spotify.com stable InRelease                             
Get:1 http://mirror.sov.uk.goscomb.net precise Release.gpg [198 B]             
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Get:2 http://mirror.sov.uk.goscomb.net precise-updates Release.gpg [198 B]     
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Get:3 http://mirror.sov.uk.goscomb.net precise-security Release.gpg [198 B]    
Get:4 http://mirror.sov.uk.goscomb.net precise Release [49.6 kB]               
Hit http://archive.canonical.com precise Release.gpg                           
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://mirror.sov.uk.goscomb.net precise-updates Release [49.6 kB]       
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://deb.opera.com stable InRelease                                      
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://deb.torproject.org precise InRelease                                
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://mirror.sov.uk.goscomb.net precise-security Release [49.6 kB]      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Get:8 http://mirror.sov.uk.goscomb.net precise/main Sources [934 kB]           
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://deb.torproject.org precise/main Sources                             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://deb.opera.com stable Release                                        
Hit http://deb.torproject.org precise/main amd64 Packages                      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://deb.torproject.org precise/main i386 Packages                       
Ign http://deb.torproject.org precise/main TranslationIndex                    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Get:9 http://mirror.sov.uk.goscomb.net precise/restricted Sources [5,470 B]    
Get:10 http://mirror.sov.uk.goscomb.net precise/universe Sources [5,019 kB]    
Hit http://ppa.launchpad.net precise/main Sources                              
Get:11 http://linux.dropbox.com precise Release.gpg [489 B]                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:12 http://linux.dropbox.com precise Release [2,603 B]                      
Ign http://deb.torproject.org precise/main Translation-en_GB                   
Ign http://deb.torproject.org precise/main Translation-en                      
Get:13 http://linux.dropbox.com precise/main amd64 Packages [1,148 B]          
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:14 http://linux.dropbox.com precise/main i386 Packages [1,148 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:15 http://mirror.sov.uk.goscomb.net precise/multiverse Sources [155 kB]    
Get:16 http://mirror.sov.uk.goscomb.net precise/main amd64 Packages [1,273 kB] 
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release.gpg                                    
Get:17 http://mirror.sov.uk.goscomb.net precise/restricted amd64 Packages [8,452 B]
Get:18 http://mirror.sov.uk.goscomb.net precise/universe amd64 Packages [4,786 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:19 http://mirror.sov.uk.goscomb.net precise/multiverse amd64 Packages [119 kB]
Get:20 http://mirror.sov.uk.goscomb.net precise/main i386 Packages [1,274 kB]  
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:21 http://mirror.sov.uk.goscomb.net precise/restricted i386 Packages [8,431 B]
Get:22 http://mirror.sov.uk.goscomb.net precise/universe i386 Packages [4,796 kB]
Get:23 http://mirror.sov.uk.goscomb.net precise/multiverse i386 Packages [121 kB]
Get:24 http://mirror.sov.uk.goscomb.net precise/main TranslationIndex [3,706 B]
Get:25 http://mirror.sov.uk.goscomb.net precise/multiverse TranslationIndex [2,676 B]
Get:26 http://mirror.sov.uk.goscomb.net precise/restricted TranslationIndex [2,596 B]
Get:27 http://mirror.sov.uk.goscomb.net precise/universe TranslationIndex [2,922 B]
Get:28 http://mirror.sov.uk.goscomb.net precise-updates/main Sources [367 kB]  
Get:29 http://mirror.sov.uk.goscomb.net precise-updates/restricted Sources [5,135 B]
Get:30 http://mirror.sov.uk.goscomb.net precise-updates/universe Sources [79.2 kB]
Get:31 http://mirror.sov.uk.goscomb.net precise-updates/multiverse Sources [4,725 B]
Get:32 http://mirror.sov.uk.goscomb.net precise-updates/main amd64 Packages [582 kB]
Get:33 http://mirror.sov.uk.goscomb.net precise-updates/restricted amd64 Packages [9,565 B]
Get:34 http://mirror.sov.uk.goscomb.net precise-updates/universe amd64 Packages [182 kB]
Get:35 http://mirror.sov.uk.goscomb.net precise-updates/multiverse amd64 Packages [9,421 B]
Get:36 http://mirror.sov.uk.goscomb.net precise-updates/main i386 Packages [593 kB]
Get:37 http://mirror.sov.uk.goscomb.net precise-updates/restricted i386 Packages [9,503 B]
Get:38 http://mirror.sov.uk.goscomb.net precise-updates/universe i386 Packages [184 kB]
Get:39 http://mirror.sov.uk.goscomb.net precise-updates/multiverse i386 Packages [10.4 kB]
Get:40 http://mirror.sov.uk.goscomb.net precise-updates/main TranslationIndex [3,564 B]
Get:41 http://mirror.sov.uk.goscomb.net precise-updates/multiverse TranslationIndex [2,605 B]
Get:42 http://mirror.sov.uk.goscomb.net precise-updates/restricted TranslationIndex [2,461 B]
Get:43 http://mirror.sov.uk.goscomb.net precise-updates/universe TranslationIndex [2,850 B]
Get:44 http://mirror.sov.uk.goscomb.net precise-security/main Sources [63.1 kB]
Get:45 http://mirror.sov.uk.goscomb.net precise-security/restricted Sources [1,950 B]
Get:46 http://mirror.sov.uk.goscomb.net precise-security/universe Sources [22.2 kB]
Get:47 http://mirror.sov.uk.goscomb.net precise-security/multiverse Sources [1,382 B]
Get:48 http://mirror.sov.uk.goscomb.net precise-security/main amd64 Packages [228 kB]
Get:49 http://mirror.sov.uk.goscomb.net precise-security/restricted amd64 Packages [3,969 B]
Get:50 http://mirror.sov.uk.goscomb.net precise-security/universe amd64 Packages [68.2 kB]
Get:51 http://mirror.sov.uk.goscomb.net precise-security/multiverse amd64 Packages [2,193 B]
Get:52 http://mirror.sov.uk.goscomb.net precise-security/main i386 Packages [237 kB]
Get:53 http://mirror.sov.uk.goscomb.net precise-security/restricted i386 Packages [3,968 B]
Get:54 http://mirror.sov.uk.goscomb.net precise-security/universe i386 Packages [69.9 kB]
Get:55 http://mirror.sov.uk.goscomb.net precise-security/multiverse i386 Packages [2,368 B]
Get:56 http://mirror.sov.uk.goscomb.net precise-security/main TranslationIndex [74 B]
Get:57 http://mirror.sov.uk.goscomb.net precise-security/multiverse TranslationIndex [71 B]
Get:58 http://mirror.sov.uk.goscomb.net precise-security/restricted TranslationIndex [71 B]
Get:59 http://mirror.sov.uk.goscomb.net precise-security/universe TranslationIndex [73 B]
Get:60 http://mirror.sov.uk.goscomb.net precise/main Translation-en_GB [96.4 kB]                 
Get:61 http://mirror.sov.uk.goscomb.net precise/main Translation-en [726 kB]                      
Get:62 http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en_GB [79.8 kB]            
Get:63 http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en [93.4 kB]               
Get:64 http://mirror.sov.uk.goscomb.net precise/restricted Translation-en_GB [2,406 B]            
Get:65 http://mirror.sov.uk.goscomb.net precise/restricted Translation-en [2,395 B]               
Get:66 http://mirror.sov.uk.goscomb.net precise/universe Translation-en_GB [5,492 B]              
Get:67 http://mirror.sov.uk.goscomb.net precise/universe Translation-en [3,341 kB]                
Get:68 http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en_GB [96.4 kB]          
Get:69 http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en [260 kB]              
Get:70 http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en_GB [79.8 kB]    
Get:71 http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en [5,694 B]       
Get:72 http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en_GB [2,406 B]    
Get:73 http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en [2,328 B]       
Get:74 http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en_GB [5,492 B]      
Get:75 http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en [108 kB]          
Get:76 http://mirror.sov.uk.goscomb.net precise-security/main Translation-en [111 kB]             
Get:77 http://mirror.sov.uk.goscomb.net precise-security/multiverse Translation-en [995 B]        
Get:78 http://mirror.sov.uk.goscomb.net precise-security/restricted Translation-en [978 B]        
Get:79 http://mirror.sov.uk.goscomb.net precise-security/universe Translation-en [43.2 kB]        
Hit http://dl.google.com stable/main amd64 Packages                                               
Hit http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main TranslationIndex
Hit http://dl.google.com stable/main amd64 Packages
Hit http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main TranslationIndex
Hit http://dl.google.com stable/main amd64 Packages
Hit http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Fetched 26.5 MB in 2min 11s (202 kB/s)
Reading package lists... Done
robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install --reinstall linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 985 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/main linux-headers-3.2.0-38-generic amd64 3.2.0-38.61 [985 kB]
Fetched 985 kB in 0s (2,381 kB/s)                  
(Reading database ... 604258 files and directories currently installed.)
Preparing to replace linux-headers-3.2.0-38-generic 3.2.0-38.61 (using .../linux-headers-3.2.0-38-generic_3.2.0-38.61_amd64.deb) ...
Unpacking replacement linux-headers-3.2.0-38-generic ...
Setting up linux-headers-3.2.0-38-generic (3.2.0-38.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Error! Bad return status for module build on kernel: 3.2.0-38-generic (x86_64)
Consult /var/lib/dkms/psmouse-alps/0.10/build/make.log for more information.
robawalsh@Dell-Inspiron-N5110:~$ 
```Apart from the ```
Error! Bad return status for module build on kernel: 3.2.0-38-generic (x86_64)
Consult /var/lib/dkms/psmouse-alps/0.10/build/make.log for more information.
```I would delete this if I knew how (I now have version 0.4), but I don't think this is the problem. 

But anyway, the headers looked reinstalled, and I tried compiling a package from source to test (nautilus-dropbox-1.4.0) and this seemed successful. 

Maybe the errors compiling the wireless drivers were more to do with something wrong with the commands used to build the drivers for my system

---

### Post by chili555 on 2013-02-23
> Maybe the errors compiling the wireless drivers were more to do with something wrong with the commands used to build the drivers for my systemI don't think so. Compiling a package of any kind, including wireless requires, among other things, linux-headers. If yours were not installed correctly for whatever reason, including luck, chance or the phase of the moon, then the package wouldn't build. Ergo, no wireless. > Consult /var/lib/dkms/[COLOR="Red"]psmouse-alps[/COLOR]/0.10/build/make.log for more information.I would do just that:```
less /var/lib/dkms/psmouse-alps/0.10/build/make.log
```I am not at all familiar with any source package for psmouse. I think this is an issue for General Help. [http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

Since you now have wireless, please use thread tools at the top to mark Solved.

---

