---
title: "Can't connect to internet pppoe"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by tech291083 on 2011-07-14
Hi,  

I have cable internet connection at home. The grey cable from my ISP goes directly into my pc from a switch placed in the building I am living in. There is no modem or router etc that I use. I have got another pc with Ubuntu 10.10 installed on it, but it does not connect to the internet with pppoe, while an old pc with Ubuntu and Windows XP (it is a dual boot system) does. What could be the prolem? The pc is ok and just like new. Is it MAC binding or something? Thanks.

---

### Post by tech291083 on 2011-07-25
Please help me, thanks

---

### Post by ddastoor on 2011-07-25
As your aware, the gnome network applet in the panel has pppoe functionality installed (are u using gnome?) 

Goto the ADSL tab and enter your pppop options.

On the PC that pppoe worked, did u set it up via the command line? or the gnome applet? Try and remember what u did for that PC.. ?

---

### Post by tech291083 on 2011-07-26
Hi ddastoor,

I tried everything I can but it does not connect at all. Please help, thanks

---

### Post by ddastoor on 2011-07-26
hi, i had this (or similar i don't remember now) problem long back... 


try installing/setting up pppoe manually:
[http://www.roaringpenguin.com/products/pppoe]("http://www.roaringpenguin.com/products/pppoe")

then run it and follow the instructions.. i believe while at it, they'll ask u if u want to startup the connection at boot, say yes

let me know if this works or not..

---

### Post by 98174 on 2011-07-26
Run
```
pppoeconf
```
from a terminal, and follow the instructions.

---

### Post by tech291083 on 2011-07-26
> **98174 said:**
> Run
```
pppoeconf
```from a terminal, and follow the instructions.

Yes, I did that as well. Went upto the last stage which says - Your connection has been triggered and use pon dsl-provider command to start the connection and poff dsl-provider to close the connection. I did this process a few times already. This process itself runs without any problem but there is no connectivity at all, please help. Thanks.

---

### Post by tech291083 on 2011-07-26
> **ddastoor said:**
> 

try installing/setting up pppoe manually:
[http://www.roaringpenguin.com/products/pppoe](http://www.roaringpenguin.com/products/pppoe)




Ok, is this the latest version of pppoe? Will it be compatible with my Ubuntu 10.10?  Just curious?  I am not sure how to set it up manually, I mean the commands etc required here to do so. But is it necessary for me to know whether it has been installed by default during installation of Ubuntu. I think the command for that is 

```
apt-cache packagename
```

```
dpkg -s packagename
```

Thanks.

---

### Post by tech291083 on 2011-07-26
I did this

```
dpkg -s ppp
```

and the output said that the package is installed.

then,

```
dpkg -s pppoe
```

the output said that the package is not installed.

---

### Post by tech291083 on 2011-07-26
I again tried the following command 

```
sudo pppoeconf
```
and followed instructions until the very last window - Connection initiated- which says -

```
The DSL connection has been triggered.
```

---

### Post by tech291083 on 2011-07-26
Is it possible for me to install pppoe from the Ubuntu CD? I found these commands useful for doing so, but not sure whether they really work or not.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ppp pppoe
```

---

### Post by ddastoor on 2011-07-27
can u reboot and then try:

```
sudo pon dsl-provider
```

If this doesn't work I'm beginning to think that maybe your ethernet NIC card doesn't have a driver or is not detected ?

can u post the output of :
```

sudo lshw | grep -i ether
sudo lsmod

```

and see if anything shows up regarding ur NIC card ?

---

### Post by ddastoor on 2011-07-27
also 

```

sudo lshw -C network

```

to see which driver, if at all has been loaded for your ethernet card...

basically, we're trying to find out whether u might need to download the driver from the internet and build it..

---

### Post by tech291083 on 2011-07-28
```
james@james-G31-M7-TE:~$ sudo lshw| grep -i ether
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
``````

james@james-G31-M7-TE:~$ sudo lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
pppoe                   9015  0 
pppox                   2054  1 pppoe
binfmt_misc             6599  1 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
i915                  290938  3 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168054  4 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
parport_pc             26058  1 
psmouse                59033  0 
led_class               2633  0 
serio_raw               4022  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport                31492  3 ppdev,parport_pc,lp
r8169                  36489  0 
mii                     4425  1 r8169

``````

james@james-G31-M7-TE:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:a2:17:24
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:febe0000-febfffff

```

After reboot....

```

james@james-G31-M7-TE:~$ sudo pon dsl-provider
[sudo] password for james: 
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

```

---

### Post by tech291083 on 2011-07-28
```
james@james-G31-M7-TE:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:a2:17:24  
          inet6 addr: fe80::2e0:4dff:fea2:1724/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130151 (130.1 KB)  TX bytes:14466 (14.4 KB)
          Interrupt:42 Base address:0x2000 

```

```

james@james-G31-M7-TE:~$ dmesg |grep eth0
[    0.734399] r8169 0000:02:00.0: eth0: RTL8102e at 0xf8062000, 00:e0:4d:a2:17:24, XID 04a00000 IRQ 42
[   10.431474] r8169 0000:02:00.0: eth0: link up
[   10.431482] r8169 0000:02:00.0: eth0: link up
[   20.672008] eth0: no IPv6 routers present

```

```

james@james-G31-M7-TE:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:         45          0   IO-APIC-edge      timer
  1:          6        615   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:      36473         84   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:          0          0   IO-APIC-fasteoi   uhci_hcd:usb5
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:       8278       1353   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb3
 23:          1       1512   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 40:          0          0   PCI-MSI-edge      pciehp
 41:          0          0   PCI-MSI-edge      pciehp
 42:         24       2442   PCI-MSI-edge      eth0
 43:      18207         58   PCI-MSI-edge      i915
 44:        219        493   PCI-MSI-edge      hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:      28369      21730   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       1559       1310   Rescheduling interrupts
CAL:         63         75   Function call interrupts
TLB:        725        667   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          3          3   Machine check polls
ERR:          1
MIS:          0

```

---

### Post by BobbyD45 on 2011-07-28
I had the same problem. I did a clean re-install from my disk and it 
connected up right away. I realise some people do not want to do it this way,but it 
worked for mr after I had tried everything else.

---

### Post by ddastoor on 2011-07-28
> **tech291083 said:**
> ```
james@james-G31-M7-TE:~$ sudo lshw| grep -i ether
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
``````

james@james-G31-M7-TE:~$ sudo lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
pppoe                   9015  0 
pppox                   2054  1 pppoe
binfmt_misc             6599  1 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
i915                  290938  3 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168054  4 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
parport_pc             26058  1 
psmouse                59033  0 
led_class               2633  0 
serio_raw               4022  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport                31492  3 ppdev,parport_pc,lp
r8169                  36489  0 
mii                     4425  1 r8169

``````

james@james-G31-M7-TE:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:a2:17:24
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:febe0000-febfffff

```

After reboot....

```

james@james-G31-M7-TE:~$ sudo pon dsl-provider
[sudo] password for james: 
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

```




yes, driver=r8169 and if u do a 
```
modprobe -vl | grep r8169

```

you should get something like:
```
kernel/drivers/net/r8169.ko

```

after you did
```
sudo pon dsl-provider

```, did u get the net ?

Also are u DHCP or static IP when u installed pppoe ?

---

### Post by ddastoor on 2011-07-28
sorry to mention, based on the above and ur confirmation of the mod prob command, it seems that ur driver's fine.. .

---

### Post by tech291083 on 2011-07-28
> **ddastoor said:**
> yes, driver=r8169 and if u do a 
```
modprobe -vl | grep r8169

```you should get something like:
```
kernel/drivers/net/r8169.ko

```after you did
```
sudo pon dsl-provider

```, did u get the net ?

Also are u DHCP or static IP when u installed pppoe ?

Hi,

I tried the command modprobe .. and got the same output that you have mentioned. But sudo pon dsl-provider again did not seem to connect me to the net. I never installed pppoe. I had no network cable attached to the pc when I installed Ubuntu 10.10. But 1% chance is that it was connected while installation and I generally choose DHCP. Thanks

---

### Post by tech291083 on 2011-07-28
```

james@james-G31-M7-TE:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

james@james-G31-M7-TE:~$ plog
Jul 29 08:21:08 james-G31-M7-TE pppd[1962]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Jul 29 08:21:08 james-G31-M7-TE pppd[1964]: pppd 2.4.5 started by root, uid 0
Jul 29 08:21:08 james-G31-M7-TE pppd[1964]: PPP session is 247
Jul 29 08:21:08 james-G31-M7-TE pppd[1964]: Connected to 00:08:a1:5e:96:31 via interface eth0
Jul 29 08:21:08 james-G31-M7-TE pppd[1964]: Using interface ppp0
Jul 29 08:21:08 james-G31-M7-TE pppd[1964]: Connect: ppp0 <--> eth0
Jul 29 08:21:08 james-G31-M7-TE pppd[1964]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access

james@james-G31-M7-TE:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

james@james-G31-M7-TE:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com

james@james-G31-M7-TE:~$ ping www.google.com
ping: unknown host www.google.com

james@james-G31-M7-TE:~$ ping 123.54.25.49
connect: Network is unreachable

james@james-G31-M7-TE:~$ ping 123.154.25.49
connect: Network is unreachable

james@james-G31-M7-TE:~$ ping 123.154.125.49
connect: Network is unreachable

james@james-G31-M7-TE:~$ ping 163.154.125.49
connect: Network is unreachable


```

Thanks, please help I am not connected yet.

---

### Post by tech291083 on 2011-07-28
> **ddastoor said:**
> As your aware, the gnome network applet in the panel has pppoe functionality installed, are u using gnome? 


I am not sure whether I am using GNOME. How do I check that? Thanks.

---

### Post by tech291083 on 2011-07-29
```
james@james-G31-M7-TE:~$ ls -l /usr/share/xsessions
total 20
-rw-r--r-- 1 root root 191 2010-09-27 22:15 gnome.desktop
-rw-r--r-- 1 root root 252 2010-09-27 22:15 gnome-failsafe.desktop
-rw-r--r-- 1 root root 198 2010-09-13 13:37 guest-restricted.desktop
lrwxrwxrwx 1 root root  24 2011-07-23 11:36 une-efl-guest-restricted.desktop -> guest-restricted.desktop
lrwxrwxrwx 1 root root  24 2011-07-23 11:36 une-guest-restricted.desktop -> guest-restricted.desktop
-rw-r--r-- 1 root root 117 2010-09-13 19:18 xsession.desktop
-rw-r--r-- 1 root root 170 2010-09-13 19:18 xterm.desktop

```

It says total 20, not sure whether there are really 20 types of desktop enviornements are installed on my Ubuntu. Or amy be it means something else. But there are a few lines in the output that seem to contain the keyword "gnome", so I guess gnome is one of the desktop environments installed, but which one I am running currently? That is a mystery to me so, I tried this.


```

james@james-G31-M7-TE:~$ env
ORBIT_SOCKETDIR=/tmp/orbit-james
SSH_AGENT_PID=1353
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=f96bbfe74d8998992f15b35a00000003-1311911574.578384-580475298
WINDOWID=20971524
GNOME_KEYRING_CONTROL=/tmp/keyring-W8ufKL
GTK_MODULES=canberra-gtk-module
USER=james
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/keyring-W8ufKL/ssh
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
SESSION_MANAGER=local/james-G31-M7-TE:@/tmp/.ICE-unix/1323,unix/james-G31-M7-TE:/tmp/.ICE-unix/1323
USERNAME=james
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/james
GDM_KEYBOARD_LAYOUT=us
LANG=en_IN
GNOME_KEYRING_PID=1304
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
GDM_LANG=en_IN
GDMSESSION=gnome
SHLVL=1
HOME=/home/james
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=james
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-4FOniL0E2k,guid=337ebbfd0d690719ff84068f00000017
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/var/run/gdm/auth-for-james-fo1v7q/database
COLORTERM=gnome-terminal
_=/usr/bin/env


```

---

### Post by tech291083 on 2011-07-29
```
DESKTOP_SESSION=gnome

```

Does this line mean that I am currently (for this session) running gnome? Thanks

---

### Post by tech291083 on 2011-07-30
I have downloaded these 2 packages from here for my Ubuntu 10.10. Now how to install them manually?

```

[pppoe]("http://packages.ubuntu.com/maverick/pppoe") (3.8-3) [**universe**]PPP over Ethernet driver

```

```

[pppoeconf]("http://packages.ubuntu.com/maverick/pppoeconf") (1.19ubuntu1)configures PPPoE/ADSL connections 
```

[http://packages.ubuntu.com/maverick/allpackages](http://packages.ubuntu.com/maverick/allpackages)


Thanks

---

### Post by ddastoor on 2011-07-31
Yes, it will mostly be in a src gz version which you have to unzip
1) gunzip <name>.tar.gz
2) tar xf <name>.tar
3) cd <name>

There will be instructions in there on how to install.
Usually, they should be:
sudo ./configure 
sudo make
sudo make install

---

### Post by ddastoor on 2011-07-31
Also, before you try installing the tar.gz version, can u try first uninstall the currently installed version by:

```
sudo apt-get remove pppoe
```

and then install again.


Also, Im just curious, when you first did pon dsl-provider, were you able to ping any site, e.g. google? like:

```
ping www.google.com
```  ??

---

### Post by tech291083 on 2011-07-31
I just double clicked on both the .deb files and the Ubuntu software Center GUI came up and I pressed the install button on the far right and install them. Restarted the pc and now I am connected to the net. This is really amazing. Here is the link to the page that tells to double click and install, that is why I did so.

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

> Double click on the package in GNOME to install it. 

But when I tried to install or update package using** sudo apt-get install/update packagename **it showed an error saying could not locate xyz package. Then I just typed **sudo apt-get update, **it asked me to insert Ubuntu CD, which I did and pressed enter, some packages were installed/updated from the CD itself. Then I tried **sudo apt-get install/update packagename **and it started installing/updating properly without any trouble. This is amazing. 

Is it always necessary to insert CD first and type **sudo apt-get update **to somehow update the system and then only you are allowed to use the internet to install/update packages with sudo?

Thanks...

---

### Post by ddastoor on 2011-07-31
hey this is great :) .. im glad it worked out : )

---

### Post by tech291083 on 2011-08-01
> **ddastoor said:**
> hey this is great :) .. im glad it worked out : )

thanks a lot, you have tried your best to help me out.

---

