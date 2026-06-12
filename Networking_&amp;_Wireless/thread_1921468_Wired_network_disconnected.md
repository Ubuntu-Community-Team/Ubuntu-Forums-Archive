---
title: "Wired network disconnected"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by maxswell on 2012-02-06
I have a FIT2PC, that I cannot enable or use either networking adapters.  I'm runing Ubuntu 10.04 currently, but have also installed 9.10 and Mint 9 with the same issue.  Basically it appears that the OS recognizes the hardware (even what kind it is) but isn't allowing me to use it properly.
[IMG]http://dl.dropbox.com/u/550963/networking2.jpg[/IMG]

Attached is a screenshot of the lshw -C network command.  
[IMG]http://dl.dropbox.com/u/550963/networking.jpg[/IMG]

This indicates what hw I have (which is correct per the fit2pc site).

I'm mostly concerned w/ the LAN port, wireless would be nice but not a necessity.  
I feel like it might be a driver issue, but not even sure how to check what driver it's using or what to replace it with.  

Also attached is a dhclient command.  I've made my account and 'Administrator' account type as well.  no idea where to go from here.
[IMG]http://dl.dropbox.com/u/550963/networking3.jpg[/IMG]

thank you

EDIT: also.. it's NOT the router or cables.  I've tested them and they work fine on other machines.  just not this one.

---

### Post by varunendra on 2012-02-07
Hi maxswell, Welcome to the forums!

Looking at the screenshots and 'guessing' the driver (since the very crucial part of its name is missing in the screenshot), I could suggest you this solution: [http://ubuntuforums.org/showpost.php?p=11477748&postcount=4](http://ubuntuforums.org/showpost.php?p=11477748&postcount=4)

But that is related to unstable/slow or intermittent connection problem. While you are completely disconnected. So, as a comprehensive detail, please post the outputs of the following commands (run in a terminal):
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

Please wrap the outputs in ```
..and..
``` tags by clicking on '#'  at the top of the box (in which you create new posts) to create the  tags, then copy-paste the output in-between those tags. This preserves  the formatting and makes it easily readable.

---

### Post by maxswell on 2012-02-07
I had tried something similar to what you linked to (installing a different driver).  Didn't seem to change anything, but I did it slightly differently (different instructions).  Here is the rest of the information you requested.  Thank you!

:~$ uname -mr
```
2.6.32-33-generic i686
```
:~$ lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Kernel driver in use: rt3090
	Kernel modules: rt3090sta
```
:~$ lsmod
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
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
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                1999  1 fbcon
lirc_igorplugusb        3838  0 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
video                  17375  0 
softcursor              1189  1 bitblit
lirc_dev                8884  1 lirc_igorplugusb
sdhci_pci               5470  0 
soundcore               6620  1 snd
lp                      7028  0 
psmouse                63677  0 
usbhid                 36110  0 
sdhci                  15494  1 sdhci_pci
vga16fb                11385  1 
output                  1871  1 video
rt3090sta             674216  0 
serio_raw               3978  0 
i2c_isch                3311  0 
led_class               2864  1 sdhci
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
hid                    67288  1 usbhid
parport                32635  2 ppdev,lp
usb_storage            39841  1 
r8169                  34140  0 
mii                     4381  1 r8169
pata_sch                1963  2 
```
:~$ ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:01:c0:0b:3f:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:24 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 
```

:~$ cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

:~$ cat /etc/resolv.conf
```
cat: /etc/resolv.conf: No such file or directory
```
:~$ route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

---

### Post by varunendra on 2012-02-07
Firstly, regardless of what method you tries earlier, you still have r8169 loaded:> **maxswell said:**
> ```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Kernel driver in use: **r8169**
```
Accordingly, please try the method I linked to in my previous post, and post back the results of:
```
lspci -nnk |grep -iA2 RTL8111
lsmod | grep r81
```

Secondly,
> **maxswell said:**
> ```
cat: /etc/resolv.conf: No such file or directory
```
That's abnormal (although possible). Make sure you typed the command correctly. If it really doesn't exist, well.. that's a bit odd. Make sure network manager is installed and nm-applet is running (look for nm-applet in "System Monitor").

Also, have you tried the latest 11.10 live cd? Some people have reported that the default r8169 driver is working smooth in the latest kernel (3.0.0.15) included in 11.10. If that's true, you may not need any workarounds at all.

---

### Post by maxswell on 2012-02-07
I've re-installed a few times since my original posting. I had just finished a fresh 10.04 Ubuntu install when you posted.   Yes, I tried 11.10, but it won't run or install (Mint 12 won't either).  There is an error, but it's off the screen so it's unclear exactly what it is.  possibly a hw incompatibility w/ the new kernel or they might require more disk space than I have (8GB SSD).  

here is the output of your commands.


:~/r8168-8.026.00$ lspci -nnk | grep -iA2 RTL8111
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Kernel driver in use: r8168
	Kernel modules: r8168, r8169
```
~/r8168-8.026.00$ lsmod | grep r81
```
r8168                 190815  0 
```
:~/r8168-8.026.00$ cat /etc/resolve.conf
```
cat: /etc/resolve.conf: No such file or directory
```

---

### Post by varunendra on 2012-02-07
Okay, so now we have the expected driver. Do you have DHCP enabled on your network (usually in the router/modem)? Does the command **sudo dhclient** return any errors?

Please post the outputs of:
```
cat /etc/nsswitch.conf
cat /etc/NetworkManager/nm-system-settings.conf
```

Also, Have you tried manually assigning IP to your ethernet interface? That is, either via NM-Applet GUI or-
```
sudo ifconfig eth0 *xx.xx.xx.xx*

```where xx.xx.xx.xx has to be replaced by an IP address relevant to your network. Although it shouldn't be required if DHCP is enabled and working correctly, but trying won't hurt.

---

### Post by maxswell on 2012-02-07
here you go.  Yes, I have DHCP running and it's working fine on 4 other machines.  I did set a static IP via network manager, but cannot ping anything from it.  I CAN ping the loopback.  What is odd is that the green link light never stays solid (as it does on other functioning machines).  It's a constant very slow blink, yet green in color.  

~$ cat /etc/nsswitch.conf
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

:~$ cat /etc/NetworkManager/nm-system-settings.conf
```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

:~$ sudo dhclient
```
[sudo] password for dddd: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFFLAGS: Operation not permitted
SIOCSIFFLAGS: Operation not permitted
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Listening on LPF/eth0/00:01:c0:0b:3f:06
Sending on   LPF/eth0/00:01:c0:0b:3f:06
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by varunendra on 2012-02-07
> **maxswell said:**
> 
```

send_packet: Network is down
```
I'm not 100% sure I'm understanding it correctly, but does **ifconfig** show the eth0 interface as "Up"? Try this:
```
sudo /etc/init.d/networking restart
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
Keep a reasonable (10-20 second) pause between each command. Then run **sudo dhclient** again. Does it make any difference?

The green light status you mentioned - is it bright or dim? There should be two lights in total. One for link and the other for activity. Is the second one completely off?

Please post the outputs of:
```
sudo lshw -C network
dmesg | grep -iE 'r81 | net | eth'
```

---

### Post by maxswell on 2012-02-07
the only light that comes on is the green, and it's NEVER solid.  it blinks very slowly.  the activity light (usually blinking amber) also NEVER comes on.  

interesting.. i'm seeing references of old driver below  r8169.  how is this possible?

:~$ sudo /etc/init.d/networking restart
```
[sudo] password for : 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1370
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:01:c0:0b:3f:06
Sending on   LPF/eth0/00:01:c0:0b:3f:06
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:01:c0:0b:3f:06
Sending on   LPF/eth0/00:01:c0:0b:3f:06
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
```
:~$ sudo ifconfig eth0 down
:~$ sudo ifconfig eth0 up
:~$ sudo dhclient
I```
nternet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFFLAGS: Operation not permitted
SIOCSIFFLAGS: Operation not permitted
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Listening on LPF/eth0/00:01:c0:0b:3f:06
Sending on   LPF/eth0/00:01:c0:0b:3f:06
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
:~$ sudo lshw -C network
 ```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:01:c0:0b:3f:06
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:24 ioport:2000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable) memory:d0120000-d013ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:d0000000-d000ffff
```
~$ dmesg | grep -iE 'r81 | net | eth'
```
[    0.945337] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.947610] eth0: RTL8168d/8111d at 0xf8068000, 00:01:c0:0b:3f:06, XID 081000c0 IRQ 24
[    3.723980] r8169: eth0: link down
[    3.724518] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   85.024244] r8169: eth0: link down
[   85.024757] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  207.693272] r8169: eth0: link down
[  207.694069] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by varunendra on 2012-02-08
> **maxswell said:**
> interesting.. i'm seeing references of old driver below  r8169.  how is this possible?
..
 ```
driver=r8169..
..
```
Hmm.. interesting indeed! If you followed all the steps given in praseodym's post I linked to, that shouldn't have happened. Let's dig some more. Please retry-
```
sudo modprobe -rfv r8169
sudo modprobe -v r8168
```(watch out for any errors)
then check:
```
lspci -nnk | grep -A2 RTL8111
lsmod | grep r81
```Does r8169 appear anywhere? Does it make any difference to the connection?

And post the outputs of-
```
cat /etc/modprobe.d/blacklist.conf | grep r81
cat /etc/modules
```

---

### Post by maxswell on 2012-02-08
yea man.. i'm lost. here are the outputs.


:~$ sudo modprobe -rfv r8169
[sudo] password for : 
```
rmmod /lib/modules/2.6.32-33-generic/kernel/drivers/net/r8169.ko
rmmod /lib/modules/2.6.32-33-generic/kernel/drivers/net/mii.ko
```
:~$ sudo modprobe -v r8168
```
insmod /lib/modules/2.6.32-33-generic/kernel/drivers/net/r8168.ko 
```
:~$ lspci -nnk | grep RTL8111
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
```
:~$ lsmod | grep r81
```
r8168                 190815  0 
:~$ cat /etc/modprobe.d/blacklist.conf | grep r81
blacklist r8169
```
:~$ cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```

---

### Post by varunendra on 2012-02-08
My bad! The lspci command should have been:
```
lspci -nnk | grep -A2 RTL8111
```But nevermind now, although I'm going to correct that in my previous post.

So far, everything seems normal, except why r8169 loaded when it is blacklisted. Just to be extra sure, please do this:
```
echo "r8168" | sudo tee -a /etc/modules
```This will add r8168 as an entry in the /etc/modules file, so that it gets loaded at boot time.

After doing this, restart computer and check which module is loaded again by:
```
lspci -nnk | grep -A2 RTL8111
lsmod | grep r81
```If we can make sure r8169 doesn't get loaded during startup while r8168 is, we may not need any further troubleshooting as the rest of the things should get fixed themselves.

And.. you didn't tell anything about connectivity after modprobing r8168 (yeah, I know you are lost.. so am I. But you are my eyes and ears here.. :)). So, don't worry about post length. Just tell me anything and everything that you think might be important. It shouldn't have required anything more than the first solution post I linked to. Yet now that it is playing with us, we do need to crosscheck every aspect - may be multiple times if required (that is, if you don't get too frustrated..).

---

### Post by maxswell on 2012-02-08
lspci -nnk | grep -A2 RTL8111
this outputs:
```
Kernel driver in use: r8169
Kernel Modules: r8168 r, 8169
```

lsmod | grep rt81
```
this command doesn't return anything.  should it?  
```

sudo modprobe -rfv r8169
returns:
```
rmmod /lib/modules/2.6.32-33-generic/kernel/drivers/net/r8169.ko
rmmod /lib/modules/2.6.32-33-generic/kernel/drivers/net/mii.ko
```

sudo modprobe -v r8168
```
returns nothing
```

I viewed the blacklist.conf file.  r8169 IS in it.  so.. the driver is still being loaded.  
how can i removed those modules?  I imagine modprobe -rfv r8169 should NOT return anything. correct?

---

### Post by varunendra on 2012-02-08
> **maxswell said:**
> [/CODE]lsmod | grep r[COLOR=Red]**t**[/COLOR]81
[CODE]this command doesn't return anything.  should it?
Oops! Sorry, a bloody mistake again!! It should have been r81 in the command.

Anyway, did you add r8168 to the /etc/modules file?

And the modprobe commands 'will' return outputs (just for confirmation) due to -v parameter (verbose). In fact, the odd thing is that **modprobe -v r8168** returned nothing while it should (insmod.... like in your previous post).

So, IF r8169 is in blacklist.conf file (and it IS), and IF r8168 is in the /etc/modules file, then:
r8169 shouldn't load (shouldn't show up in lsmod or lspci) and instead r8168 should get loaded by default (no need to those modprobe commands). But I'm completely stumped at why this is happening!:confused:

So please confirm whether r8168 is added to the /etc/modules file or not, and, AFTER adding it to that file, does r8169 still get loaded.

---

### Post by maxswell on 2012-02-08
so I ran:
cat /etc/modules

the only two uncomment entries were
```
lp
r8168
```

i ran lsmod | grep r81 
```
returned:
r8168        190815 0
```

---

### Post by varunendra on 2012-02-08
That's correct this time. Now try:
```
sudo dhclient eth0
``` to see if it gets any DHCP offers.

---

### Post by maxswell on 2012-02-08
sudo dhclient eth0
```
SIOCSIFADDR: no such device
eth0: ERROR while getting interface flags: No such device
```

if always recieved erros using this command (posted earlier in the thread).  But these messages
are new.

---

### Post by varunendra on 2012-02-08
Great!:(

So what do these say-
```
ifconfig -a
dmesg | grep -i r81
sudo lshw -C network
```

---

### Post by maxswell on 2012-02-08
:~$ ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 
```

:~$ dmesg | grep -i r81
```
[    1.004758] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.004796] r8169 0000:02:00.0: enabling device (0004 -> 0007)
[    1.004815] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.004880] r8169 0000:02:00.0: setting latency timer to 64
[    1.004978] r8169 0000:02:00.0: irq 24 for MSI/MSI-X
[    3.414410] r8169: eth0: link down
[    3.414438] r8169: eth0: link down
[  199.829069] r8169 0000:02:00.0: PCI INT A disabled
```
:~$ sudo lshw -C network
  ```
*-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable) memory:d0120000-d013ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:d0000000-d000ffff
```

---

### Post by varunendra on 2012-02-08
So although r8168 got loaded, it did not pick up the ethernet interface. Now I doubt if it was installed correctly.

But for now (before I retire to bed to recollect myself), please retry-
```
sudo modprobe -rfv r8168
```then reload it
```
sudo modprobe -v r8168
```both commands should return outputs. Afterwards recheck -
```
ifconfig -a
```to see if it lists eth0. If it doesn't, restart the computer and recheck:
```
lspci -nnk | grep -iA2 net
```
to see which driver gets loaded. I suspect it would be r8169 again (:(). If so, we are going to reinstall the r8168 driver - this time downloaded from Realtek's website: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---

### Post by maxswell on 2012-02-08
ok.. in short.. running the two modprobe commands both returned the path to the r8168 driver.

then.. ifconfig -a returned eth0  as a network device.

then I ran sudo dhclient eth0  

what's interesting was that there were no errors.. but it still never received an IP.

just DHCP discover on eth0  a few times.

I can reinstall the driver.  


Also.. just so you know. the link to the driver you left, IS the driver i have installed.  The top one (8.028.00).  Another article led me to that.  I can do it again if you'd like.

---

### Post by varunendra on 2012-02-08
The readme file in that package contains its own method of installation (autorun.sh). Did you install that way or the way suggested in the linked post?


**_PS_:**
Please try manual IP assignment to eth0 now that the desired driver is loaded:
```
sudo ifconfig eth0 xx.xx.xx.xx
```
where xx... is a relevant IP address.

---

### Post by maxswell on 2012-02-08
i think i've done it both ways. but I can't recall which on this particular installation (remember I've reinstalled a handful of times).

which way should i do it?

---

### Post by varunendra on 2012-02-08
I'm not sure. I'd say - don't mix the methods. If the package is the different one, you should try the method its readme file suggests. Just make sure you have headers for the current kernel, dkms and build essential installed before compiling the driver.

I think I would like to go with details tomorrow, as I'm feeling too sleepy to keep up now.

---

