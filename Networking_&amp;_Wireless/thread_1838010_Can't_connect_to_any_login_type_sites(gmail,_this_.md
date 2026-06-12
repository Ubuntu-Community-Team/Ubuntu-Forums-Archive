---
title: "Can't connect to any login type sites(gmail, this forum, ect)"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by morilibus on 2011-09-02
Hello,

I'm running Ubuntu 9.10, and am pretty much a noob when it comes to Linux.  However I am fairly competent and can follow directions, and have basic terminal skills.

My Problem:

I **CAN** connect to the internet, and browse many sites.
I **CANNOT  **connect to any site that requires you to login(tried with both Firefox and Epiphany); for example I can connect to [www.google.com]("http://www.google.com"), but If I try to access mail.google.com I get the "Unable to connect" page, I am able to browse this forum, but when I tried to login, I get the same error.  Thus I am accessing this forum through a virtual box running windows xp.

Through the virtual box (running on the Ubuntu system) I have no problems accessing any sites that require you to login.

I connect wired to a Asus router, I have tried disabling router firewall, and connecting directly to modem both resulting with the same issue.

I believe this must be a network problem with my system. I've tried searching the forums and trying to follow through similar issues to no avail.

So I was hoping someone could troubleshoot this with me.

here is some info based off other posts I've read.


**nm-tool**
```
marc@Tri-Serv:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        6C:F0:49:01:86:FD

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.112
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:1D:80:02:12

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```**dmesg | grep -i -e warn -e error**
```
marc@Tri-Serv:~$ dmesg | grep -i -e warn -e error
[    0.170634] ACPI Warning: Incorrect checksum in table [TAMG] - 88, should be 87 20090521 tbutils-246
[   17.600451] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   64.294983] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  418.197281] WARNING! Changing of MTU on this NICMay lead to frame reception errors!
[  500.448272] WARNING! Changing of MTU on this NICMay lead to frame reception errors!
[ 5592.512710] WARNING! Changing of MTU on this NICMay lead to frame reception errors!

```
**lsmod**
```
marc@Tri-Serv:~$ lsmod
Module                  Size  Used by
nfnetlink_queue         8736  2 
nfnetlink               4568  3 nfnetlink_queue
xt_tcpudp               2780  2 
nf_conntrack_ipv4      13352  2 
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
xt_state                1820  2 
nf_conntrack           67484  2 nf_conntrack_ipv4,xt_state
xt_NFQUEUE              2492  2 
ipt_REJECT              2812  2 
xt_mark                 1532  4 
binfmt_misc             8356  1 
vboxnetflt             14344  1 
vboxdrv               177320  2 vboxnetflt
xfs                   510016  2 
exportfs                4412  1 xfs
snd_hda_codec_atihdmi     3356  1 
iptable_filter          3100  1 
ip_tables              11692  1 iptable_filter
x_tables               16544  6 xt_tcpudp,xt_state,xt_NFQUEUE,ipt_REJECT,xt_mark,ip_tables
snd_hda_codec_realtek   203328  1 
snd_seq_dummy           2656  0 
snd_seq_oss            28608  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
coretemp                5564  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
it87                   19372  0 
hwmon_vid               2940  1 it87
snd_hda_intel          27016  0 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
lp                      8964  0 
ppdev                   6688  0 
usblp                  12636  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              22276  2 snd_seq,snd_pcm
fglrx                1989532  28 
parport_pc             31940  1 
parport                35340  3 lp,ppdev,parport_pc
snd                    59236  12 snd_hda_codec_realtek,snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
raid10                 23036  0 
raid1                  22460  0 
raid0                   8096  0 
multipath               7744  0 
linear                  5184  0 
dm_raid45              84228  0 
raid456                54140  1 
raid6_pq               80912  1 raid456
async_xor               3260  1 raid456
async_memcpy            1820  1 raid456
async_tx                3324  3 raid456,async_xor,async_memcpy
xor                    15620  3 dm_raid45,raid456,async_xor
ohci1394               29900  0 
usbhid                 38208  0 
ieee1394               86596  1 ohci1394
r8169                  32160  0 
mii                     5212  1 r8169
intel_agp              27996  0 
agpgart                34988  2 fglrx,intel_agp

```**dmesg | grep eth0**
```

marc@Tri-Serv:~$ dmesg | grep eth0
[    1.982434] eth0: RTL8168c/8111c at 0xf80d6000, 6c:f0:49:01:86:fd, XID 3c4000c0 IRQ 29
[   15.381495] r8169: eth0: link up
[   15.381501] r8169: eth0: link up
[   26.180009] eth0: no IPv6 routers present
[   68.547509] device eth0 entered promiscuous mode
[  435.572118] device eth0 left promiscuous mode
[  438.902268] r8169: eth0: link up
[  438.902541] device eth0 entered promiscuous mode
[  449.604011] eth0: no IPv6 routers present
[ 4085.909798] r8169: eth0: link down
[ 4089.760392] r8169: eth0: link up
[ 4214.179963] r8169: eth0: link down
[ 4221.713810] r8169: eth0: link up
[ 4541.245155] r8169: eth0: link down
[ 4550.313267] r8169: eth0: link up
[ 5269.349367] r8169: eth0: link down
[ 5278.278683] r8169: eth0: link up
[ 5322.431578] device eth0 left promiscuous mode
[ 5324.521724] r8169: eth0: link up
[ 5324.521988] device eth0 entered promiscuous mode
[ 5334.844508] eth0: no IPv6 routers present

```**sudo iwlist scan**
```
marc@Tri-Serv:~$ sudo iwlist scan
[sudo] password for marc: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.


```Thanks

---

### Post by wildmanne39 on 2011-09-02
Hi, there is an error message and here is a link but in short is says you have been hacked and people are trying to get your passwords.
[http://www.linuxquestions.org/questions/linux-security-4/kernel-device-eth0-entered-promiscuous-mode-756884/](http://www.linuxquestions.org/questions/linux-security-4/kernel-device-eth0-entered-promiscuous-mode-756884/)

Your version of ubuntu is to old it is no longer support so no security updates either you need to install at least 10.04 and it is the most stable right now as well.
Thank you

---

### Post by morilibus on 2011-09-02
nice,

thank you for your reply, I'll check out the link.

I have a Raid running on this system(not on the partition that the OS is running on however) Is there anything I should be careful about when upgrading as not to disturb the state of my raid?

---

### Post by wildmanne39 on 2011-09-02
Hi, you need to be careful partitioning and formatting but you need to do a clean install by reformatting the partitions that ubuntu is on then create new partitions without touching your other partitions.
Thank you

---

### Post by morilibus on 2011-09-02
ok, thank you.

I essentially have one hard drive dedicated to the ubuntu install, then I have 5 other hard drives running in a software raid-5.

so if I just reformat the main drive without disturbing the raid drives, will I be able to regain the raid again?

My main concern is this is a software raid and does depend on the OS to operate correct?

My guess is I would have to rebuild the raid again once the new install is up and running?
and as long as it set up again in the same way there shouldn't be any problems?

I'm going to do a backup of the raid in any case before proceeding to ensure I don't lose any data.

Where was the security breach shown? so I can try to ensure it doesn't happen again after the new install.

---

### Post by wildmanne39 on 2011-09-02
It said device eth0 entered promiscuous mode, in the dmesg eth0 information.

I gave a link for it and if you google that message you will find a lot of references to it.

Almost no one ever has a security problem with an updated version of ubuntu.
Thank you

---

### Post by morilibus on 2011-09-02
Ok,

Thank you again for your assistance.

---

### Post by wildmanne39 on 2011-09-02
Your welcome!

---

### Post by morilibus on 2011-09-05
New problem,

Ok, situation is as follows.


[LIST]
[*]Needed to back up data before I install ubuntu 11.04, however my 9.10 would not mount  the 3T drives I bought to back up the data. see my other problem here [http://ubuntuforums.org/showthread.php?t=1838078](http://ubuntuforums.org/showthread.php?t=1838078)
[*]huge workaround I installed ubuntu 11.04 on a virtual box, mounted the external drives there and can transfer data that way(slow 3.5 MB/s).
[*]Now on new virtual machine I have run into the same problem as this one, can't access login sites(gmail newsgroups) ect.
[/LIST]
I was able to access them initially when I first installed 11.04 on virtual box, and am trying to vigure out what I have done between being able to and not.  Or has this machine possibly been hacked aswell,  I did use the same user name for both, but different passwords.

from what I can remember the last two things I did was install Guest services for virtual box (ver 4.1.2) and SABnzbd.  I tried removing SABnzbd but the problem remains.  I have yet to try unsinstalling guest services, but that will be my next step, but I don't have that on other machine so that couldn't be a comon problem between the two.

Any ideas?  If I end up getting everything backed up (2 weeks straight of transferring data) then installing fresh 11.04, restoring data, just to have the same problem again...

---

### Post by wildmanne39 on 2011-09-05
Hi, I am going to have to research this issue further because this is a very strange issue, while I am doing that run the commands I gave you in my previous post.
Thank you

---

### Post by morilibus on 2011-09-05
ok thanks,

Also I'm currently able to login to this forum on the virtual box, but not to gmail, or newsgroups. or it might be because the problem occurred after I was already logged into this site.

These are from the virtual ubuntu 11.04
**nm-tool**
```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            pcnet32
  State:             connected
  Default:           yes
  HW Address:        08:00:27:A4:4E:4E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.4.15
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.4.2

    DNS:             192.168.1.1

```

[B]dmesg | grep -i -e warn -e error
[/B]```
[    7.585766] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.010841] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.685327] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 1166.305779]  [<c150abdf>] ? error_code+0x67/0x6c
[ 1166.351740]  [<c150abdf>] ? error_code+0x67/0x6c
[ 1620.559631]  [<c150abdf>] ? error_code+0x67/0x6c
[ 1620.566812]  [<c150abdf>] ? error_code+0x67/0x6c
[ 1620.575678]  [<c150abdf>] ? error_code+0x67/0x6c
[ 1620.584362]  [<c150abdf>] ? error_code+0x67/0x6c

```

[B]lsmod
[/B]```
Module                  Size  Used by
xfs                   735018  1 
nls_utf8               12493  1 
isofs                  39571  1 
exportfs               12870  1 xfs
vboxvideo              12484  1 
drm                   184164  2 vboxvideo
vesafb                 13449  1 
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
vboxsf                 38107  1 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ses                    17137  0 
enclosure              14656  1 ses
psmouse                73312  0 
parport_pc             32111  0 
vboxguest             199352  9 vboxsf
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usb_storage            43946  1 
floppy                 60032  0 
uas                    17676  0 
pcnet32                36760  0
```

**dmesg | grep eth0**
```
[    4.668419] pcnet32: eth0: registered as PCnet/FAST III 79C973
[   11.116052] pcnet32 0000:00:03.0: eth0: link up, 100Mbps, full-duplex
[   21.528156] eth0: no IPv6 routers present
[  726.007725] pcnet32 0000:00:03.0: eth0: link down
[  732.004438] pcnet32 0000:00:03.0: eth0: link up, 100Mbps, full-duplex

```

**sudo iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

---

### Post by wildmanne39 on 2011-09-05
I am going to research the error messages but I do not think they have anything to do with your problem, also do not think this is a network issue but I am not 100 percent sure of that.
Thank you

---

### Post by morilibus on 2011-09-05
Alright I figured out what I changed.

I was playing around with the Network Adapters for the Virtual Box.

I had it 'Bridged' Before, which allowed me to connect to the sites (gmail ect)

then I switched it to 'NAT' to see if it would make a difference in the transfer speed for the backup.

it did not, but I didn't change it back.

SO this is still probably just a problem with the 9.10 host machine.

[UPDATE]
I can't change my password on the ubuntu 9.10 machine. I go SYSTEM - ADMIN - USER AND GROUPS, I go to the properties of the user, click the 'change password' enter my old, enter my new one and it accepts, but as soon as I close that window it reverts back to my old one.

---

### Post by wildmanne39 on 2011-09-05
Hi, you still have 9.10 on a machine?
I believe not being able to change passwords was a symptom of the error message about it being hacked.
Thank you

---

### Post by morilibus on 2011-09-08
yes I still have 9.10, I need to back up my data (~4T) before I do a clean install of 10.04.  I was trying 11.04 inside of virtual box with the 9.10 machine.  I will let you know the outcome after the fresh install.

---

### Post by wildmanne39 on 2011-09-08
Hi, good luck.

---

