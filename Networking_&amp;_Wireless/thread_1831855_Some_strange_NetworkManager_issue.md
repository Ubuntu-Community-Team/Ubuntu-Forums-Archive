---
title: "Some strange NetworkManager issue"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by Flaminghedgehog on 2011-08-23
I'm currently running Ubuntu 10.04 (lucid)
GNOME: 2.30.2 (Ubuntu 2010-06-25)
Kernel: 2.6.32-31-generic (#61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011)

I don't really want to go into any detailed assumptions without explaining my situation, however I may contradict myself somewhere in this post. Oh well, here goes nothing!

I run networkmanager version 0.8. Ubuntu owner of at least 3 years now, ever since Ubuntu 8.04. Every day I'm online doing whatever, browsing various websites, playing an MMO (Spiral Knights), rarely having a problem until recently. It often happens when playing my MMO, but also happens equally when browsing websites normally on occasion.

Networkmanager seems to work okay for a few seconds and then suddenly my connection drops as if ping packets stopped being sent back and fourth between the site/game server and myself, however I'm still apparently connected to my router.

I often get worried and check to see if I'm still able to connect to my router (via 192.168.1.1 in my browser's address bar). Sometimes I'm able to, Most of the time, however, I'm not able to connect to my router which leads me to believe something is wrong with my Networkmanager.

Sometimes the problem resolves itself, however most of the time (whether it be because I'm inpatient or not) I have to input this command into the terminal if I want connectivity again.
```
$ sudo rfkill unblock wifi && sudo /etc/init.d/networking restart && sudo /etc/init.d/network-manager restart
```From here, I am able to connect just fine after it runs through it's needed processes. As of recently, it's only been giving me a few seconds of connectivity before it appears I cannot communicate with the router again. It appears my router is still connected to it's ISP, whereas I can't communicate with the router at all; that is, until I repeat this process with the command inputed in the terminal, I'm allocated some more few seconds of connectivity. Again, I am thinking the source lies with this Networkmanager application. It often makes me fusturated that this keeps happening.

Any help is appreciated. I will provide information or clarificationwhere necessary, I just didn't know what information to provide with this first post.

Thanks in advance. :)

---

### Post by praseodym on 2011-08-24
Hello,

did you update the router firmware? You may add the nameservers of your provider directly in the NM (IPv4 settings, chose "Automatically (DHCP), adresses only").

---

### Post by Flaminghedgehog on 2011-08-25
> **praseodym said:**
> Hello,

did you update the router firmware? You may add the nameservers of your provider directly in the NM (IPv4 settings, chose "Automatically (DHCP), adresses only").
Yes, I made sure everything with the router works properly and is set up properly.

The other thing I forgot to mention is the fact that I use a WPA2 passphrase to connect to my router. I could be wrong, but has Networkmanager ever had connection problems connecting (and retaining a connection) to the router? I may have read one post of this but I can't seem to properly recall.

---

### Post by praseodym on 2011-08-25
Can you show:

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by Flaminghedgehog on 2011-08-26
Yes, I can! :)

[quote="praseodym"]lspci -nnk | grep -iA2 net[/quote]```
$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
$
```[quote="praseodym"]lsmod[/quote]```
$ lsmod
Module                  Size  Used by
usbhid                 41116  0 
hid                    83600  1 usbhid
binfmt_misc             7960  1 
vboxnetadp              5710  0 
vboxnetflt             19259  0 
vboxdrv              1833616  2 vboxnetadp,vboxnetflt
sit                    10492  0 
tunnel4                 2909  1 sit
vmnet                  46710  13 
ppdev                   6375  0 
parport_pc             29958  0 
vmblock                12995  1 
vsock                  43336  0 
vmci                   60095  1 vsock
vmmon                  82510  0 
joydev                 11104  0 
dm_crypt               13043  0 
snd_hda_codec_nvhdmi     4760  1 
snd_hda_codec_si3054     4236  1 
snd_hda_codec_realtek   279072  1 
iptable_nat             5219  0 
arc4                    1473  2 
nf_nat                 19501  1 iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_conntrack           73966  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  0 
iwlagn                123060  0 
iptable_filter          2791  0 
iwlcore               125179  1 iwlagn
mac80211              238896  2 iwlagn,iwlcore
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22461  2 iptable_nat,ip_tables
uvcvideo               62819  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
cfg80211              148725  3 iwlagn,iwlcore,mac80211
snd_hda_intel          25805  5 
snd_hda_codec          85759  4 snd_hda_codec_nvhdmi,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71251  21 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms               8643  0 
psmouse                64576  0 
serio_raw               4918  0 
memstick               10121  1 jmb38x_ms
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3764  2 iwlcore,sdhci
uinput                  8456  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
nvidia              10832442  40 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
dm_raid45              75532  0 
xor                     4685  1 dm_raid45
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
video                  20623  0 
output                  2503  1 video
r8169                  39714  0 
mii                     5237  1 r8169
vga16fb                12757  1 
vgastate                9857  1 vga16fb
ahci                   37870  3 
intel_agp              29319  0 
$
```[QUOTE="praseodym"]ifconfig -a[/QUOTE]```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:90:f5:8b:76:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0xc000 

ham0      Link encap:Ethernet  HWaddr ae:1a:92:a3:70:4c  
          inet addr:5.28.64.181  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:9099 (9.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10722 (10.7 KB)  TX bytes:10722 (10.7 KB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.251.1  Bcast:192.168.251.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.231.1  Bcast:172.16.231.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:30:86:6e  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:faff:fe30:866e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3490451 (3.4 MB)  TX bytes:541565 (541.5 KB)

$ 

```[QUOTE="praseodym"]iwconfig[/QUOTE]```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"L44I2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:B8:40:27:6A   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ham0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.

vboxnet0  no wireless extensions.

$ 

```[QUOTE="praseodym"]cat /var/lib/NetworkManager/NetworkManager.state[/QUOTE]```
$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
$
```[quote="praseodym"]cat /etc/NetworkManager/nm-system-settings.conf[/Quote]```
$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
flame@system76-pc:~$ cat /etc/NetworkManager/nm-system-settings.conf
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

$ 

```[quote="praseodym"]cat /etc/network/interfaces[/quote]```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

$ 

```[quote="praseodym"]cat /etc/resolv.conf[/quote]```
$ cat /etc/resolv.conf
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.1
nameserver 68.237.161.12
$ 

```Hope this helps.

---

### Post by Flaminghedgehog on 2011-08-28
Update! I've switched over between two new routers in the past two days. Apparently the problem persists if I have a WPA2 (As far as I'm aware) passphrase. Obviously I can't disable it because my guardians are concerned about security issues.

Regardless! It has apparently gotten to the point where I'm able to hold a stable connection for a few minutes before NetworkManager decides to suddenly lose the connection without any fair warning. Moments later, after NetworkManager lost my connection, I see the "Disconnect" dialouge appears on my screen.

Mentioned in the first post, repeatedly doing ```
$ sudo rfkill unblock wifi && sudo /etc/init.d/networking restart && sudo /etc/init.d/network-manager restart
``` in the terminal seems to no longer work and I have to manually restart my computer if I want to resume any internet connectivity.

Any help is appreciated. Please help! I've been suffering with this issue for at least half a year now!

---

### Post by praseodym on 2011-08-28
The driver iwlagn can be updated by the backports-modules, the firmware by **[B]linux-firmware**[/B], respectively:

```
sudo apt-get install --reinstall linux-backports-modules-wireless-lucid-generic linux-firmware
```
You should update yor system _before_, because kernel 2.6.32-33 is up-to-date

---

### Post by Flaminghedgehog on 2011-09-05
```
$ sudo apt-get install --reinstall linux-backports-modules-wireless-lucid-generic linux-firmware
[sudo] password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-wireless-lucid-generic
$
```

This is what happened to me when I tried to input your command into the terminal.

I updated to 11.04 recently, two days ago in fact, and to find this not working is baffling to me.

Any alternatives/command line changes I can do?

---

### Post by praseodym on 2011-09-05
Please show:

```
uname -a
```

---

### Post by Flaminghedgehog on 2011-09-06
Can do!
```
$ uname -a
Linux system76-pc 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
$ 
```

---

### Post by praseodym on 2011-09-06
Ok, for Natty the package name is

```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
and reboot.

---

### Post by Flaminghedgehog on 2011-09-18
While I apologize for the late reply, I'd like to take the time to say: Thanks! That seemed to do exactly what I needed! However these problems have started appearing yet again as of recently (two days ago). A temporary solution to a temporary problem. :P

Not too long ago, VMware was giving me a load of issues. Mainly with trying to run the application itself/updating/installing/uninstalling (Yeah, I couldn't uninstall this no matter how much I tried). Honestly speaking however, I was getting sick and tired of not being able to uninstall it, so I forcefully removed it.
```
sudo rm -r /usr/bin/vmware /etc/vmware /usr/lib/vmware /usr/lib64/vmware /usr/share/man/man1/vmware.1.gz /usr/share/man/man4/vmware.4.gz
```Prior to this, I was not able to use my VMWare Workstation setup, nor update or install/remove it for the matter. I still am able to install VMWare Workstation with a message coming from the installer saying it ['cannot continue if there are other Virtual Machines running']("http://img600.imageshack.us/img600/4198/screenshotvmwareworksta.png").

This is, however, another issue. If you wish to help me address this, many thanks will be given.

I cannot help but think that me removing what was in these VMware directories/files has inadvertendly damaged my network manager setup.

I could be wrong, however.

---

