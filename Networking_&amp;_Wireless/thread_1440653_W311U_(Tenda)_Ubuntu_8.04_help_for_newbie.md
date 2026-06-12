---
title: "W311U (Tenda) Ubuntu 8.04 help for newbie"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by :Chemist on 2010-03-27
I recently purchased a new Tenda W311U USB wireless network adapter and cannot get it to work with Ubuntu 8.04.  I am very new to Ubuntu and have tried web/forum searches, but can not find a solution.  Here's what I know...

lsusb

148f:3070 Ralink Technology, Corp.

iwconfig

lo     no wireless extensions

eth0  no wireless extensions

I don't know how to check for installed drivers or how to install drivers in general.  I have an install disc that has drivers on it, but I don't think Linux is supported.

The forums mentioned using ndiswrapper to install a Windows driver, which apparently must first be installed on a Windows system.  I tried it and it called for an .inf file.  There is an Autorun.inf on the driver disc, but I don't think that's the one.  After install on Windows XP, found "rt2870.inf" in C:\Program Files\Tenda\W311U, but not sure what to do from there...or if this is correct at all.  Please help.

---

### Post by bkratz on 2010-03-27
Here is a thread which may be of help- I hope.  You should be able to follow along and see if your results are the same. See the last post on the first page, post 10  for a recap.

[http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070)


I just noticed that you are on 8.04, this may not be applicable.
Sorry

---

### Post by :Chemist on 2010-03-27
It seems like I may have 2 drivers battling for control.  I think I could handle blacklisting the wrong one, but how do I check to see which are trying to control the device....or how do I check which are installed?  Thanks for the reply.

---

### Post by bkratz on 2010-03-27
> **:Chemist said:**
> It seems like I may have 2 drivers battling for control.  I think I could handle blacklisting the wrong one, but how do I check to see which are trying to control the device....or how do I check which are installed?  Thanks for the reply.

Well as I said I don't know if they are inherent in 8.04, that's pretty long ago, but you could check

```
lsmod | grep rt2
```

and see if you see both or none.

You know there is a new LTS version 10.04 coming out soon, right?

( that was LSMOD in lowercase)

---

### Post by :Chemist on 2010-03-28
Tried suggestion in terminal...not sure what to make of it

jason@jason-desktop:~$ lsmod | grep rt2
jason@jason-desktop:~$ lsmod
Module                  Size  Used by
af_packet              23812  2 
ipv6                  268036  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
it87                   20876  0 
hwmon_vid               4352  1 it87
lp                     12324  0 
usbhid                 32128  0 
evdev                  13056  5 
snd_ca0106             36192  2 
hid                    38784  1 usbhid
snd_ac97_codec        101028  1 snd_ca0106
ndiswrapper           192920  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
nvidia               7106084  34 
snd_pcm                78724  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
serio_raw               7940  0 
snd_rawmidi            25760  2 snd_ca0106,snd_seq_midi
psmouse                40336  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  15 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
ac97_bus                3072  1 snd_ac97_codec
i2c_viapro              9876  0 
via_agp                11136  1 
snd_page_alloc         11400  2 snd_ca0106,snd_pcm
agpgart                34760  2 nvidia,via_agp
i2c_core               24832  2 nvidia,i2c_viapro
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
ext3                  136968  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
ata_generic             8324  0 
floppy                 59588  0 
via_rhine              26632  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
sata_via               12420  0 
pata_via               13316  3 
pata_acpi               8320  0 
mii                     6400  1 via_rhine
usbcore               146412  5 usbhid,ndiswrapper,ehci_hcd,uhci_hcd
libata                159728  4 ata_generic,sata_via,pata_via,pata_acpi
scsi_mod              151692  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36616  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5

Work with me here, but what I think I'm seeing are modules, memory used (size), and count and list of other modules using each?  So...I'm not really looking for a wireless adapter module, but rather what ndiswrapper is being used by?  So it says zero, so I'm guessing that nothing is trying to control my device?

I checked around to see if my W311U is listed on ndiswrapper site, but didn't find it.  I'm guessing that ndiswrapper won't support this.  This, of course, is nothing but the wild speculation of a guy that has no idea what he is doing  :)

---

### Post by :Chemist on 2010-03-28
Thought these might help too:

lshw -C Network

*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:5b:53:d1:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.11 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
--------------------------------------------------------------
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:5b:53:d1:0b  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe53:d10b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4043 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2141791 (2.0 MB)  TX bytes:412024 (402.3 KB)
          Interrupt:18 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69200 (67.5 KB)  TX bytes:69200 (67.5 KB)

---

### Post by :Chemist on 2010-03-29
So plan B:  I'm about to give up on trying to figure out how to tell what drivers I have installed and/or which are trying to control my W311U wireless network adapter.  I suppose I should move to the super-beginner forum  :)  Anyone have a recommendation for a cheap wireless network adapter (USP or PCI) for a P4 desktop that will work with 8.04 or 10.04 LTS?  My Tenda W311U was only $15 and I don't want to spend much more.

---

### Post by eeBus on 2010-04-05
Tenda W311U working fine for me on my netbook running Ubuntu 10.04 beta 1.

All I did was to add rt2870sta to the end of /etc/modules file.

Netbook has its own built in wireless 11g. I disable this with a switch at the side, so it is probably important to make sure you don't have a clash of drivers.

But this message was send using the Tenda!

---

### Post by :Chemist on 2010-04-12
Thanks for the suggestion.  I'm getting an error message when I try to add it.

Opened it in text editor, added rt2870sta and tried to save:
"Could not save the file /etc/modules.  You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Any ideas?  Glad it worked for somebody.  I'm planning on updating to 10.04 so maybe it will work then  :)

---

### Post by Jamie Jackson on 2010-04-12
You tried to edit the file as a normal user, but you need to be admin. To open gedit as root, issue the following from the command line, or enter it at the Alt-F2 runner thingy.

```
gksu gedit /etc/modules
```

---

### Post by :Chemist on 2010-04-15
Solved the problem.  Solution is here:

[http://ubuntuforums.org/showthread.php?t=1444925](http://ubuntuforums.org/showthread.php?t=1444925)

Pretty much involved upgrading to Ubuntu 9.10 and blacklisting some drivers.

Thanks to Chili555 for the solution and everyone else for the help.

:Chemist

---

