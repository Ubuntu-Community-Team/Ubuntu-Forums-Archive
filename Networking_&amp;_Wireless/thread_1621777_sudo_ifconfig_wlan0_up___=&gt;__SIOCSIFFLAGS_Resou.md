---
title: "sudo ifconfig wlan0 up   =&gt;  SIOCSIFFLAGS: Resource temporarily unavailable"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by bleausardke on 2010-11-14
Hi,

This is my first post here. I'm trying to install wireless usb Hercules HWNUm-300 but I keep getting the same problem. I'm using kubuntu 10.10

sudo ifconfig wlan0 up
 always gives this as a result   SIOCSIFFLAGS: Resource temporarily unavailable

I've tried installing using ndiswrapper and realtek linux driver, but I always get stuck at this part.

Anyone an idea how I can solve this? I've spent hours on google but can't find a solution that works.

Thanks

---

### Post by spiky001 on 2010-11-14
Hi well I have googled as well plus searched forum post cant find any help on google I found some post but were all foriegn so could not read them. Have you just installed Ubuntu?

---

### Post by bleausardke on 2010-11-14
Yes, it's a fresh install. 
The strange thing is installing the realtek linux driver worked before (I still couldn't connect, but the network was visible in network manager), but now, even after reinstalling I keep getting this error.

---

### Post by spiky001 on 2010-11-14
Have you updated drivers via eth0 with usb in machine

---

### Post by bleausardke on 2010-11-15
Yes, but than I read that might be the problem. So I removed the drivers and started again and only plugged the usb in afterwards. Same problem.

---

### Post by bleausardke on 2010-11-15
Downgrading to kubuntu 10.4 has solved the problem. Wireless network is now visible, allthough I still can't connect.

---

### Post by LeMeun on 2010-11-15
hello bleausardke,

Can you post the result of this command typed in the terminal:

sudo iwconfig -a

and also

sudo lsmod

---

### Post by bleausardke on 2010-11-15
Here it is:[B]

sofie@sofiepc:~$ sudo iwconfig -a[/B]
-a        No such device

**sofie@sofiepc:~$ sudo lsmod**
Module                  Size  Used by
ppdev                   5259  0 
ndiswrapper           184867  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_via      27111  1 
snd_hda_intel          22133  1 
snd_hda_codec          74201  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_ice1724            95837  2 
snd_ice17xx_ak4xxx      2547  1 snd_ice1724
snd_ac97_codec        100646  1 snd_ice1724
ac97_bus                1002  1 snd_ac97_codec
snd_ak4xxx_adda         7364  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114              7450  1 snd_ice1724
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  6 snd_hda_intel,snd_hda_codec,snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pt2258              2911  1 snd_ice1724
snd_i2c                 4398  2 snd_ice1724,snd_pt2258
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_ice1724,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
nouveau               467624  2 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63245  0 
ttm                    50071  1 nouveau
asus_atk0110            9017  0 
drm_kms_helper         29297  1 nouveau
snd                    54180  23 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_pt2258,snd_i2c,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3978  0 
drm                   163098  4 nouveau,ttm,drm_kms_helper
agpgart                31788  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
i2c_piix4               8527  0 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               27238  0 
floppy                 53080  0 
ieee1394               81213  1 ohci1394
ahci                   32232  0 
atl1e                  28146  0 
pata_atiixp             3148  3

**sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by LeMeun on 2010-11-15
and if you type ifconfig

then ifconfig -a

---

### Post by bleausardke on 2010-11-15
sofie@sofiepc:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:a2:9d:fc  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:fea2:9dfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:9598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8703 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:9150083 (9.1 MB)  TX bytes:1436504 (1.4 MB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2000 (2.0 KB)  TX bytes:2000 (2.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:d3:82:3c:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2038 (2.0 KB)  TX bytes:5190 (5.1 KB)

---

### Post by LeMeun on 2010-11-15
ok i might be wrong but to me it does not seems like a driver problem so ndiswrapperis doing its job as shown in the lsmod (list the module loaded)

Wlan0 is up already?

sudo ifconfig (without the -a)?

---

### Post by LeMeun on 2010-11-15
if after typing sudo ifconfig your wlan0 is listed it mean that it is a network configuration problem.

if not wlan0 after typing sudo ifconfig it mean that the interface is there but not up (ifconfig -a shows all interfaces even if they are not up) so it is another problem.

are you on a laptop? if yes do you have a button to switch off wireless?

---

### Post by bleausardke on 2010-11-15
No, I'm on a desktop. I can see the network in network manager, I just can't connect to it. I'm not getting an IP address

---

### Post by LeMeun on 2010-11-15
try with iwconfig to set up the essid and the encryption then run dhclient wlan0 to get the ip

---

### Post by bleausardke on 2010-11-15
I've tried setting the essid and do'nt get an error. 
But iwconfig wlan0 shows 

wlan0     IEEE 802.11g  **ESSID:off/any  **
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:24 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 1914
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:08:d3:82:3c:88
Sending on   LPF/wlan0/00:08:d3:82:3c:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by LeMeun on 2010-11-15
yes without the essid assigned the dhclient won't work on wifi interface.

you did a similar command when you tried to set the essid?
sudo iwconfig wlan0 essid MY_WIFI

If yes then network manager is blocking the iwconfig command, you could turn it off just to test if you can login to your access point with iwconfig but you might lost your connection with eth0 as well. Ending up with no internet at all.

Here is what i would try if i was in your shoes:

ps -ax (find the PID # of the network manager ex: 1234)

kill 1234 (kill the process for now, will resume if you reboot)

cd /etc/init.d/
./networking stop

now internet is off! and normally nothing is using your card

test the iwconfig command again
sudo iwconfig wlan0 essid MY_WIFI
then iwconfig to see if your essid has been assigned.

if you want your internet back you can reboot or simply type
sudo ifconfig eth0 up (should be up but just in case)
sudo dhclient eth0

firefox should show you ubuntu forum now if not reboot

---

### Post by bleausardke on 2010-11-15
I've tried, but can't assign essid. It remains off/any.
The strange thing is I know it was set correctly right after I installed the driver with ndiswrapper.
So I don't understand what made this change.

---

### Post by miodziu on 2010-11-15
I have had the same problem.
I have just tried to run
```

nm-applet

```
on console and then my wlan0 connection automatically appeared, with all settings I set earlier (essid, key, ...)
But when I kill nm-applet, connection is lost...

I don't know, why it work, but works. I use wifi to write this post :)

Why do nm-applet help? Anobody knows?

---

### Post by bleausardke on 2010-11-16
I'm on KDE so I don't have nm-applet. But I'll install gnome too and give it a try!

---

### Post by LeMeun on 2010-11-16
network manager-applet I suppose, you should give it a try

---

### Post by bleausardke on 2010-11-16
Hi all,

I reinstalled my system and now chose for ubuntu 10.4.
I got my wifi working with ndiswrapper (without prblems) but it's timing out frequently. 
Maybe the connection isn't strong enough.
I don't know what was wrong under kubuntu, but this has been solved for me now.
Thanks for your help!

---

### Post by miodziu on 2010-11-17
I also resolve my problems... without system reinstall :)

And I knew, what was wrong!
The Network Manager uses option "keep connection configuration encrypted" and this is the reason, why iwconfig doesn't work!

Disable this option and then everything will be working (iwconfig etc...)

---

### Post by A-rap on 2011-02-01
I've been messin with this last 2 days. Those iwconfig and other commands aint havin no effect, because i just cant get wlan0 up.
Can somebody tell me where i could modify "The Network Manager uses option "keep connection configuration encrypted"".... ?
Thank you!

---

### Post by Khufucius on 2011-02-08
I am running into this as well.

I'm running Ubuntu 10.04 server, and using an EnGenius EUB9603H USB wireless device.

I've installed a driver using ndiswrapper, done a "sudo modprobe ndiswrapper," and when I try to bring the wlan0 interface up or down, I get the same "Resource temporarily unavailable" error.

Using "ifconfig -a" I can see the wlan0 device, with information that is similar to what was posted previously.  It sounds like exactly the same issue.

I'd like to echo the previous poster's question -- is there any way to turn off this "keep connection information encrypted" switch?

Thanks.

---

