---
title: "wired internet very slow"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by timmmdogg on 2010-02-21
I am very new to Linux, although not completely computer illiterate.  I have installed ubuntu on an old laptop.  I am able to connect to the internet via a wired ethernet connection, however the speed is very slow, both in downloads and web surfing.

My broad band is very fast (about 20mb/s) so that is not the issue.  Surfing, downloading, and watching high quality video is no problem with my other lap top.

As I am a linux neophyte, I was not able to navigate some previous forums on this topic because I don't understand all the technical details and jargon. 

Can someone help?

---

### Post by northd_tech on 2010-02-21
First, go to this website and run both tests (for both IPv4 on the left and IPv6 on the right).  You can actually do this from a windows machine (or ubuntu)- it is just testing your router and ISP.

[http://www.ip6.me](http://www.ip6.me)

Post the results here when you get a chance.

Then if you can boot into ubuntu, open a terminal window (Applications > Accessories > Terminal, waaay down at the bottom of the list).  If you can also open a text editor (Applications > Accessories > Kate) or else type "gedit" in the terminal window that you've got open.

As you run these commands, paste the results into the text editor from the terminal window.  Save the file as something like "NetworkResultsBroken1.txt" or something similar (hopefully to a USB stick that you already plugged in to ubuntu so that it is already mounted and recognized).

Then pull the USB stick and reboot to Windows (or use another computer) to copy/paste post the results of these commands here (from that text file that you saved):

```
lspci

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig

sudo iwlist scan

nm-tool
```This is going to tell us a lot of information about your network hardware and current network configuration.

edit:  if you think the cable connection will stay connected long enough, you could probably post the results from the terminal window directly here under ubuntu (if I understand you correctly).

---

### Post by timmmdogg on 2010-02-22
Thanks so much for your reply!  When I get back home tonight I will do the following and respost.
 
I have already run the IPv4 vs. IPv6 test.  My router is IPv4.  I can also tell you that IPv6 is disabled in my network settings.
 
The rest I will run and repost tonight.
 
Thanks!

---

### Post by timmmdogg on 2010-02-22
rachel@rachel-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:09.0 Ethernet controller: Conexant Systems, Inc. HCF 56k Modem (rev 08)
00:09.1 Communication controller: Conexant Systems, Inc. HCF 56k Modem (rev 05)
00:0a.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

rachel@rachel-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_maestro3           19364  8 
snd_ac97_codec        101216  1 snd_maestro3
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  1 snd_pcm
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
pcmcia                 36808  0 
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
snd_timer              22276  7 snd_pcm,snd_seq
yenta_socket           24296  1 
joydev                 10240  0 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
x_tables               16544  1 ip_tables
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
psmouse                56500  0 
snd                    59204  20 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               5280  0 
i2c_piix4               9932  0 
soundcore               7264  1 snd
tulip                  48320  0 
intel_agp              27484  1 
agpgart                34988  1 intel_agp


rachel@rachel-laptop:~$ uname -a
Linux rachel-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux


rachel@rachel-laptop:~$ sudo lshw -C network 
[sudo] password for rachel: 
Sorry, try again.
[sudo] password for rachel: 
  *-network               
       description: Ethernet interface
       product: HCF 56k Modem
       vendor: Conexant Systems, Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 08
       serial: 00:50:8b:ac:42:26
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.64 latency=160 maxlatency=40 mingnt=20 multicast=yes
       resources: irq:9 ioport:1400(size=256) memory:f4000000-f4003fff


rachel@rachel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8b:ac:42:26  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8bff:feac:4226/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51207 errors:6 dropped:0 overruns:0 frame:6
          TX packets:10 errors:34323 dropped:0 overruns:0 carrier:68914
          collisions:0 txqueuelen:1000 
          RX bytes:68624821 (68.6 MB)  TX bytes:648 (648.0 B)
          Interrupt:9 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

rachel@rachel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


rachel@rachel-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


rachel@rachel-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tulip
  State:             connected
  Default:           yes
  HW Address:        00:50:8B:AC:42:26

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

---

### Post by Letrazzrot on 2010-02-22
I am a Linux noob, but in the slim chance that this may help, I'll tell you what I had to do fix my slow/intermittent  internet problem:

I turned off DHCP in the router, then set my computer's IP manually (static).  Then, instead of using the router's IP as the DNS, I manually set the DNS address to whatever the ISP has given me (I found those IPs in the router config).  Appearently, you can set the DNS servers in the network setup or whatever it is (the GUI application), but I'm not yet sure how to set multiple ones there (my ISP gives me 2 addresses).

Just setting the one DNS manually, instead of having my router forward it, seems to work fine. Before this, I had tried messing with the MTU, and Ip6 settings with no noticeable affect.

With my ISP, I don't think I can count on the DNS always being the same, but I doubt (hope!) they won't change often.

I don't know *why* it works, but it is, as far as I can tell, the only thing that turned my internet from basically unusable to perfectly fine.

---

### Post by northd_tech on 2010-02-23
> **timmmdogg said:**
>  **lspci**
00:09.0 **Ethernet** controller: **Conexant** Systems, Inc. **HCF**  56k Modem (rev 08  )
00:09.1 Communication controller: Conexant Systems, Inc. HCF 56k Modem  (rev 05)

**  lsmod**
Module                  Size  Used by
tulip                  48320  0 
  
 **uname -a**
laptop **2.6.31-19-generic** #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC  2010 **i686** GNU/Linux

  sudo lshw -C network 
  *-network               
       description: **Ethernet interface**
       product: **HCF 56k Modem**
       vendor: Conexant Systems, Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 08
       serial: 00:50:8b:ac:42:26
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes **driver=tulip**  driverversion=1.1.15 ip=192.168.1.64 latency=160 maxlatency=40 mingnt=20  multicast=yes
       resources: irq:9 ioport:1400(size=256) memory:f4000000-f4003fff
[B]
ifconfig[/B] 
eth0      Link encap:Ethernet  HWaddr 00:50:8b:ac:42:26  
          **inet addr:**192.168.1.64  Bcast:192.168.1.255   Mask:255.255.255.0
          [COLOR=Red]**inet6 addr: fe80::250:8bff:feac:4226/64  Scope:Link**[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51207 errors:6 dropped:0 overruns:0 frame:6
          TX packets:10 errors:34323 dropped:0 overruns:0 carrier:68914
          collisions:0 txqueuelen:1000 
          RX bytes:**68624821 (68.6 MB)**  TX bytes:**648 (648.0 B)**
          Interrupt:9 Base address:0x1400 

lo        Link encap:Local Loopback  
          **inet addr:**127.0.0.1  Mask:255.0.0.0
          [COLOR=Red]**inet6 addr: ::1/128 Scope:Host**[/COLOR]
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          [COLOR=Purple]RX bytes:240 (240.0 B)  TX bytes:240  (240.0 B)[/COLOR]

 ** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

**  nm-tool**
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0]  ----------------------------------------------------
  Type:              Wired
  **Driver:            tulip**
  State:             connected
  Default:           yes
  HW Address:        00:50:8B:AC:42:26

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254
OK- sorry it's taken so long- I was helping shop online for ancient hard  drives to make sure they would work with a relative's old PC (who won't  just let me put Linux on it).

Well...  umm... you've apparently  got an "integrated" Conexant HCF 56K modem/ethernet controller chip.   I've seen things similar to that before (sound/modem, etc.), but it's  been **a while**.  I never tried to run one under Linux though.  I'm  guessing this must be an older laptop, and I couldn't find any trace of  wireless anything.

This one might take some research (even for  other flavors of linux might help, I'd search for "Conexant HCF ethernet  linux" as a start).  I searched this forum and only found 2 threads  from 2008, and unfortunately, those were only for the 56K modem portion  of the chip that you've apparently got in there--- they both had  different [cable] ethernet network interfaces than you have- hmmm...

[http://ubuntuforums.org/showthread.php?t=833732&highlight=Conexant+HCF](http://ubuntuforums.org/showthread.php?t=833732&highlight=Conexant+HCF)

[http://ubuntuforums.org/showthread.php?t=899870&highlight=Conexant+HCF](http://ubuntuforums.org/showthread.php?t=899870&highlight=Conexant+HCF)

If  you've got open USB ports, adding a wireless USB adapter is an option  (and has the bonus of being transportable from computer to computer).   You would want to be **sure to do some research about USB interfaces  here first though**- as about 1/2 of them have been notoriously  "difficult" under unbuntu & Karmic 9.10 especially.  Also, some of  the PC-card adapters are rumored to be rock-stable under Linux, but the  connector cables are often/usually/always :-\" very fragile from my experience (and they  often get lost which makes the laptop's PC-card useless from that point forward). 

Also,  it looks like you've still got IPv6 sticking around- see the red parts I  bolded above- that might have something to do with your internet speed,  and I can probably help you disable that if you would like.  For  comparison, my ifconfig says this for my wireless (note there is no  "inet6 addr"):

> eth1      Link encap:Ethernet  HWaddr  00:01:00:03:b0:01  
          **inet addr**:192.xx.xx.xx   Bcast:192.xx.xx.xx  Mask:255.255.255.0
          UP BROADCAST RUNNING  MULTICAST  MTU:1500  Metric:1
          RX packets:75620 errors:0  dropped:0 overruns:0 frame:235482
          TX packets:50803  errors:30 dropped:0 overruns:0 carrier:0
          collisions:0  txqueuelen:1000 
          RX bytes:84878587 (84.8 MB)  TX  bytes:19509710 (19.5 MB)
          Interrupt:19 Let  me know if you want to attack the IPv6 thing- we might still be able to  speed things up with your settings, and it is connecting enough to  download almost 70MB.   (Unfortunately, I won't be much help with a  Conexant 56K Modem/ethernet :confused:-that's  a new one on me, but I have seen quite a few of the modem-only and  their sound chips in some older laptops).

If you want to watch  the progress or participate, I'll be focusing most of my  (not-so-Conexant 56K ;) ) IPv6/speed test stuff on this thread (or feel  free to PM me, Tim):

[http://ubuntuforums.org/showthread.php?t=1412994](http://ubuntuforums.org/showthread.php?t=1412994)

edit: That's a 32-bit version of the **2.6.31-19-generic **kernel, if you need that information.

---

### Post by timmmdogg on 2010-02-23
Thanks so much for your lengthy reply!The computer is old, nine years to be exact.We can run it through the IPv6 disable process if you think that might help.Also, I have a PCI wi-fi card for the computer, if you think using that would help.  It's an older model Belkin (probably at least 5 years old).  Should I plug the card in and re-run those diagnostics?

---

