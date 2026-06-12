---
title: "Cannot connect to internet after 12.04 install"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by stephenconnolly on 2012-11-18
Hello,

I'm having problems connecting to the internet after install Ubuntu 12.04, I can confirm that there is nothing wrong with my router. I have a ethernet cable connect to my Ubuntu machine and all worked fine in the previous release of Ubuntu.

But for some reason with this release, its causing me problems. 

Any help appreciated. 

Regards,
Stephen

---

### Post by wildmanne39 on 2012-11-18
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by stephenconnolly on 2012-11-18
Thanks Wild Man,

I tried this command on my Mac Book Pro, but I'm getting the following error:

-bash: wget: command not found

Regards,
Stephen

---

### Post by wildmanne39 on 2012-11-18
Hi, were you connected to the internet with your wired connection when you ran the command? did you just copy and paste the whole thing for accuracy?
Thanks

---

### Post by stephenconnolly on 2012-11-19
I was connected to internet via WiFi on my Mac Book Pro. Yes, I copied and pasted for accuracy.

Stephen

---

### Post by wildmanne39 on 2012-11-19
Hi, but your wifi connection is not working right? so please use your wired connection and run the command again.
Thanks

---

### Post by stephenconnolly on 2012-11-20
Wild Man, 

No, the Wifi connection is fine. My laptop connects via Wifi with no problems. 

The problem is with my old PC running Ubuntu 12.04 (its an old machine I'm using as a media centre, it has no Wifi capability), I have it connect to my router via an ethernet cable. But it wont connect to the internet.

Please note, there was no problems connecting to the internet with the previous Ubunutu release.

Regards,

---

### Post by wildmanne39 on 2012-11-20
Hi,please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
ifconfig
rfkill list all
lsmod
nm-tool
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by stephenconnolly on 2012-11-21
Wild Man, details below:

```
stephen@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux
```

```
stephen@ubuntu:~$ lspci -nnk | grep -iA2 net
01:09.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
	Subsystem: Dell Device [1028:8127]
	Kernel driver in use: b44
```

```
stephen@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1e68:0045 TrekStor GmbH & Co. KG 
```

```
stephen@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59232 (59.2 KB)  TX bytes:59232 (59.2 KB)


```

```
stephen@ubuntu:~$ rfkill list all
stephen@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
appletalk              29192  0 
dm_crypt               22528  1 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
dcdbas                 14098  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                72919  0 
serio_raw              13027  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
shpchp                 32325  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158438  10 rfcomm,bnep
nls_utf8               12493  0 
ppdev                  12849  0 
cifs                  257941  0 
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414655  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
b44                    31364  0 
ssb                    50691  1 b44
floppy                 60310  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
usb_storage            39646  1 

```

```
stephen@ubuntu:~$ nm-tool

** (process:2601): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

NetworkManager Tool

State: unknown


** (process:2601): WARNING **: error: could not connect to NetworkManager
```

---

### Post by stephenconnolly on 2012-11-26
Wild Man, just wondering if you have any thoughts on this.

Regards,

---

### Post by wildmanne39 on 2012-11-26
Hi, I think I know what is causing this issue please post the output of:
```
cat /etc/network/interfaces
```
if anything else is in the file except
```
auto lo
iface lo inet loopback
```
open the file with gedit and remove the extra content then save the file and reboot.
Thanks

---

### Post by stephenconnolly on 2012-12-03
Thank WIld Man, yes I did have other details in that file. So I've commented them out now and rebooted. 

I can now see the network connections but I still don't have a connection to the internet.

---

### Post by chili555 on 2012-12-05
Wild Man will be away for a few days and I've been asked to help. Please post:```
nm-tool
dmesg | grep -e eth -e b44
sudo ifconfig eth0 up
sudo dhclient eth0
```Any warnings, errors, messages,etc. will be helpful, so please post them.

---

### Post by stephenconnolly on 2012-12-09
Thanks Chili555, details below:


```
stephen@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:0F:1F:59:B1:5E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.21
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


stephen@ubuntu:~$ 

```


```
stephen@ubuntu:~$ dmesg | grep -e eth -e b44
[    0.296195] i2c-core: driver [aat2870] using legacy suspend method
[    0.296198] i2c-core: driver [aat2870] using legacy resume method
[    1.802979] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.880223] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.900999] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:0f:1f:59:b1:5e
[   24.022616] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.819874] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.820878] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.816208] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[   31.816214] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[   31.816433] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.864023] eth0: no IPv6 routers present
stephen@ubuntu:~$ 

```


```
stephen@ubuntu:~$ sudo dhclient eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists
stephen@ubuntu:~$ 

```

---

### Post by stephenconnolly on 2012-12-09
Ok, I have a connection to the internet now. Those commands seemed to work. 

I would love an explanation as to what I was doing wrong.

---

### Post by chili555 on 2012-12-09
I'm a bit mystified as to whether Network Manager is actually running. I suspect we started the ethernet connection the old-fashioned way, with dhclient. Let's do some checking:```
ps aux | grep -i network
cat /var/log/syslog | grep etwork | tail -n20
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
```

---

