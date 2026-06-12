---
title: "Unable to activate Wireless with laptop"
date: 2006-03-26
forum: Networking &amp; Wireless
---

### Post by Aero-Z on 2006-03-26
Hi all,

I have a Fujitsu-Siemens Amilo A1650g laptop with Atheros integrated wireless. The chipset is AR5005G, madwifi shows AR5212. I have the device in network settings and it says that it's ok. 
The problem is that I'm unable to turn wireless on - the wireless led never starts shining. I put Start wireless when booting from BIOS, but it won't start.
The problem might be that I can turn on the wireless with buttons - Fn or with on other button next to the shut down button. These need software ofcorse and Fujitsu don't have that kind of software for linux.

```
lsmod
Module                  Size  Used by
radeon                 96097  0
drm                    63701  1 radeon
wlan_wep                4864  1
ip_conntrack_netbios_ns     3009  0
ipt_REJECT              5441  1
xt_state                2241  2
ip_conntrack           49261  2 ip_conntrack_netbios_ns,xt_state
nfnetlink               6489  1 ip_conntrack
xt_tcpudp               3265  5
iptable_filter          3137  1
ip_tables              11657  1 iptable_filter
x_tables               12613  4 ipt_REJECT,xt_state,xt_tcpudp,ip_tables
nls_utf8                2241  1
ntfs                  187924  1
dm_mirror              19985  0
dm_mod                 50521  1 dm_mirror
video                  14917  0
button                  6609  0
battery                 9285  0
ac                      4933  0
ipv6                  225569  10
lp                     12297  0
parport_pc             25445  0
parport                34313  2 lp,parport_pc
nvram                   8393  0
ohci1394               31749  0
ieee1394              288665  1 ohci1394
ehci_hcd               29005  0
ohci_hcd               19805  0
joydev                  9473  0
8139cp                 21185  0
ath_pci                65440  0
8139too                25409  0
ath_rate_sample        13192  1 ath_pci
mii                     5313  2 8139cp,8139too
wlan                  118812  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               147536  3 ath_pci,ath_rate_sample
snd_atiixp             19157  1
snd_seq_dummy           3781  0
snd_seq_oss            28993  0
snd_seq_midi_event      7105  1 snd_seq_oss
snd_seq                47153  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_atiixp_modem       15433  0
snd_seq_device          8909  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_ac97_codec         83937  2 snd_atiixp,snd_atiixp_modem
snd_pcm_oss            45009  0
snd_ac97_bus            2497  1 snd_ac97_codec
snd_mixer_oss          16449  1 snd_pcm_oss
snd_pcm                76869  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              22597  2 snd_seq,snd_pcm
snd                    50501  12 snd_atiixp,snd_seq_oss,snd_seq,snd_atiixp_modem,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9377  1 snd
snd_page_alloc         10441  3 snd_atiixp,snd_atiixp_modem,snd_pcm
ext3                  116809  1
jbd                    53077  1 ext3

```

```
ifconfig
ath0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet6 addr: fe80::202:e3ff:fe47:83d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:6 dropped:0 overruns:0 frame:6
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:f8960000-f8970000

``` 

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""  Nickname:"localhost.localdomain"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

```
iwlist ath0 scan
ath0      Failed to read scan data : Resource temporarily unavailable

```

I don't know what to do anymore. Laptop with a wireless is pointless. Don't wanna use Windows but seems that I don't have much choice. 
To me it seems that I'm very close to get this to work if I only could enable the device.

---

### Post by ghanthar on 2006-03-26
Not sure about that but maybe you can try with ndiswrapper.
enable universe repos and do a 
```
sudo apt-get install ndiswrapper-utils ndisgtk
``` System--> Administration --> Windows Wireless Drivers 
Click install new driver and select your cards original windows driver. If it says hardware present than probably it did work. Do a 
```
sudo modprobe ndiswrapper 
``` If you are lucky your wireless led would shine :)
You can also check the ndiswrapper website at [http://ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net") to see if your card is supported.
[COLOR=Red] note: sometimes ndiswrapper does not work on 1st try so check the website to be sure that your card is supported.[/COLOR]

---

### Post by Aero-Z on 2006-03-26
Got ndiswrapper installed from.
From terminal I get:
```
 ndiswrapper -l
Installed drivers:
net5211         driver installed, hardware present

```

modprobe ndiswrapper also works and lsmod shows ndiswrapper too. Problem is that system can't find the device.
Seems that my card ain't working with ndiswrapper.

---

### Post by ghanthar on 2006-03-27
Weird 
if its says "hardware present" than you system shoul see it. What do you get on dmesg? I just tried it lsmod list ndiswrapper even if it is not configured correctly but on dmesg output you can see if there is a problem.
By the way I'm not sure if I can hlp you even after your post of dmesg output :( but I'll try. :)

---

### Post by supsup on 2006-04-26
I have the same laptop.
To enable wireless you have 2 ways:
1. download and compile lates version of madwifi-ng driver. load module with
    option rfkill=1. With this option the atheros chipset  ignores wireless button        state 
2. Secon option: download and install acer_acpi driver. 
   compile and install. check dmesg. if OK. 
#echo "enabled : 1" > /proc/acpi/acer/wireless to put
wireless on (including led) 

Hope it helps.

---

### Post by Aero-Z on 2006-05-02
[QUOTE=supsup]I have the same laptop.
To enable wireless you have 2 ways:
1. download and compile lates version of madwifi-ng driver. load module with
    option rfkill=1. With this option the atheros chipset  ignores wireless button        state 
2. Secon option: download and install acer_acpi driver. 
   compile and install. check dmesg. if OK. 
#echo "enabled : 1" > /proc/acpi/acer/wireless to put
wireless on (including led) 

Hope it helps.[/QUOTE]
Thanks, the second option worked. :)
Now I have 2 more questions:
1) How to modprobe acer_acpi when booting
2) After every reboot I have to re-enter
```
echo "enabled : 1" > /proc/acpi/acer/wireless
``` 
for the wireless to start up again.

---

### Post by LeFou on 2006-05-02
```
sudo apt-get install ndiswrapper-utils ndisgtk
``` 

I like this ndisgtk; mine now says my driver is installed and my hardware is present. Can't ping, though, and iwconfig shows

```

lo no wireless extensions
eth0 no wireless extensions
wlan0 no wireless extensions
sit0 no wireless extensions

```

> sudo /sbin/iwconfig wlan0 essid dizzy
Error for wireless request "Set ESSID:
SET failed on device wlan ; Invalid argument.

dizzy is the same essid that I have on my other wireless computer, on which I am now typing this post.

---

### Post by Aero-Z on 2006-05-02
[QUOTE=LeFou]```
sudo apt-get install ndiswrapper-utils ndisgtk
``` 

I like this ndisgtk; mine now says my driver is installed and my hardware is present. Can't ping, though, and iwconfig shows

```

lo no wireless extensions
eth0 no wireless extensions
wlan0 no wireless extensions
sit0 no wireless extensions

```

> sudo /sbin/iwconfig wlan0 essid dizzy
Error for wireless request "Set ESSID:
SET failed on device wlan ; Invalid argument.

dizzy is the same essid that I have on my other wireless computer, on which I am now typing this post.[/QUOTE]

Why did you post this here?

---

### Post by LeFou on 2006-05-02
[QUOTE=Aero-Z]Why did you post this here?[/QUOTE]

was hoping ghanthar might know a quick way to go ahead and bring up the wlan0 through ndisgtk... it has a "configure network" dialogue, but there's no wlan0 in there when I go to it.

Anyway, the full description of my adventure is in a different thread ("airlink" something...)

---

### Post by supsup on 2006-05-02
[QUOTE=Aero-Z]Thanks, the second option worked. :)
Now I have 2 more questions:
1) How to modprobe acer_acpi when booting
2) After every reboot I have to re-enter
```
echo "enabled : 1" > /proc/acpi/acer/wireless
``` 
for the wireless to start up again.[/QUOTE]

I'm not running ubuntu 5.10 right now.  But it should be like this
1. write acer_acpi in file /etc/modules.
```
 echo "acer_acpi" >> /etc/modules 
```
 The system loads modules from this
file at boot time.
2. It depends what u exactly want. For example, insert 
```
echo "enabled : 1" > /proc/acpi/acer/wireless
``` 
 line into /etc/rc.local
You should load acer_acpi to use this.

---

### Post by Aero-Z on 2006-05-04
Thanks for those. Now one more question. Where do I have to put:
```
echo "enabled : 0" > /proc/acpi/acer/wireless
```
to disable the interface when rebooting the system?

---

