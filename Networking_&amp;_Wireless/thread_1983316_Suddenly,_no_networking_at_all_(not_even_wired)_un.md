---
title: "Suddenly, no networking at all (not even wired) under Ubuntu 10.04"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by elias.alberto on 2012-05-20
Using Ubuntu 10.04 on a Dell Inspiron 1525 laptop with wireless network Broadcom BCM4312. Everything used to work normally.

A couple months ago, it started to disconnect from my wireless network with no apparent reason, and it wouldn't connect again unless I reboot the notebook. Sometimes it would also kill the Network Manager, so that little networking icon right beside the clock would disappear (which I solved going to terminal and running nm-applet every time it was killed).
Yesterday I was working using wired networking (which is very unusual) and wireless networking simultaneously when, with no apparent reason at all (I didn't install or update anything), it totally stopped working. Now it will see wireless networks and will detect when an ethernet cable is plugged, but won't connect to neither of them. The icon for nm-applet beside the clock will even show two little green dots as if it was about to connect to the network, but then it fails.
It's probably not a hardware problem, since I could use the wireless network after booting Ubuntu 12.04 from a thumbdrive (I had to use a usb wifi adapter in order to install the restricted drivers required for Broadcom adapters to work under Ubuntu 12.04, but after I've done it, I've unplugged the usb wifi adapter and connected normally to my wireless network).
I think it's a software problem because I tried to connect to my wireless network under ubuntu 10.04 using the external usb adapter I mentioned (which has different chipset) and even though it could see wifi networks, also couldn't connect to them.

Please note: without networking at all on my computer, I can't simply uninstall stuff and reinstall it from repository using apt-get. Should I need to install anything, I'll need instruction on how to download it in another computer and then transfer it via usb stick. Or maybe there's a way to install stuff on my 10.04 distro after I've booted 12.04 in live mode from a thumb drive?

So, if anyone can shed light on this problem... :P

---

### Post by praseodym on 2012-05-20
Please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/resolv.conf
ifconfig -a
rfkill list
iwconfig
dmesg | egrep 'eth0|wlan0' 
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by elias.alberto on 2012-05-20
** After running the comands, I've been messing with my settings and found out what was preventing me to connect to any network: I had both ipv6 and ipv4 enabled. Once I disabled ipv6, I could connect normally to wired and wireless networks. It seems weird to me to find this was the problem, because I was kept connected for quite a while after I changed these settings (I didn't even remember I did it, so I haven't thought this could be the problem). If you've never come through such a seemingly unexplainable problem, beware of ipv6. 
I'm still having problems with nm-applet auto-killing itself occasionally and, as I said, the wireless network (long before I set up ipv6) would sometimes disconnect and only work again after rebooting (I have a very wild guess this might be related to heating problems)**

As I booted, nm-applet wasn't running, so I ran nm-applet and first tried to connect to a wired network (each try is when nm-applet said "foo_client_state_changed_cb"), then to a wireless network, and got this:

```
elias@Alberto-PC:~$ nm-applet
** (nm-applet:2145): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2145): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2145): DEBUG: foo_client_state_changed_cb
** (nm-applet:2145): DEBUG: foo_client_state_changed_cb
** (nm-applet:2145): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:2145): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:2145): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:2145): DEBUG: foo_client_state_changed_cb
** (nm-applet:2145): DEBUG: foo_client_state_changed_cb
** (nm-applet:2145): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:2145): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:2145): DEBUG: going for offline with icon: notification-network-wireless-disconnected

```

I left it running while I ran the commands requested. A few minutes AFTER I finished running them, it said:
```
** Message: Caught signal 15, shutting down...
elias@Alberto-Pc:~$ 
```

Here are the commands requested. I also ran a ping at the beginning and modified dmesg to show 'eth|wlan' because I thought it would be more relevant.

```
elias@Alberto-PC:~$ ping 8.8.8.8
connect: Network is unreachable
elias@Alberto-PC:~$ uname -a
Linux Alberto-PC 2.6.32-41-generic-pae #89-Ubuntu SMP Fri Apr 27 23:59:24 UTC 2012 i686 GNU/Linux
elias@Alberto-PC:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
	Kernel driver in use: sky2
	Kernel modules: sky2
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
elias@Alberto-PC:~$ 
elias@Alberto-PC:~$ lsmod
Module                  Size  Used by
hidp                   11083  0 
aes_i586                7268  359 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
rfcomm                 33453  4 
sco                     7949  2 
bridge                 45678  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30656  17 hidp,rfcomm,bnep
vmnet                  42766  13 
ppdev                   5259  0 
parport_pc             26250  0 
vsock                  39533  0 
vmci                   68257  1 vsock
vmmon                  60904  0 
dm_crypt               11331  0 
joydev                  8740  0 
snd_hda_codec_idt      52074  1 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_intel          22165  2 
arc4                    1153  2 
snd_hda_codec          74297  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
b43                   164132  0 
sdhci_pci               5502  0 
dell_laptop             6888  0 
mac80211              205434  1 b43
btusb                  11053  2 
bluetooth              49892  10 hidp,rfcomm,sco,bnep,l2cap,btusb
uvcvideo               57470  0 
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
dcdbas                  5490  1 dell_laptop
sdhci                  15654  1 sdhci_pci
snd                    54244  17 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ricoh_mmc               2923  0 
psmouse                63677  0 
serio_raw               3978  0 
cfg80211              126528  2 b43,mac80211
led_class               2864  2 b43,sdhci
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usbhid                 36206  0 
hid                    67288  2 hidp,usbhid
i915                  290852  3 
drm_kms_helper         29329  1 i915
drm                   164436  4 i915,drm_kms_helper
ohci1394               27238  0 
i2c_algo_bit            5028  1 i915
intel_agp              24671  2 i915
ssb                    38934  1 b43
ieee1394               81213  1 ohci1394
sky2                   41072  0 
video                  17375  1 i915
output                  1871  1 video
ahci                   32712  3 
agpgart                31788  2 drm,intel_agp
elias@Alberto-PC:~$ cat /etc/resolv.conf
# Generated by NetworkManager
elias@Alberto-PC:~$ ifconfig -a
eth0      Link encap:Ethernet  Endereço de HW 00:23:ae:******  
          endereço inet6: fe80::223:******/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:210 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:8 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:68986 (68.9 KB) TX bytes:1424 (1.4 KB)
          IRQ:16 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:92487 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:92487 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:11504916 (11.5 MB) TX bytes:11504916 (11.5 MB)

pan0      Link encap:Ethernet  Endereço de HW 5e:a3:04:******  
          BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  Endereço de HW 00:50:56:******  
          inet end.: 192.168.179.1  Bcast:192.168.179.255  Masc:255.255.255.0
          endereço inet6: fe80::250:******/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:46 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  Endereço de HW 00:50:56:******  
          inet end.: 172.16.111.1  Bcast:172.16.111.255  Masc:255.255.255.0
          endereço inet6: fe80::250:******/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:45 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  Endereço de HW 00:24:2b:******  
          endereço inet6: fe80::224:2bff:******/64 Escopo:Link
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:30 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:13 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:6522 (6.5 KB) TX bytes:2250 (2.2 KB)

elias@Alberto-PC:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
elias@Alberto-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

elias@Alberto-PC:~$ dmesg | egrep 'eth|wlan'
[    1.013419] sky2 eth0: addr 00:23:ae:******
[   19.998101] udev: renamed network interface wlan0 to wlan1
[   21.555570] sky2 eth0: enabling interface
[   21.555763] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.509786] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   27.521995] bridge-wlan1: device is wireless, enabling SMAC
[   27.522001] bridge-wlan1: up
[   27.522005] bridge-wlan1: attached
[   27.522057] bridge-wlan1: disabling the bridge
[   27.532052] bridge-wlan1: down
[   27.532060] bridge-wlan1: detached
[   35.117352] wlan1: deauthenticating from 00:a0:55:****** by local choice (reason=3)
[   35.117493] wlan1: direct probe to AP 00:a0:55:****** (try 1)
[   35.120651] wlan1: direct probe responded
[   35.120656] wlan1: authenticate with AP 00:a0:55:****** (try 1)
[   35.122365] wlan1: authenticated
[   35.122383] wlan1: associate with AP 00:a0:55:****** (try 1)
[   35.124989] wlan1: RX AssocResp from 00:a0:55:****** (capab=0x411 status=0 aid=5)
[   35.124994] wlan1: associated
[   35.125754] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   35.158865] bridge-wlan1: device is wireless, enabling SMAC
[   35.158869] bridge-wlan1: up
[   35.158873] bridge-wlan1: attached
[   45.136039] wlan1: no IPv6 routers present
[   45.300140] wlan1: deauthenticating from 00:a0:55:****** by local choice (reason=3)
[   45.300722] bridge-wlan1: disabling the bridge
[   45.312308] bridge-wlan1: down
[   45.312315] bridge-wlan1: detached
[  781.309333] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  781.309665] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  781.309935] bridge-eth0: up
[  781.309939] bridge-eth0: attached
[  781.359111] sky2 eth0: Link is down.
[  782.324675] bridge-eth0: disabling the bridge
[  782.337027] bridge-eth0: down
[  782.337036] bridge-eth0: detached
[  783.083994] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  783.084614] bridge-eth0: up
[  783.084618] bridge-eth0: attached
[  791.688113] eth0: no IPv6 routers present
[  848.673060] wlan1: deauthenticating from 00:a0:55:****** by local choice (reason=3)
[  848.857307] wlan1: direct probe to AP 00:a0:55:****** (try 1)
[  848.859583] wlan1: direct probe responded
[  848.859589] wlan1: authenticate with AP 00:a0:55:****** (try 1)
[  848.861286] wlan1: authenticated
[  848.861323] wlan1: associate with AP 00:a0:55:****** (try 1)
[  848.863867] wlan1: RX AssocResp from 00:a0:55:****** (capab=0x411 status=0 aid=4)
[  848.863871] wlan1: associated
[  859.300236] wlan1: deauthenticating from 00:a0:55:****** by local choice (reason=3)
elias@Alberto-PC:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
elias@Alberto-PC:~$ 
```

---

### Post by praseodym on 2012-05-20
Open "Users&Groups", tick any user rights in "extended" and login again. After that, remove any wired profiles in "cable" and "DSL" and reboot. After that remove the wireless profile and setup a new one.

The wireless network seems "hidden", this is no security advantage, better broadcast the ESSID (router settings)

---

### Post by elias.alberto on 2012-05-20
My wireless network is not hidden, I'm aware it would not increase security. I have it setup to use WPA2/AES, a non-trivial passphrase longer than 20 characters, and WPS disabled. That should be enough. :P

I did all the other things you've mentioned, but as the problem only happens eventually, I'll still have to wait to see if it was fixed. Nevertheless, I consider things as reasonably fixed for now, and I'm going to change this topic to "solved".

Thanks for all your help and your prompt responses, **praseodym**! :KS

---

