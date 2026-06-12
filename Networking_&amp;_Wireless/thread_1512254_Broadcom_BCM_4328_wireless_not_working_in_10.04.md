---
title: "Broadcom BCM 4328 wireless not working in 10.04"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by gtmaneki on 2010-06-17
A friend of mine has a Dell Inspiron 1501 laptop, and the wireless suddenly stopped working when she upgraded from Ubuntu 9.10 to 10.04.  The restricted Broadcom STA driver installs, but the computer cannot discover or connect to any wireless networks.

I ran 'lspci -vnn | grep 14e4' and got that it is a Broadcom Corporation BCM4328 with PCI-ID 14e4:4328.

I have tried the strategies at [http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979), [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43), and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20Internet%20Access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20Internet%20Access) with no luck (or I could have done something wrong).  I haven't tried ndiswrapper yet though.  

Any suggestions on getting the wireless working?

---

### Post by wheredidrealitygo on 2010-06-17
verify (with lsmod) that the b43 driver is not loaded, and if it is, remove it with rmmod. verify that the 'wl' ( lsmod | grep wl ) driver *is* being loaded.

more broadcom specific wireless help is located [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

I have this same exact chipset ( 14e4:4328 ) in my Macbook, and it works fine with the 'wl' driver, more stable than under OS X actually.

Good luck.

---

### Post by gtmaneki on 2010-06-25
> **wheredidrealitygo said:**
> verify (with lsmod) that the b43 driver is not loaded, and if it is, remove it with rmmod. verify that the 'wl' ( lsmod | grep wl ) driver *is* being loaded.

more broadcom specific wireless help is located [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

I have this same exact chipset ( 14e4:4328 ) in my Macbook, and it works fine with the 'wl' driver, more stable than under OS X actually.

Good luck.

Thanks for the advice.  It turns out that b43 was loaded and wl wasn't.  Following you suggestion, I ran the following:

```

sudo rmmod b43
sudo modprobe wl
sudo /etc/init.d/networking restart

```

So I rerun lsmod | grep wl and find it this time.  

However, wireless still isn't working.

---

### Post by gtmaneki on 2010-06-28
Well, now everything is working.  I would like to thank [earthpigg](http://ubuntuforums.org/showpost.php?p=9223467&postcount=21) and somebody else whose post I ran across while I was looking for solutions.

Here's what I did:
1. Reinstalled 10.04.
2. Booted 10.04, stuck the live CD, into the drive and mounted it.
3. Double-clicked on /media/Ubuntu 10.04 LTS i386/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb and tried to install it.  It told me I had one unmet dependency, dkms.
4. Double-clicked on /media/Ubuntu 10.04 LTS i386/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb and installed it.
5. Tried to install packages "bcmwl-kernel-source" and "bcmwl-modaliases," but got an error from apt-get.  So I installed the package "patch," which then allowed me to install the bcmwl packages.

Then boom! Wireless finally worked.  wheredidrealitygo was right that I needed the wl driver, but this was the only way I was able to get them working.

For the record, I also have the ssb module installed.  I'm glad ssb could also be loaded, since the b44 module controlling the wired networking depends on it.

---

### Post by gtmaneki on 2010-07-02
Well, I'm marking this thread back as unsolved, because the wireless quit working a few days later after I gave the laptop back.  I'm not sure what transpired in the meantime.

Here's the output from lsmod.  You can see that the ssb module is loaded, but the wireless has also worked while ssb was loaded.  wl is also loaded. b44 is for wired networking, and needs ssb in order to load.  See anything here that could be conflicting with wl?

```

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_idt      51914  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
b44                    25542  0 
ssb                    37336  1 b44
mii                     4381  1 b44
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7596  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
radeon                674135  3 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
wl                   1959598  0 
dell_wmi                1793  0 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
ati_agp                 5094  0 
sdhci_pci               5470  0 
dell_laptop             6856  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
sdhci                  15462  1 sdhci_pci
led_class               2864  1 sdhci
dcdbas                  5422  1 dell_laptop
ricoh_mmc               2923  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
k8temp                  3024  0 
agpgart                31724  3 ttm,drm,ati_agp
i2c_piix4               8335  0 
shpchp                 28820  0 
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32008  3 
pata_atiixp             3148  0 

```

I also tried reinstalling the bcmwl packages with "sudo apt-get install --reinstall bcmwl*", with the output below:

```

Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting bcmwl-kernel-source for regex 'bcmwl*'
Note, selecting bcmwl-modaliases for regex 'bcmwl*'
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0B/905kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 125018 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace bcmwl-modaliases 5.60.48.36+bdcom-0ubuntu3 (using .../bcmwl-modaliases_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Unpacking replacement bcmwl-modaliases ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-21-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Setting up bcmwl-modaliases (5.60.48.36+bdcom-0ubuntu3) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic

```

---

### Post by subru77 on 2010-07-06
> **gtmaneki said:**
> 
Here's what I did:
1. Reinstalled 10.04.
2. Booted 10.04, stuck the live CD, into the drive and mounted it.
3. Double-clicked on /media/Ubuntu 10.04 LTS i386/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb and tried to install it.  It told me I had one unmet dependency, dkms.
4. Double-clicked on /media/Ubuntu 10.04 LTS i386/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb and installed it.
5. Tried to install packages "bcmwl-kernel-source" and "bcmwl-modaliases," but got an error from apt-get.  So I installed the package "patch," which then allowed me to install the bcmwl packages.


This worked for me .. Thanks . Hope it does not stop working later :)

---

### Post by gtmaneki on 2010-07-20
> **subru77 said:**
> This worked for me .. Thanks . Hope it does not stop working later :)

Awesome!  I hope it stays working.  

I've given up on getting the broadcom wireless working.  Instead, I bought my friend a [USB wireless adapter](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122321) and that works just fine -- I plugged it in, and it worked perfectly.  I'm going to mark this thread as solved, although it was solved by a suboptimal method.

Cheers, y'all.

---

### Post by cyberctrl on 2011-01-25
Duuuuude!!!
thanks!!!was trying this the whole day and I solved it based on your post!
thanks

---

### Post by ajitubunt on 2012-05-11
Just simplifying this as it worked for me.

open Terminal and type following comands...
sudo apt-get update
sudo apt-get install patch
sudo apt-get install dkms
sudo apt-get install bcmwl-kernel-source

Last command will take little longer. Once done, reboot. You are good to go now.

---

