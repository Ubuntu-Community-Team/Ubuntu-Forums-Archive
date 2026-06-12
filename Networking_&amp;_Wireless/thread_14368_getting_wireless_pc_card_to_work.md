---
title: "getting wireless pc card to work"
date: 2005-02-06
forum: Networking &amp; Wireless
---

### Post by stevetxt on 2005-02-06
I bought a D-Link DWL 650 wireless card to use with my laptop, based on the ubuntu hardware support page.   I don't know how to tell what chipset is in it but on the side of the box it refers to "Atheros Super G Turbo Mode."  

What do I need to do to get the card recognized.  Whether I insert the card in the pcmcia slot before booting or later, my network configurations under the gnome computer menu show only the eth0 device corresponding to my usual ethernet connection.  

I dual boot Windows XP, which I seldom use, but used it to check this and the card works right off there.  I have the Ubuntu wiki WiFiHowto but it doesn't seem to help with this.  Is there some configuration I need to try first?

Thanks.

Steve

---

### Post by mccan on 2005-02-08
Hi Steve,

I have a DWL-G630 card, so a bit different, but this is how I got it to work:

-- I did the expert install and picked the module for the wireless card.  The network was not loaded from this and it may not be necessary...

-- I downloaded the latest xp driver for the card from d-link website (the one of the CD may have been fine, but I did not have the CD handy).  I unzipping the archive.  

-- I ran computer/system configuration/synaptic and updated everything and then used synaptic to install ndiswrapper package.  

-- I installed the xp driver using the ndiswrapper program (I found instructions on the forum and google groups.  I think the switches were -i first to install and then -m (?) to write the settings.  

-- I ran computer/system configuration/networking and added wlan0 (disabled the built in network eth0 first).  I used a hex key as I could not get the ascii key to work.

I don't know if you would go through these same steps, but maybe one of them will give you an idea of what to do.

Good luck,

David

---

### Post by stevetxt on 2005-02-10
Thanks, Dave.

Actually, my d-link gwl 650 seems to be supported more directly in Ubuntu.  It has an atheros chipset, and uses madwifi driver modules instead of ndswrapper.  I finally got it working with them.

Best,

Steve

---

### Post by thedr9wningman on 2005-03-14
[QUOTE=mccan]Hi Steve,

I have a DWL-G630 card, so a bit different, but this is how I got it to work:

-- I did the expert install and picked the module for the wireless card.  The network was not loaded from this and it may not be necessary...

-- I downloaded the latest xp driver for the card from d-link website (the one of the CD may have been fine, but I did not have the CD handy).  I unzipping the archive.  

-- I ran computer/system configuration/synaptic and updated everything and then used synaptic to install ndiswrapper package.  

-- I installed the xp driver using the ndiswrapper program (I found instructions on the forum and google groups.  I think the switches were -i first to install and then -m (?) to write the settings.  

-- I ran computer/system configuration/networking and added wlan0 (disabled the built in network eth0 first).  I used a hex key as I could not get the ascii key to work.

I don't know if you would go through these same steps, but maybe one of them will give you an idea of what to do.

Good luck,

David[/QUOTE]


I've done all of this stuff (several times) and I still can't get the thing to work.  My system recognises the wlan0 slot, but I can't manage to activate the bloody card!  I've Ndiswrapped to my heart's content, I've modprobed and all this other crap, and I've gotten the thing to work only once.  Whether I have the card in the machine or not, I can't get it to actually stick!  When I click enable, it enables for about a second and then automatically un-checks (thereby indicating it has been disabled)  The whole reason for having this laptop is for wireless service, and now I can't seem to get the goddamned thing working!  HELP! ](*,) 

This is a Dell Lattitude, 500Mhz system, 128 MB RAM with Ubuntu 'warty' installed.  I've used synaptic packages to try to support all of this stuff, but to be honest, I'm new at this.  I used to program in linux, but I've never had my own computer with it.  I do not have room for Windoze, so I don't have it on this system.  But I'm surely considering it with all these difficulties!!!  It doesn't seem worth it to have to do all this stuff and still not have the bloody thing work!!!

transcript below:

---
cedric@fuse:~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

You have new mail in /var/mail/cedric
cedric@fuse:~ $ lsmod
Module                  Size  Used by
ndiswrapper            88592  0
acx_pci               127180  0
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230148  8
af_packet              20872  2
3c589_cs               12552  1
ds                     17796  5 3c589_cs
iptable_filter          3072  0
ip_tables              16896  1 iptable_filter
button                  6936  0
ac                      5132  0
battery                 9740  0
snd_es1968             29188  1
snd_ac97_codec         59268  1 snd_es1968
snd_pcm_oss            48296  0
snd_mixer_oss          16640  2 snd_pcm_oss
snd_pcm                85540  2 snd_es1968,snd_pcm_oss
snd_page_alloc         11144  2 snd_es1968,snd_pcm
snd_timer              23300  1 snd_pcm
gameport                4736  1 snd_es1968
snd_mpu401_uart         7296  1 snd_es1968
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  9 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd
uhci_hcd               29328  0
usbcore               104292  4 ndiswrapper,uhci_hcd
yenta_socket           19328  1
pcmcia_core            63156  3 3c589_cs,ds,yenta_socket
pci_hotplug            30640  0
intel_agp              20512  1
agpgart                31784  1 intel_agp
floppy                 54996  0
rtc                    12216  0
pcspkr                  3816  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
tsdev                   7168  0
lp                     10436  0
evdev                   9216  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109672  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   26160  865
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


cedric@fuse:~ $ ndiswrapper -i AIRPLUS.inf
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

airplus is already installed. Use -e to remove it
cedric@fuse:~ $ sudo ndiswrapper -m
Password:
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

modprobe config already contains alias directive
cedric@fuse:~ $ insmod /usr/sbin/ndiswrapper
insmod: error inserting '/usr/sbin/ndiswrapper': -1 Operation not permitted
^^^Seems to be the issue??  But I have no IDEA what that entails or means.... :x 


Thanks!

---

### Post by USSJoin on 2005-03-22
[QUOTE=thedr9wningman]
cedric@fuse:~ $ insmod /usr/sbin/ndiswrapper
insmod: error inserting '/usr/sbin/ndiswrapper': -1 Operation not permitted
^^^Seems to be the issue??  But I have no IDEA what that entails or means.... :x 
[/QUOTE]

Well, just as a general idea, if you type a command in ubuntu, and it responds with "not permitted," it often needs a preceeding "sudo." I can see you weren't logged in as root when you tried it- try

```

sudo insmod /usr/sbin/ndiswrapper

```

And see what happens.

---

### Post by thedr9wningman on 2005-03-23
[QUOTE=USSJoin]Well, just as a general idea, if you type a command in ubuntu, and it responds with "not permitted," it often needs a preceeding "sudo." I can see you weren't logged in as root when you tried it- try

```

sudo insmod /usr/sbin/ndiswrapper

```

And see what happens.[/QUOTE]

Um, similar problem. 
```

innsmod: error inserting '/user/sbin/ndiswrapper': -1 Invalid module format

```

---

