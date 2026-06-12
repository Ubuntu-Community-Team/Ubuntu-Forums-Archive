---
title: "cant figure out how to install driver for Broadcom BCM43XG..."
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by superfrogman94 on 2009-12-06
i need help trying to figure this out... i got as far as getting the driver to appear (which it previously didnt) and it failed either to no internet (i dont have access to wired at the computer using ubuntu) or it just stops and dose not activate and sometimes it even freezes the computer. i can download stuff in windows and use them in ubuntu. so if someone could help me id greatly appreciate it!


P.S  some of the guides i found to fix this either didnt work... or required wired internet( which i do not have access on the computer from my location. i am writing this on windows vista (which i hate)


please help a new ubuntu user ( i really wanna use ubuntu but i cant use wireless internet!!!)

---

### Post by peakpc on 2009-12-06
Hi, I finally figured out the secret to making my broadcom work.
You have to install (enable) the hardware drivers running from the Live CD then (of course you can't reboot to make it stick, but if you install to the HD now it will be available after install and you can enable and reboot it get it working. At least this worked for me. (after one bad install and trying all the options in other posts.) p.s. put the live cd back in after reboot so it can be used as a software source.

---

### Post by superfrogman94 on 2009-12-06
i might have tried it already but ill try it again to be sure thanks for the help. brb soon

---

### Post by superfrogman94 on 2009-12-06
well i got it to work...sorta

i have to keep reinstalling the package and keep trying to activate the driver to make it connect.. however my computer becomes unstable and completly freezes(have to turn it off to get pc back...)  even if i restart i still have to do all of this, sometimes it dosnt freeze but most of he time it does.... help!!!!!!!!!!!!!!

---

### Post by techiewannabe on 2009-12-06
I fought with this same problem. I solved it by installing the firmware. I can't remember the exact site that I got the firmware from, but still have the package on my desktop. (Do you want me to try to send it to you.) The title of the file I downloaded was: b43-firmware_1.1-Ocafuego1_all.deb. There are probably several sites where you can find the firmware.

Good luck.

Tecchiewannabe

---

### Post by superfrogman94 on 2009-12-06
yes please send it to [email]spongebob94@optonline.net[/email]

anyway i hope it works!

---

### Post by techiewannabe on 2009-12-06
Superfrogman94:

I took another look and was able to locate the website from which I downloaded the firmware. It is at: [http://ubuntu.cafuego.net/dists/jaunty-cafuego/all/](http://ubuntu.cafuego.net/dists/jaunty-cafuego/all/).

Good luck.

Techiewannabe

---

### Post by superfrogman94 on 2009-12-06
thanks! well i try it soon (i gtg somewhere now)

---

### Post by superfrogman94 on 2009-12-06
nope... installing the firmware didnt seem to do anything... i still have the same problems as before.

help!!!!!!!!

---

### Post by techiewannabe on 2009-12-06
Sorry that the firmware didn't work. I'm very much a "newbie," so I don't feel confident offering any other advice.

Techiewannabe

---

### Post by superfrogman94 on 2009-12-06
well thanks anyway (maybe i didnt intsall it right...) well theres gotta be SOME WAY right?

anyone else? help

---

### Post by lexfati on 2009-12-06
Let's find some information about your wireless card to start.  You will need to open a terminal.  (From the menu at the top, select Applications > Accessories > Terminal.

When you have a terminal open, type in this command to find your wireless card information.

```
lspci | grep Wireless
```

Please post the output of that command.

---

### Post by superfrogman94 on 2009-12-06
> **lexfati said:**
> Let's find some information about your wireless card to start.  You will need to open a terminal.  (From the menu at the top, select Applications > Accessories > Terminal.

When you have a terminal open, type in this command to find your wireless card information.

```
lspci | grep Wireless
```

Please post the output of that command.
nothing happens for lspci | grep Wireless but lspci gives me...

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) 
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02) 
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1) 
04:03.0 Network controller: Broadcom Corporation BCM43XG (rev 01) 
04:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

any ideas? please

---

### Post by superfrogman94 on 2009-12-06
please can someone help? iv been trying to figure this out forever!

---

### Post by northd_tech on 2009-12-06
Hi.

It might help if you posted the results of entering the following commands into a terminal:

```
lsmod

lsusb

lshw -C network

ifconfig

iwconfig

netstat -v

```I haven't ever worked with the Broadcom B43XG, but I've been working with Broadcom 4321 and/or 4328 for over a year with good success.

That interface might have something in common with these Broadcom "cousins":

[B][B]Using the b43 driver instead of the Broadcom STA wireless driver "wl"
[http://ubuntuforums.org/showthread.php?t=1071298](http://ubuntuforums.org/showthread.php?t=1071298)

[/B][B]How to install native broadcom drivers for  BCM4311, BCM4312, BCM4321, and BCM4322  
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

[/B][/B][B][B]8.04 BCM4318 wireless issues 
[http://ubuntuforums.org/showthread.php?t=1339560](http://ubuntuforums.org/showthread.php?t=1339560)

[/B][/B]Edit:  You probably want to read this older thread specifically about the BCM43XG:

[http://ubuntuforums.org/showthread.php?t=234748](http://ubuntuforums.org/showthread.php?t=234748)
[B] 

[/B]

---

### Post by lexfati on 2009-12-07
Superfrogman94,

I've been trying to find about your card online,

> 04:03.0 Network controller: Broadcom Corporation BCM43XG (rev 01)

and according to [this person's experience]("http://www.goodjobsucking.com/"), [Broadcom's proprietary driver]("http://www.broadcom.com/support/802.11/linux_sta.php") works for your card.

I've don't have experience with your particular card, but I have built this driver to work for a bcm4328 card.  It does involve some command line work.

The second link in northd_tech's last post (#15) explains how to install the driver, but you may have to install module-assistant or at least build-essential before you can perform the 'make' commands.  These packages get the headers you need and configure the system so that you can build drivers.  If you can temporarily use a wired connection to get onto the Internet the command to get the package is:

```
sudo apt-get install module-assistant
```

followed by this to prepare your system for building:

```
sudo m-a prepare
```

Of course, you will need to make sure to download the correct driver.  If you are not sure if you have a 32 or 64 bit system you can check with uname -m

```
uname -m
```

If you see "x86_64" you need the 64 bit version.

I know this gets a bit technical, especially if your just starting.  I would recommend reading both the Broadcom README and the second link from post #15 as a starting point.

---

### Post by superfrogman94 on 2009-12-07
my results

          lshw -C network 



     ```
WARNING: you should run this program as super-user.  
   *-network                
        description: Ethernet interface  
        product: 82566DC Gigabit Network Connection  
        vendor: Intel Corporation  
        physical id: 19  
        bus info: pci@0000:00:19.0  
        logical name: eth0  
        version: 02  
        serial: 00:19:d1:1a:bc:29  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.1-0 latency=0 multicast=yes  
        resources: irq:28 memory:dffe0000-dfffffff memory:dffdb000-dffdbfff ioport:ecc0(size=32)  
   *-network UNCLAIMED  
        description: Network controller  
        product: BCM43XG  
        vendor: Broadcom Corporation  
        physical id: 3  
        bus info: pci@0000:04:03.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: latency=64  
        resources: memory:dceec000-dceeffff  

```lsmod

    ```
Module                  Size  Used by  
 binfmt_misc             8356  1  
 ppdev                   6688  0  
 snd_usb_audio          84224  1  
 snd_usb_lib            16284  1 snd_usb_audio  
 saa7115                13872  1  
 snd_hda_codec_idt      59844  1  
 snd_hda_intel          26920  2  
 snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep               7200  2 snd_usb_audio,snd_hda_codec  
 em28xx                 80968  0  
 ir_common              48512  1 em28xx  
 v4l2_common            17500  2 saa7115,em28xx  
 videodev               36736  3 saa7115,em28xx,v4l2_common  
 v4l1_compat            14496  1 videodev  
 snd_pcm_oss            37920  0  
 snd_mixer_oss          16028  1 snd_pcm_oss  
 snd_pcm                75296  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 videobuf_vmalloc        6496  1 em28xx  
 videobuf_core          17952  2 em28xx,videobuf_vmalloc  
 tveeprom               11872  1 em28xx  
 snd_seq_dummy           2656  0  
 snd_seq_oss            28576  0  
 snd_seq_midi            6432  0  
 joydev                 10272  0  
 iptable_filter          3100  0  
 ip_tables              11692  1 iptable_filter  
 x_tables               16544  1 ip_tables  
 snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi  
 snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              22276  2 snd_pcm,snd_seq  
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 dell_wmi                2564  0  
 dcdbas                  7292  0  
 psmouse                56500  0  
 serio_raw               5280  0  
 snd                    59204  19 snd_usb_audio,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore               7264  1 snd  
 snd_page_alloc          9156  2 snd_hda_intel,snd_pcm  
 lp                      8964  0  
 parport                35340  2 ppdev,lp  
 hid_logitech            8412  0  
 ff_memless              5188  1 hid_logitech  
 usbhid                 38208  1 hid_logitech  
 usb_storage            52576  0  
 e1000e                122124  0  
 intel_agp              27484  0  
 agpgart                34988  1 intel_agp  
 
```ifconfig

          
  
      ```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:1a:bc:29   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Memory:dffe0000-e0000000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  

```iwconfig :(
```

    <!--         @page { margin: 0.79in }         P { margin-bottom: 0.08in }     -->      lo        no wireless extensions.  
 

 eth0      no wireless extensions.

```netstat -v (very long!)

```
           c-73c-0-7686aca196eb4  
 unix  3      [ ]         STREAM     CONNECTED     11451     
 unix  3      [ ]         STREAM     CONNECTED     11450    /tmp/orbit-joseph/linc-77b-0-31d7da90a1d22  
 unix  3      [ ]         STREAM     CONNECTED     11448     
 unix  3      [ ]         STREAM     CONNECTED     11449    /tmp/orbit-joseph/linc-776-0-1dca2978a1c57  
 unix  3      [ ]         STREAM     CONNECTED     11447     
 unix  2      [ ]         STREAM     CONNECTED     11441     
 unix  3      [ ]         STREAM     CONNECTED     11440    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11439     
 unix  3      [ ]         STREAM     CONNECTED     11434    @/dbus-vfs-daemon/socket-3gIi6FqL  
 unix  3      [ ]         STREAM     CONNECTED     11429     
 unix  3      [ ]         STREAM     CONNECTED     11435    @/dbus-vfs-daemon/socket-O2o9VYTf  
 unix  3      [ ]         STREAM     CONNECTED     11428     
 unix  3      [ ]         STREAM     CONNECTED     11425    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     11424     
 unix  3      [ ]         STREAM     CONNECTED     11421    @/tmp/.ICE-unix/1731  
 unix  3      [ ]         STREAM     CONNECTED     11420     
 unix  3      [ ]         STREAM     CONNECTED     11419    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11418     
 unix  3      [ ]         STREAM     CONNECTED     11417    /tmp/orbit-joseph/linc-742-0-23a2d03756c0f  
 unix  3      [ ]         STREAM     CONNECTED     11416     
 unix  3      [ ]         STREAM     CONNECTED     11413    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     11412     
 unix  3      [ ]         STREAM     CONNECTED     11408    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11407     
 unix  3      [ ]         STREAM     CONNECTED     11406    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     11405     
 unix  3      [ ]         STREAM     CONNECTED     11401    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     11400     
 unix  3      [ ]         STREAM     CONNECTED     11398    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11397     
 unix  3      [ ]         STREAM     CONNECTED     11396    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11395     
 unix  3      [ ]         STREAM     CONNECTED     11392    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     11391     
 unix  2      [ ]         STREAM     CONNECTED     11385     
 unix  3      [ ]         STREAM     CONNECTED     11380    /tmp/orbit-joseph/linc-77b-0-31d7da90a1d22  
 unix  3      [ ]         STREAM     CONNECTED     11379     
 unix  3      [ ]         STREAM     CONNECTED     11378    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     11377     
 unix  3      [ ]         STREAM     CONNECTED     11376    /tmp/orbit-joseph/linc-776-0-1dca2978a1c57  
 unix  3      [ ]         STREAM     CONNECTED     11375     
 unix  3      [ ]         STREAM     CONNECTED     11374    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     11373     
 unix  3      [ ]         STREAM     CONNECTED     11370    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11369    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11368     
 unix  3      [ ]         STREAM     CONNECTED     11367     
 unix  3      [ ]         STREAM     CONNECTED     11366    /tmp/orbit-joseph/linc-77b-0-31d7da90a1d22  
 unix  3      [ ]         STREAM     CONNECTED     11365     
 unix  3      [ ]         STREAM     CONNECTED     11364    /tmp/orbit-joseph/linc-776-0-1dca2978a1c57  
 unix  3      [ ]         STREAM     CONNECTED     11363     
 unix  3      [ ]         STREAM     CONNECTED     11362    /tmp/orbit-joseph/linc-73f-0-1c1c94b3d8725  
 unix  3      [ ]         STREAM     CONNECTED     11359     
 unix  3      [ ]         STREAM     CONNECTED     11356    /tmp/orbit-joseph/linc-73f-0-1c1c94b3d8725  
 unix  3      [ ]         STREAM     CONNECTED     11355     
 unix  3      [ ]         STREAM     CONNECTED     11348    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     11347     
 unix  3      [ ]         STREAM     CONNECTED     11346    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     11345     
 unix  3      [ ]         STREAM     CONNECTED     11264    @/dbus-vfs-daemon/socket-hGVuFgeh  
 unix  3      [ ]         STREAM     CONNECTED     11263     
 unix  3      [ ]         STREAM     CONNECTED     11265    @/dbus-vfs-daemon/socket-CpmfrCXZ  
 unix  3      [ ]         STREAM     CONNECTED     11262     
 unix  3      [ ]         STREAM     CONNECTED     11259    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11258     
 unix  3      [ ]         STREAM     CONNECTED     11253    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11252     
 unix  3      [ ]         STREAM     CONNECTED     11245    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11244     
 unix  3      [ ]         STREAM     CONNECTED     11242    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     11241     
 unix  3      [ ]         STREAM     CONNECTED     11236    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11235     
 unix  3      [ ]         STREAM     CONNECTED     11227    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11226     
 unix  3      [ ]         STREAM     CONNECTED     11218    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11217     
 unix  3      [ ]         STREAM     CONNECTED     11208    /tmp/orbit-joseph/linc-73c-0-7686aca196eb4  
 unix  3      [ ]         STREAM     CONNECTED     11207     
 unix  3      [ ]         STREAM     CONNECTED     11202    @/dbus-vfs-daemon/socket-xRJbUUbA  
 unix  3      [ ]         STREAM     CONNECTED     11201     
 unix  3      [ ]         STREAM     CONNECTED     11203    @/dbus-vfs-daemon/socket-K98KvS1x  
 unix  3      [ ]         STREAM     CONNECTED     11200     
 unix  3      [ ]         STREAM     CONNECTED     11199    /tmp/orbit-joseph/linc-763-0-25ccd078169cd  
 unix  3      [ ]         STREAM     CONNECTED     11198     
 unix  3      [ ]         STREAM     CONNECTED     11192    @/dbus-vfs-daemon/socket-U9hc7PtG  
 unix  3      [ ]         STREAM     CONNECTED     11191     
 unix  3      [ ]         STREAM     CONNECTED     11193    @/dbus-vfs-daemon/socket-QTXez5VM  
 unix  3      [ ]         STREAM     CONNECTED     11190     
 unix  3      [ ]         STREAM     CONNECTED     11184    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11183     
 unix  3      [ ]         STREAM     CONNECTED     11180    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11179     
 unix  3      [ ]         STREAM     CONNECTED     11160    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11159     
 unix  3      [ ]         STREAM     CONNECTED     11158    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11157     
 unix  3      [ ]         STREAM     CONNECTED     11156    /tmp/orbit-joseph/linc-763-0-25ccd078169cd  
 unix  3      [ ]         STREAM     CONNECTED     11155     
 unix  3      [ ]         STREAM     CONNECTED     11154    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11153     
 unix  3      [ ]         STREAM     CONNECTED     11151    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11150     
 unix  3      [ ]         STREAM     CONNECTED     11149    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     11148     
 unix  3      [ ]         STREAM     CONNECTED     11152    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     11147     
 unix  3      [ ]         STREAM     CONNECTED     11146    /tmp/orbit-joseph/linc-756-0-cadd9eb2079e  
 unix  3      [ ]         STREAM     CONNECTED     11145     
 unix  3      [ ]         STREAM     CONNECTED     11140    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11138     
 unix  3      [ ]         STREAM     CONNECTED     11139    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11137     
 unix  3      [ ]         STREAM     CONNECTED     11142    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     11136     
 unix  3      [ ]         STREAM     CONNECTED     11128    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     11127     
 unix  3      [ ]         STREAM     CONNECTED     11135    /tmp/orbit-joseph/linc-763-0-25ccd078169cd  
 unix  3      [ ]         STREAM     CONNECTED     11123     
 unix  3      [ ]         STREAM     CONNECTED     11122    /tmp/orbit-joseph/linc-73f-0-1c1c94b3d8725  
 unix  3      [ ]         STREAM     CONNECTED     11119     
 unix  3      [ ]         STREAM     CONNECTED     11124    /tmp/orbit-joseph/linc-73d-0-66bdd6c613fac  
 unix  3      [ ]         STREAM     CONNECTED     11114     
 unix  3      [ ]         STREAM     CONNECTED     11111    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11110     
 unix  3      [ ]         STREAM     CONNECTED     11109    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     11107     
 unix  3      [ ]         STREAM     CONNECTED     11108    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     11104     
 unix  3      [ ]         STREAM     CONNECTED     11097    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11096     
 unix  3      [ ]         STREAM     CONNECTED     11094    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     11093     
 unix  3      [ ]         STREAM     CONNECTED     11055    /tmp/orbit-joseph/linc-73c-0-7686aca196eb4  
 unix  3      [ ]         STREAM     CONNECTED     11054     
 unix  3      [ ]         STREAM     CONNECTED     11053    /tmp/orbit-joseph/linc-73f-0-1c1c94b3d8725  
 unix  3      [ ]         STREAM     CONNECTED     11052     
 unix  3      [ ]         STREAM     CONNECTED     11049    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     11048     
 unix  3      [ ]         STREAM     CONNECTED     11045    /tmp/orbit-joseph/linc-74b-0-7dc12891d5706  
 unix  3      [ ]         STREAM     CONNECTED     11044     
 unix  3      [ ]         STREAM     CONNECTED     11041    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     11040     
 unix  3      [ ]         STREAM     CONNECTED     11004    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     11003     
 unix  3      [ ]         STREAM     CONNECTED     11002    /tmp/orbit-joseph/linc-757-0-167b5dfb86fd  
 unix  3      [ ]         STREAM     CONNECTED     11001     
 unix  3      [ ]         STREAM     CONNECTED     10998    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     10997     
 unix  3      [ ]         STREAM     CONNECTED     10992    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10991     
 unix  3      [ ]         STREAM     CONNECTED     10990    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10989     
 unix  3      [ ]         STREAM     CONNECTED     10975    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10974     
 unix  3      [ ]         STREAM     CONNECTED     10942    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10941     
 unix  3      [ ]         STREAM     CONNECTED     10917    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10916     
 unix  3      [ ]         STREAM     CONNECTED     10913    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10912     
 unix  3      [ ]         STREAM     CONNECTED     10879    /tmp/orbit-joseph/linc-74c-0-619d6abc9d40d  
 unix  3      [ ]         STREAM     CONNECTED     10878     
 unix  3      [ ]         STREAM     CONNECTED     10875    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     10874     
 unix  3      [ ]         STREAM     CONNECTED     10870    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10869     
 unix  3      [ ]         STREAM     CONNECTED     10835    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10834     
 unix  3      [ ]         STREAM     CONNECTED     10824    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10823     
 unix  3      [ ]         STREAM     CONNECTED     10822    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10821     
 unix  3      [ ]         STREAM     CONNECTED     10819    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10818     
 unix  3      [ ]         STREAM     CONNECTED     10817    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10816     
 unix  3      [ ]         STREAM     CONNECTED     10815    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10814     
 unix  3      [ ]         STREAM     CONNECTED     10809    /tmp/orbit-joseph/linc-74a-0-58c89e0082e46  
 unix  3      [ ]         STREAM     CONNECTED     10808     
 unix  3      [ ]         STREAM     CONNECTED     10805    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     10804     
 unix  3      [ ]         STREAM     CONNECTED     10788    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10787     
 unix  3      [ ]         STREAM     CONNECTED     10781    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10780     
 unix  3      [ ]         STREAM     CONNECTED     10697    /home/joseph/.pulse/7a3a13e3cd9def70c62007194b16c377-runtime/native  
 unix  3      [ ]         STREAM     CONNECTED     10696     
 unix  3      [ ]         STREAM     CONNECTED     10691    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10690     
 unix  3      [ ]         STREAM     CONNECTED     10688    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10687     
 unix  3      [ ]         STREAM     CONNECTED     10653    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10652     
 unix  3      [ ]         STREAM     CONNECTED     10651    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10650     
 unix  3      [ ]         STREAM     CONNECTED     10647    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10646     
 unix  3      [ ]         STREAM     CONNECTED     10352    @/tmp/.ICE-unix/1731  
 unix  3      [ ]         STREAM     CONNECTED     10351     
 unix  3      [ ]         STREAM     CONNECTED     10349    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10348     
 unix  3      [ ]         STREAM     CONNECTED     10275    @/tmp/.ICE-unix/1731  
 unix  3      [ ]         STREAM     CONNECTED     10274     
 unix  3      [ ]         STREAM     CONNECTED     10273    /tmp/.esd-1000/socket  
 unix  3      [ ]         STREAM     CONNECTED     10272     
 unix  3      [ ]         STREAM     CONNECTED     10270    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10269     
 unix  3      [ ]         STREAM     CONNECTED     10267    /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     10266     
 unix  3      [ ]         STREAM     CONNECTED     10265    /tmp/orbit-joseph/linc-73c-0-7686aca196eb4  
 unix  3      [ ]         STREAM     CONNECTED     10264     
 unix  3      [ ]         STREAM     CONNECTED     10261    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     10260     
 unix  3      [ ]         STREAM     CONNECTED     10258    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10257     
 unix  3      [ ]         STREAM     CONNECTED     10253    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10252     
 unix  3      [ ]         STREAM     CONNECTED     10249    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10248     
 unix  3      [ ]         STREAM     CONNECTED     10218    @/tmp/.ICE-unix/1731  
 unix  3      [ ]         STREAM     CONNECTED     10217     
 unix  3      [ ]         STREAM     CONNECTED     10216    /tmp/orbit-joseph/linc-720-0-113f5c613c07c  
 unix  3      [ ]         STREAM     CONNECTED     10215     
 unix  3      [ ]         STREAM     CONNECTED     10212    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     10211     
 unix  3      [ ]         STREAM     CONNECTED     10207    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10206     
 unix  3      [ ]         STREAM     CONNECTED     10205    @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     10204     
 unix  3      [ ]         STREAM     CONNECTED     10033    /home/joseph/.pulse/7a3a13e3cd9def70c62007194b16c377-runtime/native  
 unix  3      [ ]         STREAM     CONNECTED     10032     
 unix  3      [ ]         STREAM     CONNECTED     10027    /tmp/orbit-joseph/linc-712-0-225cdcc4d4eb1  
 unix  3      [ ]         STREAM     CONNECTED     10026     
 unix  3      [ ]         STREAM     CONNECTED     10023    /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     10022     
 unix  3      [ ]         STREAM     CONNECTED     10017    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10016     
 unix  3      [ ]         STREAM     CONNECTED     10013    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10012     
 unix  2      [ ]         DGRAM                    10006     
 unix  3      [ ]         STREAM     CONNECTED     10005    @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     10004     
 unix  3      [ ]         STREAM     CONNECTED     10003    /tmp/orbit-joseph/linc-70c-0-26e289c4d1652  
 unix  3      [ ]         STREAM     CONNECTED     10002     
 unix  3      [ ]         STREAM     CONNECTED     9999     /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     9998      
 unix  3      [ ]         STREAM     CONNECTED     9995     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9994      
 unix  3      [ ]         STREAM     CONNECTED     9993     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     9992      
 unix  3      [ ]         STREAM     CONNECTED     9987     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     9986      
 unix  3      [ ]         STREAM     CONNECTED     9968     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9967      
 unix  3      [ ]         STREAM     CONNECTED     9942     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9938      
 unix  3      [ ]         STREAM     CONNECTED     9933     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     9932      
 unix  3      [ ]         STREAM     CONNECTED     9934     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9931      
 unix  3      [ ]         STREAM     CONNECTED     9873     /tmp/orbit-joseph/linc-705-0-79ff38668ed73  
 unix  3      [ ]         STREAM     CONNECTED     9872      
 unix  3      [ ]         STREAM     CONNECTED     9869     /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     9868      
 unix  3      [ ]         STREAM     CONNECTED     9862     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9861      
 unix  3      [ ]         STREAM     CONNECTED     9858     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     9857      
 unix  3      [ ]         STREAM     CONNECTED     9787     /tmp/orbit-joseph/linc-6b4-0-6f009d2b823dc  
 unix  3      [ ]         STREAM     CONNECTED     9786      
 unix  3      [ ]         STREAM     CONNECTED     9783     /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     9782      
 unix  3      [ ]         STREAM     CONNECTED     9778     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9777      
 unix  3      [ ]         STREAM     CONNECTED     9716     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     9715      
 unix  3      [ ]         STREAM     CONNECTED     9714     /tmp/orbit-joseph/linc-6c3-0-4610f24547ed1  
 unix  3      [ ]         STREAM     CONNECTED     9713      
 unix  3      [ ]         STREAM     CONNECTED     9710     /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     9709      
 unix  3      [ ]         STREAM     CONNECTED     9670     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9669      
 unix  3      [ ]         STREAM     CONNECTED     9667     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     9666      
 unix  3      [ ]         STREAM     CONNECTED     9654     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     9653      
 unix  3      [ ]         STREAM     CONNECTED     9643     /tmp/orbit-joseph/linc-6f9-0-df6c28b17838  
 unix  3      [ ]         STREAM     CONNECTED     9642      
 unix  3      [ ]         STREAM     CONNECTED     9639     /tmp/orbit-joseph/linc-6fb-0-4de3fedc1080e  
 unix  3      [ ]         STREAM     CONNECTED     9638      
 unix  3      [ ]         STREAM     CONNECTED     9632     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     9631      
 unix  3      [ ]         STREAM     CONNECTED     9422     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9421      
 unix  3      [ ]         STREAM     CONNECTED     9408     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9407      
 unix  3      [ ]         STREAM     CONNECTED     9356     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     9355      
 unix  3      [ ]         STREAM     CONNECTED     9354     @/tmp/dbus-mEmFtXs75M  
 unix  3      [ ]         STREAM     CONNECTED     9353      
 unix  3      [ ]         STREAM     CONNECTED     9345     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     9344      
 unix  3      [ ]         STREAM     CONNECTED     9326     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     9325      
 unix  3      [ ]         STREAM     CONNECTED     9324      
 unix  3      [ ]         STREAM     CONNECTED     9323      
 unix  3      [ ]         STREAM     CONNECTED     9311     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     9310      
 unix  3      [ ]         STREAM     CONNECTED     9112     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     9111      
 unix  2      [ ]         DGRAM                    9099      
 unix  3      [ ]         STREAM     CONNECTED     8944     @/tmp/gdm-session-iUvfZEcv  
 unix  3      [ ]         STREAM     CONNECTED     8942      
 unix  2      [ ]         DGRAM                    7789      
 unix  3      [ ]         STREAM     CONNECTED     7087     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7086      
 unix  3      [ ]         STREAM     CONNECTED     7083     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     7082      
 unix  3      [ ]         STREAM     CONNECTED     7037     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7019      
 unix  2      [ ]         DGRAM                    7016      
 unix  3      [ ]         STREAM     CONNECTED     7005     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     7004      
 unix  3      [ ]         STREAM     CONNECTED     6863     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6862      
 unix  3      [ ]         STREAM     CONNECTED     6809     @/tmp/.X11-unix/X0  
 unix  3      [ ]         STREAM     CONNECTED     6799      
 unix  3      [ ]         STREAM     CONNECTED     6798     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6797      
 unix  3      [ ]         STREAM     CONNECTED     6794     /var/run/acpid.socket  
 unix  3      [ ]         STREAM     CONNECTED     6793      
 unix  2      [ ]         DGRAM                    6764      
 unix  3      [ ]         STREAM     CONNECTED     6762     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6761      
 unix  2      [ ]         DGRAM                    6734      
 unix  3      [ ]         STREAM     CONNECTED     6733     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6732      
 unix  3      [ ]         STREAM     CONNECTED     6197     @/var/run/hald/dbus-4kdR5dmFQB  
 unix  3      [ ]         STREAM     CONNECTED     6196      
 unix  3      [ ]         STREAM     CONNECTED     6193     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6192      
 unix  3      [ ]         STREAM     CONNECTED     6179     @/var/run/hald/dbus-4kdR5dmFQB  
 unix  3      [ ]         STREAM     CONNECTED     6178      
 unix  3      [ ]         STREAM     CONNECTED     6176     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6175      
 unix  3      [ ]         STREAM     CONNECTED     6174     @/var/run/hald/dbus-4kdR5dmFQB  
 unix  3      [ ]         STREAM     CONNECTED     6161      
 unix  3      [ ]         STREAM     CONNECTED     6158     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6157      
 unix  3      [ ]         STREAM     CONNECTED     6160     @/var/run/hald/dbus-4kdR5dmFQB  
 unix  3      [ ]         STREAM     CONNECTED     6144      
 unix  3      [ ]         STREAM     CONNECTED     6142     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6141      
 unix  3      [ ]         STREAM     CONNECTED     6131     /var/run/acpid.socket  
 unix  3      [ ]         STREAM     CONNECTED     6130      
 unix  3      [ ]         STREAM     CONNECTED     6125     @/var/run/hald/dbus-4kdR5dmFQB  
 unix  3      [ ]         STREAM     CONNECTED     6122      
 unix  3      [ ]         STREAM     CONNECTED     6124     @/var/run/hald/dbus-4kdR5dmFQB  
 unix  3      [ ]         STREAM     CONNECTED     6121      
 unix  3      [ ]         STREAM     CONNECTED     6101     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     6100      
 unix  3      [ ]         STREAM     CONNECTED     6088     @/var/run/hald/dbus-4kdR5dmFQB  
 unix  3      [ ]         STREAM     CONNECTED     6087      
 unix  3      [ ]         STREAM     CONNECTED     5744     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5742      
 unix  2      [ ]         DGRAM                    5741      
 unix  2      [ ]         DGRAM                    5550      
 unix  2      [ ]         DGRAM                    5366      
 unix  3      [ ]         STREAM     CONNECTED     5249     @/var/run/hald/dbus-Zu6Wetbqhb  
 unix  3      [ ]         STREAM     CONNECTED     5248      
 unix  2      [ ]         DGRAM                    5184      
 unix  3      [ ]         STREAM     CONNECTED     5176     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5174      
 unix  3      [ ]         STREAM     CONNECTED     5175     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5168      
 unix  3      [ ]         STREAM     CONNECTED     5155     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5154      
 unix  3      [ ]         STREAM     CONNECTED     5151     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5127      
 unix  3      [ ]         STREAM     CONNECTED     5150     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5124      
 unix  3      [ ]         STREAM     CONNECTED     5119      
 unix  3      [ ]         STREAM     CONNECTED     5118      
 unix  2      [ ]         DGRAM                    5116      
 unix  3      [ ]         STREAM     CONNECTED     5084     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5083      
 unix  3      [ ]         STREAM     CONNECTED     5080     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5078      
 unix  2      [ ]         DGRAM                    5075      
 unix  3      [ ]         STREAM     CONNECTED     5054      
 unix  3      [ ]         STREAM     CONNECTED     5053      
 unix  3      [ ]         STREAM     CONNECTED     5055     /var/run/dbus/system_bus_socket  
 unix  3      [ ]         STREAM     CONNECTED     5051      
 unix  3      [ ]         DGRAM                    3171      
 unix  3      [ ]         DGRAM                    3170      
 unix  3      [ ]         STREAM     CONNECTED     3125     @/com/ubuntu/upstart  
 unix  3      [ ]         STREAM     CONNECTED     3122      
 netstat: no support for `AF IPX' on this system.  
 netstat: no support for `AF AX25' on this system.  
 netstat: no support for `AF X25' on this system.  
 netstat: no support for `AF NETROM' on this system.  
 
```

---

### Post by superfrogman94 on 2009-12-07
> **lexfati said:**
> Superfrogman94,

I've been trying to find about your card online,



and according to [this person's experience]("http://www.goodjobsucking.com/"), [Broadcom's proprietary driver]("http://www.broadcom.com/support/802.11/linux_sta.php") works for your card.

I've don't have experience with your particular card, but I have built this driver to work for a bcm4328 card.  It does involve some command line work.

The second link in northd_tech's last post (#15) explains how to install the driver, but you may have to install module-assistant or at least build-essential before you can perform the 'make' commands.  These packages get the headers you need and configure the system so that you can build drivers.  If you can temporarily use a wired connection to get onto the Internet the command to get the package is:

```
sudo apt-get install module-assistant
```followed by this to prepare your system for building:

```
sudo m-a prepare
```Of course, you will need to make sure to download the correct driver.  If you are not sure if you have a 32 or 64 bit system you can check with uname -m

```
uname -m
```If you see "x86_64" you need the 64 bit version.

I know this gets a bit technical, especially if your just starting.  I would recommend reading both the Broadcom README and the second link from post #15 as a starting point.

thanks for the info i will try it when i get access to wired( which is the all the way downstairs in my house .....

---

