---
title: "Wireless Connection Problem"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by JazzyJoe70 on 2011-07-27
I have a Dell Latitude D400.  I am a new Ubuntu user and just installed Ubuntu 11.04 32-bit.  I am unable to see my wireless network router SBC 2WIRE.  The wireless device is Broadcom BCM4306 Rev 2 802.11 bg and it is currently using the B43 driver. 

Kernel Boot Message:
    
B43legacy-ph0 error: Firmware file "b43legacy/ucode4.fw" not found or load failed.
    
B43legacy-ph0 error: You must go to [http://linuxwireless.org](http://linuxwireless.org) and download the correct firmware (version 3)

I'm not familiar with Ubuntu, but I went ahead and installed it to try it out.  Everything works fine except for the wireless network connection. I need some help please!

---

### Post by thefasterblueone on 2011-07-27
Open 'Synaptic Package Manager', search for B43 , select 'b43-fwcutter' and one of the 'firmware-b43-installer' that relates to the BCM4306 Rev 2 that you have.

Look for Supported chipsets:
 - BCM4301
 - BCM4303
 - BCM4306/2   <-----this is the one you want.

---

### Post by JazzyJoe70 on 2011-07-27
I tried it but didn't work it gave me some errors. This is what i have in the Synaptic Package Manager:

b43-fwcutter
firmware-b43-installer
firmware-b43-lpphy-installer
firmware-b43legacy-installer

the last one 'firmware-b43legacy-installer' has the BCM4306/2.  I went ahead and selected this one but did not work. I read some other threads and i typed dmesg | grep b43 and it gave my the following.

adrian@adrian-Latitude-D400:~$ dmesg | grep b43
[    1.768815] b43-pci-bridge 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   19.560700] b43legacy-phy0: Broadcom 4306 WLAN found
[   19.595608] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   19.595631] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   19.621638] b43legacy-phy0 debug: Radio initialized
[   20.513972] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   20.513980] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

---

### Post by wildmanne39 on 2011-07-27
Hi, are you connected to a wired connection when your tried to install from synaptic?

---

### Post by JazzyJoe70 on 2011-07-27
yes I was connected, should i disconnect and try it again?

---

### Post by JazzyJoe70 on 2011-07-27
I'm still not able to connect. I've been trying to fix this problem all day. I'm so tempted to just go back to Windows XP. everything seems to be working fine except for the wireless connection issue. Come on Ubuntu don't let me down.

---

### Post by thefasterblueone on 2011-07-27
Did you also install 'b43-fwcutter'. Pretty sure you need this also.

---

### Post by wildmanne39 on 2011-07-27
Hi, this is what you need b43-fwcutter with the firmware-b43legacy-installer I have the same card but have not install it in a long time.

You will need to be connected to your wired connection to install the drivers and after you install them unplug your wired connection and restart your system.

Also if anything else is installed for your driver like the sta

Post back here if you get errors, if it works let us know and please mark the thread solved.

 or kernel bcmwl-kerrnel-source remove it.
Thank you

---

### Post by JazzyJoe70 on 2011-07-27
yes i installed b43-fwcutter.

---

### Post by thefasterblueone on 2011-07-27
[http://linuxwireless.org/en/users/Drivers/b43?highlight=%28BCM4306%29]("http://linuxwireless.org/en/users/Drivers/b43?highlight=%28BCM4306%29")

---

### Post by wildmanne39 on 2011-07-27
Hi, if you want to do it in a terminal you need to do this.
```
sudo apt-get install b43-fwcutter
```
```
sudo apt-get install firmware-b43legacy-installer

```

---

### Post by JazzyJoe70 on 2011-07-27
ok i ran them both but the b43legacy-installer gave me an error.  

firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1

i went ahead and restart the computer but it still didn't work.

---

### Post by wildmanne39 on 2011-07-27
Hi, and is that the same error you get when you try to install it from synaptic?

---

### Post by JazzyJoe70 on 2011-07-27
adrian@adrian-Latitude-D400:~$ sudo apt-get install b43-fwcutter

Reading package lists... Done
Building dependency tree        
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 198 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:165
14e4:4320)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wildmanne39 on 2011-07-27
Hi, run these command please and post the results please.
```
lspci -nn | grep 0280
```
Thank you

---

### Post by JazzyJoe70 on 2011-07-27
This is what the wireless lan controller is using for driver the B43 driver. 

 *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcfec000-fcfedfff

---

### Post by JazzyJoe70 on 2011-07-27
adrian@adrian-Latitude-D400:~$ lspci -nn | grep 0280
01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

---

### Post by wildmanne39 on 2011-07-27
Hi, I installed them on my system through synaptic and through the terminal to make sure they installed and they did.
Please run these commands and if you get errors please post them here.
```
sudo apt-get update && sudo apt-get upgrade
```
I am checking to make sure you can install any packages at this time or if the package manager is broken.
Thank you

---

### Post by JazzyJoe70 on 2011-07-27
I ran the update and upgrade everything installed fine except for b43legacy

Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nm_geo on 2011-07-27
> **wildmanne39 said:**
> Hi, I installed them on my system through synaptic and through the terminal to make sure they installed and they did.
Please run these commands and if you get errors please post them here.
```
sudo apt-get update && sudo apt-get upgrade
```I am checking to make sure you can install any packages at this time or if the package manager is broken.
Thank you

+1 on
 the update & upgrade are probably needed going to be a large number of updates.

---

### Post by nm_geo on 2011-07-27
You might try the firmware-b43-installer..
Remove the legacy firmware ..

This does not agree with the Linux B43 link but who knows.

> [COLOR=Red]Not supported card here (PCI id 14e4:165
14e4:4320)!
Use b43 firmware. This is just for the b43legacy driver[/COLOR].

Strange indeed.. more history perhaps and it will not hurt a thing.

---

### Post by JazzyJoe70 on 2011-07-27
I deleted the legacy drivers and restarted the computer but it still didn't work.

---

### Post by nm_geo on 2011-07-27
> **JazzyJoe70 said:**
> I deleted the legacy drivers and restarted the computer but it still didn't work.

Did you install the firmware-b43-installer <<< note not legacy
and make sure b43-fwcutter is installed.
Try that then 

```
dmesg | grep firmware
```

---

### Post by JazzyJoe70 on 2011-07-27
yes both firmware-b43-installer and b43-fwcutter are installed.

---

### Post by nm_geo on 2011-07-27
> **JazzyJoe70 said:**
> yes both firmware-b43-installer and b43-fwcutter are installed.

please in terminal

```
sudo modprobe b43 
```

```
dmesg | grep firmware
```

```
lsmod
```

```
sudo lshw -C network
```

---

### Post by JazzyJoe70 on 2011-07-27
dmesg | grep firmware

[   25.296206] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

lsmod

Module                  Size  Used by
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
i915                  450944  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
b43legacy             127415  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0 
b43                   296610  0 
mac80211              257001  2 b43legacy,b43
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   180037  2 i915,drm_kms_helper
soundcore              12600  1 snd
ppdev                  12849  0 
parport_pc             32111  1 
shpchp                 32345  0 
cfg80211              156212  3 b43legacy,b43,mac80211
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
dcdbas                 14054  0 
psmouse                73312  0 
lp                     13349  0 
serio_raw              12990  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
tg3                   131476  0 
ssb                    45942  2 b43legacy,b43
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6d:06:9f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5705-v3.11 ip=192.168.1.98 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:fcff0000-fcffffff memory:fd000000-fd00ffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcfec000-fcfedfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:1f:40:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by nm_geo on 2011-07-27
Okay you have removed the legacy firmware correct?

I think we need to reboot.. without ethernet cable..

Then let's run all those commands again.

We have a conflict ssb                    45942  2 b43legacy,b43

---

### Post by thefasterblueone on 2011-07-27
Can you run this and post results.

```
rfkill list
```

---

### Post by JazzyJoe70 on 2011-07-27
It seem like b43legacy is still there I thought I had deleted the file. I went to synaptic and seleted b43legacy and right click for complete removal.

adrian@adrian-Latitude-D400:~$ dmesg | grep firmware
[   23.601861] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

adrian@adrian-Latitude-D400:~$ lsmod
Module                  Size  Used by
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
i915                  450944  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
b43legacy             127415  0 
ppdev                  12849  0 
yenta_socket           27230  0 
drm                   180037  2 i915,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
parport_pc             32111  1 
soundcore              12600  1 snd
serio_raw              12990  0 
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
b43                   296610  0 
mac80211              257001  2 b43legacy,b43
cfg80211              156212  3 b43legacy,b43,mac80211
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
tg3                   131476  0 
ssb                    45942  2 b43legacy,b43
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

adrian@adrian-Latitude-D400:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6d:06:9f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:fcff0000-fcffffff memory:fd000000-fd00ffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcfec000-fcfedfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:1f:40:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by nm_geo on 2011-07-27
Let's try to remove the b43legacy

```
sudo rmmod -f b43legacy
```

```
sudo modprobe b43
```

---

### Post by JazzyJoe70 on 2011-07-27
*** rfkill list ****
adrian@adrian-Latitude-D400:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

*************

Ok i ran the following commands and restarted the computer
sudo modprobe b43
sudo rmmod -f b43legacy

---

### Post by nm_geo on 2011-07-27
> **JazzyJoe70 said:**
> *** rfkill list ****
adrian@adrian-Latitude-D400:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

*************

Ok i ran the following commands and restarted the computer
sudo modprobe b43
sudo rmmod -f b43legacy


Shows us the mods & drivers that are loaded
```
lsmod
```

Show us the current eth0 and wlan0
```
sudo lshw -C network
```

---

### Post by JazzyJoe70 on 2011-07-27
adrian@adrian-Latitude-D400:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
i915                  450944  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
pcmcia                 39671  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
arc4                   12473  2 
drm_kms_helper         40745  1 i915
b43legacy             127415  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
drm                   180037  2 i915,drm_kms_helper
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
dcdbas                 14054  0 
psmouse                73312  0 
parport_pc             32111  1 
shpchp                 32345  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
b43                   296610  0 
mac80211              257001  2 b43legacy,b43
cfg80211              156212  3 b43legacy,b43,mac80211
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
tg3                   131476  0 
firewire_ohci          31504  0 
ssb                    45942  2 b43legacy,b43
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


adrian@adrian-Latitude-D400:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6d:06:9f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:fcff0000-fcffffff memory:fd000000-fd00ffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcfec000-fcfedfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:1f:40:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by nm_geo on 2011-07-27
Ok we have not got that b43legacy under control.  we can blacklist it and then it should not return when you reboot.  Right now we have both b43 and b43legacy trying to run the wireless card.. Not good we need one or the other ..

So 

```
echo "blacklist b43legacy" >> /etc/modprobe.d/blacklist.conf 

```

Reading on the linux b43 link tells me you need the b43legacy, but apparently it did not work earlier.  We can always try it later..Just copy and paste the command above.. 

```
cat /etc/modprobe.d/blacklist.conf 
```

we should see b43legacy blacklisted... We can get it out later..

Then let's try another reboot...

---

### Post by JazzyJoe70 on 2011-07-27
I get the following:

bash: /etc/modprobe.d/blacklist.conf:  Permission denied

---

### Post by nm_geo on 2011-07-28
I hate Natty LOL

Ok 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```add this line ```
blacklist b43legacy
``` and then save and close

---

### Post by nm_geo on 2011-07-28
I forgot something on the echo.. sheech..
No problem the other way might be best...
go ahead and do 

```
cat /etc/modprobe.d/blacklist.conf 
```

after blacklisting the b43legacy.. That way we know it is in there..

---

### Post by JazzyJoe70 on 2011-07-28
adrian@adrian-Latitude-D400:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
snd_intel8x0           33213  2 
joydev                 17322  0 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
i915                  450944  2 
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
ppdev                  12849  0 
yenta_socket           27230  0 
drm                   180037  2 i915,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
dcdbas                 14054  0 
psmouse                73312  0 
parport_pc             32111  1 
soundcore              12600  1 snd
shpchp                 32345  0 
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
usb_storage            43946  1 
tg3                   131476  0 
ssb                    45942  1 b43
firewire_core          56138  1 firewire_ohci
uas                    17676  0 
crc_itu_t              12627  1 firewire_core




adrian@adrian-Latitude-D400:~$ sudo lshw -C network
[sudo] password for adrian: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6d:06:9f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:fcff0000-fcffffff memory:fd000000-fd00ffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcfec000-fcfedfff

---

### Post by nm_geo on 2011-07-28
Are we having fun yet?  well we have one driver ... but no firmware

hmmm..

```
modprobe b43
``````
dmesg | grep firmware
```

---

### Post by JazzyJoe70 on 2011-07-28
I typed both commands and nothing happened.

---

### Post by nm_geo on 2011-07-28
```
sudo apt-get install firmware-b43-installer
```

make sure we have some firmware installed..

then run 

```
lsmod
```

```
sudo lshw -C network
```

---

### Post by JazzyJoe70 on 2011-07-28
adrian@adrian-Latitude-D400:~$ sudo apt-get install firmware-b43-installer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
adrian@adrian-Latitude-D400:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
snd_intel8x0           33213  2 
joydev                 17322  0 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
i915                  450944  2 
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
ppdev                  12849  0 
yenta_socket           27230  0 
drm                   180037  2 i915,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
dcdbas                 14054  0 
psmouse                73312  0 
parport_pc             32111  1 
soundcore              12600  1 snd
shpchp                 32345  0 
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
usb_storage            43946  0 
tg3                   131476  0 
ssb                    45942  1 b43
firewire_core          56138  1 firewire_ohci
uas                    17676  0 
crc_itu_t              12627  1 firewire_core



adrian@adrian-Latitude-D400:~$ sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6d:06:9f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:fcff0000-fcffffff memory:fd000000-fd00ffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcfec000-fcfedfff

---

### Post by nm_geo on 2011-07-28
About the last shot I have for now..
We are going to remove the blacklist b43legacy by changing the line to blacklist b43.

```
sudo gedit /etc/modprobe.d/blacklist.conf
```Just delete the legacy part or delete the whole line.

add 
```
blacklist b43
```we are going to try the b43legacy again alone.. 

Go to Synaptic search on _bcm_ you should see the firmwares that are installed.
remove all but the firmware-b43legacy-installer and we still need the b43-fwcutter.. Only those two...

reboot with cable detached .. Then connect it if no wireless shows up..

---

### Post by JazzyJoe70 on 2011-07-28
Well it still didn't work after blacklisting b43 it still shows up when i do lsmod & sudo lshw -C network.

I want to thank you for all the help you did today.  I was really hoping to enjoy Ubuntu but it seems too complicated.  I'll probably just go back to Windows XP.

I'll probably continue tomorrow for a little bit, but if its going nowhere then I'll just go back.

Thank you once again for your help!

---

### Post by nm_geo on 2011-07-28
> **JazzyJoe70 said:**
> Well it still didn't work after blacklisting b43 it still shows up when i do lsmod & sudo lshw -C network.

I want to thank you for all the help you did today.  I was really hoping to enjoy Ubuntu but it seems too complicated.  I'll probably just go back to Windows XP.

I'll probably continue tomorrow for a little bit, but if its going nowhere then I'll just go back.

Thank you once again for your help!

Until you reboot b43 will be showing up ..

---

### Post by JazzyJoe70 on 2011-07-28
PROBLEM NOT SOLVED but I will post Solved just so I can close this thread and start a new one in hopes of resolving this wireless issue that i am having.

---

