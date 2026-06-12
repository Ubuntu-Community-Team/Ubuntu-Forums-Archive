---
title: "wireless not working"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by pabrachan on 2010-10-14
I was really delighted with the user friendliness of the ubuntu 10 installation procedure. I could do it myself without any ones help. Unfortunately the wireless connection is not working. I am using a acer aspire 4820T computer. When I try to connect, it says no devices detected. please help.

Here are some more details about my system, I got by executing the commands recommended in other posts in this forum. I hope it will help you to give me a solution. I am very non technical. So please help. 

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

abrachan@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05) 
01:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0) 
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01) 
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02) 
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02) 
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02) 
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02) 
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02) 
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02) 
abrachan@ubuntu:~$ 
abrachan@ubuntu:~$ 
abrachan@ubuntu:~$ lsusb 
Bus 002 Device 004: ID 19d2:fff5 ONDA Communication S.p.A. 
Bus 002 Device 003: ID 046d:c510 Logitech, Inc. Cordless Mouse 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 005: ID 064e:a219 Suyin Corp. 
Bus 001 Device 004: ID 054c:0439 Sony Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
abrachan@ubuntu:~$ 
abrachan@ubuntu:~$ 
abrachan@ubuntu:~$ lshw -c 
Hardware Lister (lshw) - B.02.14 
usage: lshw [-format] [-options ...] 
       lshw -version 

	-version        print program version (B.02.14) 

format can be 
	-html           output hardware tree as HTML 
	-xml            output hardware tree as XML 
	-short          output hardware paths 
	-businfo        output bus information 

options can be 
	-class CLASS    only show a certain class of hardware 
	-C CLASS        same as '-class CLASS' 
	-c CLASS        same as '-class CLASS' 
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
	-quiet          don't display status 
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.) 
	-numeric        output numeric IDs (for PCI, USB, etc.) 

abrachan@ubuntu:~$ lshw -c network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: AR8151 v1.0 Gigabit Ethernet 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: c0 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
       resources: memory:d3400000-d343ffff ioport:2000(size=128) 
  *-network UNCLAIMED 
       description: Network controller 
       product: Broadcom Corporation 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
       resources: memory:d2400000-d2403fff 
abrachan@ubuntu:~$ 
abrachan@ubuntu:~$ 
abrachan@ubuntu:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB) 

abrachan@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

abrachan@ubuntu:~$ lsmud 
No command 'lsmud' found, did you mean: 
 Command 'lsmod' from package 'module-init-tools' (main) 
lsmud: command not found 
abrachan@ubuntu:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
udf                    85529  1 
crc_itu_t               1715  1 udf 
vfat                   10866  1 
fat                    55350  1 vfat 
nls_utf8                1421  2 
isofs                  33399  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279040  1 
joydev                 11072  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon 
font                    8053  1 fbcon 
bitblit                 5811  1 fbcon 
softcursor              1565  1 bitblit 
vga16fb                12757  0 
vgastate                9857  1 vga16fb 
snd_hda_intel          25677  2 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               6924  1 snd_hda_codec 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss 
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              23649  2 snd_pcm,snd_seq 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
i915                  321160  3 
snd                    71106  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
uvcvideo               62467  0 
videodev               40518  1 uvcvideo 
v4l1_compat            15495  2 uvcvideo,videodev 
v4l2_compat_ioctl32    12020  1 videodev 
psmouse                64576  0 
serio_raw               4918  0 
acer_wmi               15829  0 
soundcore               8052  1 snd 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
led_class               3764  1 acer_wmi 
drm_kms_helper         30742  1 i915 
drm                   199204  4 i915,drm_kms_helper 
i2c_algo_bit            6024  1 i915 
video                  20623  1 i915 
output                  2503  1 video 
lp                      9336  0 
parport                37160  2 ppdev,lp 
intel_agp              29095  2 i915 
usbhid                 41084  0 
hid                    83440  1 usbhid 
usb_storage            49833  2 
ahci                   37870  2 
abrachan@ubuntu:~$

---

### Post by yourbuddyrohan on 2010-10-14
I am facing same issue. However when I boot with 2.6.32.25 header image, wireless works fine.

---

### Post by eslim80 on 2010-10-14
Hi Sir..what you mean by reboot "with 2.6.32.25 header image" then wireless working fine? How to get the image? I am using aspire 4310 and now facing the same problems too...errrrrrrrrrrrrr

---

### Post by nlsthzn on 2010-10-14
[S]Greetings... from this forum post [here]("http://ubuntuforums.org/showthread.php?t=1453370&page=2") on Ubuntu Forums they mention two possible solutions...

Try [this one]("http://ubuntuforums.org/showthread.php?t=1447901") and/or [this one]("http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/") and see how that goes... (Please note both these are assuming you have an Atheros AR928x network card in your Asus...)

You can run "lspci | more" in a terminal to see what card you have and if not the an Atheros AR928x you can give us that info so long :)[/S]

Ninja edit: See you gave the output of lspci and you have a Broadcom and not Atheros card so nothing I pasted above is relevant... sorry...

---

### Post by yourbuddyrohan on 2010-10-18
> **eslim80 said:**
> Hi Sir..what you mean by reboot "with 2.6.32.25 header image" then wireless working fine? How to get the image? I am using aspire 4310 and now facing the same problems too...errrrrrrrrrrrrr
I upgraded from Lucid to Maverick, 2.6.32.25 header image was installed in Lucid.

---

### Post by johnnytm on 2010-10-18
can u post the results from```
[SIZE=3]lspci -nn | grep 'Broadcom'[/SIZE]
```[SIZE=3] and ```
ifconfig
``` 
[/SIZE]

---

