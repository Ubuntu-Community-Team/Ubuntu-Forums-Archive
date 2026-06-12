---
title: "RTL8188CE with Toshiba A660 Wifi Problems"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by Trezitorul on 2012-02-13
First Post...let me know if I am forgetting anything.
I have been working on my wifi for a few weeks now but can not seem to make it work. Essentially I have a Toshiba A660 with an RTL8188CE wifi card from Realtek and at my university it is having an awful time with the network. I have tried everything I have come across with no success. 
The card can scan and it even connects using network manager. However, after some amount of time the connection just hangs (pings just stop). Then the card might disconnect, or it might keep trying to maintain the connection but with no internet (wireshark reveals that it is broadcasting about asking about the IP without a response or that it is waiting on a DHCP request)
On my desk there seem to be random sweet spots where the connection is marginally more stable.
Additionally there are a lot of packets in wireshark with the code low/unexpected TTL.
One complication there are many Cisco routers everywhere so I can see more than one access point with good signal strength. Each of these AP has the same ESSID.
A
Things I have tried:
-Installing the driver from Realtek
-A number of kernels 3.0.0.12 - 16, 3.1 and 3.2 
-setting ips=0
-Wicd (just tries to obtain ip address endlessly)
connecting manually via CLI: dhclient just endlessly sends out    DHCP requests.)
-Editing network.conf setting managed to true
-Banging head against computer(not very effective)

Any help will be greatly appreciated!

---

### Post by varunendra on 2012-02-14
Hi Trezitorul,
Welcome to the forums!

Although your problem already seems above my level, I hope you wouldn't mind if I try. If no other experts picked it up, and I couldn't help solving it either, I'd personally try to contact some 'true expert' and ask for his help.

To provide a detailed info about your current hardware, drivers and settings, please post the outputs of:
```
lsb_release -d; uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig
iwconfig
cat /etc/network/interfaces
cat /etc/nsswitch.conf
cat /etc/NetworkManager/NetworkManager.conf
route -n
```

While posting, please wrap the outputs in 'Code' tags by clicking on **#** at the top of the edit box to generate the tags, then copy-paste the outputs in-between those tags.

---

### Post by Trezitorul on 2012-02-18
Thanks for your help!
Alright here are all of the outputs requested. 
```

trezitorul@Trezitorul:~$ lsb_release -d;uname -mr
Description:	Ubuntu 11.10
3.0.0-16-generic x86_64


trezitorul@Trezitorul:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Toshiba America Info Systems Device [1179:fd30]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
	Kernel driver in use: rtl8192ce


trezitorul@Trezitorul:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  4 
nvidia              11713772  42 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
rtl8192ce              79472  0 
serio_raw              13166  0 
rtl8192c_common        74576  1 rtl8192ce
rtlwifi               105520  1 rtl8192ce
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              471589  3 rtl8192ce,rtl8192c_common,rtlwifi
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17646  0 
cfg80211              202604  2 rtlwifi,mac80211
memstick               16569  1 jmb38x_ms
mei                    41480  0 
sparse_keymap          13890  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  3 
libahci                26861  1 ahci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
r8169                  52788  0 


trezitorul@Trezitorul:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:70:27:4b  
          inet addr:18.250.6.163  Bcast:18.250.255.255  Mask:255.255.0.0
          inet6 addr: fe80::1e75:8ff:fe70:274b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9406 errors:0 dropped:2 overruns:0 frame:0
          TX packets:4338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4275054 (4.2 MB)  TX bytes:887556 (887.5 KB)
          Interrupt:45 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46120 (46.1 KB)  TX bytes:46120 (46.1 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:a5:6e:24  
          inet addr:18.111.121.148  Bcast:18.111.127.255  Mask:255.255.224.0
          inet6 addr: fe80::1e65:9dff:fea5:6e24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2048310 (2.0 MB)  TX bytes:650575 (650.5 KB)





trezitorul@Trezitorul:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MIT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C8:4C:75:5F:75:12   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



trezitorul@Trezitorul:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

 




trezitorul@Trezitorul:~$ cat /etc/nsswitch.conf
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





trezitorul@Trezitorul:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true





trezitorul@Trezitorul:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         18.250.0.1      0.0.0.0         UG    0      0        0 eth0
18.111.96.0     0.0.0.0         255.255.224.0   U     2      0        0 wlan0
18.250.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0




```

---

### Post by praseodym on 2012-02-18
Which encryption mode do you use? I recommend WPA2-AES if possible. Did you uninstall the networkmanager for using Wicd? Installed the Add-On from Wicd?

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service wicd restart
```
Choose **wlan0** as interface and **wext** as driver in wicd.

---

### Post by varunendra on 2012-02-18
Hmm.. so 'the expert' is already here :). Definitely the time for me to sit back and just watch the game!

However, *praseodym*, shouldn't the entry in NetworkManager.conf-
> **Trezitorul said:**
> ```

[ifupdown]
managed=**true**
```
be set to 'False' when the 'etc/network/interfaces file only contains the loopback interface? Well of-course it won't matter if the OP has to try wicd, but isn't that an unnecessary and non-default value for NM? Just wondering.

---

### Post by praseodym on 2012-02-18
"true" only means, that any additional entries in the "interfaces" are (normally) **not** ignored by the NM. It is woth a try (I am also interested in it ;-) )

---

### Post by Trezitorul on 2012-02-18
I currently am not using encryption for simplicity.

I have run the commands suggested. I did not know there was an add on for wicd. Either way I installed it and then shutdown network manager. At first wicd did not want to connect so I started to play with the settings. In the end, once it connects it is very stable. However, to get it to connect I had to set:
Driver = nl80211
DHCP Client = dhclient
Route Table Flushing = route

The only problem is that WICD seems to have a terrible time obtaining the IP address so several reconnects are often needed. It is still better than what was happening before with network manager. Any suggestions on improving WICD's connection characteristics.

---

### Post by praseodym on 2012-02-18
Try uninstalling the networkmanager "completely"

---

### Post by Trezitorul on 2012-02-18
I did after I tested it. I used:

```
sudo apt-get-remove --purge network-manager
```

Is there anything else I need to do?

---

### Post by varunendra on 2012-02-18
> **Trezitorul said:**
> Is there anything else I need to do?
Disabling IPv6 maybe?
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by Trezitorul on 2012-02-19
I disabled IPV6 but no dice, for some reason wicd connected much better earlier today but now it can't get an IP at all. 

One thing I did notice was that in the file that I edited for disabling IPV6. There were a lot of references to ICMP. I have run wireshark on the connection and I saw a lot of TCP errors (namely Low/Unexpected TTL) additionally I have seen references to ICMP quite often in the wireshark logs. 

Another interesting bit of trivia when I check the connection using iwconfig (believe this is the command) it shows that a non trivial "Invalid Misc" errors are occuring.

Additionally, when I run dmesg it usually shows that the direct probe fails 3 times and then times out.

I know that the routers we have here are actually acting as switches connecting me to another router somewhere else and then to the internet. Would this cause problems?

Thanks for all the help!

---

### Post by Trezitorul on 2012-03-17
Bump

---

### Post by praseodym on 2012-03-17
There is a new driver 0005.1230.2011  on the Realtek-Homepage

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722)

---

### Post by Trezitorul on 2012-03-17
Hmmm, I had that driver installed but I figured I would uninstall it and try again. However, now when I try to install the driver I get this error.

```

make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
make[1]: *** No rule to make target `Driver'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make: *** [all] Error 2

```

---

### Post by praseodym on 2012-03-17
Did you install the latest headers?

```
sudo apt-get install --reinstall linux-headers-generic build-essential
```
Try "sudo make" instead as described in the readme.

---

### Post by Trezitorul on 2012-03-17
Hmmm, I just reinstalled the headers and tried again along with using sudo (I was in root mode before). No dice. 

Is it possible their installer is not compatible with the 3.0.0.16 kernel?

---

### Post by praseodym on 2012-03-18
Hm, maybe some driver problems from the Realtek side. Try this one:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget [http://media.cdn.ubuntu-de.org/forum/attachments/55/37/2844083-rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/55/37/2844083-rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz)
tar xvf 2844083-rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot and check:

```
modinfo rtl8192ce | egrep 'versi|filen'
locate rtl8192ce.ko
lsmod
dmesg | grep rtl8
iwconfig
```

---

