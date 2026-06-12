---
title: "Problems connecting to the Internet."
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by Trikster on 2011-10-09
hi Guys

I upgraded from Ubuntu 9.10 to Ubuntu 10.04. Since then i am not able to connect to the Internet. I am connected to a DHCP network.

Here is the dump of ifconfig

eth0 Link encap:Ethernet  HWaddr 00:33:1e:bc:de:6e  
       inet6 addr: fe80::224:1dff:fefa:ad3e/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
       TX packets:73 errors:0 dropped:0 overruns:0 carrier:0 
       collisions:0 txqueuelen:1000 
      RX bytes:0 (0.0 B)  TX bytes:11625 (11.6 KB)
       Interrupt:26 Base address:0x2000

 

eth0:avahi Link encap:Ethernet  HWaddr 00:33:1e:bc:de:6e            
       inet addr:169.254.8.55  Bcast:169.254.255.255  Mask:255.255.0.0

       UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
       Interrupt:26 Base address:0x2000
 

lo    Link encap:Local Loopback  
     inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING  MTU:16436  Metric:1
       RX packets:780 errors:0 dropped:0 overruns:0 frame:0 
       TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0 
       RX bytes:62112 (62.1 KB)
       TX bytes:62112 (62.1 KB)

 And when i run sudo pppoeconf i get this message

Sorry, I scanned 2 interfaces, but the Access            
           Concentrator of your provider did not respond. Please     
           check your network and modem cables. Another reason       
           for the scan failure may also be another running pppoe    
           process which controls the modem.  
                      


This is the dump of my Interfaces file.

auto eth0
iface eth0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0:avahi
iface eth0:avahi inet manual

And if i run ifup eth0 command i get this message.

interface eth0 already configured

i have tried everything i know:(.Please help.

---

### Post by praseodym on 2011-10-09
Remove the 2 lines with "avahi" in the /etc/network/interfaces and try

```
sudo pppoeconf eth0
```
directly.

---

### Post by Trikster on 2011-10-09
Hi
Thanks for the reply

I followed these steps but still Internet wont connect.:confused:

---

### Post by praseodym on 2011-10-09
Are you connected to a router containing the Login/PW? If yes, delete anything _except_

```
auto lo
iface lo inet loopback
```
and reboot.

If not (single Modem), add yourself to the group 'dip'

```
sudo adduser $USER dip
```
deactivate the NM in Autostart, login again and try

```
sudo pppoeconf eth0
```

again.

---

### Post by Trikster on 2011-10-09
hi

Im using a dial-up connection that has User-Id and a Password, so i took the first approach.

After making the changes and rebooting and running the 
sudo pppoeconf eth0 command, 
It showed me the Wired network disconnected icon on the desktop, and it shows "Auto eth0" connection in the list of connection on the task bar.
But when I try to connect its not connecting. 

Also in the interfaces file I found these entries

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

I tried changing manual to dhcp and then connecting, but still no use.

Thanks.

---

### Post by praseodym on 2011-10-09
Uninstall the NM and run "pppoeconf" again:

```
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo pppoeconf eth0
```

---

### Post by Trikster on 2011-10-09
hi

I had run all the commands. 
Now I cannot see the network list on the taskbar - it says "Network Manager is not running".

But still i cannot access the Internet :)

Thanks

---

### Post by praseodym on 2011-10-09
Ok, please show:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
ps aux | grep Network
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by Trikster on 2011-10-09
here you go.....



uname -a

Linux ubuntu 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux



lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [11fc:8168] (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169



lsmod

Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71 
snd_pcm_oss            35308  0 
tileblit                1999  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
i915                  288963  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 i915
drm                   163651  4 i915,drm_kms_helper
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63677  0 
intel_agp              24375  2 i915
video                  17375  1 i915
ppdev                   5259  0 
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
lp                      7028  0 
output                  1871  1 video
parport_pc             25962  1 
joydev                  8740  0 
parport                32635  3 ppdev,lp,parport_pc
usbhid                 36110  0 
hid                    67288  1 usbhid
floppy                 53016  0 
r8169                  34140  0 
mii                     4381  1 r8169





ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:33:1e:bc:de:6e  
          inet6 addr: fe80::224:1dff:fefa:ad3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1428 (1.4 KB)
          Interrupt:26 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3088 (3.0 KB)  TX bytes:3088 (3.0 KB)




ps aux | grep Network

username    1570  0.0  0.0   3324   788 pts/0    S+   22:47   0:00 grep --color=auto Network

cat /etc/resolv.conf
# Generated by NetworkManager

cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory

---

### Post by praseodym on 2011-10-09
Try this:

```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
```

---

### Post by Trikster on 2011-10-09
hi
Thanks for the prompt response.

I tried these commands but still cant connect.:(

---

### Post by praseodym on 2011-10-09
Ok:

```
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
dmesg | grep r8
```
please.

---

### Post by Trikster on 2011-10-10
hi
here you go

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:33:1e:bc:de:6e 
          inet6 addr: fe80::224:1dff:fefa:ad3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1428 (1.4 KB)
          Interrupt:26 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)





cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual



cat /etc/resolv.conf

# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.8.4


dmesg | grep r8

[    1.140460] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.140486] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.140536] r8169 0000:02:00.0: setting latency timer to 64
[    1.140610] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[   18.609242] r8169: eth0: link up
[   18.609251] r8169: eth0: link up

---

### Post by praseodym on 2011-10-10
Well, now it gets complicated:

Install these files:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-34-generic_2.6.32-34.77_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-34-generic_2.6.32-34.77_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-34_2.6.32-34.77_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-34_2.6.32-34.77_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.34.40_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.34.40_i386.deb)

Save them on your Desktop and install via:

```
cd Desktop/
sudo dpkg -i linux-*.deb
```
Then add the CD/DVD to your software sources and install the packages **dkms** and **build-essential**
Download the driver directly from here and also save it on your Desktop:

[http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2)

and continue installing:

```
tar xvf r8168-8.025.00.tar.bz2
cd r8168-8.025.00
sudo modprobe -rf r8169
sudo ./autorun.sh
echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by Trikster on 2011-11-14
hi 
Sorry for the very late reply.

What i did is i formatted my entire PC.
Installed win and Ubuntu again.
This time i installed Ubuntu 10.04-LTS.
But even with the new installation im getting the same error.
Is this a bug in ubuntu, i have read the same problems in other forums and no one seems to have a solution for this. 
Please let me know if there are other reliable Linux distros that i can install.

---

### Post by praseodym on 2011-11-14
You are using a single modem? No Router?

---

### Post by Trikster on 2011-11-14
Actually i have neither router nor modem. The ISP provider has a single switch outside somewhere which may be attached to a router, from there he gives different connections to different houses.

---

### Post by praseodym on 2011-11-14
Ask your ISP if a modem is neccessary. The signal itself is analog, the PC needs something digital to work with. Any neighbor you can ask?

---

### Post by Trikster on 2011-11-14
Actually, the same connection work fine with windows XP. I create a dhcp dial up connection in windows. Its only ubuntu that is giving the problem. It used to work in Ubuntu 8

P.S: A while ago i disconnected all network cables and installed ubuntu from winXP for the 2nd time in 2 days.Still no use:(

---

### Post by praseodym on 2011-11-14
Ok,


```
gksudo gedit /etc/network/interfaces
```
Remove anything _but_
```
auto lo
iface lo inet loopback
```
save, close the editor, remove you wired profiles in "wired" and "DSL" (if any) in the network-manager applet, and reboot.

---

### Post by Trikster on 2011-11-14
ok
I did this.
On reboot a new wired connection profile called "Auto Ethernet" got created but im not able to connect to internet.

Contents of interface file does not change. Its still has entry only for "lo"

---

### Post by praseodym on 2011-11-14
Please show now:

```
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
lsmod
```

---

### Post by Trikster on 2011-11-14
here  you go...........

k@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:33:1e:bc:de:6e  
          inet6 addr: fe80::224:1dff:fefa:ad3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2004 (2.0 KB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

k@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
k@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory
k@ubuntu:~$ lsmod
Module                  Size  Used by
pppoe                   8368  0 
pppox                   2074  1 pppoe
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  3 
ppdev                   5259  0 
drm_kms_helper         29329  1 i915
parport_pc             25962  1 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  4 i915,drm_kms_helper
lp                      7028  0 
joydev                  8740  0 
psmouse                63677  0 
serio_raw               3978  0 
intel_agp              24375  2 i915
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
floppy                 53016  0 
r8169                  34140  0 
mii                     4381  1 r8169
usb_storage            39841  1

---

### Post by praseodym on 2011-11-14
Edit your wired connection and add the nameservers ```
8.8.8.8,8.8.4.4
``` in "IPv4 settings". For this choose "Automatic (DHCP), addresses only" and add them in "DNS-servers".

---

### Post by Trikster on 2011-11-14
hi

not working.ARRRRRRRRRRRRRRRRRRRRRRRRRRRRRRR

---

### Post by Trikster on 2011-11-15
ok.
If this is not possible.
I have another internet connection, which i use only for office purpose. 
This one has a modem and in XP when i connect the network cable, i have to login to a ISP provider site and enter my user id and pass.
Atleast tell me how should i configure this.

---

### Post by praseodym on 2011-11-15
In the NetworkManager applet use "DSL" for adding Username/PW

---

