---
title: "Help with internet"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by collinge on 2010-11-27
okay... i used to dual boot ubuntu 9.something with my XP. i would actually switch the HDs around. I got another computer to put the linux HD in - similar in style. Both are dells. 

The problem is when i ran another ethernet cable to my linux from my router, i now have no internet on that machine. 

i have looked around on the treads and i have tried the code

cat /etc/resolv.conf

all it says it "Network Manager"

I cant paste the output of large commands becasue i have to maunually type them in... any idea?

---

### Post by MooPi on 2010-11-27
Can you post the contents of this file
```
/etc/network/interfaces
```
It is from 5 to 10 lines not to long if your concerned.

---

### Post by collinge on 2010-11-27
all it says is :
auto lo
iface lo net loopback

---

### Post by MooPi on 2010-11-27
I think we have a simple fix
```
gksudo gedit /etc/network/interface
```
Add at the end of the file add
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```
Proof read save and close.
Then in terminal
```
sudo ifconfig eth0 up
```
Test your connection. If it's not working try a reboot.

---

### Post by collinge on 2010-11-27
When i run ifconfig i get : ERROR while getting interface flags: no such device

---

### Post by MooPi on 2010-11-27
Did you edit the /etc/network/interfaces file ?
I'm going to need to see the results from
less /etc/network/interfaces>netwoked
This command will deposit a text file in your home directory. Attach that file to your next post for review.

---

### Post by karthick87 on 2010-11-27
Did you  run

```
sudo ifconfig eth0 up
```

---

### Post by fubeca6 on 2010-11-27
Thank you MooPi! I was having the same problem - it seems to be resolved after editing the /etc/network/interfaces file and running the <ifconfig eth0 up>, etc.  Hopefully it keeps working :) 

Thank you!

---

### Post by collinge on 2010-11-27
i did the ifconfig command.. the output of the network doc reads:

auto lo
iface lo inet interface
# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by MooPi on 2010-11-27
OOPs wrong person

Okay Houston we have a problem
```
lspci>mypci
```
```
lsmod>mymods
```
This will deposit text files in your home folder named mypci & mymods
Please attach these to your next post.

---

### Post by collinge on 2010-11-27
sorry for the format - i had copy output to Wine-notepad - transfer to windows on another computer and ... Wollah
```
 My Mod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_emu10k1_synth       6140  0 
snd_emux_synth         32860  1 snd_emu10k1_synth
snd_seq_virmidi         5628  1 snd_emux_synth
snd_seq_midi_emul       6332  1 snd_emux_synth
snd_emu10k1           135136  3 snd_emu10k1_synth
snd_ac97_codec        101216  1 snd_emu10k1
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  2 snd_emu10k1,snd_pcm
snd_util_mem            4156  2 snd_emux_synth,snd_emu10k1
snd_hwdep               7200  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6940  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                50224  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6920  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 10272  0 
ppdev                   6688  0 
snd                    59204  18 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
parport_pc             31940  1 
iptable_filter          3100  0 
lp                      8964  0 
ip_tables              11692  1 iptable_filter
dell_wmi                2564  0 
shpchp                 32272  0 
parport                35340  3 ppdev,parport_pc,lp
psmouse                56180  0 
serio_raw               5280  0 
dcdbas                  7292  0 
x_tables               16544  1 ip_tables
intel_rng               4444  0 
hid_logitech            8412  0 
ff_memless              5188  1 hid_logitech
usbhid                 38208  1 hid_logitech
floppy                 54916  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
e100                   32452  0 
mii                     5212  1 e100
intel_agp              27484  1 
agpgart                34988  1 intel_agp

```

My PCI
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:08.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)
```

---

### Post by collinge on 2010-11-27
do you think its the tower? or at least the onboard ethernet controller... i might change towers and see it that gets it if this doesnt work

---

### Post by MooPi on 2010-11-27
Your computer is recognizing the adapter & module (Intel Corporation 82557/8/9/0/1 Ethernet Pro 100---module e100) so they exist and should be working, At least I'm going to temporarily go with that idea.
Lets try ifconfig another time
```
ifconfig
ifconfig eth0
ifconfig eth1

``` Each separately to see the if possibly something else is going on.

---

### Post by collinge on 2010-11-27
```
collinge@Linux:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:07:e9:f0:27:84  
          inet6 addr: fe80::207:e9ff:fef0:2784/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:626595 (626.5 KB)  TX bytes:10044 (10.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6343 (6.3 KB)  TX bytes:6343 (6.3 KB)

collinge@Linux:~$ ifconfig eth0
eth0: error fetching interface information: Device not found
collinge@Linux:~$ ifconfig eth1
eth1: error fetching interface information: Device not found
collinge@Linux:~$ 

```

---

### Post by MooPi on 2010-11-27
Problem solved I think
```
gksudo gedit /etc/network/interfaces
```
Substitute eth0 with eth2 
Save and close. 
```
ifconfig eth2 up
```
Check connection. I suspect that you may have had alternate NIC cards attached to the computer at one time or another which changed the desigantion from eth0 to eth2. I have a bootable flash drive that contains six alternate eth connections configured.

---

### Post by collinge on 2010-11-27
no luck

---

### Post by MooPi on 2010-11-27
That last set of instructions should have worked, something is a miss. I just noticed something from your earlier post containing the file in question.Yours reads:```
auto lo
iface lo inet interface
# The primary network interface
auto eth0
iface eth0 inet dhcp
```
And it should read:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth0 inet dhcp
```
Copy and paste the above code with gedit. Name the file ```
interfaces
```
then ```
sudo cp interfaces /etc/network/
```
That should overwrite your file making the correction.
```
sudo ifconfig eth2 up
```
Check connection, or reboot.

---

