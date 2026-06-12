---
title: "newbie to ubuntu needs wireless help"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by jetbangdink on 2011-04-25
Ok i have two wireless usb adapters. one is a netgear wna1100 which i have an installation cd for. with windows xp (born and raised xp) i would insert the disc and it would autorun and open a software installer. i just downloaded ubuntu because i am tired of paying for new copies of windows everytime i make a hardware change (i call microsoft they wont give me anymore new keys) so i have never used ubuntu before but i must say i am impressed (other than i dont know how to work it for my life lol) the other wireless usb is a cisco ae1000 which i have read some threads about and i was overwhelmed being reminded of the 100 digit lines of code from DOS lol. so with the netgear i inserted the disc no auto run im like ok ill just manually open and run the autorun.exe..... no run. at this point i just start trying to open .exe files none of them will open and im geting this error with a huge command line output. so i say ok ill try with the ae1000 which by the way i dont even know how to locate hardware to see if its even recognised. i remembered that i lost my disc when i had xp and could download the driver from the cisco site. i could just use a flash drive to transfer the driver from my laptop to my desktop with ubuntu locate the hardware and manually update the driver by telling it to locate the update in the flashdrive..... well cisco doesnt have a driver for linux and i dont know how to do that on ubuntu anyway... so my desktop has no internet...all i really want to do is play world of warcraft on this desktop and cant even get the internet to work lol. neither usb is working i dont know how to get them to work im clueless could someone please help lol

---

### Post by MooPi on 2011-04-25
Lets start by using only one of your adapters. Insert the usb device then go to applications and open a terminal. Typing in terminal ```
lsusb
```
```
iwconfig
```
```
lsmod
```
Copy and paste the results for each command back here so we can help.
I have just researched what chip is used for the Cisco usd adapter. It uses Ralink rt2870 chip and it is supported by Linux if that helps you make a choice. Also found that the netgear device uses an Atheros chip and should use the the ath9k driver. Both seem to work with native Linux drivers so no need for ndiswrapper.

---

### Post by majorawesome on 2011-04-25
BTW you can't run .exe AKA executables in ubuntu (or any other OS than windows for that matter) and all of the programs you need (hopefully) will be in the software center

---

### Post by jetbangdink on 2011-04-25
im on my laptop so i couldent coy and paste but im gonna type the code i believe your looking for 
 
Bus 001 Device 009: ID 0846: 9030 NetGear, Inc.
 
i dont have internet on my desktop with ubuntu so im using my laptop looking for troubleshoots lol

---

### Post by MooPi on 2011-04-25
You could copy and paste the results to a text file then transfer to your laptop via a portable drive ?

---

### Post by jetbangdink on 2011-04-25
ive done alot of reading and it seems nobody is really getting this problem resolved at all. ive read threads specific to both of my adapters and cant find a solution. i dont have internet on the desktop with ubuntu which is making things even harder because i cant just enter the lines of code in terminal to download and install the drivers. i mean i kind of figured that support on theese types of issues was going to be thin because everything is made for windows but jeeze lol

---

### Post by jetbangdink on 2011-04-25
yeah i think i can do that if its possible to open a text file from ubunto on windows lol lemme try and ill post results

---

### Post by MooPi on 2011-04-25
Make certain to rename the file ```
something.txt
``` .txt being the important part

---

### Post by jetbangdink on 2011-04-25
well luckily i was able to change the file type it saves on ubunto as to a txt file heres the code
 
Bus 005 Device 003: ID 046d:c05a Logitech, Inc. 
Bus 005 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 008: ID 05dc:a782 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
lo no wireless extensions.
 
 
eth0 no wireless extensions.
 
 
Module Size Used by
nls_iso8859_1 3261 1 
nls_cp437 4931 1 
vfat 9201 1 
fat 48240 1 vfat
usb_storage 40172 1 
nls_utf8 1069 1 
isofs 30022 1 
binfmt_misc 6599 1 
snd_hda_codec_nvhdmi 12879 4 
snd_intel8x0 25632 2 
snd_ac97_codec 99227 1 snd_intel8x0
ac97_bus 1014 1 snd_ac97_codec
snd_hda_intel 22107 0 
snd_hda_codec 87552 2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep 5040 1 snd_hda_codec
snd_pcm 71475 4 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_seq_midi 4588 0 
snd_rawmidi 17783 1 snd_seq_midi
snd_seq_midi_event 6047 1 snd_seq_midi
snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event
snd_timer 19067 2 snd_pcm,snd_seq
nouveau 516971 2 
ttm 56633 1 nouveau
drm_kms_helper 30200 1 nouveau
snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq
drm 168054 4 nouveau,ttm,drm_kms_helper
snd 49006 14 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp 26360 0 
soundcore 880 1 snd
agpgart 32011 3 ttm,drm,intel_agp
ppdev 5556 0 
i2c_algo_bit 5168 1 nouveau
snd_page_alloc 7120 3 snd_intel8x0,snd_hda_intel,snd_pcm
psmouse 59033 0 
serio_raw 4022 0 
usbhid 36882 0 
parport_pc 26058 1 
hid 67742 1 usbhid
lp 7342 0 
parport 31492 3 ppdev,parport_pc,lp
floppy 54311 0 
tg3 123310 0

---

### Post by zipperback on 2011-04-25
You might want to read over the information on this page:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

- zipperback
:popcorn:

---

### Post by zipperback on 2011-04-25
And this one.
[http://ubuntuforums.org/showthread.php?t=1735775&highlight=netgear+wireless](http://ubuntuforums.org/showthread.php?t=1735775&highlight=netgear+wireless)

- zipperback
:popcorn:

---

### Post by zipperback on 2011-04-25
And you should probably search through the following for information regarding your wifi as well.

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

[b]Could you please tell us the exact make and model of your wifi adapters? 
Look on the physical adapters and see what they say. 
The output from your lsusb query isn't providing the specific information regarding your netgear adapter.
Also, it would probably be best if you only had one of them installed at a time until you get one of them working.
[/b]

- zipperback
:popcorn:

---

### Post by MooPi on 2011-04-25
If your going to use the Netgear let's try a few commands to see if we can get it fired up.
From terminal ```
sudo modprobe ath9k
```
```
sudo ifconfig wlan0 inet up
```
See if your network applet sees the device and if you can connect. You will probably need to add the module to /etc/modules
```
sudo gedit /etc/modules
```
Add the red text at the end to the file
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
[COLOR="Red"]ath9k[/COLOR]
```

---

### Post by jetbangdink on 2011-04-25
all it said was my netgear should be supported lol

---

### Post by jetbangdink on 2011-04-25
ok i typed everything verbatum but how do i turn the last text red lol

---

### Post by bkratz on 2011-04-25
> **jetbangdink said:**
> ok i typed everything verbatum but how do i turn the last text red lol



Well don't worry about the color--it was only done to show where it would be added, and if the earlier steps did no good then adding it would not help anyway, that only insured that it loaded that module at boot time.

---

### Post by jetbangdink on 2011-04-25
ok after typing everything when i went to save it said could not find the file /ect/modules.

---

### Post by bkratz on 2011-04-25
misstyped--that was etc not ect

---

### Post by jetbangdink on 2011-04-25
sorry lol ok i ran the process again checking for spelling saved and nothin happened lol

---

### Post by jetbangdink on 2011-04-25
none of this is helping lol everything that has been said to input into terminal results in. command not found, uknown command, device not present, no default destination available. my sound worked on install where as with windows i had to download the driver from HP drivers site. this is what i need. i need to be able to download the driver onto a flash drive from my laptop. open it in ubuntu on my desktop and place it in the appropriate destination. then tell ubutnu to locate the driver from that destination to operate the usb. using lsusb in terminal tells me ubuntu knows its there it just doesnt know how to operate it and needs a driver. where do i find the driver to work the device? how do i open it in ubunto? where to i set the destination to save the driver to operate from? and how do i tell ubuntu to use that driver to operate the device.

---

### Post by spike_seti on 2011-04-25
i am using a D-links wireless pci card right out of the box because BCM is to much to play with to work

---

### Post by jetbangdink on 2011-04-25
yeah it doesnt seem like anyone has a solution for this problem all the threads on this wirless usb that say solved is because they ended up using a different brand that worked lol i have read thread after thread of this exact same problem and no one has an answer 
if i could get ndiswrapper to work it might work i dunno also the install disc has the drivers on it and a couple .dll files i dont understand why they cant be used to oprate the device maybe because its only for windows. i have a 32bit system running ubuntu apparently it is possible to get this usb working just noone sems to know how or the ones that did get it to work didnt document how they did it.. shortly put i love ubuntu allready other than i cant get the internet to work and at this point its either get one of theese usb to work or have to switch back to installing windows every 30 days because my key no longer works

---

### Post by jetbangdink on 2011-04-25
i have two wireless usb adapters one is: Cisco linksys ae1000, and the other is : NetGear wna1100, and apparently neither of them is going to work... kind of suprising no one has figured out a simple process to get them to work since they are both 2 of only like 4 wireless usb adapters sold from walmart lol i dunno im about to just give and go back to spending a day installing windows every 30 days

---

### Post by MooPi on 2011-04-26
The Cisco is just as easy as the Netgear, it's just that you picked the netgear so I concentrated on that model.
Here is another possible solution for the Netgear
[http://sourceforge.net/projects/ath9k-htc/]("http://sourceforge.net/projects/ath9k-htc/")
Go to the Other versions and look for Maverick fixed.
After you've downloaded the .deb file open a terminal where you've save it and type ```
sudo dpkg -i ath9k_htc-installer.1.0.1-maverick-fixed.deb
```

---

### Post by jetbangdink on 2011-04-26
thats the problem lol i dont have internet on the desktop so i have to save any files to a flash drive from my laptop and load them onto the desktop i just installed ubuntu last night so i have no idea what im doing really. after i used my lap top to download the files onto a flash drive and i plug the flash drive into my desktop then what? how do i acess the files and where do i put them and how would i open a terminal specific to those files 
 
also i started a new thread with alot more info correctly done with all the info on all three of the wireless usb i have i dont care which one i have to use i just want internet lol

---

