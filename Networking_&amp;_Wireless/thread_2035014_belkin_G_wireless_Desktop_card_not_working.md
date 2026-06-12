---
title: "belkin G wireless Desktop card not working"
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by anonymusneo on 2012-07-29
Hi all :) first time linux user here


i am using my wireless card on win7 with driver f5d7000_v7032_0831.exe

ubuntu 11.10 is installed on virtual box



i have tried ndiswrapper , R74092us.exe
after installing i get 

bcmwl5 : invalid driver!
bcmwl5a : invalid driver!




iwconfig
> lo        no wireless extensions.
eth0      no wireless extensions.
lsmod
> Module                  Size  Used by
vboxguest             195204  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
vesafb                 13489  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
parport_pc             32114  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
psmouse                73673  0 
serio_raw              12990  0 
i2c_piix4              13093  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
ahci                   21634  2 
libahci                25727  1 ahci
e1000                 101773  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
sudo lshw -C network
>   *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:f1:5b:10
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:10 memory:f0000000-f001ffff ioport:d010(size=8)
lspci -nn
> 00:00.0 Host bridge [0600]: Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02)
00:01.0 ISA bridge [0601]: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] [8086:7000]
00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef]
00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
00:04.0 System peripheral [0880]: InnoTek Systemberatung GmbH VirtualBox Guest Service [80ee:cafe]
00:05.0 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 01)
00:06.0 USB Controller [0c03]: Apple Computer Inc. KeyLargo/Intrepid USB [106b:003f]
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
00:0d.0 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
rfkill list all
> does nothing

Thanks in advance :)

---

### Post by Kirk Schnable on 2012-07-29
If Ubuntu is running in VirtualBox, is there actually a reason to set it up to have physical access to the network card?  VirtualBox supports NAT and bridged networking already, and I was not under the impression that special drivers were required for that.

Kirk

---

### Post by Cheesehead on 2012-07-29
Kirk Schnable is right.
The VM Guest (Ubuntu) should show an ethernet (not wireless) connection,
The VM Host (Windows) should control the actual wireless connection.

The VM host software (VBox Application) provides a virtual router between the upstream windows-controlled network connection and the downstream VMs. That's why the VMs show an eth connection. The Network control panel within VBox has various configuration options, but the default will work.

The default VBox install on a host, and the default Ubuntu install in a guest should be able to get an internet connection with NO configuration by the user. Ubuntu's Network Managershould offer and ethernet connection that just works.

---

### Post by anonymusneo on 2012-07-30
Hi , 

Thanks for your replies . but i saw a video 

[http://www.youtube.com/watch?v=Ngs5GUOA5ts&feature=my_liked_videos&list=LL2kak-3BWyTzBkWMr2bm7ig](http://www.youtube.com/watch?v=Ngs5GUOA5ts&feature=my_liked_videos&list=LL2kak-3BWyTzBkWMr2bm7ig)

here he has backtrack installed on Virtualbox sort of similar software

If his distro is working, cant mine work? :)


thanks

---

### Post by Cheesehead on 2012-07-31
Sure, but you should probably ask him how he did it that way.
He also specified backtrack for various reasons.
Versions of airmon work on Windows. That's easier.

---

