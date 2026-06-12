---
title: "It says &quot;Connected&quot; but it's not"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by d21 on 2011-10-02
Aloha,

after that winzoz xp died on an old pc i gave to my mom&sister, i thought to give them an OS i shouldn't fix every 2 days.


I was naive: the fresh install can't connect via wireless.

I've a Netgrear router with a secure key.
Randomly changing the settings Ubuntu shows me this icon (that looks to me like "Only local connection" but i don't know the meaning for sure): 
[IMG]http://dl.dropbox.com/u/21658304/02102011657.jpg[/IMG]

while if i set the secure key as Wpa Personal i have this icon (that looks like the right one):
[IMG]http://dl.dropbox.com/u/21658304/02102011656.jpg[/IMG]

In both cases i have the "Connection Estabilished" alert, but that's not true, as you can see from this SS:
[img]http://dl.dropbox.com/u/21658304/02102011654.jpg[/img]

The following are my Terminal "answers", to my "questions":
**IWCONFIG**
[img]http://dl.dropbox.com/u/21658304/02102011658.jpg[/img]

**IFCONFIG**
[img]http://dl.dropbox.com/u/21658304/02102011659.jpg[/img]

**TRYING TO PING**
[img]http://dl.dropbox.com/u/21658304/02102011662.jpg[/img]

Waiting for some genius to help me with it :p

---

### Post by wildmanne39 on 2011-10-02
Hi, welcome to the forum! Let's see if see can get this working, I am going to need some information, please no more pictures they take up a lot of room.

The only thing that I seen from the pictures is that you have your router set to ad-hoc it will it needs to be set to managed mode.

Open a terminal by hitting ctrl+alt+t then copy and paste the information into it, then paste the outcome here:
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by chili555 on 2011-10-02
> The only thing that I seen from the pictures is that you have your router set to ad-hoc it will it needs to be set to managed mode.The wireless interface is set to ad hoc; not the router.

Your iwconfig shows your mode is 'ad hoc.' That is for computer-to-computer connections, not for computer-to-router and thence to the internet.

Please click the Network Manager icon and disconnect, then select Edit Connections. Select Wireless and select Edit. Set the mode to Infrastructure and remove all other settings. Save and close everything and then click the NM icon again. See your own router and try to connect.

---

### Post by d21 on 2011-10-02
Thanks for the answer pps :D

@Chili, the problem is i can't see my own router:
[IMG]http://dl.dropbox.com/u/21658304/02102011667.jpg[/IMG]

@Wild, these are the responses from the terminal:

```
anna@computer-cucina:~$ lspci | grep Network



anna@computer-cucina:~$ cat /etc/lab-release; uname -a
cat: /etc/lab-release: No such file or directory
Linux computer-cucina 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux



anna@computer-cucina:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             unavailable
  Default:           no
  HW Address:        00:0E:A6:51:EC:BF

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        00:1F:1F:03:3E:EF

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



anna@computer-cucina:~$ lspci -nnk |grep -iA2 net
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
	Subsystem: ASUSTeK Computer Inc. A7V600-X Motherboard [1043:80ed]
	Kernel driver in use: via-rhine



anna@computer-cucina:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


anna@computer-cucina:~$ rfkill list all
0: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no



anna@computer-cucina:~$ sudo iwlist scan
[sudo] password for anna: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results



anna@computer-cucina:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52200  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13562  1 nf_nat_pptp
nf_conntrack_proto_gre    13353  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16922  0 
nf_conntrack_sip       24652  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_conntrack_ftp       13106  1 nf_nat_ftp
iptable_nat            12977  0 
nf_nat                 24827  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18125  2 iptable_filter,iptable_nat
x_tables               21907  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
arc4                   12473  2 
snd_wavefront          34696  0 
snd_via82xx            24685  2 
radeon                896428  3 
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
snd_via82xx_modem      18305  0 
snd_cs4236             29291  0 
snd_wss_lib            30006  2 snd_wavefront,snd_cs4236
snd_ac97_codec        105614  2 snd_via82xx,snd_via82xx_modem
rt2500usb              22621  0 
snd_opl3_lib           18760  2 snd_wavefront,snd_cs4236
snd_hwdep              13274  2 snd_wavefront,snd_opl3_lib
ac97_bus               12642  1 snd_ac97_codec
rt2x00usb              19693  2 rt73usb,rt2500usb
snd_pcm                80244  5 snd_via82xx,snd_cs4236,snd_via82xx_modem,snd_wss_lib,snd_ac97_codec
rt2x00lib              39075  3 rt73usb,rt2500usb,rt2x00usb
binfmt_misc            13213  1 
snd_mpu401             13800  0 
snd_mpu401_uart        13865  4 snd_wavefront,snd_via82xx,snd_cs4236,snd_mpu401
mac80211              257001  2 rt2x00usb,rt2x00lib
snd_seq_midi           13132  0 
ttm                    65184  1 radeon
snd_rawmidi            25269  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
drm_kms_helper         40745  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
cfg80211              156212  2 rt2x00lib,mac80211
snd_timer              28659  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         14110  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  5 radeon,ttm,drm_kms_helper
snd                    55295  19 snd_wavefront,snd_via82xx,snd_cs4236,snd_via82xx_modem,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_ac97_codec,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 radeon
ns558                  12618  0 
i2c_viapro             12969  0 
snd_page_alloc         14073  4 snd_via82xx,snd_via82xx_modem,snd_wss_lib,snd_pcm
parport_pc             32111  1 
gameport               15027  3 snd_via82xx,ns558
shpchp                 32345  0 
soundcore              12600  1 snd
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
via_rhine              27131  0 
pata_via               13368  2 
sata_via               13464  0 

```

---

### Post by wildmanne39 on 2011-10-02
Hi. if you do it like chili555 says you do not need to change the router settings you change the setting using network manager it is a little icon in the top right corner of the screen by the speaker.
I was incorrect where the setting needs to be changed.

Click on edit connection.
Thank you

---

### Post by chili555 on 2011-10-02
Please try:```
sudo su
iwconfig wlan0 mode managed
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot.

Now let us see:```
sudo iwlist wlan0 scan
```You will never see your router in ad hoc mode.

---

### Post by d21 on 2011-10-02
did all the commands with no errors shown.

the rebooted.

then:

```
anna@computer-cucina:~$ sudo iwlist wlan0 scan
[sudo] password for anna: 
wlan0     Interface doesn't support scanning : Device or resource busy

anna@computer-cucina:~$ sudo iwlist wlan0 scan
wlan0     No scan results

anna@computer-cucina:~$ sudo iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by wildmanne39 on 2011-10-02
Hi, please post the results of:
```
lsusb
```
```
dmesg | egrep 'rt2|firm|rt7|wlan0'
```
```
lsmod | grep -e rt2 -e rt7
```
Thank you

---

### Post by chili555 on 2011-10-02
Did mode: managed stick?```
iwconfig
```When you edit connections in Network Manager, all all settings removed? Is mode Infrastructure?

---

### Post by d21 on 2011-10-02
@wild

```
anna@computer-cucina:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a81:0203 Chesen Electronics Corp. Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



anna@computer-cucina:~$ dmesg | egrep 'rt2|firm|rt7|wlan0'
[   12.227416] Registered led device: rt73usb-phy0::radio
[   12.227492] Registered led device: rt73usb-phy0::assoc
[   12.227556] Registered led device: rt73usb-phy0::quality
[   12.229554] usbcore: registered new interface driver rt73usb
[   12.433562] ADDRCONF(NETDEV_UP): wlan0: link is not ready



anna@computer-cucina:~$ lsmod |grep -e rt2 -e rt7
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19693  1 rt73usb
rt2x00lib              39075  2 rt73usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211



```

@chili

```
anna@computer-cucina:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
anna@computer-cucina:~$ 


```

and about edit connections:
[IMG]http://dl.dropbox.com/u/21658304/Screenshot.png[/IMG]

should i create one, even if no connection is shown from scanning?!

---

### Post by chili555 on 2011-10-02
> should i create one, even if no connection is shown from scanning?!No, please. 'Create New Wireless Network' creates an ad hoc computer-to-computer network; that's just what we do *not* want.

Can you confirm you have the needed firmware rt73bin?```
ls /lib/firmware | grep rt7
```Also, is the interface up?```
sudo ifconfig wlan0 up
```If there is an error or warning, it will be informative, so please post it.

I'd studying your readings, as I'm sure the Wild Man is, too...

---

### Post by d21 on 2011-10-02
ok, i'll stay far from that then :

meanwhile: thanks for your patience :)

EDIT:

```
anna@computer-cucina:~$ ls /lib/firmware | grep rt7
rt73.bin


anna@computer-cucina:~$ sudo ifconfig wlan0 up
[sudo] password for anna: 


anna@computer-cucina:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:51:ec:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8544 (8.5 KB)  TX bytes:8544 (8.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:03:3e:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by chili555 on 2011-10-02
It is up and gives every sign of being a perfectly working wireless interface. Still no scan results?```
sudo iwlist wlan0 scan
```Are you certain you are near a working wireless access point?>  Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        00:1F:1F:03:3E:EF

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

[COLOR="Red"]??? none ???[/COLOR]



---

### Post by wildmanne39 on 2011-10-02
Hi, you can also try:
```
sudo iwconfig wlan0 power off
```
see if that brings it to life.
Thank you

---

### Post by d21 on 2011-10-02
nuthin'

:frown:

a guy from italian forum suggested i could check out for "ndiswrapper"... can it be of some help?

BTW, the strange thing is that i installed ubuntu 11 live from CD, and while on live, internet did work!!!

this is awkward...

---

### Post by wildmanne39 on 2011-10-02
Hi, you do not need ndiswrapper, and it usually does not work as well.

Unplug your wired connection then run this command and post the results please:
```
sudo cat /var/log/syslog | grep etwork | tail -n50
```
Did you try what I suggested in my last post?
Thank you

---

### Post by d21 on 2011-10-02
yes i tried that, but still no scan results...

what you mean about "unplugging my connection?"

the machine with linux has only wireless usb pen, and i'm writing this from another machine with windows 7 + wireless usb pen (same model of the other).

What do i have to unplug?


EDIT:

to be sure i gave the command again and now it gave me this:```
anna@computer-cucina:~$ sudo iwconfig wlan0 power off
[sudo] password for anna: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Invalid argument.
anna@computer-cucina:~$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Invalid argument.

```

i think this means the settings is already given?

now the led is flashing all the time...

---

### Post by wildmanne39 on 2011-10-02
Hi, was the light off before?
Try these 2 commands please:
```
sudo iwlist scan
```
```
iwlist chan
```
if you do not have a wired connection then just run the other command that I gave you and post all the results of that command here, I am looking for more error messages.
Thank you

---

### Post by d21 on 2011-10-02
```
anna@computer-cucina:~$ sudo cat /var/log/syslog | grep network | tail -n50
Oct  2 20:17:41 computer-cucina kernel: [ 1350.112021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:18:13 computer-cucina kernel: [ 1382.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:18:45 computer-cucina kernel: [ 1414.112024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:19:17 computer-cucina kernel: [ 1446.112025] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:19:49 computer-cucina kernel: [ 1478.112022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:20:21 computer-cucina kernel: [ 1510.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:20:53 computer-cucina kernel: [ 1542.112025] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:21:25 computer-cucina kernel: [ 1574.112022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:21:57 computer-cucina kernel: [ 1606.112021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:22:29 computer-cucina kernel: [ 1638.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:23:01 computer-cucina kernel: [ 1670.112028] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:23:33 computer-cucina kernel: [ 1702.112024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:24:05 computer-cucina kernel: [ 1734.112024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:24:37 computer-cucina kernel: [ 1766.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:25:09 computer-cucina kernel: [ 1798.112024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:25:41 computer-cucina kernel: [ 1830.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:26:13 computer-cucina kernel: [ 1862.112025] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:26:45 computer-cucina kernel: [ 1894.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:27:17 computer-cucina kernel: [ 1926.112024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:27:49 computer-cucina kernel: [ 1958.112044] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:28:21 computer-cucina kernel: [ 1990.112024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:28:53 computer-cucina kernel: [ 2022.112033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:29:25 computer-cucina kernel: [ 2054.112019] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:29:57 computer-cucina kernel: [ 2086.112019] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:30:29 computer-cucina kernel: [ 2118.112021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:31:01 computer-cucina kernel: [ 2150.112017] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:31:33 computer-cucina kernel: [ 2182.112022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:32:05 computer-cucina kernel: [ 2214.112022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:32:37 computer-cucina kernel: [ 2246.112021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:33:09 computer-cucina kernel: [ 2278.112024] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:33:41 computer-cucina kernel: [ 2310.112026] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:34:13 computer-cucina kernel: [ 2342.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:34:45 computer-cucina kernel: [ 2374.112060] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:35:17 computer-cucina kernel: [ 2406.112028] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:35:49 computer-cucina kernel: [ 2438.112040] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:36:21 computer-cucina kernel: [ 2470.112020] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:36:53 computer-cucina kernel: [ 2502.112083] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:37:25 computer-cucina kernel: [ 2534.112021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:37:57 computer-cucina kernel: [ 2566.112021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:38:29 computer-cucina kernel: [ 2598.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:39:01 computer-cucina kernel: [ 2630.112020] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:39:33 computer-cucina kernel: [ 2662.112023] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:40:05 computer-cucina kernel: [ 2694.112020] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:40:37 computer-cucina kernel: [ 2726.112022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 20:43:53 computer-cucina NetworkManager[430]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'd21'.
Oct  2 20:44:03 computer-cucina kernel: [ 2932.206668] wlan0: Creating new IBSS network, BSSID 1a:a6:08:3a:90:b7
Oct  2 22:42:52 computer-cucina kernel: [ 5360.270600] wlan0: Creating new IBSS network, BSSID e2:6e:bb:f3:41:ad
Oct  2 22:42:52 computer-cucina NetworkManager[416]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'd21'.
Oct  2 22:43:23 computer-cucina kernel: [ 5391.072021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Oct  2 22:43:55 computer-cucina kernel: [ 5423.072021] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)



anna@computer-cucina:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results



anna@computer-cucina:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.412 GHz (Channel 1)



```

---

### Post by wildmanne39 on 2011-10-02
Hi, the errors you are getting means it is still trying to use ad-hoc.

Go into network manager and click on create a new wireless connection, then make sure your settings look like this, refer to screenshots.

Also while setting up wireless set security or encryption to wpa2.
Thank you

---

### Post by d21 on 2011-10-02
really?! even if "wireless connections" was empty?! >__<

ok, i went in Edit -> Wireless tab-> Add, and set up a connection like your screenshots + wpa personal with the right password...

... and?

---

### Post by wildmanne39 on 2011-10-02
Hi, restart your computer and see if it detects networks?
Thank you

---

### Post by wildmanne39 on 2011-10-02
Hi, I do not think that is going to work and if it does not delete the connection you made.

I have researched your error message and the command that chili555 gave you should have got rid of it.

I also found some old bug reports on it but nothing recent and no solutions.
If it does no work and after you delete the wireless connection, then run these commands please.
```
iwconfig
```
```
sudo rfkill unblock all
```
Thank you.

---

### Post by d21 on 2011-10-02
no changes....

i'd reinstall it, but wifi never worked... maybe i'll try to install Hardy Heron...

or we have any chance to solve, you think?

i feel guilty making you wasting time :(

---

### Post by d21 on 2011-10-02
LOOOOL! WAIT WAIT!

I'm running ubuntu on live cd, and it finds wireless networks o____O

but it doesn't recognize the password:

i have an Open WEP key, but ubuntu only make me chose among Wep r0/128 (hex or ascii), wep 128, leap, dynamic wep....

i've tried web 40\128 & wep 128 and it doesn't connect...

---

### Post by d21 on 2011-10-02
well, listen to this:

Just to try, I installed Hardy Heron: when i was live it did find my wireless (not making me connect due to password issue), but after i installed it it didn't show me the wireless anymore!!!

Exactly the same that happens with Natty Narwhal...

funny...

---

### Post by wildmanne39 on 2011-10-02
Hi, it could be due to a different issue when you reinstall you have to start all over with the commands I have already given you to see what has changed.

There is no version of ubuntu older then 10.04 that is still supported, if you want to try one different then 11.04 then I recommend 10.04.

It probably will not work with out some tweaking but do not create a wireless connection, post the results of ```
lsmod
```
```
iwconfig
```
so we can see if the driver is loaded and with there is a conflicting one loaded.

I have a usb device that uses the same driver and as soon as I boot after I have installed ubuntu it finds my network.
Thank you

---

### Post by d21 on 2011-10-02
There must be something different in how usb wireless device are managed from the live cd version, to the installed one...

Tomorrow i'll post some code, so maybe it's possible to figure it out...

2 am now in Rome, g'night and thank you for now ^_^

---

### Post by binary00mind on 2011-10-02
@d21 you don't have to be so angry, there could be many reasons why all this is happening to you. 
Try this approach, instead of Live CD use Alternate Text Installer CD. 
Install from the underground. Network configuration comes up within 2 minutes. If it sees your network, then installer will find it. Once configured (very simple interface) it will save your settings forever before you even have a chance to see your desktop.

---

### Post by wildmanne39 on 2011-10-02
Hi, it is not just usb devices, the livecd has drivers and firmware in it that is not installed by default in ubuntu because of legal reasons, but I imagine if it does not setup as ad-hoc then it is just a matter of removing the extra driver that gets loaded sometimes.
Thank you

---

### Post by d21 on 2011-10-05
Problem solved!

Of course was the most simple thing: the usb wireless receiver is broken!

It does flash, it is recognized by the system, but the receiving stuff is dead!

I tried using another receiver on the pc and now it is working!!! >___<

Sorry if i make you guys waste time QQ

---

### Post by wildmanne39 on 2011-10-05
Hi, I am glad you found a solution.

---

