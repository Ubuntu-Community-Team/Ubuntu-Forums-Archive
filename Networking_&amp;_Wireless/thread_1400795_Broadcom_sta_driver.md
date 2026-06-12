---
title: "Broadcom sta driver"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by KegHead on 2010-02-07
Hi!

After a recent update I can't load the broadcom sta driver.

Message:

see  /var/log/jockey.log

Can anyone help!??

Thanks!
Head

Keg

---

### Post by chili555 on 2010-02-07
Please do:```
sudo cat /var/log/jockey.log | grep rt2
```Let's see what the message is.

---

### Post by KegHead on 2010-02-07
Hi!

No output via command in terminal.

KegHead

---

### Post by chili555 on 2010-02-07
Then how about:```
dmesg | grep rt2
```Thanks.

---

### Post by KegHead on 2010-02-07
zero

---

### Post by chili555 on 2010-02-07
Pardon me, I made a mistake. Sorry. Let's just see:```
sudo cat /var/log/jockey.log
```

---

### Post by KegHead on 2010-02-07
nada

---

### Post by chili555 on 2010-02-07
Was the Broadcom STA driver *wl*? Please post:```
lsmod

```Do you have internet connectivity through wired ethernet?

---

### Post by KegHead on 2010-02-07
jim@jim-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 38208  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
iptable_filter          3100  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
dell_wmi                2564  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                56500  0 
serio_raw               5280  0 
compal_laptop           3728  0 
dcdbas                  7292  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms               9600  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               10072  1 jmb38x_ms
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  1 sdhci
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
jim@jim-laptop:~$

---

### Post by chili555 on 2010-02-07
I found this:  [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630)

I was especially interested in this:> I have solved the problem by removing linux-backports-modules-2.6.31-1-generic which contained the bogus lib80211.ko. I have no idea why I installed that package in the first place. Now wl.ko loads correctly (and automatically)I suggest you try:```
sudo apt-get remove linux-backports-modules-*
sudo modprobe wl
iwconfig
```Is your wireless back?

---

### Post by KegHead on 2010-02-07
no

jim@jim-laptop:~$ sudo apt-get remove linux-backports-modules-*
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting linux-backports-modules-alsa-2.6.31-19-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-karmic-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-14-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-karmic-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-18-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-wireless-karmic-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-karmic-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-15-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-17-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-14-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-18-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-headers-karmic-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-16-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-17-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-headers-karmic-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-19-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-wireless-karmic-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-15-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-16-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-18-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-15-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-19-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-17-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-18-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-14-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-karmic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-17-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-16-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-14-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-19-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-alsa-2.6.31-16-generic for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-2.6.31-15-generic-pae for regex 'linux-backports-modules-*'
Note, selecting linux-backports-modules-karmic-generic for regex 'linux-backports-modules-*'
The following packages will be REMOVED:
  linux-backports-modules-2.6.31-19-generic linux-backports-modules-karmic
  linux-backports-modules-karmic-generic
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 4,841kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140748 files and directories currently installed.)
Removing linux-backports-modules-karmic ...
Removing linux-backports-modules-karmic-generic ...
Removing linux-backports-modules-2.6.31-19-generic ...
Bus error
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Bus error


jim@jim-laptop:~$ sudo modprobe wl
FATAL: Module wl not found.
jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jim@jim-laptop:~$

---

### Post by chili555 on 2010-02-07
> Removing linux-backports-modules-2.6.31-19-generic ...
Bus error
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Bus errorI have never seen this before. Please try:```
sudo apt-get -f update
```Also please look in Synaptic and see if all instances of linux-backports-modules are actually removed and if bcmwl-kernel-source is installed. Please fix.

---

### Post by KegHead on 2010-02-07
Hi!

Performed request.

jim@jim-laptop:~$ sudo apt-get -f update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [900B]                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages
Fetched 3,629B in 1s (2,860B/s)
Reading package lists... Done
jim@jim-laptop:~$

---

### Post by KegHead on 2010-02-08
Hi!

Anyone?

KegHead

---

### Post by chili555 on 2010-02-08
Did it work to add the module *wl*?```
sudo modprobe wl
iwconfig
```Is your wireless back?

---

### Post by KegHead on 2010-02-08
no,

jim@jim-laptop:~$ sudo modprobe wl
FATAL: Module wl not found.
jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jim@jim-laptop:~$

---

### Post by northd_tech on 2010-02-08
Hi KegHead,

Have you tried downloading the STA driver directly from Broadcom and compiling it?  You will need to get the correct version (32-bit *vs.* 64-bit):

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Here is an informative thread about the Broadcom chipsets:

[http://ubuntuforums.org/showthread.php?t=1368699&page=3](http://ubuntuforums.org/showthread.php?t=1368699&page=3)

You also might need to manually install wireless tools and 1 or 2 other packages for WEP/WPA access.

---

### Post by KegHead on 2010-02-08
Hi!

Broadcom sta wireless driver.

 Now it shows that the driver is active but not in use.

KegHead

---

### Post by worldsayshi on 2010-02-08
I also have problems with Broadcom STA driver. Worked fine until some recent update. 

It finds the networks but can't connect to them. Asks me for the passphrase over and over. In the "Hardware Drivers" dialogue "removing" the driver doesn't seem to make any difference, it behaves the same (not sure if reboot is required to disable the driver), as if some other native driver (not suited) is used in stead and in either case.

---

### Post by chili555 on 2010-02-08
> **KegHead said:**
> Hi!

Broadcom sta wireless driver.

 Now it shows that the driver is active but not in use.

KegHeadIs your ethernet active? If you disconnect the ethernet, can you click and activate the wireless driver?

---

### Post by KegHead on 2010-02-09
Hi!

It's hard to believe, but I turned on my Dell mini 9 and the wireless fired up this morning.

It must of been a gremlin or ghost lurking around.

Go figure!

BTW-Thanks for all the help!

KegHead

---

### Post by DrDaveyAtoms on 2010-02-09
Glad to hear it finally works KegHead. I had the same problem which I fought with for about a week. It felt very satisfying to see the wireless strength bar appear on my Linux desktop!

If anyone else is having this problem please check out [http://ubuntuforums.org/showthread.php?t=1398937&highlight=DrDaveyAtoms](http://ubuntuforums.org/showthread.php?t=1398937&highlight=DrDaveyAtoms) where I have given a description of how I solved it.

---

### Post by KegHead on 2010-02-09
copy.

KegHead

---

