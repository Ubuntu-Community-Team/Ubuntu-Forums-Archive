---
title: "wireless on karmic."
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by catlover2 on 2010-03-20
i have a  Atheros AR5001X+ Wireless Network Adapter
and i am hoping that i can use it, if not maybe a 
suggestion of a usb one.

thanks!

---

### Post by coffeeaddict22 on 2010-03-20
Hi,
Shouldn't be a problem.  Have a look at [this page in the wiki.]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")

---

### Post by catlover2 on 2010-03-21
thanks, but i need a little help installing the ath5k thing,
im a complete beginner at Linux.

---

### Post by coffeeaddict22 on 2010-03-21
Go into System/Administration/Hardware Drivers.  It should be in there I think.

---

### Post by catlover2 on 2010-03-21
i get this:

---

### Post by coffeeaddict22 on 2010-03-21
OK.
Can you post back the output of 
```
nm-tool
lshw -C network 
lsmod
```
So we can see what you've got so far?

---

### Post by catlover2 on 2010-03-21
ok, here it is.




```
reed@reeds-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:0F:B0:9A:E0:E3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:11:F5:7E:70:64

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TOBY:            Infra, 00:23:75:09:52:B0, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    The Bees Building: Infra, 00:14:6C:F7:41:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    biatch:          Infra, 00:26:F2:07:16:58, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    beverly1999:     Infra, 00:21:29:66:D6:04, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NETGEAR:         Infra, 00:26:F2:22:FD:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 31
    MinasTirith2:    Infra, 00:17:3F:E2:06:D3, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA2
    NETGEAR:         Infra, 00:22:3F:7E:F6:86, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    NETGEAR:         Infra, 00:1B:2F:4F:9B:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP


reed@reeds-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:9a:e0:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:3000(size=256) memory:e0210800-e02108ff
  *-network:1
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 01
       serial: 00:11:f5:7e:70:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:e0200000-e020ffff
reed@reeds-laptop:~$ lsmod

```

---

### Post by gordintoronto on 2010-03-21
> **catlover2 said:**
> thanks, but i need a little help installing the ath5k thing,
im a complete beginner at Linux.

You don't have to install any software, your wireless should "just work." I think you were referred to some obsolete information.

See this page:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

### Post by catlover2 on 2010-03-21
ok but im not sure were to go to connect to the network.

---

### Post by coffeeaddict22 on 2010-03-21
You're doing fine. 
If you look at the output of nm-tool, there's a lot of info.  You're currently connected on wired; so ignore that bit.

The wireless is working, and can see a series of networks, but you haven't chosen one.  Up on the top panel is an icon that looks like an antenna; left click on it and choose to connect to a network.  Enter the settings you need and you should be away, with two caveats.

1) If you're one of the 3 people in range with your network SSID still set to NETGEAR, you are leaving your network too easy to crack into.  Change it.

2) And if you're on any one of the 4 networks all on a frequency of 2437, you'll probably still have problems.  Change the channel in the router settings.  

Post back if you need more help.

---

### Post by gordintoronto on 2010-03-21
> **catlover2 said:**
> ok but im not sure were to go to connect to the network.

I use a slightly different approach, which has always worked for me.  The Network Manager icon should be near the top-right, near the volume control. Right-click on it, select "edit connections." Select the Wireless tab, click on "add". You will need to know the SSID, encryption type and password. When you're all finished, it should connect.

---

### Post by catlover2 on 2010-03-21
i don't see an antenna on the top bar?

---

### Post by slooksterpsv on 2010-03-21
Do you have the notification bar added? - I'm using a USB Belkin 54g for my desktop it works great.

You may need to update your kernel and disable ath_hal in blacklist. I'll see if I can find the link and post it here.

---

### Post by catlover2 on 2010-03-21
I found that if I click the network icon I get a menu with all the networks in range,
when I try to connect  to mine I put in the password it tells me I need the default keyring
but I have not set it so im not sure what to do...

---

### Post by coffeeaddict22 on 2010-03-22
Try going into System/Preferences/Network Connections and adding it there.  There's a bit of a glitch in the way Network Manager handles priveleges I think.

---

### Post by catlover2 on 2010-03-22
wow, it even wants my "keyring" password there!
to change it in the network connections.

---

### Post by TBABill on 2010-03-22
I believe it's asking you to create a keyring password, not to enter one previously created. Keeps others from going online with your connection. I use it to keep my children off the internet unless I input the password to enable the connection. Since this is your first time using wireless on this installation of Ubuntu it prompts you to create the password...not a big deal, just set one and enjoy your new wireless capability.

---

### Post by catlover2 on 2010-03-22
this is what it says:

                           enter password for default keyring to unlock

     the application "nm-connection-editor" (usr/bin/nm-connection-editor) wants to acces the default 
keyring, but it is locked




i have tried entering a desired password but the box just reappears.

---

### Post by TBABill on 2010-03-22
Did you try your "root" password? Is it possible you set it to the same as your root password during installation?

---

### Post by catlover2 on 2010-03-22
as far as i know i do not have a root password, i did not set it in the installation.

---

### Post by coffeeaddict22 on 2010-03-23
Your keyring password may be your logon, although you may need to do the following first:
Go into System/Admin/Users and Groups; click on the keyring in the centre at the bottom, and then on your name.  On the window hat opens, the third option is User Priveleges.  Make sure that "Connect to Wireless" is checked; then back out and try again.

---

### Post by catlover2 on 2010-03-23
the wireless thing was already checked,
and the keyring was not my username on password...

---

### Post by coffeeaddict22 on 2010-03-23
Hi,
You don't have a "root" password as such.  Ubuntu locks users out of the root account.
You do however have access via sudo.  That's what your login password does.

Suggest you try deleting the gnome keyring- as per [this thread.]("http://ubuntuforums.org/showthread.php?p=4377271")  If you've messed up your keyring, that may be your best option.

---

### Post by catlover2 on 2010-03-23
```
reed@reeds-laptop:~$ rm ~/.gnome2/keyrings/default.keyring
rm: cannot remove `/home/reed/.gnome2/keyrings/default.keyring': No such file or directory
reed@reeds-laptop:~$ gnome-keyring-manager ubuntu-desktop
gnome-keyring-manager: command not found
reed@reeds-laptop:~$ 

```

i tried both of them.

---

### Post by coffeeaddict22 on 2010-03-24
Sorry, wasn't paying attention.

Have you tried opening the menu off the icon, and instead of clicking on the network you want to connect to, choose "Connect to hidden wireless network".  Put the details in there.

---

### Post by catlover2 on 2010-03-24
> **coffeeaddict22 said:**
> Sorry, wasn't paying attention.

Have you tried opening the menu off the icon, and instead of clicking on the network you want to connect to, choose "Connect to hidden wireless network".  Put the details in there.

same difference, it STILL wants my keyring. :confused:

---

### Post by GJCGJC on 2010-03-24
Sorry to intrude here, but I think I may be having a similar problem. My router is also using the frequency 2437, but I can't change it because I bought it years ago, before I knew very much about computers and still used windows, and can't remember the password to access the settings.

Can I ask why that is a bad frequency, and whether there is anything I can do about it other than buy another router?

Thanks

---

### Post by rory526 on 2010-03-24
I think the keyring is set to your original login password. Have you ever changed your password? Try your original one.

---

### Post by catlover2 on 2010-03-25
> **rory526 said:**
> I think the keyring is set to your original login password. Have you ever changed your password? Try your original one.


i already tried that, it is not my password, i have never changed it.

---

### Post by coffeeaddict22 on 2010-03-25
Catlover,
Sorry, just looking back and saw something I missed.  Can you post the output of ```
nm-tool
lshw -C network
lsmod
```again please?  I think you've got a driver problem.

---

### Post by coffeeaddict22 on 2010-03-25
GJCGJC,
What the "2347" was about was the output of ```
sudo iwlist scan
``` Its an awesome Linux tool that spots all the nearby networks.  Catlover's output was 
 ```
 Wireless Access Points 
    TOBY:            Infra, 00:23:75:09:52:B0, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    The Bees Building: Infra, 00:14:6C:F7:41:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    biatch:          Infra, 00:26:F2:07:16:58, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    beverly1999:     Infra, 00:21:29:66:D6:04, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NETGEAR:         Infra, 00:26:F2:22:FD:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 31
    MinasTirith2:    Infra, 00:17:3F:E2:06:D3, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA2
    NETGEAR:         Infra, 00:22:3F:7E:F6:86, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    NETGEAR:         Infra, 00:1B:2F:4F:9B:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP
```

If you look at it, there are 3 that still have the default manufacturer's network SSID, which is kindof like leaving a window open for any nearby burglars.
In addition, there are 4 networks within range that are on the network frequency of 2437 MHz, which makes for a heap of crosstalk, and is guaranteed to cause network problems. That's why having a modem on 2437 was such a bad idea.  There's 11 channels or so, so there's plenty of choice if you want to change.

If you've got an older modem, you should be able to find some way of resetting it; it's often a button you press with a pentip.  That puts it back to the manufacturers settings, and you can then use the default username and pwd for whatever brand of modem you've got(You should be able to find them with Google).

---

### Post by catlover2 on 2010-03-26
```
reed@reeds-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:0F:B0:9A:E0:E3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         200.100.5.53
    Prefix:          30 (255.255.255.252)
    Gateway:         200.100.5.54

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             68.87.69.150


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:11:F5:7E:70:64

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    MinasTirith2:    Infra, 00:17:3F:E2:06:D3, Freq 2422 MHz, Rate 54 Mb/s, Strength 28 WPA2
    NETGEAR:         Infra, 00:26:F2:22:FD:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    NETGEAR:         Infra, 00:1B:2F:4F:9B:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    The Bees Building: Infra, 00:14:6C:F7:41:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    The Caterpillar's Cave: Infra, 00:1D:7E:64:A2:CE, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA


reed@reeds-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:9a:e0:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=200.100.5.53 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:3000(size=256) memory:e0210800-e02108ff
  *-network:1
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 01
       serial: 00:11:f5:7e:70:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:e0200000-e020ffff
reed@reeds-laptop:~$ lsmod

```






mine is the caterpillar's cave by the way.

---

### Post by coffeeaddict22 on 2010-03-26
And ```
lsmod
```?

---

### Post by catlover2 on 2010-03-26
> **coffeeaddict22 said:**
> And ```
lsmod
```?

```
reed@reeds-laptop:~/Documents$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
ecb                     2524  2 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
ath5k                 124772  0 
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
mac80211              181140  1 ath5k
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
led_class               4096  1 ath5k
pcmcia                 36808  0 
ath                     8060  1 ath5k
iptable_filter          3100  0 
snd_rawmidi            22176  1 snd_seq_midi
joydev                 10240  0 
yenta_socket           24296  2 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
cfg80211               93052  3 ath5k,mac80211,ath
rsrc_nonstatic         11644  1 yenta_socket
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
lp                      8964  0 
serio_raw               5280  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32272  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52768  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
i915                  226120  2 
drm                   160032  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
reed@reeds-laptop:~/Documents$ 

```

sorry, didn't know it hadn't done both of them.

---

### Post by coffeeaddict22 on 2010-03-26
No prob.

What's the output of ```
sudo iwconfig
```
Your wireless interface has a logical name of wmaster0.  I've seen differing opinions on this, but the only documentation I've ever found suggested that's the generic "driver" that the kernel uses to interface with any wireless connections.  I've never found a good answer to why it comes up, but it's often a driver issue.

---

### Post by catlover2 on 2010-03-26
> **coffeeaddict22 said:**
> No prob.

What's the output of ```
sudo iwconfig
```Your wireless interface has a logical name of wmaster0.  I've seen differing opinions on this, but the only documentation I've ever found suggested that's the generic "driver" that the kernel uses to interface with any wireless connections.  I've never found a good answer to why it comes up, but it's often a driver issue.


```
reed@reeds-laptop:~/Documents$ sudo iwconfig
[sudo] password for reed: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

reed@reeds-laptop:~/Documents$ 






```




ok...

---

### Post by coffeeaddict22 on 2010-03-26
OK. 
```
ifconfig -a
``` now?

---

### Post by catlover2 on 2010-03-26
> **coffeeaddict22 said:**
> OK. 
```
ifconfig -a
``` now?

```
reed@reeds-laptop:~/Documents$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:9a:e0:e3  
          inet addr:200.100.5.53  Bcast:200.100.5.55  Mask:255.255.255.252
          inet6 addr: fe80::20f:b0ff:fe9a:e0e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234956 errors:17 dropped:194 overruns:14 frame:0
          TX packets:136638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:327537341 (327.5 MB)  TX bytes:10863086 (10.8 MB)
          Interrupt:21 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1240 (1.2 KB)  TX bytes:1240 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:f5:7e:70:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-F5-7E-70-64-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

reed@reeds-laptop:~/Documents$ 

```


any more?

---

### Post by coffeeaddict22 on 2010-03-26
Try ```
ifconfig up wlan0
```

---

### Post by catlover2 on 2010-03-27
> **coffeeaddict22 said:**
> Try ```
ifconfig up wlan0
```


```
reed@reeds-laptop:~/Documents$ ifconfig up wlan0
SIOCSIFADDR: Permission denied
up: ERROR while getting interface flags: No such device
reed@reeds-laptop:~/Documents$ sudo ifconfig up wlan0
[sudo] password for reed: 
SIOCSIFADDR: No such device
up: ERROR while getting interface flags: No such device
reed@reeds-laptop:~/Documents$ 

```

ok...:confused:

---

### Post by coffeeaddict22 on 2010-03-28
Sorry, having trouble finding documentation.  wmaster0 is deprecated in the latest kernel, so it's on it's way out (and nobody's crying).  It's an internal interface the wireless driver uses, but Network Manager goofs up on occasion and uses it directly, which causes problems.  Removing Network Manager and using an alternative (eg wicd) is a reasonable option; if it was me, I'd download the beta of Ubuntu 10.04 and install that, as that's got the latest kernel which should fix your problems.  Other options:

Check you haven't got another card of some sort loaded; that's caused problems for others.

There might be something in the output of ```
cat /var/log/syslog
``` Have a look, and post that back.  The lines with Network Manager in them will be the key.

---

### Post by catlover2 on 2010-03-28
> **coffeeaddict22 said:**
> Sorry, having trouble finding documentation.  wmaster0 is deprecated in the latest kernel, so it's on it's way out (and nobody's crying).  It's an internal interface the wireless driver uses, but Network Manager goofs up on occasion and uses it directly, which causes problems.  Removing Network Manager and using an alternative (eg wicd) is a reasonable option; if it was me, I'd download the beta of Ubuntu 10.04 and install that, as that's got the latest kernel which should fix your problems.  Other options:

Check you haven't got another card of some sort loaded; that's caused problems for others.

There might be something in the output of ```
cat /var/log/syslog
``` Have a look, and post that back.  The lines with Network Manager in them will be the key.


```
03
Mar 28 12:27:01 reeds-laptop kernel: [    1.511254] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): carrier is OFF
Mar 28 12:27:01 reeds-laptop kernel: [    1.511704] agpgart-intel 0000:00:00.0: detected 32636K stolen memory
Mar 28 12:27:01 reeds-laptop kernel: [    1.513201] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too')
Mar 28 12:27:01 reeds-laptop kernel: [    1.542358] usb 1-5: new high speed USB device using ehci_hcd and address 3
Mar 28 12:27:01 reeds-laptop kernel: [    1.568042] [drm] Initialized drm 1.1.0 20060810
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 28 12:27:01 reeds-laptop kernel: [    1.588945] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 28 12:27:01 reeds-laptop kernel: [    1.588955] i915 0000:00:02.0: setting latency timer to 64
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): now managed
Mar 28 12:27:01 reeds-laptop kernel: [    1.599635] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar 28 12:27:01 reeds-laptop kernel: [    1.599674] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Mar 28 12:27:01 reeds-laptop kernel: [    1.707923] 8139too Fast Ethernet driver 0.9.28
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): bringing up device.
Mar 28 12:27:01 reeds-laptop kernel: [    1.708026]   alloc irq_desc for 21 on node -1
Mar 28 12:27:01 reeds-laptop kernel: [    1.708031]   alloc kstat_irqs on node -1
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): preparing device.
Mar 28 12:27:01 reeds-laptop kernel: [    1.708040] 8139too 0000:02:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Mar 28 12:27:01 reeds-laptop kernel: [    1.709142] eth0: RealTek RTL8139 at 0x3000, 00:0f:b0:9a:e0:e3, IRQ 21
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar 28 12:27:01 reeds-laptop kernel: [    1.731436]   alloc irq_desc for 20 on node -1
Mar 28 12:27:01 reeds-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0
Mar 28 12:27:01 reeds-laptop kernel: [    1.731441]   alloc kstat_irqs on node -1
Mar 28 12:27:01 reeds-laptop kernel: [    1.731451] ohci1394 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 28 12:27:01 reeds-laptop kernel: [    1.737317] usb 1-5: configuration #1 chosen from 1 choice
Mar 28 12:27:01 reeds-laptop kernel: [    1.771866] Initializing USB Mass Storage driver...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k')
Mar 28 12:27:01 reeds-laptop kernel: [    1.772538] scsi2 : SCSI emulation for USB Mass Storage devices
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 28 12:27:01 reeds-laptop kernel: [    1.772655] usbcore: registered new interface driver usb-storage
Mar 28 12:27:01 reeds-laptop kernel: [    1.772659] USB Mass Storage support registered.
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): now managed
Mar 28 12:27:01 reeds-laptop kernel: [    2.025552] usb-storage: device found at 3
Mar 28 12:27:01 reeds-laptop kernel: [    2.025555] usb-storage: waiting for device to settle before scanning
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Mar 28 12:27:01 reeds-laptop kernel: [    2.025698] usb 1-3.1: new low speed USB device using ehci_hcd and address 4
Mar 28 12:27:01 reeds-laptop kernel: [    2.027912] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[e0210000-e02107ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): bringing up device.
Mar 28 12:27:01 reeds-laptop kernel: [    2.103350] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:01 reeds-laptop kernel: [    2.689467] [drm] fb0: inteldrmfb frame buffer device
Mar 28 12:27:01 reeds-laptop kernel: [    2.689481] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Mar 28 12:27:01 reeds-laptop kernel: [    2.776434] render error detected, EIR: 0x00000010
Mar 28 12:27:01 reeds-laptop kernel: [    2.776439] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
Mar 28 12:27:01 reeds-laptop kernel: [    2.776453] render error detected, EIR: 0x00000010
Mar 28 12:27:01 reeds-laptop kernel: [    2.786969] [drm] LVDS-8: set mode 1024x768 10
Mar 28 12:27:01 reeds-laptop kernel: [    2.787447] usb 1-3.1: configuration #1 chosen from 1 choice
Mar 28 12:27:01 reeds-laptop kernel: [    2.797632] usbcore: registered new interface driver hiddev
Mar 28 12:27:01 reeds-laptop kernel: [    2.846097] Console: switching to colour frame buffer device 128x48
Mar 28 12:27:01 reeds-laptop kernel: [    2.846640] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input6
Mar 28 12:27:01 reeds-laptop kernel: [    2.846754] generic-usb 0003:0461:4D22.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.7-3.1/input0
Mar 28 12:27:01 reeds-laptop kernel: [    2.846775] usbcore: registered new interface driver usbhid
Mar 28 12:27:01 reeds-laptop kernel: [    2.846778] usbhid: v2.6:USB HID core driver
Mar 28 12:27:01 reeds-laptop kernel: [    2.907514] usb 1-3.2: new full speed USB device using ehci_hcd and address 5
Mar 28 12:27:01 reeds-laptop kernel: [    3.008014] usb 1-3.2: device descriptor read/64, error -32
Mar 28 12:27:01 reeds-laptop kernel: [    3.049349] xor: automatically using best checksumming function: pIII_sse
Mar 28 12:27:01 reeds-laptop kernel: [    3.068008]    pIII_sse  :  3635.000 MB/sec
Mar 28 12:27:01 reeds-laptop kernel: [    3.068012] xor: using function: pIII_sse (3635.000 MB/sec)
Mar 28 12:27:01 reeds-laptop kernel: [    3.072712] device-mapper: dm-raid45: initialized v0.2594b
Mar 28 12:27:01 reeds-laptop kernel: [    3.200150] usb 1-3.2: device descriptor read/64, error -32
Mar 28 12:27:01 reeds-laptop kernel: [    3.316204] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f5865401199]
Mar 28 12:27:01 reeds-laptop kernel: [    3.331441] PM: Starting manual resume from disk
Mar 28 12:27:01 reeds-laptop kernel: [    3.331447] PM: Resume from partition 8:5
Mar 28 12:27:01 reeds-laptop kernel: [    3.331450] PM: Checking hibernation image.
Mar 28 12:27:01 reeds-laptop kernel: [    3.331641] PM: Resume from disk failed.
Mar 28 12:27:01 reeds-laptop kernel: [    3.360091] EXT4-fs (sda1): barriers enabled
Mar 28 12:27:01 reeds-laptop kernel: [    3.381438] kjournald2 starting: pid 376, dev sda1:8, commit interval 5 seconds
Mar 28 12:27:01 reeds-laptop kernel: [    3.381480] EXT4-fs (sda1): delayed allocation enabled
Mar 28 12:27:01 reeds-laptop kernel: [    3.381485] EXT4-fs: file extents enabled
Mar 28 12:27:01 reeds-laptop kernel: [    3.384973] EXT4-fs: mballoc enabled
Mar 28 12:27:01 reeds-laptop kernel: [    3.384993] EXT4-fs (sda1): mounted filesystem with ordered data mode
Mar 28 12:27:01 reeds-laptop kernel: [    3.400080] usb 1-3.2: new full speed USB device using ehci_hcd and address 6
Mar 28 12:27:01 reeds-laptop kernel: [    3.492156] usb 1-3.2: device descriptor read/64, error -32
Mar 28 12:27:01 reeds-laptop kernel: [    3.684165] usb 1-3.2: device descriptor read/64, error -32
Mar 28 12:27:01 reeds-laptop kernel: [    3.876174] usb 1-3.2: new full speed USB device using ehci_hcd and address 7
Mar 28 12:27:01 reeds-laptop kernel: [    4.284031] usb 1-3.2: device not accepting address 7, error -32
Mar 28 12:27:01 reeds-laptop kernel: [    4.346051] type=1505 audit(1269804406.912:2): operation="profile_load" pid=400 name=/usr/share/gdm/guest-session/Xsession
Mar 28 12:27:01 reeds-laptop kernel: [    4.349299] type=1505 audit(1269804406.915:3): operation="profile_load" pid=401 name=/sbin/dhclient3
Mar 28 12:27:01 reeds-laptop kernel: [    4.350200] type=1505 audit(1269804406.915:4): operation="profile_load" pid=401 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 28 12:27:01 reeds-laptop kernel: [    4.350687] type=1505 audit(1269804406.915:5): operation="profile_load" pid=401 name=/usr/lib/connman/scripts/dhclient-script
Mar 28 12:27:01 reeds-laptop kernel: [    4.372192] usb 1-3.2: new full speed USB device using ehci_hcd and address 8
Mar 28 12:27:01 reeds-laptop kernel: [    4.447612] type=1505 audit(1269804407.012:6): operation="profile_load" pid=402 name=/usr/bin/evince
Mar 28 12:27:01 reeds-laptop kernel: [    4.462585] type=1505 audit(1269804407.027:7): operation="profile_load" pid=402 name=/usr/bin/evince-previewer
Mar 28 12:27:01 reeds-laptop kernel: [    4.471389] type=1505 audit(1269804407.035:8): operation="profile_load" pid=402 name=/usr/bin/evince-thumbnailer
Mar 28 12:27:01 reeds-laptop kernel: [    4.507549] type=1505 audit(1269804407.071:9): operation="profile_load" pid=404 name=/usr/lib/cups/backend/cups-pdf
Mar 28 12:27:01 reeds-laptop kernel: [    4.508633] type=1505 audit(1269804407.075:10): operation="profile_load" pid=404 name=/usr/sbin/cupsd
Mar 28 12:27:01 reeds-laptop kernel: [    4.784031] usb 1-3.2: device not accepting address 8, error -32
Mar 28 12:27:01 reeds-laptop kernel: [    4.784216] hub 1-3:1.0: unable to enumerate USB device on port 2
Mar 28 12:27:01 reeds-laptop kernel: [    4.872209] usb 1-3.4: new high speed USB device using ehci_hcd and address 9
Mar 28 12:27:01 reeds-laptop kernel: [    4.980583] usb 1-3.4: configuration #1 chosen from 1 choice
Mar 28 12:27:01 reeds-laptop kernel: [    4.980734] hub 1-3.4:1.0: USB hub found
Mar 28 12:27:01 reeds-laptop kernel: [    4.980821] hub 1-3.4:1.0: 4 ports detected
Mar 28 12:27:01 reeds-laptop kernel: [    5.268231] usb 1-3.4.1: new high speed USB device using ehci_hcd and address 10
Mar 28 12:27:01 reeds-laptop kernel: [    5.381097] usb 1-3.4.1: configuration #1 chosen from 1 choice
Mar 28 12:27:01 reeds-laptop kernel: [    5.381717] scsi3 : SCSI emulation for USB Mass Storage devices
Mar 28 12:27:01 reeds-laptop kernel: [    5.381850] usb-storage: device found at 10
Mar 28 12:27:01 reeds-laptop kernel: [    5.381853] usb-storage: waiting for device to settle before scanning
Mar 28 12:27:01 reeds-laptop kernel: [    5.468235] usb 1-3.4.2: new high speed USB device using ehci_hcd and address 11
Mar 28 12:27:01 reeds-laptop kernel: [    5.579603] usb 1-3.4.2: configuration #1 chosen from 1 choice
Mar 28 12:27:01 reeds-laptop kernel: [    5.579975] scsi4 : SCSI emulation for USB Mass Storage devices
Mar 28 12:27:01 reeds-laptop kernel: [    5.580125] usb-storage: device found at 11
Mar 28 12:27:01 reeds-laptop kernel: [    5.580128] usb-storage: waiting for device to settle before scanning
Mar 28 12:27:01 reeds-laptop kernel: [    7.024213] usb-storage: device scan complete
Mar 28 12:27:01 reeds-laptop kernel: [    7.030930] scsi 2:0:0:0: CD-ROM            SONY     DVD RW DRU-830A  SS25 PQ: 0 ANSI: 0
Mar 28 12:27:01 reeds-laptop kernel: [    7.309298] sr1: scsi3-mmc drive: 62x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 28 12:27:01 reeds-laptop kernel: [    7.309470] sr 2:0:0:0: Attached scsi CD-ROM sr1
Mar 28 12:27:01 reeds-laptop kernel: [    7.309571] sr 2:0:0:0: Attached scsi generic sg2 type 5
Mar 28 12:27:01 reeds-laptop kernel: [   10.380571] usb-storage: device scan complete
Mar 28 12:27:01 reeds-laptop kernel: [   10.381662] scsi 3:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9451 PQ: 0 ANSI: 0
Mar 28 12:27:01 reeds-laptop kernel: [   10.382253] sd 3:0:0:0: Attached scsi generic sg3 type 0
Mar 28 12:27:01 reeds-laptop kernel: [   10.385130] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Mar 28 12:27:01 reeds-laptop kernel: [   10.580288] usb-storage: device scan complete
Mar 28 12:27:01 reeds-laptop kernel: [   10.580913] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch III     035f PQ: 0 ANSI: 4
Mar 28 12:27:01 reeds-laptop kernel: [   10.581437] sd 4:0:0:0: Attached scsi generic sg4 type 0
Mar 28 12:27:01 reeds-laptop kernel: [   10.582268] sd 4:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Mar 28 12:27:01 reeds-laptop kernel: [   10.583262] sd 4:0:0:0: [sdc] Write Protect is off
Mar 28 12:27:01 reeds-laptop kernel: [   10.583266] sd 4:0:0:0: [sdc] Mode Sense: 17 00 00 00
Mar 28 12:27:01 reeds-laptop kernel: [   10.583270] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 28 12:27:01 reeds-laptop kernel: [   10.585011] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 28 12:27:01 reeds-laptop kernel: [   10.585018]  sdc: sdc1
Mar 28 12:27:01 reeds-laptop kernel: [   10.602387] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Mar 28 12:27:01 reeds-laptop kernel: [   10.602392] sd 4:0:0:0: [sdc] Attached SCSI disk
Mar 28 12:27:01 reeds-laptop kernel: [   16.650881] udev: starting version 147
Mar 28 12:27:01 reeds-laptop kernel: [   16.685015] Adding 1389580k swap on /dev/sda5.  Priority:-1 extents:1 across:1389580k 
Mar 28 12:27:01 reeds-laptop kernel: [   16.867096] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 28 12:27:01 reeds-laptop kernel: [   16.869062] lp: driver loaded but no devices found
Mar 28 12:27:01 reeds-laptop kernel: [   16.876465] intel_rng: FWH not detected
Mar 28 12:27:01 reeds-laptop kernel: [   16.922286] EXT4-fs (sda1): internal journal on sda1:8
Mar 28 12:27:01 reeds-laptop kernel: [   17.113851] cfg80211: Calling CRDA to update world regulatory domain
Mar 28 12:27:01 reeds-laptop kernel: [   17.212497] cfg80211: World regulatory domain updated:
Mar 28 12:27:01 reeds-laptop kernel: [   17.212504]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 28 12:27:01 reeds-laptop kernel: [   17.212508]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 12:27:01 reeds-laptop kernel: [   17.212513]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 28 12:27:01 reeds-laptop kernel: [   17.212517]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 28 12:27:01 reeds-laptop kernel: [   17.212521]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 12:27:01 reeds-laptop kernel: [   17.212525]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 12:27:01 reeds-laptop kernel: [   17.264985]   alloc irq_desc for 22 on node -1
Mar 28 12:27:01 reeds-laptop kernel: [   17.264991]   alloc kstat_irqs on node -1
Mar 28 12:27:01 reeds-laptop kernel: [   17.265002] ath5k 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 28 12:27:01 reeds-laptop kernel: [   17.265084] ath5k 0000:02:02.0: registered as 'phy0'
Mar 28 12:27:01 reeds-laptop kernel: [   17.892554] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 28 12:27:01 reeds-laptop kernel: [   18.055085] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 28 12:27:01 reeds-laptop kernel: [   18.055133] Intel ICH 0000:00:1f.5: setting latency timer to 64
Mar 28 12:27:01 reeds-laptop kernel: [   18.117905] ath: EEPROM regdomain: 0x64
Mar 28 12:27:01 reeds-laptop kernel: [   18.117910] ath: EEPROM indicates we should expect a direct regpair map
Mar 28 12:27:01 reeds-laptop kernel: [   18.117916] ath: Country alpha2 being used: 00
Mar 28 12:27:01 reeds-laptop kernel: [   18.117919] ath: Regpair used: 0x64
Mar 28 12:27:01 reeds-laptop kernel: [   18.130737] phy0: Selected rate control algorithm 'minstrel'
Mar 28 12:27:01 reeds-laptop kernel: [   18.131682] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Mar 28 12:27:01 reeds-laptop kernel: [   18.133297] yenta_cardbus 0000:02:04.0: CardBus bridge found [1179:ff00]
Mar 28 12:27:01 reeds-laptop kernel: [   18.133324] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
Mar 28 12:27:01 reeds-laptop kernel: [   18.133328] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
Mar 28 12:27:01 reeds-laptop kernel: [   18.133335] yenta_cardbus 0000:02:04.0: TI: mfunc 0x00111c12, devctl 0x44
Mar 28 12:27:01 reeds-laptop kernel: [   18.276052] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input7
Mar 28 12:27:01 reeds-laptop kernel: [   18.292476] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
Mar 28 12:27:01 reeds-laptop kernel: [   18.364775] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x08b0, PCI irq 16
Mar 28 12:27:01 reeds-laptop kernel: [   18.364782] yenta_cardbus 0000:02:04.0: Socket status: 30000020
Mar 28 12:27:01 reeds-laptop kernel: [   18.364788] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
Mar 28 12:27:01 reeds-laptop kernel: [   18.364800] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
Mar 28 12:27:01 reeds-laptop kernel: [   18.364805] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
Mar 28 12:27:01 reeds-laptop kernel: [   18.365112] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
Mar 28 12:27:01 reeds-laptop kernel: [   18.365117] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
Mar 28 12:27:01 reeds-laptop kernel: [   18.899960] intel8x0_measure_ac97_clock: measured 58037 usecs (2796 samples)
Mar 28 12:27:01 reeds-laptop kernel: [   18.899966] intel8x0: clocking to 48000
Mar 28 12:27:01 reeds-laptop kernel: [   19.021515] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
Mar 28 12:27:01 reeds-laptop kernel: [   19.021576] pci 0000:03:00.0: reg 20 io port: [0xfce0-0xfcff]
Mar 28 12:27:01 reeds-laptop kernel: [   19.021610] pci 0000:03:00.0: supports D1 D2
Mar 28 12:27:01 reeds-laptop kernel: [   19.021614] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 12:27:01 reeds-laptop kernel: [   19.021620] pci 0000:03:00.0: PME# disabled
Mar 28 12:27:01 reeds-laptop kernel: [   19.021659] pci 0000:03:00.2: reg 10 32bit mmio: [0x000000-0x0000ff]
Mar 28 12:27:01 reeds-laptop kernel: [   19.021707] pci 0000:03:00.2: supports D1 D2
Mar 28 12:27:01 reeds-laptop kernel: [   19.021711] pci 0000:03:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 12:27:01 reeds-laptop kernel: [   19.021716] pci 0000:03:00.2: PME# disabled
Mar 28 12:27:01 reeds-laptop kernel: [   19.021753] pci 0000:03:00.3: reg 10 32bit mmio: [0x000000-0x0007ff]
Mar 28 12:27:01 reeds-laptop kernel: [   19.021762] pci 0000:03:00.3: reg 14 io port: [0x00-0x7f]
Mar 28 12:27:01 reeds-laptop kernel: [   19.021808] pci 0000:03:00.3: supports D2
Mar 28 12:27:01 reeds-laptop kernel: [   19.021811] pci 0000:03:00.3: PME# supported from D2 D3hot D3cold
Mar 28 12:27:01 reeds-laptop kernel: [   19.021816] pci 0000:03:00.3: PME# disabled
Mar 28 12:27:01 reeds-laptop kernel: [   19.021856] yenta_cardbus 0000:02:04.0: EnE: chaning testregister 0xC9, 04 -> 04
Mar 28 12:27:01 reeds-laptop kernel: [   19.021993] uhci_hcd 0000:03:00.0: enabling device (0000 -> 0001)
Mar 28 12:27:01 reeds-laptop kernel: [   19.022004] uhci_hcd 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 28 12:27:01 reeds-laptop kernel: [   19.022018] uhci_hcd 0000:03:00.0: UHCI Host Controller
Mar 28 12:27:01 reeds-laptop kernel: [   19.022103] uhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 5
Mar 28 12:27:01 reeds-laptop kernel: [   19.022138] uhci_hcd 0000:03:00.0: irq 16, io base 0x00003880
Mar 28 12:27:01 reeds-laptop kernel: [   19.022274] usb usb5: configuration #1 chosen from 1 choice
Mar 28 12:27:01 reeds-laptop kernel: [   19.022325] hub 5-0:1.0: USB hub found
Mar 28 12:27:01 reeds-laptop kernel: [   19.022336] hub 5-0:1.0: 2 ports detected
Mar 28 12:27:01 reeds-laptop kernel: [   19.022454] ehci_hcd 0000:03:00.2: enabling device (0000 -> 0002)
Mar 28 12:27:01 reeds-laptop kernel: [   19.022462] ehci_hcd 0000:03:00.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
Mar 28 12:27:01 reeds-laptop kernel: [   19.022514] ehci_hcd 0000:03:00.2: EHCI Host Controller
Mar 28 12:27:01 reeds-laptop kernel: [   19.022565] ehci_hcd 0000:03:00.2: new USB bus registered, assigned bus number 6
Mar 28 12:27:01 reeds-laptop kernel: [   19.022615] ehci_hcd 0000:03:00.2: irq 16, io mem 0x28000800
Mar 28 12:27:01 reeds-laptop kernel: [   19.032264] ehci_hcd 0000:03:00.2: USB 2.0 started, EHCI 1.00
Mar 28 12:27:01 reeds-laptop kernel: [   19.032463] usb usb6: configuration #1 chosen from 1 choice
Mar 28 12:27:01 reeds-laptop kernel: [   19.032513] hub 6-0:1.0: USB hub found
Mar 28 12:27:01 reeds-laptop kernel: [   19.032525] hub 6-0:1.0: 2 ports detected
Mar 28 12:27:01 reeds-laptop kernel: [   19.032691] ohci1394 0000:03:00.3: enabling device (0080 -> 0083)
Mar 28 12:27:01 reeds-laptop kernel: [   19.032702] ohci1394 0000:03:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 28 12:27:01 reeds-laptop kernel: [   19.032711] ohci1394 0000:03:00.3: setting latency timer to 64
Mar 28 12:27:01 reeds-laptop kernel: [   19.090094] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[28000000-280007ff]  Max Packet=[1024]  IR/IT contexts=[4/8]
Mar 28 12:27:01 reeds-laptop kernel: [   19.122789] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 28 12:27:01 reeds-laptop kernel: [   19.182232] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Mar 28 12:27:01 reeds-laptop kernel: [   19.183897] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Mar 28 12:27:01 reeds-laptop kernel: [   19.184638] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Mar 28 12:27:01 reeds-laptop kernel: [   19.185237] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Mar 28 12:27:01 reeds-laptop kernel: [   19.186021] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Mar 28 12:27:01 reeds-laptop kernel: [   19.271113] __ratelimit: 6 callbacks suppressed
Mar 28 12:27:01 reeds-laptop kernel: [   19.271119] type=1505 audit(1269804421.835:13): operation="profile_replace" pid=1010 name=/usr/share/gdm/guest-session/Xsession
Mar 28 12:27:01 reeds-laptop kernel: [   19.273381] type=1505 audit(1269804421.839:14): operation="profile_replace" pid=1011 name=/sbin/dhclient3
Mar 28 12:27:01 reeds-laptop kernel: [   19.274287] type=1505 audit(1269804421.839:15): operation="profile_replace" pid=1011 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 28 12:27:01 reeds-laptop kernel: [   19.274779] type=1505 audit(1269804421.839:16): operation="profile_replace" pid=1011 name=/usr/lib/connman/scripts/dhclient-script
Mar 28 12:27:01 reeds-laptop kernel: [   19.301714] type=1505 audit(1269804421.867:17): operation="profile_replace" pid=1012 name=/usr/bin/evince
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): preparing device.
Mar 28 12:27:01 reeds-laptop kernel: [   19.308628] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Mar 28 12:27:01 reeds-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  modem-manager is now available
Mar 28 12:27:01 reeds-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Trying to start the supplicant...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 28 12:27:01 reeds-laptop kernel: [   19.349084] usb 6-2: new high speed USB device using ehci_hcd and address 2
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 28 12:27:01 reeds-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 28 12:27:01 reeds-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 28 12:27:01 reeds-laptop dhclient: All rights reserved.
Mar 28 12:27:01 reeds-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 28 12:27:01 reeds-laptop dhclient: 
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  dhclient started with pid 1029
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 28 12:27:01 reeds-laptop dhclient: Listening on LPF/eth0/00:0f:b0:9a:e0:e3
Mar 28 12:27:01 reeds-laptop kernel: [   19.368838] type=1505 audit(1269804421.935:18): operation="profile_replace" pid=1012 name=/usr/bin/evince-previewer
Mar 28 12:27:01 reeds-laptop dhclient: Sending on   LPF/eth0/00:0f:b0:9a:e0:e3
Mar 28 12:27:01 reeds-laptop kernel: [   19.377763] type=1505 audit(1269804421.943:19): operation="profile_replace" pid=1012 name=/usr/bin/evince-thumbnailer
Mar 28 12:27:01 reeds-laptop dhclient: Sending on   Socket/fallback
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Mar 28 12:27:01 reeds-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Mar 28 12:27:01 reeds-laptop kernel: [   19.413908] type=1505 audit(1269804421.979:20): operation="profile_replace" pid=1040 name=/usr/lib/cups/backend/cups-pdf
Mar 28 12:27:01 reeds-laptop kernel: [   19.414983] type=1505 audit(1269804421.979:21): operation="profile_replace" pid=1040 name=/usr/sbin/cupsd
Mar 28 12:27:02 reeds-laptop kernel: [   19.429484] type=1505 audit(1269804421.995:22): operation="profile_replace" pid=1041 name=/usr/sbin/mysqld-akonadi
Mar 28 12:27:02 reeds-laptop kernel: [   19.511988] usb 6-2: configuration #1 chosen from 1 choice
Mar 28 12:27:02 reeds-laptop kernel: [   19.524157] hub 6-2:1.0: USB hub found
Mar 28 12:27:02 reeds-laptop kernel: [   19.524573] hub 6-2:1.0: 4 ports detected
Mar 28 12:27:02 reeds-laptop gdm-binary[880]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 28 12:27:02 reeds-laptop gdm-simple-slave[1052]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 28 12:27:02 reeds-laptop gdm-binary[880]: WARNING: Unable to find users: no seat-id found
Mar 28 12:27:02 reeds-laptop kernel: [   19.836035] usb 6-2.3: new high speed USB device using ehci_hcd and address 3
Mar 28 12:27:02 reeds-laptop kernel: [   19.964176] usb 6-2.3: configuration #1 chosen from 1 choice
Mar 28 12:27:02 reeds-laptop kernel: [   19.965960] hub 6-2.3:1.0: USB hub found
Mar 28 12:27:02 reeds-laptop kernel: [   19.996938] hub 6-2.3:1.0: 4 ports detected
Mar 28 12:27:02 reeds-laptop wpa_supplicant[1023]: CTRL-EVENT-SCAN-RESULTS 
Mar 28 12:27:02 reeds-laptop kernel: [   20.332045] usb 6-2.3.1: new high speed USB device using ehci_hcd and address 4
Mar 28 12:27:03 reeds-laptop kernel: [   20.433260] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:03 reeds-laptop kernel: [   20.433571] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0011066600000041]
Mar 28 12:27:03 reeds-laptop kernel: [   20.477789] usb 6-2.3.1: configuration #1 chosen from 1 choice
Mar 28 12:27:03 reeds-laptop kernel: [   20.484480] scsi5 : SCSI emulation for USB Mass Storage devices
Mar 28 12:27:03 reeds-laptop kernel: [   20.484641] usb-storage: device found at 4
Mar 28 12:27:03 reeds-laptop kernel: [   20.484643] usb-storage: waiting for device to settle before scanning
Mar 28 12:27:03 reeds-laptop avahi-daemon[879]: Registering new address record for fe80::20f:b0ff:fe9a:e0e3 on eth0.*.
Mar 28 12:27:03 reeds-laptop cron[1198]: (CRON) INFO (pidfile fd = 3)
Mar 28 12:27:03 reeds-laptop init: apport pre-start process (1195) terminated with status 1
Mar 28 12:27:03 reeds-laptop anacron[1228]: Anacron 2.3 started on 2010-03-28
Mar 28 12:27:03 reeds-laptop init: apport post-stop process (1214) terminated with status 1
Mar 28 12:27:03 reeds-laptop cron[1240]: (CRON) STARTUP (fork ok)
Mar 28 12:27:03 reeds-laptop cron[1240]: (CRON) INFO (Running @reboot jobs)
Mar 28 12:27:03 reeds-laptop kernel: [   21.010451] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:04 reeds-laptop anacron[1228]: Will run job `cron.daily' in 5 min.
Mar 28 12:27:04 reeds-laptop anacron[1228]: Will run job `cron.weekly' in 10 min.
Mar 28 12:27:04 reeds-laptop anacron[1228]: Jobs will be executed sequentially
Mar 28 12:27:04 reeds-laptop kernel: [   21.626247] ppdev: user-space parallel port driver
Mar 28 12:27:04 reeds-laptop kernel: [   21.710927] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:05 reeds-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar 28 12:27:05 reeds-laptop kernel: [   22.208159] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4.1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4.1/1-3.4.1:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4.2
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4.2/1-3.4.2:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Failed to get parent
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Failed to get parent
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Failed to get parent
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb4
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Failed to get parent
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 058F:6254
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 0461:4D22
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 058F:6254
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 058F:6254
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4.1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 05E3:0723
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 058F:6254
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4.2
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 0D49:7201
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 058F:6254
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 058F:6254
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-5
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-5
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 054C:02D1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0/usb5
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Failed to get parent
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0/usb5/5-0:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0/usb5
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Failed to get parent
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-0:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2.3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 05E3:0608
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2.3/6-2.3.1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2.3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 05E3:0608
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2.3/6-2.3.1/6-2.3.1:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2.3/6-2.3.1
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 059F:1016
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2.3/6-2.3:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2.3
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 05E3:0608
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2/6-2:1.0
Mar 28 12:27:05 reeds-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.2/usb6/6-2
Mar 28 12:27:05 reeds-laptop udev-configure-printer: Device vendor/product is 05E3:0608
Mar 28 12:27:05 reeds-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Mar 28 12:27:05 reeds-laptop dhclient: DHCPOFFER of 200.100.5.53 from 200.100.5.54
Mar 28 12:27:05 reeds-laptop dhclient: DHCPREQUEST of 200.100.5.53 on eth0 to 255.255.255.255 port 67
Mar 28 12:27:05 reeds-laptop dhclient: DHCPACK of 200.100.5.53 from 200.100.5.54
Mar 28 12:27:05 reeds-laptop dhclient: bound to 200.100.5.53 -- renewal in 39276 seconds.
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>    address 200.100.5.53
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>    prefix 30 (255.255.255.252)
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>    gateway 200.100.5.54
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>    nameserver '208.67.222.222'
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>    nameserver '208.67.220.220'
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>    nameserver '68.87.69.150'
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>    domain name 'hsd1.wa.comcast.net.'
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 28 12:27:05 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 28 12:27:05 reeds-laptop avahi-daemon[879]: Joining mDNS multicast group on interface eth0.IPv4 with address 200.100.5.53.
Mar 28 12:27:05 reeds-laptop avahi-daemon[879]: New relevant interface eth0.IPv4 for mDNS.
Mar 28 12:27:05 reeds-laptop avahi-daemon[879]: Registering new address record for 200.100.5.53 on eth0.IPv4.
Mar 28 12:27:06 reeds-laptop console-kit-daemon[903]: WARNING: Couldn't read /proc/885/environ: Failed to open file '/proc/885/environ': No such file or directory
Mar 28 12:27:06 reeds-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 28 12:27:06 reeds-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 28 12:27:06 reeds-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 28 12:27:06 reeds-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 28 12:27:07 reeds-laptop kernel: [   24.989099] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:08 reeds-laptop acpid: client connected from 1140[107:114]
Mar 28 12:27:08 reeds-laptop kernel: [   25.487016] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:08 reeds-laptop kernel: [   25.867214] usb-storage: device scan complete
Mar 28 12:27:08 reeds-laptop kernel: [   25.910679] scsi 5:0:0:0: Direct-Access     LaCie    Hard Drive            PQ: 0 ANSI: 4
Mar 28 12:27:08 reeds-laptop kernel: [   25.911203] sd 5:0:0:0: Attached scsi generic sg5 type 0
Mar 28 12:27:08 reeds-laptop kernel: [   25.920702] sd 5:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Mar 28 12:27:08 reeds-laptop kernel: [   26.022786] sd 5:0:0:0: [sdd] Write Protect is off
Mar 28 12:27:08 reeds-laptop kernel: [   26.022791] sd 5:0:0:0: [sdd] Mode Sense: 10 00 00 00
Mar 28 12:27:08 reeds-laptop kernel: [   26.022795] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Mar 28 12:27:07 reeds-laptop ntpdate[1604]: step time server 91.189.94.4 offset -0.922780 sec
Mar 28 12:27:07 reeds-laptop kernel: [   26.056484] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Mar 28 12:27:08 reeds-laptop kernel: [   26.056495]  sdd:
Mar 28 12:27:08 reeds-laptop kernel: [   26.144074] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:08 reeds-laptop kernel: [   26.524170]  sdd1
Mar 28 12:27:08 reeds-laptop kernel: [   26.648261] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:08 reeds-laptop kernel: [   27.188347] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Mar 28 12:27:08 reeds-laptop kernel: [   27.188355] sd 5:0:0:0: [sdd] Attached SCSI disk
Mar 28 12:27:09 reeds-laptop kernel: [   27.280027] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:09 reeds-laptop kernel: [   27.781214] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:11 reeds-laptop kernel: [   29.792018] eth0: no IPv6 routers present
Mar 28 12:27:21 reeds-laptop kernel: [   39.388029] __ratelimit: 3 callbacks suppressed
Mar 28 12:27:21 reeds-laptop kernel: [   39.388034] ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar 28 12:27:21 reeds-laptop kernel: [   39.394547] ACPI: EC: GPE storm detected, transactions will use polling mode
Mar 28 12:27:22 reeds-laptop wpa_supplicant[1023]: CTRL-EVENT-SCAN-RESULTS 
Mar 28 12:27:24 reeds-laptop gnome-session[1713]: WARNING: Could not parse desktop file /home/reed/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
Mar 28 12:27:24 reeds-laptop gnome-session[1713]: WARNING: could not read /home/reed/.config/autostart/xfconf-migration-4.6.desktop
Mar 28 12:27:24 reeds-laptop gnome-session[1713]: WARNING: Could not parse desktop file /home/reed/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name'
Mar 28 12:27:24 reeds-laptop gnome-session[1713]: WARNING: could not read /home/reed/.config/autostart/xfce4-settings-helper-autostart.desktop
Mar 28 12:27:25 reeds-laptop kernel: [   43.803284] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:26 reeds-laptop kernel: [   44.309074] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:26 reeds-laptop kernel: [   44.952398] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:27 reeds-laptop kernel: [   45.450908] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:27 reeds-laptop kernel: [   46.098101] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:28 reeds-laptop kernel: [   46.613954] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:28 reeds-laptop pulseaudio[1811]: ratelimit.c: 14 events suppressed
Mar 28 12:27:31 reeds-laptop kernel: [   49.449964] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:31 reeds-laptop kernel: [   49.968012] [drm] DAC-6: set mode 640x480 0
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto The Caterpillar's Cave'
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto The Caterpillar's Cave' has security, but secrets are required.
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 28 12:27:40 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 28 12:27:42 reeds-laptop pulseaudio[1811]: ratelimit.c: 5 events suppressed
Mar 28 12:27:50 reeds-laptop kernel: [   68.875577] UDF-fs: Partition marked readonly; forcing readonly mount
Mar 28 12:27:50 reeds-laptop kernel: [   68.918950] UDF-fs INFO UDF: Mounting volume 'SHADOWS_AND_LIGHT', timestamp 2003/04/29 15:02 (1e5c)
Mar 28 12:27:51 reeds-laptop ntfs-3g[2035]: Version 2009.4.4 external FUSE 27
Mar 28 12:27:51 reeds-laptop ntfs-3g[2035]: Mounted /dev/sdd1 (Read-Write, label "Reeds Pics 2", NTFS 3.1)
Mar 28 12:27:51 reeds-laptop ntfs-3g[2035]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077
Mar 28 12:27:51 reeds-laptop ntfs-3g[2035]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sdd1,blkdev,blksize=4096
Mar 28 12:27:52 reeds-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Mar 28 12:27:52 reeds-laptop wpa_supplicant[1023]: CTRL-EVENT-SCAN-RESULTS 
Mar 28 12:27:57 reeds-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Mar 28 12:28:32 reeds-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Mar 28 12:28:32 reeds-laptop wpa_supplicant[1023]: CTRL-EVENT-SCAN-RESULTS 
Mar 28 12:28:37 reeds-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Mar 28 12:29:32 reeds-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Mar 28 12:29:32 reeds-laptop wpa_supplicant[1023]: CTRL-EVENT-SCAN-RESULTS 
Mar 28 12:29:37 reeds-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Mar 28 12:30:29 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Mar 28 12:30:29 reeds-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (The Caterpillar's Cave)
Mar 28 12:30:29 reeds-laptop NetworkManager: <info>  Marking connection 'Auto The Caterpillar's Cave' invalid.
Mar 28 12:30:29 reeds-laptop NetworkManager: <info>  Activation (wlan0) failed.
Mar 28 12:30:29 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 28 12:30:29 reeds-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Mar 28 12:30:29 reeds-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Wireless connection 1'
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Wireless connection 1' has security, but secrets are required.
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 28 12:30:33 reeds-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 28 12:30:35 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Mar 28 12:30:35 reeds-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (The Caterpillar's Cave)
Mar 28 12:30:35 reeds-laptop NetworkManager: <info>  Marking connection 'Wireless connection 1' invalid.
Mar 28 12:30:35 reeds-laptop NetworkManager: <info>  Activation (wlan0) failed.
Mar 28 12:30:35 reeds-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 28 12:30:35 reeds-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Mar 28 12:30:35 reeds-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 28 12:30:52 reeds-laptop wpa_supplicant[1023]: CTRL-EVENT-SCAN-RESULTS 
Mar 28 12:32:02 reeds-laptop anacron[1228]: Job `cron.daily' started
Mar 28 12:32:02 reeds-laptop anacron[2143]: Updated timestamp for job `cron.daily' to 2010-03-28
reed@reeds-laptop:~$ 

```


here it is!:)

---

### Post by catlover2 on 2010-03-28
> **coffeeaddict22 said:**
> ...if it was me, I'd download the beta of Ubuntu 10.04 and install that, as that's got the latest kernel which should fix your problems.  Other options...


as in here?
[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

---

### Post by coffeeaddict22 on 2010-03-28
Nope, here:[http://www.ubuntu.com/testing/lucid/beta1]("http://www.ubuntu.com/testing/lucid/beta1")

---

### Post by catlover2 on 2010-03-28
> **coffeeaddict22 said:**
> Nope, here:[http://www.ubuntu.com/testing/lucid/beta1](http://www.ubuntu.com/testing/lucid/beta1)


guess what? hare i am on ubuntu 10.04 and it STILL WANTS my keyring!!

im not sure what to do at this point, maybe set my computer on fire?:biggrin:

---

### Post by bcbc on 2010-03-29
> **catlover2 said:**
> guess what? hare i am on ubuntu 10.04 and it STILL WANTS my keyring!!

im not sure what to do at this point, maybe set my computer on fire?:biggrin:

Go into Applications, Accessories, Passwords and encryption keys, and delete the entry that is there. (or delete /home/uname/.gnome2.keyrings/login.keyring).

I then rebooted the system and it had another one created with my login password. At least that's what it appears to do (I deleted my own keyring to test this, and everything appears to work still).

---

### Post by catlover2 on 2010-03-29
> **bcbc said:**
> Go into Applications, Accessories, Passwords and encryption keys, and delete the entry that is there. (or delete /home/uname/.gnome2.keyrings/login.keyring).

I then rebooted the system and it had another one created with my login password. At least that's what it appears to do (I deleted my own keyring to test this, and everything appears to work still).

now, it just wont connect to the network, i gave it the correct password and i tried
the connect to hidden network, and it still did not work...

---

### Post by catlover2 on 2010-03-31
bump

---

### Post by bcbc on 2010-03-31
> **catlover2 said:**
> bump
I don't know much about your wireless - I had my own wireless issues but a different driver.

Try this thread - it's the same wireless that you have: [http://ubuntuforums.org/showpost.php?p=8794256](http://ubuntuforums.org/showpost.php?p=8794256)

---

### Post by catlover2 on 2010-03-31
> **bcbc said:**
> I don't know much about your wireless - I had my own wireless issues but a different driver.

Try this thread - it's the same wireless that you have: [http://ubuntuforums.org/showpost.php?p=8794256](http://ubuntuforums.org/showpost.php?p=8794256)


i did not get to much out of that thread...
but thanks anyway!

---

### Post by coffeeaddict22 on 2010-04-01
Hi,
Now you're on a new install, post the output of 
```
nm-tool
lshw -C network
sudo iwlist scan
```
again.
I'm assuming the problem is that it largely works, you just can't connect becuase it asks for your keyring when you input a passkey?

---

### Post by catlover2 on 2010-04-01
> **coffeeaddict22 said:**
> Hi,
Now you're on a new install, post the output of 
```
nm-tool
lshw -C network
sudo iwlist scan
```again.
I'm assuming the problem is that it largely works, you just can't connect becuase it asks for your keyring when you input a passkey?

```
reed@reeds-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:0F:B0:9A:E0:E3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         100.168.1.2
    Prefix:          30 (255.255.255.252)
    Gateway:         100.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             68.87.69.150


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:11:F5:7E:70:64

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    MinasTirith2:    Infra, 00:17:3F:E2:06:D3, Freq 2422 MHz, Rate 54 Mb/s, Strength 30 WPA2
    The Caterpillar's Cave: Infra, 00:1D:7E:64:A2:CE, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    NETGEAR:         Infra, 00:1B:2F:4F:9B:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    The Bees Building: Infra, 00:14:6C:F7:41:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA


reed@reeds-laptop:~$ 

```
```
reed@reeds-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:9a:e0:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=100.168.1.2 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:3000(size=256) memory:e0210800-e02108ff
  *-network:1
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 01
       serial: 00:11:f5:7e:70:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:e0200000-e020ffff
reed@reeds-laptop:~$ 

```
```
reed@reeds-laptop:~$ sudo iwlist scan
[sudo] password for reed: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:64:A2:CE
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"The Caterpillar's Cave"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000017ae6022f
                    Extra: Last beacon: 112ms ago
                    IE: Unknown: 001654686520436174657270696C6C617227732043617665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:14:6C:F7:41:34
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"The Bees Building"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007bbd68663
                    Extra: Last beacon: 112ms ago
                    IE: Unknown: 00115468652042656573204275696C64696E67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1B:2F:4F:9B:1A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005a8595ac355
                    Extra: Last beacon: 512ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101000002A34000
                    IE: Unknown: DD1A00037F0301000000001B2F4F9B1A021B2F4F9B1A64002C011D08

reed@reeds-laptop:~$ 

```


here you go.

---

### Post by catlover2 on 2010-04-01
> **bcbc said:**
> Go into Applications, Accessories, Passwords and encryption keys, and delete the entry that is there. (or delete /home/uname/.gnome2.keyrings/login.keyring).

I then rebooted the system and it had another one created with my login password. At least that's what it appears to do (I deleted my own keyring to test this, and everything appears to work still).


i did this, so now it doesn't want my keyring...

---

### Post by coffeeaddict22 on 2010-04-03
So it's working?

---

### Post by catlover2 on 2010-04-03
> **coffeeaddict22 said:**
> So it's working?


no, now it just wont connect, i put in all the (correct) info in connection editor,
and the icon spins but it finally just says that its not connected.:confused:

---

### Post by coffeeaddict22 on 2010-04-03
What happens if you try going through the "Connect to Hidden Wireless Network..." option down the bottom of the dialog that pops up when you left click on the network manager applet?

---

### Post by catlover2 on 2010-04-03
> **coffeeaddict22 said:**
> What happens if you try going through the "Connect to Hidden Wireless Network..." option down the bottom of the dialog that pops up when you left click on the network manager applet?
  yes, i have...

---

### Post by coffeeaddict22 on 2010-04-03
You did unplug the wired connection as well, didn't you? ( It won't hop onto the wireless while you're plugged in).

---

### Post by catlover2 on 2010-04-03
> **coffeeaddict22 said:**
> You did unplug the wired connection as well, didn't you? ( It won't hop onto the wireless while you're plugged in).

yes, i will be away till Wednesday so i might not reply for a while.

---

### Post by coffeeaddict22 on 2010-04-03
Both "the Caterpillar's Cave" and The Bees building" are on channel 11.  If you're trying to connect to either, go into the router settings and change the channel.

---

### Post by catlover2 on 2010-04-05
> **coffeeaddict22 said:**
> Both "the Caterpillar's Cave" and The Bees building" are on channel 11.  If you're trying to connect to either, go into the router settings and change the channel.


ok i did that, still no luck.

---

### Post by catlover2 on 2010-04-07
i just got back from my trip and i got the strangest message:
The Caterpillar's Cave
connection established!
so i have no idea why it is suddenly working, (i am posting this from the wireless)
but if it continues to work i will mark this thread as solved.

---

### Post by bigpimpin1 on 2010-04-07
I can't seem to get my wireless to work. Too bad, I enjoy Linux but I'll probably go back to Windows now. I think it's ridiculous there are this many problems with the wireless on Ubuntu 9.10. How can they have not noticed this in the testing or released a decent solution for this. Oh, well.

---

### Post by wfarr_09 on 2010-04-07
> **bigpimpin1 said:**
> I can't seem to get my wireless to work. Too bad, I enjoy Linux but I'll probably go back to Windows now. I think it's ridiculous there are this many problems with the wireless on Ubuntu 9.10. How can they have not noticed this in the testing or released a decent solution for this. Oh, well.

Funny .... I'm Having Problems just getting my UBU910 Install to notice my network.

---

### Post by catlover2 on 2010-04-08
> **catlover2 said:**
> i just got back from my trip and i got the strangest message:
The Caterpillar's Cave
connection established!
so i have no idea why it is suddenly working, (i am posting this from the wireless)
but if it continues to work i will mark this thread as solved.


ok, after further testing now it will not connect to the [COLOR=Red]_Wired_[/COLOR] network!
Im not sure why this is, it does not bother me at the moment, but i would 
like to get it working soon, 
thanks all!

---

### Post by slooksterpsv on 2010-04-09
Just wait till Lucid Lynx comes out, that's what I'm using and it's way way better - still getting used to the window control buttons on the left, but I love it - wireless actually works!

---

### Post by mark bower on 2010-04-09
For the record, on 9.10 I have installed the Netgear PCI WPN311 and it works out of the box.  I use only MAC address security.  I am now in the process of purchasing two more WPN311s - no more ndiswrapper.

And now to struggle with getting Kismet going.

mark

---

### Post by catlover2 on 2010-04-09
> **slooksterpsv said:**
> Just wait till Lucid Lynx comes out, that's what I'm using and it's way way better - still getting used to the window control buttons on the left, but I love it - wireless actually works!

i have the beta of 10.04...

---

### Post by catlover2 on 2010-04-11
bump

---

### Post by catlover2 on 2010-04-11
:confused:                                                                                                                          :confused:
 pretty much what i'm thinking now,
all the sudden, my computer would not connect to the net,
wireless or not.
just now i daisy-chained two routers together and:
auto eth0: connection established! 

so any thoughts on this are greatly appreciated!

-catlover

---

### Post by catlover2 on 2010-04-12
bump

---

### Post by slooksterpsv on 2010-04-13
9 Questions:
1. What kind of computer do you have?
2. What is your BIOS Version?
3. Can you see wireless networks and just not connect?
4. Are you using WPA, WPA2, WEP, etc.?
5. Do you still have a Windows Partition?
6. What's your signal strength?
7. What kind of Wireless router is it (a/b/g/n)?
8. What's the firmware version on the router?
9. Do you have another wireless router you could try it with?

---

### Post by catlover2 on 2010-04-13
> **slooksterpsv said:**
> 9 Questions:
1. What kind of computer do you have?
2. What is your BIOS Version?
3. Can you see wireless networks and just not connect?
4. Are you using WPA, WPA2, WEP, etc.?
5. Do you still have a Windows Partition?
6. What's your signal strength?
7. What kind of Wireless router is it (a/b/g/n)?
8. What's the firmware version on the router?
9. Do you have another wireless router you could try it with?

1.ubuntu 9.10 
2 500GB external HDs
40GB internal hd
 
toshiba satellite
intel celeron
prossesser
1.40GHZ
479MB/RAM
so much hardware...-just ask!

2.don't know, I'm not sure how to find out.
3.yikes! I'm on my wireless right now!
4.wpa
5.no
6. within a foot of my computer.
7.802.11g
8. linksys wrt54g v.4.30.11
9.yes, but i forgot its password and the reset button wont work.

---

### Post by slooksterpsv on 2010-04-14
> **catlover2 said:**
> 1.ubuntu 9.10 
2 500GB external HDs
40GB internal hd
 
toshiba satellite
intel celeron
prossesser
1.40GHZ
479MB/RAM
so much hardware...-just ask!

2.don't know, I'm not sure how to find out.
3.yikes! I'm on my wireless right now!
4.wpa
5.no
6. within a foot of my computer.
7.802.11g
8. linksys wrt54g v.4.30.11
9.yes, but i forgot its password and the reset button wont work.

1. Sorry meant specific - like Toshiba Satelite T8234 whatever
2. Go into BIOS and there should be a version number like 1.4 or 2.11 or that
3. ok
4. Have you tried without WPA
5. Ok bios update is out
6. ** Big issue, if you are as close as 6ft within the distance of your wireless router, you can have connection issues. This is one item that could be the cause of your issue**
7. good
8. Good, check for a firmware update on linksys website
9. Hmmm... yeah without the password or reset button its useless - well can you wire in and get into the config via 192.168.1.1 or that?

Try out #6 seriously

---

### Post by catlover2 on 2010-04-14
> **slooksterpsv said:**
> 1. Sorry meant specific - like Toshiba Satelite T8234 whatever
2. Go into BIOS and there should be a version number like 1.4 or 2.11 or that
3. ok
4. Have you tried without WPA
5. Ok bios update is out
6. ** Big issue, if you are as close as 6ft within the distance of your wireless router, you can have connection issues. This is one item that could be the cause of your issue**
7. good
8. Good, check for a firmware update on linksys website
9. Hmmm... yeah without the password or reset button its useless - well can you wire in and get into the config via 192.168.1.1 or that?

Try out #6 seriously

1.Toshiba satellite m30x-s191td
2.PhoenixBIOS v1.90
4.no but i will.
5.you mean i should update my bios?
6. i tried that, still no luck, it still won't connect.
8.im not sure how to do that, the linksys website seems to tell me how to do it 
on a mac or pc, not linux.
9. i meant i forgot the password at 192.168.1.1
thanks!


edit:
i tried "disable" on the security tab in the setup, same deal, wont connect.

---

### Post by catlover2 on 2010-04-18
bump

---

### Post by slooksterpsv on 2010-04-18
Looks like you'll have to wait until Lucid Lynx comes out - Karmic Koala makes my wireless drop and not reconnect after being connected for 10 min. Lucid Lynx, no issues - just apps crashing where its beta 2 (not to be used as your main OS, use it to test it out on your hardware.

---

### Post by catlover2 on 2010-04-18
> **slooksterpsv said:**
> Looks like you'll have to wait until Lucid Lynx comes out - Karmic Koala makes my wireless drop and not reconnect after being connected for 10 min. Lucid Lynx, no issues - just apps crashing where its beta 2 (not to be used as your main OS, use it to test it out on your hardware.

i do have the beta of lucid lynx installed...

---

### Post by slooksterpsv on 2010-04-19
> **catlover2 said:**
> 1.ubuntu 9.10 
2 500GB external HDs
40GB internal hd
....(continued)

You stated above you have Ubuntu 9.10 which is Karmic Koala, Lucid Lynx is 10.04 (which is in Beta 2 at the moment). So which one? Have you considered looking into Fedora?

---

### Post by catlover2 on 2010-04-19
> **slooksterpsv said:**
> You stated above you have Ubuntu 9.10 which is Karmic Koala, Lucid Lynx is 10.04 (which is in Beta 2 at the moment). So which one? Have you considered looking into Fedora?

oops!
i meant 10.04!
i have a fedora dvd, but i cannot seem to find a way to 
boot without installing:rolleyes:, so any pointers are appreciated.
catlover

---

### Post by slooksterpsv on 2010-04-19
Install it, not really going to hurt anything unless you've already migrated your data over

---

### Post by catlover2 on 2010-04-19
> **slooksterpsv said:**
> Install it, not really going to hurt anything unless you've already migrated your data over

install what?
fedora?
but then that'll delete ubuntu right?

---

### Post by slooksterpsv on 2010-04-21
Yes it will, unless you setup your partitions differently

---

### Post by catlover2 on 2010-04-21
> **slooksterpsv said:**
> Yes it will, unless you setup your partitions differently
just a thought, what about installing fedora to a external HD?

---

### Post by catlover2 on 2010-04-24
bump

---

### Post by catlover2 on 2010-04-26
bump

---

