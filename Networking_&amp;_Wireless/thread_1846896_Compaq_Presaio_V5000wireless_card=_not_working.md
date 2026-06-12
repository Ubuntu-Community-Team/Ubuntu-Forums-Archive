---
title: "Compaq Presaio V5000/wireless card= not working"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by big d andre on 2011-09-19
I'm new to Ubuntu and I have this problem with my Compaq Presario V5000. I just installed the latest Ubuntu and for some reason the blue wireless LED light isn't turning on. If someone can give me some directions that'd be very helpful. Or at least a helpful link would work.

---

### Post by wildmanne39 on 2011-09-19
Hi, welcome to the forum! please run these commands in a terminal by hitting ctrl+alt+t, then paste the commands into the terminal, then paste the results here.
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by big d andre on 2011-09-19
#1 cat /etc/lsb-release; uname -a


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux domenic-Presario-V5000-RG324UA-ABA 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux

#2 sudo lshw -C network


 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:41:ce:3f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.68 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff

#3 lspci -nn | grep -e 0280 -e 0200

06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

#4 iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

#5 rfkill list all


0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

#6 lsmod


Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_atiixp             19400  2 
snd_atiixp_modem       18624  0 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
radeon                900494  3 
snd_pcm                80042  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  5 radeon,ttm,drm_kms_helper
psmouse                73312  0 
snd                    55295  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
k8temp                 12872  0 
soundcore              12600  1 snd
i2c_piix4              13095  0 
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_algo_bit           13184  1 radeon
video                  18951  0 
ati_agp                13202  0 
shpchp                 32345  0 
ndiswrapper           192828  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
ssb                    45942  0 
8139cp                 22497  0 
pata_atiixp            12968  2 

I'm not sure how to post or respond on forums, so if there is a template for this forum a link to one would be great to view.

---

### Post by wildmanne39 on 2011-09-19
Hi, two things one it shows the hardware switch is off, you  can turn it on with a button that slides or pushes, or a key like fn f11 something like that all computers are a little different.

Second please run this command and it will install the driver and firmware.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
When it is done unplug your wired connection and restart your computer and it should work let me know either way please.
Thank you

---

### Post by big d andre on 2011-09-19
The hardware button is not functioning for some reason (it won't light up). I know for a fact that it's not the wireless card for it was working yesterday when I was running CrunchBang

---

### Post by wildmanne39 on 2011-09-19
Hi, do you know for a fact that the switch is on, do you know how it turns on with your computer?

Please run these commands:
```
rfkill list all
```
```
lsmod | grep b43
```
Thank you

---

### Post by big d andre on 2011-09-19
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ lsmod |grep b43
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ lsmod | grep b43
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo lsmod | grep b43
[sudo] password for domenic: 
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ su lsmod | grep b43
Unknown id: lsmod
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo lsmod | grep b43
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ 

The second command doesn't seem to work. And no i'm not sure how it turns on (specifically) but there is a little square button that lights up when i turn it on.

---

### Post by wildmanne39 on 2011-09-19
Hi, when you ran this command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
did you get any errors?

Did you restart your computer?

Also try this please, unplug your wired first, but do not restart your computer after you run this last command.
```
sudo rmmod -f hp-wmi
```
Thank you

---

### Post by big d andre on 2011-09-19
No, I showed you exactly what I saw in the terminal. 

This is what i got from the last command


domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rmod -f hp-wmi
[sudo] password for domenic: 
sudo: rmod: command not found
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rmmod -f hp-wmi
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ 
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rmmod -f hp-wmi
ERROR: Removing 'hp_wmi': No such file or directory
domenic@domenic-Presario-V5000-RG324UA-ABA:~$

---

### Post by wildmanne39 on 2011-09-19
Hi, all right try it this way please:
```
rfkill list all
sudo rmmod -f hp_wmi
sudo rfkill unblock all
```
Thank you

---

### Post by big d andre on 2011-09-19
Ok, so I thought maybe that it wasn't functioning because I had closed the terminal (I'm not sure what I'm doing) but I went back through this thread and re-entered everything and these are my results. But for some reason I wasn't getting any result at all every time I entered [rfkill list all] I never got a result. Is there anything else I could do that would help?

domenic@domenic-Presario-V5000-RG324UA-ABA:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux domenic-Presario-V5000-RG324UA-ABA 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo lshw -C network
[sudo] password for domenic: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:41:ce:3f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.68 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ lspci -nn | grep -e 0280 -e 0200
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

domenic@domenic-Presario-V5000-RG324UA-ABA:~$ rfkill list all
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_atiixp             19400  2 
snd_atiixp_modem       18624  0 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
radeon                900494  3 
snd_pcm                80042  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13666  0 
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  5 radeon,ttm,drm_kms_helper
psmouse                73312  0 
snd                    55295  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
k8temp                 12872  0 
soundcore              12600  1 snd
i2c_piix4              13095  0 
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_algo_bit           13184  1 radeon
video                  18951  0 
ati_agp                13202  0 
shpchp                 32345  0 
ndiswrapper           192828  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
ssb                    45942  0 
8139cp                 22497  0 
pata_atiixp            12968  2 
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo apt0get install b43-fwcutter firmware-b43-installer
sudo: apt0get: command not found
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ rfkill list all
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ lsmod | grep b43
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo: apt0get: command not found
No command 'sudo:' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudo:: command not found
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo lsmod | grep b43
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rmmod -f hp-wmi
ERROR: Removing 'hp_wmi': No such file or directory
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ rfkill list all
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rmmod -f hp_wmi
ERROR: Removing 'hp_wmi': No such file or directory
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rfkill unblock all
domenic@domenic-Presario-V5000-RG324UA-ABA:~$

---

### Post by wildmanne39 on 2011-09-19
Hi, let's try this I just noticed that you have ndiswrapper installed we need to remove it then we are going to manually load the driver and see if it comes on.
```
sudo modprobe -rf ndiswrapper

sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
then disconnect your wired connection and run this command please.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thank you

---

### Post by big d andre on 2011-09-20
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo modprobe -rf ndiswrapper
[sudo] password for domenic: 
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndisgtk is not installed, so not removed
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo /etc/modprobe.d/ndiswrapper.conf
sudo: /etc/modprobe.d/ndiswrapper.conf: command not found
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rm -r /etc/ndiswrapper*
rm: cannot remove `/etc/ndiswrapper*': No such file or directory
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rm -r /etc/ndiswrapper/*
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo rm -r/etc/ndiswrapper/*
rm: invalid option -- '/'
Try `rm --help' for more information.
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo depmod -a
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo su
root@domenic-Presario-V5000-RG324UA-ABA:/home/domenic# echo b43 >> /etc/modules
root@domenic-Presario-V5000-RG324UA-ABA:/home/domenic# exit
exit
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ 


Hi again, I hope you can still help me with this. Yesterday I had to get off my computer so I couldn't continue but I just ran the last of those commands and these are the results. There seemed to be no response with these though..

sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a

---

### Post by wildmanne39 on 2011-09-20
Hi, alright in post 12 the first set of commands run them one at a time and copy and paste all commands into the terminal so you are sure to get it right.

Then the commands in the 2nd box copy all of it at one time and paste into the terminal, it is all one command.

Then follow the directions in post 12 and see if it works.

If not post
```
lsmod
```
again.
Thank you

---

### Post by big d andre on 2011-09-20
[IMG]screenshot.png[/IMG]
I wanted you to be able to see what I did. It didn't do anything? I think. Anyways here's lsmod


domenic@domenic-Presario-V5000-RG324UA-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_atiixp             19400  3 
snd_atiixp_modem       18624  0 
snd_ac97_codec        105614  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
radeon                900494  3 
snd_pcm                80042  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
hp_wmi                 13418  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13666  1 hp_wmi
ttm                    65184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 radeon
snd                    55295  13 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   184164  5 radeon,ttm,drm_kms_helper
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  3 snd_atiixp_modem,snd_atiixp,snd_pcm
k8temp                 12872  0 
video                  18951  0 
i2c_algo_bit           13184  1 radeon
ati_agp                13202  0 
i2c_piix4              13095  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
8139cp                 22497  0 
ssb                    45942  0 
pata_atiixp            12968  2 
domenic@domenic-Presario-V5000-RG324UA-ABA:~$

---

### Post by praseodym on 2011-09-20
Please show the outputs of the following commands:

```
grep b43 /etc/modprobe.d/*
rfkill list
dmesg | grep b43
cat /var/lib/NetworkManager/NetworkManager.state
iwconfig
```

---

### Post by wildmanne39 on 2011-09-20
Hi, that got rid of ndiswrapper, many commands when you run them they only show output if there is an error.

Try this please and if this does not work I have a method that will install the drivers for sure but I am still concerned about the hard block.
```
sudo modprobe b43
```
Thank you

---

### Post by big d andre on 2011-09-20
@wildmanne39 I have a few questions, one is how to make those boxes you put your codes in and the other is how do you upload a picture?

domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo modprobe b43
[sudo] password for domenic: 
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ 

The results^^

@should I be running your codes along with the ones already have ran? Just making sure they won't undo or contradict with anything I 've done..

---

### Post by wildmanne39 on 2011-09-20
Hi, to use the boxes you click on this # above the text you type.

To upload a picture click on the paper click above the text window.

Yes is is ok to run all the codes posted here.
Thank you

---

### Post by big d andre on 2011-09-20
Alright thank you :) So what is it that I have to do to fix this problem?


@praseodym  Here are your results :)

domenic@domenic-Presario-V5000-RG324UA-ABA:~$ grep b43 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43legacy
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ dmesg | grep b43
[    1.377691] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 5457.512593] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 5458.210430] Registered led device: b43-phy0::radio
[ 5458.865402] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5458.865413] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5458.865422] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
domenic@domenic-Presario-V5000-RG324UA-ABA:~$

---

### Post by wildmanne39 on 2011-09-20
Hi, this should fix it, the hardware block is gone. run these last set of commands one at a time.
Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then unplug your wired connection

Open a terminal and do:

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```

This command will most like tell you it already exists but continue with the other commands.  sudo mkdir /lib/firmware/b43
Then it should work.
Thank you

---

### Post by praseodym on 2011-09-20
Did you install the firmware packages as mentioned above? If yes, try this package:

```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Did you deactivate the STA-driver? If no, do that, if yes (or never used it):

```
gksudo gedit /etc/modprobe.d/broadcom-sta-common.conf
```
and remove the line

> blacklist b43
save, exit and reboot.

---

### Post by big d andre on 2011-09-20
@wildmanne39 When you say one at a time do you mean in a separate terminal for each one? Also I tried the second command and got this 

domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo mkdir /lib/firmware/b43
[sudo] password for domenic: 
domenic@domenic-Presario-V5000-RG324UA-ABA:~$ sudo cp Desktop/b43/*  /lib/firmware/b43
cp: cannot stat `Desktop/b43/*': No such file or directory
domenic@domenic-Presario-V5000-RG324UA-ABA:~

---

### Post by wildmanne39 on 2011-09-20
Hi, no you can do them all in the same terminal, just do one line and wait at a time.

About the second line when you downloaded the zip file I gave you did you drag it to your desktop?

When you are done if it does not work do what praseodym said in his last post about 
> gksudo gedit /etc/modprobe.d/broadcom-sta-common.conf

and remove the line

Quote:
blacklist b43 
 
Thank you

---

### Post by pvtryan on 2011-09-20
Wildmanne looks like he's got the solution, Domenic. If you can't figure it out from that, make sure you've downloaded the zip file and I'll help you out tomorrow.

---

### Post by big d andre on 2011-09-22
Thank you Wildmanne39, my friend pvtryan helped me out today and used what you did in #21. It's working now, so thank you very much. And thank you praseodym for helping. Thanks guys.

---

### Post by wildmanne39 on 2011-09-22
Hi, your welcome! that is great, I am glad it is working. 
Enjoy

---

### Post by dupuntu on 2011-10-16
Hi, all,
 
Minutes ago, I figured this out.

The wireless switch on the v5000 toggles on/off.

Pressing it once turns off wireless. Kills the card.

Pressing it again turns it on, without lighting the button, and it won't light the button or activate wireless unless you reboot.

The switch knows when it's on or off, but it doesn't let you know.

If it's off when you shut down, it will stay off for that boot session. You will not be able to connect unless you resort to the terminal gymnastics seen on this thread.

But if it's on, unconnected but on, unlit, when you shut down, it will light up and connect upon reboot.

dp

---

### Post by BobCFC on 2011-10-20
> **dupuntu said:**
> Hi, all,
 
Minutes ago, I figured this out.

The wireless switch on the v5000 toggles on/off.

Pressing it once turns off wireless. Kills the card.

Pressing it again turns it on, without lighting the button, and it won't light the button or activate wireless unless you reboot.

The switch knows when it's on or off, but it doesn't let you know.

If it's off when you shut down, it will stay off for that boot session. You will not be able to connect unless you resort to the terminal gymnastics seen on this thread.

But if it's on, unconnected but on, unlit, when you shut down, it will light up and connect upon reboot.

dp


dp is right.  I install the b43 packages and had an entry for wlan0 but the blue light was still not coming on.  

if you run **rfkill list all** you can see the wifi button toggles the state for

1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Make sure hard blocked is set to NO and when you reboot the blue light comes on.

---

### Post by filthygovmploye on 2012-02-19
i am having the same problem, but i have a different wireless card. 4311 instead of 4318. where do i start with the instructions? post 21? i am obviously a noob as well... thank

-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:80000000-80003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:0d:4c:0d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.9 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d0100000-d0100fff ioport:2000(size=64)
alex@alex-Presario-V5000-EZ430UA-ABA:~$ ^C
alex@alex-Presario-V5000-EZ430UA-ABA:~$

---

### Post by filthygovmploye on 2012-02-19
here is from step 6 on first page....i dont have ndis listed inthere

      Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  8 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  4 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
snd                    55902  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
i915                  509519  3 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
drm                   192194  4 i915,drm_kms_helper
lib80211               14570  1 wl
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25727  1 ahci
e100                   36289  0

---

### Post by filthygovmploye on 2012-02-19
here is the kilfast command

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

then i pressed the wirelss button and it says this:
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

also, i could start my own thread, but this was already going....

---

### Post by wildmanne39 on 2012-02-19
Hi, please show:
```
cat /etc/lsb-release; uname -a
```
and always put all information in one post with code tags which is the # key.
Thanks

---

### Post by filthygovmploye on 2012-02-19
lex@alex-Presario-V5000-EZ430UA-ABA:~$ sudo mkdir /lib/firmware/b43
[sudo] password for alex: 
mkdir: cannot create directory `/lib/firmware/b43': File exists
alex@alex-Presario-V5000-EZ430UA-ABA:~$ sudo cp Desktop/b43/*  /lib/firmware/b43alex@alex-Presario-V5000-EZ430UA-ABA:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
alex@alex-Presario-V5000-EZ430UA-ABA:~$ sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
alex@alex-Presario-V5000-EZ430UA-ABA:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
alex@alex-Presario-V5000-EZ430UA-ABA:~$ sudo modprobe b43
alex@alex-Presario-V5000-EZ430UA-ABA:~$ 


well, i dunno what fixed it, but i ran the stuff from step 21, and after the last command i pressed the button and it lit up...

not sure what its all aboot

#DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux alex-Presario-V5000-EZ430UA-ABA 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux
alex@alex-Presario-V5000-EZ430UA-ABA:~$ 
#

thanks for all the help!!! can you tell me what was going on? i am really new to this, so i dont know WTF i did!

dont understand the # code commads... link? i dl'd the bf43 thing, and it did a long list of things in the terminal, so maybe that did it...

---

### Post by wildmanne39 on 2012-02-19
Hi, the steps in 21 installed the firmware for your wireless driver that is what made it work.
Enjoy

---

### Post by filthygovmploye on 2012-02-20
it s back to not working again. read in a post about clashing drivers?

---

### Post by wildmanne39 on 2012-02-20
Hi filthygovmploye, I see that you do have another driver let's remove at.
Please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then reboot with wired connection unplugged.
Thanks

---

### Post by filthygovmploye on 2012-02-20
sweetnees! it works now! i noticed there is a sticky on these cards, but is there a faq like on page 3 here of how the wireles button works i n ubuntu?

---

### Post by wildmanne39 on 2012-02-20
Hi filthygovmploye, I am glad it is working.

No there is not a faq on wireless buttons that I know of, what is the issue with your wireless button? If your wireless works I would not worry about it.

There are some that do not work well and we can run some commands to get the wireless to come on in those cases but I am not sure that the button works after that.
Thanks

---

### Post by filthygovmploye on 2012-02-20
ya i meant a faq on how the wireless card is supposed to work when it is working correctly. ie, when i shut the laptop, reopen it, is it supposed to come on auto (it is) but i think thats what caused it to fail earlier. 

thanks for all the help!!!

---

### Post by wildmanne39 on 2012-02-20
Hi, what caused the fail earlier was you had two drivers installed and it caused a conflict.

However the more you turn your wireless switch on and off the more likely you will have a problem.
Thanks

---

### Post by bossman_bst on 2012-03-09
Hi, I tried all the other thing s that you guys post before, but the only thing I miss is enabling the wireless adapter in the network manager, I already installed the b43 dirver and is active but for some reason dont leave me enable the wifi connection. please if you can make a step by step or a video showing how to enable will be perfect I'm a novice with 0 hours of experience in programation .

---

### Post by praseodym on 2012-03-09
Hi bossman_bst,

please open a terminal with CTRL+ALT+T and show the outputs of the commands:

```
lspci -nnk
lsmod
iwconfig
rfkill list
```

---

### Post by wildmanne39 on 2012-03-09
I see you beat me to it, I was working on the post at the same time.

---

### Post by CJasper on 2012-08-31
ok Im having the same problem with my V5000 with windows 7 ultimate. I replaced the screen on this thing and when  I put it all back together the wifi light will not come on. I have uninstalled hte drivers and reinstalled them and still nothing.. I also tred to open a terminal but I guess I have no clue what I am doing because all I can find on my computer is the command prompt and it will not take the commands that were posted. so what am I doing wrong and can you please help me. thanks

---

### Post by bloodcloak666 on 2013-01-04
Thank you Wild man,I got my compaq presario v500 wireless working now,but following your instructions!  


Thanks a bunch

---

### Post by lurgee on 2013-01-28
> **Wild Man said:**
> Hi, two things one it shows the hardware switch is off, you  can turn it on with a button that slides or pushes, or a key like fn f11 something like that all computers are a little different.

Second please run this command and it will install the driver and firmware.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
When it is done unplug your wired connection and restart your computer and it should work let me know either way please.
Thank you
No, thank you, Wild Man!  Another fumbling idiot saved!

---

### Post by Ubun2NoobDude on 2013-07-12
Hi guys - I hope I'm not in the wrong for posting on this thread - I wasn't sure whether to start a new one since this is so close to my issue as well.   I too am having issues with my wireless not working on my Compaq Presario V5000, although I've installed ubuntu 12.04.  I have run the commands in the terminal and:

x@Xyz:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux Xyz 3.5.0-34-generic #55~precise1-Ubuntu SMP Fri Jun 7 16:32:06 UTC 2013 i686 athlon i386 GNU/Linux
x@Xyz:~$ sudo lshw -C network
[sudo] password for x: 
Sorry, try again.
[sudo] password for x: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=wl latency=64
       resources: irq:9 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bc:b2:fe
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=67.180.78.214 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
x@Xyz:~$ lspci -nn | grep -e 0280 -e 0200
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
x@Xyz:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

x@Xyz:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
x@Xyz:~$ lsmod
Module                  Size  Used by
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
dm_crypt               22572  1 
bnep                   17791  2 
rfcomm                 38104  0 
bluetooth             189585  10 bnep,rfcomm
parport_pc             32115  0 
ppdev                  12850  0 
wl                   3032548  1 
snd_atiixp_modem       18621  5 
snd_atiixp             19342  2 
snd_ac97_codec        106118  2 snd_atiixp_modem,snd_atiixp
joydev                 17394  0 
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                81124  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              181041  1 wl
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                91381  0 
lib80211               14041  1 wl
i2c_piix4              13094  0 
hp_wmi                 13653  0 
snd                    62675  20 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13032  0 
soundcore              14636  1 snd
shpchp                 32326  0 
sparse_keymap          13659  1 hp_wmi
snd_page_alloc         14109  3 snd_atiixp_modem,snd_atiixp,snd_pcm
k8temp                 12913  0 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
radeon                837045  3 
ttm                    76326  1 radeon
8139too                23312  0 
drm_kms_helper         47459  1 radeon
drm                   239971  5 radeon,ttm,drm_kms_helper
8139cp                 26760  0 
video                  19117  0 
i2c_algo_bit           13317  1 radeon
wmi                    18745  1 hp_wmi
pata_atiixp            13000  2 
ati_agp                13243  0

---

### Post by praseodym on 2013-07-12
Hi,

uninstall the Broadcom-STA driver after installing the firmware as described above:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot and check
```

iwconfig
rfkill list
```

---

### Post by Ubun2NoobDude on 2013-07-12
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic
Use 'apt-get autoremove' to remove them.

 Wow that's a quick reply! thanks for the help - I'm totally new to all of this - Should I "autoremove" them or just leave it as is?

nvm - just auto removed..

---

### Post by Ubun2NoobDude on 2013-07-12
it gave me this after those last commands:

iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          lo        no wireless extensions.
eth0      no wireless extensions.

Ps:  I have no freaking idea why the heck it's putting smileys in the text i copy pasted.. tried to delete but they keep placing themselves in...  *facepalm*

---

### Post by Ubun2NoobDude on 2013-07-12
WHOA!!    WOOOOOOT!!!   Nevermind - IT WORKS!!!!! I FREAKIN LOVE YOU MAN!!!! It just occurred to me to press the wifi button and lo and behold its on and my wifi connections are showing up.  thank you SOOOOOOO much!!!!!!!   Made me day - I've been working on this for a few hours here and there for weeks now.  YOU ROCK!  again, much mahalo!!

A.

---

### Post by praseodym on 2013-07-13
Does wireless work?

---

### Post by Ubun2NoobDude on 2013-07-13
yep! worked perfectly thank you.  But when I first installed, I didn't check sign in automatically so I had to keep putting in my master passwd - so I reinstalled and got it to auto login - now have to go through all the updates again, and then your wireless fix all over again lol *facepalm*  fingers crossed!!!  again, thanks for the help!

---

### Post by Ubun2NoobDude on 2013-07-13
just wanted to quick follow up:  reinstalled, and with your help, all good and it's rockin!  thanks n take care

---

