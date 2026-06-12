---
title: "MythTV with multiple HVR-2200 cards"
date: 2011-11-13
forum: Multimedia Software
---

### Post by flickyll on 2011-11-13
Hello,
 
I have ubuntu 11.10 64-bit installed and have loaded Myth TV.  After reading numerous forums, I have managed to get one of my Hauppauge HVR-2200 cards recognised.  However, I get the following output from dmesg | grep 7164:
 
```

[    0.973004] pci 0000:01:00.0: [1131:7164] type 0 class 0x000480
[    0.977644] pci 0000:02:00.0: [1131:7164] type 0 class 0x000480
[    0.985641] pci 0000:03:00.0: [1131:7164] type 0 class 0x000480
[    7.107435] saa7164 driver loaded
[    7.107476] saa7164 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.108903] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[    7.108906] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb800000
[    7.108910] saa7164 0000:01:00.0: setting latency timer to 64
[    7.279996] saa7164_downloadfirmware() no first image
[    7.280006] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    7.331473] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    7.331475] saa7164_downloadfirmware() firmware loaded.
[    7.331492] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    7.331498] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    7.331499] saa7164_downloadfirmware() BSLSize = 0x0
[    7.331500] saa7164_downloadfirmware() Reserved = 0x0
[    7.331502] saa7164_downloadfirmware() Version = 0x1661c00
[   12.824146] saa7164_downloadimage() Image downloaded, booting...
[   12.927849] saa7164_downloadimage() Image booted successfully.
[   14.966025] saa7164_downloadimage() Image downloaded, booting...
[   16.625277] saa7164_downloadimage() Image booted successfully.
[   16.669533] tveeprom 17-0000: audio processor is SAA7164 (idx 43)
[   16.669534] tveeprom 17-0000: decoder processor is SAA7164 (idx 40)
[   16.669536] saa7164[0]: Hauppauge eeprom: model=89619
[   16.981500] DVB: registering new adapter (saa7164)
[   19.602987] DVB: registering new adapter (saa7164)
[   19.603216] saa7164[0]: registered device video0 [mpeg]
[   19.832658] saa7164[0]: registered device video1 [mpeg]
[   20.043781] saa7164[0]: registered device vbi0 [vbi]
[   20.043817] saa7164[0]: registered device vbi1 [vbi]
[   20.045613] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.045616] saa7164[1]: Your board isn't known (yet) to the driver.
[   20.045616] saa7164[1]: Try to pick one of the existing card configs via
[   20.045617] saa7164[1]: card=<n> insmod option.  Updating to the latest
[   20.045617] saa7164[1]: version might help as well.
[   20.045676] saa7164[1]: Here are valid choices for the card=<n> insmod option:
[   20.045693] saa7164[1]:    card=0 -> Unknown
[   20.045704] saa7164[1]:    card=1 -> Generic Rev2
[   20.045716] saa7164[1]:    card=2 -> Generic Rev3
[   20.045728] saa7164[1]:    card=3 -> Hauppauge WinTV-HVR2250
[   20.045742] saa7164[1]:    card=4 -> Hauppauge WinTV-HVR2200
[   20.045755] saa7164[1]:    card=5 -> Hauppauge WinTV-HVR2200
[   20.045769] saa7164[1]:    card=6 -> Hauppauge WinTV-HVR2200
[   20.045783] saa7164[1]:    card=7 -> Hauppauge WinTV-HVR2250
[   20.045797] saa7164[1]:    card=8 -> Hauppauge WinTV-HVR2250
[   20.047152] CORE saa7164[1]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]
[   20.047156] saa7164[1]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb000000
[   20.047163] saa7164 0000:02:00.0: setting latency timer to 64
[   20.047172] saa7164_initdev() Unsupported board detected, registering without firmware
[   20.047208] saa7164 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.047210] saa7164[2]: Your board isn't known (yet) to the driver.
[   20.047210] saa7164[2]: Try to pick one of the existing card configs via
[   20.047211] saa7164[2]: card=<n> insmod option.  Updating to the latest
[   20.047211] saa7164[2]: version might help as well.
[   20.047267] saa7164[2]: Here are valid choices for the card=<n> insmod option:
[   20.047284] saa7164[2]:    card=0 -> Unknown
[   20.047295] saa7164[2]:    card=1 -> Generic Rev2
[   20.047307] saa7164[2]:    card=2 -> Generic Rev3
[   20.047319] saa7164[2]:    card=3 -> Hauppauge WinTV-HVR2250
[   20.047332] saa7164[2]:    card=4 -> Hauppauge WinTV-HVR2200
[   20.047346] saa7164[2]:    card=5 -> Hauppauge WinTV-HVR2200
[   20.047360] saa7164[2]:    card=6 -> Hauppauge WinTV-HVR2200
[   20.047374] saa7164[2]:    card=7 -> Hauppauge WinTV-HVR2250
[   20.047387] saa7164[2]:    card=8 -> Hauppauge WinTV-HVR2250
[   20.048717] CORE saa7164[2]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]
[   20.048721] saa7164[2]/0: found at 0000:03:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfa800000
[   20.048727] saa7164 0000:03:00.0: setting latency timer to 64
[   20.048742] saa7164_initdev() Unsupported board detected, registering without firmware

```
 
I have the latest firmware installed in /lib/firmware, although it doesn't seem to make any difference as to whether it is here or in /lib/firmware/`uname -r`.  These files are:
 
NXP7164-2010-03-10.1.fw
v4l-saa7164-1.0.2-3.fw
v4l-saa7164-1.0.3-3.fw
 
The only way I got the first card recognised was to edit /etc/modprobe.d/options.conf and put in:
 
```
options saa7164 card=4
```
 
I also tried card=5 and card=6, which made no difference.
 
Does anyone have any suggestions as to what I can try to get the other two cards working?  If you need me to supply the output from any commands, I am happy to do so.
 
Thanks and regards,
Flickyll

---

### Post by flickyll on 2011-11-19
SOLVED!!!  :D  Nothing worse than trolling Google results for hours with no real answers, so here's what I did:

Stripped off Oneiric (Ubuntu 11.10) and loaded up Lucid (Ubuntu 10.4.3).  This was the critical bit!
Created a directory in my home directory in which to do everything to follow:
```

mkdir hvr2200_setup
cd hvr2200_setup

```Of the following, I just installed mercurial but it probably doesn't hurt to get the rest:
```

sudo apt-get install mercurial libncurses5-dev unzip

```If you are behind a proxy, set the http_proxy environment variable with the following:
```
export http_proxy=http://username:password@host:port
```Note:  not all proxies require a username/password pair.

```

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh

```You can also retrieve the above via your favorite web browser if you prefer.

```

sh extract.sh
sudo cp *fw /lib/firmware

```Note:  the extract.sh script will tell you to put the files in /lib/firmware/`uname -r`.  Apparently, if you put them in /lib/firmwre, they are not affected by kernel changes/upgrades.  Certainly seems to work OK for me in the parent directory.

```

hg clone http://kernellabs.com/hg/saa7164-stable

```There is a development version available, but I found the stable tree worked just fine.  If you are behind a proxy, make sure you have correctly set your http_proxy environment variable or hg clone won't work for you.  There is a gz available at the above site which you can access via a web browser, but I went for the hg clone myself (because I didn't know if the gz file was an accurate/up-to-date representation of the tree.)

```

cd saa7164-stable
make CONFIG_DVB_FIREDTV:=n
sudo make install
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.2-3.fw
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp v4l-saa7164-1.0.*-3.fw /lib/firmware
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware
sudo reboot

```It is worth noting if you stuff up the make command, you can do a
```
make distclean
```
before the
```
make CONFIG_DVB_FIREDTV:=n
```
to clean down any garbage from the bad make.

Of the above, I'm not entirely certain any more than the NXP firmware file is required.  However, after hours of tearing my hair out, I took no chances and copied everything across.

I found an excellent discussion of this at the Australian Media Centre community.  In particular, the posts of ZeSurfer at [http://www.pcmediacenter.com.au/forum/topic/37541-hauppauge-hvr-2200-tuner-install-guide/page__hl__%2Bhauppauge+%2Bhvr%3D2200+%2Btuner+%2Binstall+%2Bguide__st__60](http://www.pcmediacenter.com.au/forum/topic/37541-hauppauge-hvr-2200-tuner-install-guide/page__hl__%2Bhauppauge+%2Bhvr%3D2200+%2Btuner+%2Binstall+%2Bguide__st__60).

Again, this ran like a dream under Lucid.  I would love to see it working on the latest kernel, but as this is just for a HTPC box, it's really not that big a deal for me.  Far more important for the tuners to work!

I hope you find the above useful.

Cheers,
Flickyll

---

### Post by flickyll on 2012-06-16
Hi again,

After an upgrade to 12.04 recently, I thought I would share my thoughts.

In short, go for 12.04!!!  :D

It looks like the drivers are now in the kernel, so you can skip all the compilation stuff in my earlier post.  Very nice for those who are not programmers and don't know how to fix the copious error messages generated in versions 11.x.

I still had to grab the firmware from [www.steventoth.net](www.steventoth.net) and copy it to /lib/firmware, but that's a no-brainer.

I did find 12.04 to be slightly less stable than 11.04 early on, but that's not really surprising with a new release.  A couple of months in and things seem to be settling down nicely.  That said, it was orders of magnitude easier to get all my hardware behaving in harmony in this release.

Cheers,
Flickyll

---

