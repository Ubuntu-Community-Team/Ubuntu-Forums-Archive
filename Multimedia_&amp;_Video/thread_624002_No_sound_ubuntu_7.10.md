---
title: "No sound ubuntu 7.10"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by Synth3t1c on 2007-11-26
So I have no sound in gutsy.  What gives?  I installed gutsy earlier in the semester and I had sound, now I can't figure out what gives!?

lspci:
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

```

Anyone know how to fix it?


PCM volume is up as well

---

### Post by Synth3t1c on 2007-11-27
bump

---

### Post by Mixmastermichael on 2007-11-27
Yeah I am having the same problem, it was working fine until about a week ago.  I am using a Dell 9100.

If you could somehow help me out, I would really appreciate it.

---

### Post by nzadLithium on 2007-11-27
can both of you post your output from lsmod?

---

### Post by surg30n on 2007-11-27
> **Synth3t1c said:**
> So I have no sound in gutsy.  What gives?  I installed gutsy earlier in the semester and I had sound, now I can't figure out what gives!?

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

Anyone know how to fix it?


Try to build alsa from source

[http://alsa-project.org/main/index.php/Matrix:Vendor-ATI](http://alsa-project.org/main/index.php/Matrix:Vendor-ATI)

---

### Post by Yellow Pasque on 2007-11-27
If you can't get ALSA working, make sure you try OSSv4 before reinstalling the OS or switching to another one. See the link in my sig.

---

### Post by Synth3t1c on 2007-11-27
> **Temüjin said:**
> If you can't get ALSA working, make sure you try OSSv4 before reinstalling the OS or switching to another one. See the link in my sig.

i did what the sig said, but here are my problems:

1.) the launcher panel thing does nothing
2.) my hotkeys on my keyboard now do nothing (i.e., mute, change volume, etc...)

basically thats it...

---

### Post by Yellow Pasque on 2007-11-27
I'm not sure about 2), but to fix 1) you need to remove the mixer icon from your toolbar and add a custom application launcher for ossxmix in its place.

> You need to control the volume with a program called ossxmix. You can manually run it by typing ossxmix in a terminal. Here's how to replace your current volume/speaker icon with the correct one:
Remove your current volume icon from the panel. (Right click it for that option)
Then right click on the empty space left behind and select "Add to Panel"
Click the button that says custom app launcher.
In the command field, type ossxmix -d0
Select whatever name and icon you want (I use /usr/share/icons/gnome/32x32/status/stock_volume-max.png for the icon and "Mixer" for the name)
And, of course, hit OK.

---

### Post by dustman on 2007-11-27
hello!

I have the same problem. After the upgrade to gutsy gibbon, the sound is no longer working. It was working fine in feisty. 
```
lspci
``` give me:
```
dustman@dustman-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

```

If i try to enter "alsamixer" my primary device looks muted, but i cannot increase the volume (I've attached a screenshot of alsamixer). 


Cheers!


Radu

---

### Post by Synth3t1c on 2007-11-27
> **Temüjin said:**
> I'm not sure about 2), but to fix 1) you need to remove the mixer icon from your toolbar and add a custom application launcher for ossxmix in its place.
can you tell me how to use ossmix? like a diagram with text added in gnome paint or something.

---

### Post by nzadLithium on 2007-11-27
are we trying to fix these peoples alsa or just trying to convert them to oss?

and i would like to point out the oss sound mixing is alot messier than alsa (which just goes :) ) can sound mixing in oss even be done??

---

### Post by nzadLithium on 2007-11-27
and can someone plz post the output of lsmod. It's great that you guys all want to post lspci because that tells us what card you have but there are things in between your card and sound output it doesnt go direct... like the modules!

---

### Post by dustman on 2007-11-27
output of lsmod:

```
Module                  Size  Used by
ipv6                  273892  8
binfmt_misc            12936  1
af_packet              24840  4
fglrx                 656352  25
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0
autofs4                23044  0
cpufreq_userspace       5280  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9612  0
cpufreq_stats           7232  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0
button                  8976  0
sbs                    19592  0
container               5504  0
ac                      6148  0
dock                   10656  0
video                  18060  0
battery                11012  0
sbp2                   24072  0
parport_pc             37412  0
lp                     12580  0
parport                37448  3 ppdev,parport_pc,lp
pcmcia                 41388  0
joydev                 11328  0
usbhid                 29536  0
8139too                27776  0
yenta_socket           27532  1
rsrc_nonstatic         14080  1 yenta_socket
hid                    28928  1 usbhid
pcspkr                  4224  0
snd_hda_intel         263712  1
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
ide_cd                 32672  0
cdrom                  37536  1 ide_cd
snd_pcm                80388  1 snd_hda_intel
snd_timer              24324  1 snd_pcm
snd                    54660  5 snd_hda_intel,snd_pcm,snd_timer
soundcore               8800  1 snd
psmouse                39952  0
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
serio_raw               8068  0
shpchp                 34580  0
i2c_piix4               9740  0
i2c_core               26112  1 i2c_piix4
pci_hotplug            32704  1 shpchp
ati_agp                10124  0
agpgart                35016  2 fglrx,ati_agp
evdev                  11136  4
ext3                  133896  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sd_mod                 30336  4
8139cp                 25088  0
mii                     6528  2 8139too,8139cp
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
atiixp                  7056  0 [permanent]
ide_core              116804  2 ide_cd,atiixp
ehci_hcd               36492  0
ohci_hcd               22916  0
usbcore               138632  4 usbhid,ehci_hcd,ohci_hcd
sata_sil               12168  3
ata_generic             8452  0
libata                125168  2 sata_sil,ata_generic
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor

```

hope this helps :D

---

### Post by Yellow Pasque on 2007-11-27
> **Synth3t1c said:**
> can you tell me how to use ossmix? like a diagram with text added in gnome paint or something.

Read carefully, the command is oss**x**mix, not ossmix ;)

> are we trying to fix these peoples alsa or just trying to convert them to oss?
We're trying to get their sound fixed. Using OSSv4 is a means to this end. I recommend trying to fix ALSA first, and then trying OSS as an alternative. As I say when I offer the solution: "Before you reinstall your OS or switch to another..." How soon in the troubleshooting process users do this depends on their patience and whether they look at the procedure to install OSS and perceive it as easier than fixing ALSA.

---

### Post by nzadLithium on 2007-11-27
ok so the sound modules are in place but im not sure there the right ones. all of them have intel written all over. I'll have a look later tonight and see if i can find out whats going on.

Temujin i didnt mean to make that look like it targeted you i was kinda annoyed that people were impatient and automatically decided they were going to use oss even though they probably have no idea of the differences between alsa and oss and how much of a disadvantage it is to switch.

---

### Post by limac on 2007-11-27
try this, it SHOULD work 4 u. NOTE: while compiling remember to change the .14 to .15 of the alsa driver.

try this: [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29%C%28intel%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29%C%28intel%29)

---

### Post by dustman on 2007-11-27
the thing is that i tried about 20 solutions today (and undoed them). I couldn't get th sound card to work. I wonder why every time there is a new release, it has tons of things that don't work or that have incompatibilities with all sorts of hardware? :| I think i'll go back to feisty for now, and leave gutsy alone...hope that the next release will be more compatible with my hardware ( which btw i cannot change cause it's a laptop).


Cheers!


Radu

---

### Post by nzadLithium on 2007-11-28
ok i think i found the problem. It seems to be loading the wrong driver. In the alsa hardware database your card is supposed to use the driver snd-atiixp or if you have an old version (anything under 0.9.0beta11) you need to load snd-card-atiixp
      ```

       # ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-atiixp
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss
       
```

copy and paste that into /etc/modules

you'll need to use gksudo gedit /etc/modules to edit that file other wise you wont be able to save.

then restart your pc. see if you have sound. If you dont then change 
alias snd-card-0 snd-atiixp
to 
alias snd-card-0 snd-card-atiixp

one of those should work. This all assumes you only have one soundcard in your pc. If you have more than one then we'll have to figure out which card is which.

---

### Post by gdr8205 on 2007-12-02
hi,
i converted to OSS b/c i had no more patience tryn to get my alsa workn, can sum1 plz hlp me get alsa back also get it working?
thanks
Garrett

ps im running Ubuntu 7.10

Oss is working for me but i want to try to get alsa to work

---

### Post by gdr8205 on 2007-12-02
this post has a lot of my computer info on it alrdy if it hlps:
[http://ubuntuforums.org/showthread.php?t=628342](http://ubuntuforums.org/showthread.php?t=628342)

---

### Post by slyboots on 2007-12-02
Hi.
On my Dell Latitude D630 was no sound so i tried to install it first:

 sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

reboot

(this solve the issue but after suspend or hibernate was it not working correctly. And it wont switch wien jack connector was injected) 

Then i use this:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)


but the microphone was not working and the vibrating noise by high volume was occuring. So i used this:

After a few weeks of no sound with the d630 and the 2.6.22 kernel, I finally found this solution, which worked for me. I must warn you that I am kind of new to linux and can make no guarantees that this solution will work or that it will not hurt your system. I found it on [http://onemansjourneyintolinux.blogs...30-update.html](http://onemansjourneyintolinux.blogs...30-update.html) , so thanks to commenter Mike, who is an angel.
Here goes:
1. Get the latest alsa drivers from Georgia Tech's website
Quote:
wget [http://www.gtlib.gatech.edu/pub/suse...070804.tar.bz2](http://www.gtlib.gatech.edu/pub/suse...070804.tar.bz2)
2. extract it
3. change directory to the directory with the extracted files
4. configure with
Quote:
./configure --with-cards-hda-intel
5.
Quote:
make
6.
Quote:
sudo make install
7. reboot
I hope it works as well for you guys as it did for me. Good luck.

And it work good.

[B][COLOR="Red"]I TRIED INSTALL FRESH INSTALL ON NEW HDD AND I FOUND THAT WIEHT EVERY INSTALL WAS SOUND GOOD AND MICROPHONE HAVE WORKED. BUT ON MY OLD INSTALL (GUTSY TOO) WONT IT WORK. SO I HAVE MAKED SAME STEPS ONE MORE TIME, BUT NOTHING CHANGE. 

WHAT SHOULD I DO TO REMOVE THE DRIVERS OF AUDIO AND GET FRESH INSTALL.[/COLOR][/B]

---

### Post by dustman on 2008-01-02
> **slyboots said:**
> 

....

After a few weeks of no sound with the d630 and the 2.6.22 kernel, I finally found this solution, which worked for me. I must warn you that I am kind of new to linux and can make no guarantees that this solution will work or that it will not hurt your system. I found it on [http://onemansjourneyintolinux.blogs...30-update.html](http://onemansjourneyintolinux.blogs...30-update.html) , so thanks to commenter Mike, who is an angel.
Here goes:
1. Get the latest alsa drivers from Georgia Tech's website
Quote:
wget [http://www.gtlib.gatech.edu/pub/suse...070804.tar.bz2](http://www.gtlib.gatech.edu/pub/suse...070804.tar.bz2)
2. extract it
3. change directory to the directory with the extracted files
4. configure with
Quote:
./configure --with-cards-hda-intel
5.
Quote:
make
6.
Quote:
sudo make install
7. reboot
I hope it works as well for you guys as it did for me. Good luck.

And it work good.

[B][COLOR="Red"]I TRIED INSTALL FRESH INSTALL ON NEW HDD AND I FOUND THAT WIEHT EVERY INSTALL WAS SOUND GOOD AND MICROPHONE HAVE WORKED. BUT ON MY OLD INSTALL (GUTSY TOO) WONT IT WORK. SO I HAVE MAKED SAME STEPS ONE MORE TIME, BUT NOTHING CHANGE. 

WHAT SHOULD I DO TO REMOVE THE DRIVERS OF AUDIO AND GET FRESH INSTALL.[/COLOR][/B]

man, that freakin' worked!!! YES now i have glorious sound :D
Thanks a lot!

---

