---
title: "Wireless problems==frustrated in Texas==need help."
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by balebozb on 2012-06-21
I'm using the rt2870sta driver, and I get this message when I tried ifconfig wlan0 up. "SIOCSIFFLAGS: Operation not permitted". When I do the "iwlist wlan0 s" command; it shows this== "Interface doesn't support scanning : Network is down". lsmod shows that the rt2870sta is indeed loaded, too.

Here's the output of "iwconfig wlan0"==
root@ubuntu:/home/barrybozarth# iwconfig wlan0
wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@ubuntu:/home/barrybozarth# 

By the way, I'm running Ubuntu 10.04 and using Wicd. I thought it would help to use that instead of Network-Manager. 

My chipset is as follows==Ralink 148f:5370.

Using the lsusb command gives the following message:

root@ubuntu:/home/barrybozarth# lsusb
Bus 002 Device 002: ID 05ac:0307 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




I've tried everything I know to do, including ndiswrapper, and I still can't get it to connect. Any help would be appreciated.

Thanks yall,
Barry

---

### Post by azmyth on 2012-06-21
I could be wrong but you may need to use another driver

rt2800usb

sudo rmmod rt2870sta
sudo modprobe rt2800usb

I use to use a device on 10.04 that needed that driver rt2870sta and I ended up having to compile the driver from source.

---

### Post by balebozb on 2012-06-21
I just tried what you said, here is what I got.

root@ubuntu:/home/barrybozarth# rmmod rt2870sta
root@ubuntu:/home/barrybozarth# modprobe rt2800usb
root@ubuntu:/home/barrybozarth# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
root@ubuntu:/home/barrybozarth# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

How did you compile your driver?

---

### Post by wildmanne39 on 2012-06-21
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by balebozb on 2012-06-22
Hi Guys, 
Here is the output requested: thanks for your help.

root@ubuntu:/home/barrybozarth# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuntu 2.6.32-41-generic #91-Ubuntu SMP Wed Jun 13 11:44:43 UTC 2012 i686 GNU/Linux
root@ubuntu:/home/barrybozarth# 

root@ubuntu:/home/barrybozarth# lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

root@ubuntu:/home/barrybozarth# lsusb
Bus 002 Device 002: ID 05ac:0307 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@ubuntu:/home/barrybozarth# 

root@ubuntu:/home/barrybozarth# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

root@ubuntu:/home/barrybozarth# 

root@ubuntu:/home/barrybozarth# rfkill list all
root@ubuntu:/home/barrybozarth# 

root@ubuntu:/home/barrybozarth# lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168753  2 vboxnetadp,vboxnetflt
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1631  4 
xt_state                1098  7 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ip6table_filter         2343  1 
ac97_bus                1002  1 snd_ac97_codec
ip6_tables             11227  1 ip6table_filter
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
nf_nat_irc              1124  0 
snd_seq_oss            26722  0 
nf_conntrack_irc        3332  1 nf_nat_irc
snd_seq_midi            4557  0 
nf_nat_ftp              1836  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
tileblit                1999  1 fbcon
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_timer              19130  2 snd_pcm,snd_seq
vga16fb                11385  1 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vgastate                8961  1 vga16fb
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2271  1 
pcmcia                 30784  0 
joydev                  8740  0 
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  290035  1 
ip_tables               9991  1 iptable_filter
yenta_socket           20408  1 
soundcore               6620  1 snd
drm_kms_helper         29329  1 i915
ppdev                   5259  0 
lp                      7028  0 
intel_agp              24375  2 i915
rsrc_nonstatic         10015  1 yenta_socket
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport_pc             25962  1 
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
drm                   163779  3 i915,drm_kms_helper
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_algo_bit            5028  1 i915
agpgart                31724  3 intel_agp,drm
video                  17375  1 i915
parport                32635  3 ppdev,lp,parport_pc
psmouse                63677  0 
shpchp                 28835  0 
output                  1871  1 video
dell_wmi                1793  0 
serio_raw               3978  0 
dcdbas                  5422  0 
ndiswrapper           184709  0 
floppy                 53016  0 
3c59x                  31839  0 
mii                     4381  1 3c59x
usbhid                 36110  0 
hid                    67288  1 usbhid
root@ubuntu:/home/barrybozarth#

---

### Post by balebozb on 2012-06-22
I can run modprobe rt2870sta, and wlan0 will show up in iwconfig and ifconfig, too.

---

### Post by balebozb on 2012-06-22
Hi Guys and Gals,

When I run modprobe rt2870sta; here's the output of the only two things that change.

root@ubuntu:/home/barrybozarth# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@ubuntu:/home/barrybozarth# 

root@ubuntu:/home/barrybozarth# lsmod
Module                  Size  Used by
rt2870sta             461811  0 
binfmt_misc             6587  1 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168753  2 vboxnetadp,vboxnetflt
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1631  4 
xt_state                1098  7 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ip6table_filter         2343  1 
ac97_bus                1002  1 snd_ac97_codec
ip6_tables             11227  1 ip6table_filter
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
nf_nat_irc              1124  0 
snd_seq_oss            26722  0 
nf_conntrack_irc        3332  1 nf_nat_irc
snd_seq_midi            4557  0 
nf_nat_ftp              1836  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
tileblit                1999  1 fbcon
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_timer              19130  2 snd_pcm,snd_seq
vga16fb                11385  1 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vgastate                8961  1 vga16fb
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2271  1 
pcmcia                 30784  0 
joydev                  8740  0 
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  290035  1 
ip_tables               9991  1 iptable_filter
yenta_socket           20408  1 
soundcore               6620  1 snd
drm_kms_helper         29329  1 i915
ppdev                   5259  0 
lp                      7028  0 
intel_agp              24375  2 i915
rsrc_nonstatic         10015  1 yenta_socket
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport_pc             25962  1 
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
drm                   163779  3 i915,drm_kms_helper
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_algo_bit            5028  1 i915
agpgart                31724  3 intel_agp,drm
video                  17375  1 i915
parport                32635  3 ppdev,lp,parport_pc
psmouse                63677  0 
shpchp                 28835  0 
output                  1871  1 video
dell_wmi                1793  0 
serio_raw               3978  0 
dcdbas                  5422  0 
ndiswrapper           184709  0 
floppy                 53016  0 
3c59x                  31839  0 
mii                     4381  1 3c59x
usbhid                 36110  0 
hid                    67288  1 usbhid
root@ubuntu:/home/barrybozarth# 

I appreciate the help, yall.
Barry

---

### Post by wildmanne39 on 2012-06-22
Hi, you are using the wrong driver so you will need to blacklist it and also get rid of ndiswrapper.

Please do:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
``` 
Then follow the directions in this link:
[http://ubuntuforums.org/showthread.php?t=1949996&highlight=5370](http://ubuntuforums.org/showthread.php?t=1949996&highlight=5370)
Thanks

---

### Post by praseodym on 2012-06-22
Hi,

the rt2870sta driver does not contain the device ID (using 10.04 here, too). Add the ID to the driver via:

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2870sta/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rfv rt2870sta
sudo modprobe -v rt2870sta
```
or: try this driver installation:

[http://forum.ubuntuusers.de/topic/c300ru-usb-rt2860-kein-ieee-802-11n/#post-2831641](http://forum.ubuntuusers.de/topic/c300ru-usb-rt2860-kein-ieee-802-11n/#post-2831641)

Adding the ID to rt2870sta does not work anymore with kernel 3.x. With this kernels the ID needs to be added to the rt2800usb module.

---

### Post by praseodym on 2012-06-22
P.S.: Ndiswrapper needs to be uninstalled as described. Check if you created an "Ad-Hoc" network instead of "infrastructure" mode. If so, remove the profile and create a new one.

---

### Post by chili555 on 2012-06-22
> the rt2870sta driver does not contain the device ID I believe the version he compiled does include the device ID as it creates an interface wlan0:> wlan0 RTxx70 Wireless ESSID:""
Mode:Auto Frequency=2.412 GHz
Link Quality=10/100 Signal level:0 dBm Noise level:-143 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
This step is not needed:> echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2870sta/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rfv rt2870sta
sudo modprobe -v rt2870staI believe we are going to find he did not make the needed changes to config.mk before he compiled.

@balebozb--
Did the README mention changes to config.mk? Did you make them? If not, please do so and recompile:```
cd Desktop/RT2870  [COLOR="Red"]<--or wherever you extracted the file[/COLOR]
sudo su
make clean
make
make install
exit
```

---

### Post by balebozb on 2012-06-22
Hi Yall,
Problem solved==I followed Wildmann39's suggestion to install the rt5370sta driver==and now, problem solved.
Thanks yall,
Barry

---

### Post by wildmanne39 on 2012-06-22
Hi, that is great!!! please use thread tools to mark the thread solved.
Enjoy

---

### Post by balebozb on 2012-06-22
Well, Wildmann39; just marked it. Thanks a million!

---

