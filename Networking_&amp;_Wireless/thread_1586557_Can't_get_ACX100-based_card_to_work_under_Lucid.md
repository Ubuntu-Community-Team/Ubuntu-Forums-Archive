---
title: "Can't get ACX100-based card to work under Lucid"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by bgii_2000 on 2010-10-02
OK, so let's get some preliminaries out of the way.

I really don't know what I'm doing.  I know how to use the command line (though, I'm not often sure EXACTLY what I'm doing with it), I know basically what sudo is.  Beyond that I'm pretty lost if you were to ask me to explain any of linux/ubuntu/unix/etc...

However.  I'm good at following instructions.

I have an ancient Toshiba Satellite 1415 laptop.

[LIST]
[*]1.8GHz Celeron
[*]256MB RAM
[*]nVidia GeForce4 420Go (with nVidia X drivers actually working, woooo!)
[*]Intel integrated 10/100 Ethernet
[*]DVD-ROM/CD+/-RW drive [non-functioning]
[*]integrated 802.11b card [non-functioning]
[/LIST].

I've installed Lucid via PXE (see above RE: non-functioning optical disc drive).  It was a hassle to do so, but since I've not been able to get this laptop to boot from a usb drive, it seemed the way to go.  However, the PXE setup process is not exactly straightforward; therefore I THINK I installed it correctly because most everything else works fine, but I really have no way of knowing.

More preliminaries:

As the built-in wireless card in the Laptop has been dead for longer than I care to remember, I'm attempting to use a PCMCIA D-Link DWL-650+ (not a 650 or a 650G or a 650G+) which says that it's supposed to work "out of the box" with the ACX100 driver.

lspci returns the line:
```
05:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

```

ifconfig returns info on "eth0" and "lo", the ethernet, and loopback interfaces respectively.  It makes no mention of a wlan0 interface.

iwconfig reports (correctly) that eth0 and lo have no wireless extentions.

lsmod returns:
```
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd_seq_oss            26726  0 
font                    7557  1 fbcon
snd_seq_midi            4557  0 
bitblit                 4707  1 fbcon
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 30784  0 
softcursor              1189  1 bitblit
nvidia               4701243  32 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
yenta_socket           20408  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_timer              19098  2 snd_pcm,snd_seq
intel_agp              24119  1 
rsrc_nonstatic         10015  1 yenta_socket
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                31724  2 nvidia,intel_agp
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                  8708  0 
soundcore               6620  1 snd
shpchp                 28820  0 
lp                      7060  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
ppdev                   5259  0 
video                  17375  0 
parport_pc             25962  1 
toshiba_acpi            8662  0 
output                  1871  1 video
parport                32635  3 lp,ppdev,parport_pc
psmouse                63245  0 
serio_raw               3978  0 
e100                   28211  0 
mii                     4381  1 e100
floppy                 53016  0 

```

No mention of ACX, WLAN, or wireless anything.

There was a huge amount of info in the Kernel boot messages.  dmesg | grep "wlan_module_name" returns nothing.

This seems noteworthy: lshw -C network returns:
```
 *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:00:39:68:7f:92
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.60.105 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:fceff000-fcefffff ioport:df40(size=64)
  *-network UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: ioport:d800(size=32) memory:20010000-20010fff memory:20000000-2000ffff

```
That "UNCLAIMED" up there would seem to indicate a problem.

I'm running Ubuntu 10.04.1 LTS.  Kernel/architecture is 2.6.32-25-generic i686.  This laptop ancient and cheap, so it's definitely 32bit.

I've tried following various tutorials for getting an ACX100 based-card to work, but keep running into errors that the tutorial doesn't cover.  The main problem seems to be that almost all the info out there is out-dated by about 2 years.  The ACX100 project's Wiki at TheSourceForge states, "[Ubuntu 9.10 deprecated linux-restricted-modules in favor of DKMS. (Good luck with that)]("http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu")" 

So, uh, yeah.  Any help here would be hot.

---

### Post by chili555 on 2010-10-02
The module acx.ko has been omitted from the mainline and Ubuntu kernel for some time. It is buggy, slow, unreliable, nasty and ugly and it doesn't love its mommy.

There are many threads here about acx100 and you may find one that's successful. I doubt it.

You might try ndiswrapper if you have or can download the Windows XP .inf and .sys files.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Although it's not clearly stated, this:> dmesg | grep "wlan_module_name" returns nothing.Actually means dmesg | grep acx. In human language, read out the kernel messages but only the lines with 'acx' in them. You will have none as I explained.

---

### Post by chili555 on 2010-10-02
Here is a thread that says he got his working with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520](http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520)

See post #8.

---

### Post by bgii_2000 on 2010-10-02
See, if the Internet would just say that, my life would be this much easier.  Well... I guess it does now.

**Chili555**, thanks for the helping hand.  I'll give nsidwrapper a go

---

### Post by bkratz on 2010-10-02
This is a very useful site to find things about Ubuntu rather than just google.

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by chili555 on 2010-10-02
> thanks for the helping hand. I'll give nsidwrapper a goPost back if you get stuck. We'll be glad to assist.

---

