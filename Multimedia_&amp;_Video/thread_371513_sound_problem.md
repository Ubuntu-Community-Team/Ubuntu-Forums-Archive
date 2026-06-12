---
title: "sound problem"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by sauravbhaumik on 2007-02-27
In Ubuntu, I get the same volume of sound with master volume = 58% as I get in Windows with master volume = 7%

Why is the difference? Is it normal or else, a fault of my own copy of Ubuntu?
In the volume control ->edit ->preference, I checked all and maximized them. No improvement.
My volume applet : ```
Volume Applet 2.16.1
Volume control for your GNOME Panel.

Using GStreamer 0.10.
© 2004 Ronald Bultje
```
Any help?

---

### Post by renzokuken on 2007-02-27
run the following command from the terminal and play with the settings

```
alsamixer
```

let me know if it makes any difference.

do you know what audio chipset you have?

```
lspci
```
should give some info on it

---

### Post by sauravbhaumik on 2007-02-27
alsamixer was okay, no problem was found there.

Here is the output of lspci:```
saurav@saurav:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
saurav@saurav:~$ 

```

May be you can help me.
Thanks.

---

### Post by renzokuken on 2007-02-28
ok, thanks......so it appears you have an intel sound chipset, could you now run

```
lsmod
```
so we can see which driver/module the soundchip is using

also, are you using gstreamer or alsa for sound? go to System -> Admin -> Sound and see which engine you are using. if its using gstreamer or oss then try alsa instead

---

### Post by sauravbhaumik on 2007-02-28
```
saurav@saurav:~$ lsmod
Module                  Size  Used by
isofs                  38076  0 
udf                    89348  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
i915                   21632  2 
drm                    74644  3 i915
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ieee80211              35272  0 
ieee80211_crypt         7552  1 ieee80211
af_packet              24584  0 
nls_iso8859_1           5248  2 
nls_cp437               6912  2 
vfat                   14720  2 
fat                    56348  1 vfat
lp                     12964  0 
tsdev                   9152  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
psmouse                41352  0 
evdev                  11392  1 
serio_raw               8452  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
8139cp                 24832  0 
8139too                29056  0 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
floppy                 63044  0 
mii                     6912  2 8139cp,8139too
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4352  0 
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
hw_random               7320  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
i2c_i810                6276  0 
i2c_algo_bit           10376  1 i2c_i810
i2c_core               23424  2 i2c_ec,i2c_algo_bit
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
piix                   11780  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
saurav@saurav:~$ 


```

Thanks.
I use alsa. But as my Ubuntu is 6.10 edgy, there is no sound option in system->administration.
Thank you very much. May be this time you can help me fix my problem.

---

### Post by renzokuken on 2007-02-28
well you appear to be using appropriate drivers.

my suggestion would be to compile the latest alsa-driver from source. the latest is 1.0.14rc2 which has much better support for newer hardware than 1.0.12 which comes with edgy. cant promise it will fix anything but it worked for my sound problems

its very easy to do

get the latest alsa-driver (1.0.14rc2) from [www.alsa-project.org](www.alsa-project.org)

extract it

```

sudo apt-get install build-essential
cd /path/to/extracted/alsa-driver/folder
./configure
make
sudo make install

```

reboot and see if anything improves

EDIT: you may also need to install the kernel-headers for your kernel.

---

### Post by sauravbhaumik on 2007-02-28
Well I did all these but I think there is something wrong. After the installation of a sound driver and reboot, the sound is muted by default. But in this case, actually NO change was observed.
May be the sound driver is not the culprit. 
In suse linux 10.1, I get the sound as loud as in Ubuntu. But in windows environment, the sound is many times louder.
What makes linux lagging?
Can you suggest something more?

---

### Post by renzokuken on 2007-02-28
sorry, this is probably out of my limited abilities now.

have you tried googling or checking the ubuntu bugs page ( [http://launchpad.net](http://launchpad.net) ) for your specific hardware?

EDIT: my only other suggestion would be to try and compile alsa-driver again using the following line instead

```
./configure --with-cards=hda-intel
```

---

### Post by ozPATT on 2007-03-01
hi, i followed your steps above, to compile 1.0.13 as that is the latest stable release. I restarted, and i get to the login screen, put in my details, and then when I continue, it just hangs...

i restarted using kernel -10 instead of -11 and it restarted for me but the configuration I did as above didnt have any effect on that kernel. The without thinking, I went ahead and recompiled using the -10 kernel.. now both of them hang when logging in. 

Urgent help requested on this. It seems that the basic functions of my laptop such as headphones, are better left broken :(

I can log in using safe mode, and everything is command line stuff, i can view all my folders and files, but I dont know how to fix it

Please help

Patrick

---

