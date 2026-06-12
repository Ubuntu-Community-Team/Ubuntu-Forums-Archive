---
title: "Can't access Internet"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by Sedgewick on 2011-07-27
I just installed Ubuntu 11.0.4 x64 on my laptop and I can connect to my router. I can access it, even see other computers on the network, but I can't access Internet. Pinging google doesn't work, all I get is a message about an unknown host. 

I am working off a DSL line which works on windows 7 on the same laptop (wifi). However, I need to set up my DNS. If anyone has a solution, I'd be happy to try it out, Ubuntu really seems fun.

---

### Post by wildmanne39 on 2011-07-27
Hi, if this is wireless you are trying to get working please run these commands in a terminal
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
if this is a usb adapter run this also
```
lsusb
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by newbie-user on 2011-07-27
Sounds like you might be having a DNS issue.  Open up network manager, edit your wireless network, and make sure that you haven't manually assigned any DNS servers.  Set your connection to get everything automatically.  All that information should come from your router or local dhcp server.  

Alternatively, if you want to manually specify DNS servers, you can add those within network manager.  Try adding Google's DNS servers, 8.8.8.8 and 8.8.4.4.  After applying the settings, you should be able to resolve hostnames and ping google.

---

### Post by Sedgewick on 2011-07-27
Has for not setting any DNS, I am pretty sure I have to set one, considering I have to set one when I am connecting on Windows.

This is for the 'sudo lshw -C network' command

```
PCI (sysfs)  




SCSI                      
  *-network        
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:cf:72:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=10.43.14.223 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2a00000-d2a0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:05:00.5
       logical name: eth0
       version: 03
       serial: e0:cb:4e:63:78:da
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 memory:d0200000-d0203fff ioport:9100(size=128) ioport:9000(size=256)

```This is for the 'lspci -nn | grep 0280' command:
```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

```for the 'iwconfig' command:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"aerius"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:37:A6:C8:8E:20   
          Bit Rate=65 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:0   Missed beacon:0


```
for the 'rfkill list all' command:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```I must warn that this is not the result typed from my home network, so if there is anything that would've change with the network, it must not be considered. 

Also, I think its fairly obvious its a problem with this specific network since I had absolutely no problem login in from my uni. 

I don't know what you mean by a USB adapter, but I am fairly sure it's not one since the card is integrated and nothing is plugged in. 



EDIT: To Newbie-user,
I initially tried to connect while everything was on auto, to no avail. I then switched it to Automatic (DHCP) addresses only, and entered the 2 DNS my ISP provided (the 2 I have to enter in my windows configuration in order to connect). When that did not work, I went into Manual and entered a local ip that my router would assign (192.168.0.102), the same subnet mask and the gateway of my router while still having the same 2 aforementioned DNS.

Thank you all for your help.

---

### Post by wildmanne39 on 2011-07-27
Hi, run these commands please and post the outcome.
```
lsmod
```
```
dmesg | grep wlan0
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Sedgewick on 2011-07-27
Hi again.I have returned home only to find out that I can't connect to my router anymore (The computer disconnects itself after trying for about 10 seconds).

I ran all the previous command again, from my home this time, and this I found that iwconfig was the only one to change. 

Here is what it shows from my home:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

Then, lsmod:
```
$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_conexant    57511  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30486  1 snd_seq_midi
ath9k                 118238  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              294370  1 ath9k
fglrx                2739144  86 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
psmouse                73535  0 
videodev               82052  1 uvcvideo
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
serio_raw              13166  0 
v4l2_compat_ioctl32    17078  1 videodev
jmb38x_ms              17596  0 
ath                    23773  2 ath9k,ath9k_hw
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               16520  1 jmb38x_ms
cfg80211              178528  3 ath9k,mac80211,ath
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  0 
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
sdhci_pci              13989  0 
jme                    40728  0 
sdhci                  27387  1 sdhci_pci

```

Finally, dmesg:
```
$ dmesg | grep wlan0
[   16.146265] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  313.362762] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  313.364638] wlan0: authenticated
[  313.364666] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  313.368851] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  313.368857] wlan0: associated
[  313.369528] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  327.650760] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  328.779727] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  328.785411] wlan0: authenticated
[  328.802537] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  328.806388] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  328.806396] wlan0: associated
[  332.279543] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  333.389979] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  333.391949] wlan0: authenticated
[  333.391989] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  333.396289] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  333.396296] wlan0: associated
[  354.432862] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  477.886246] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  477.888168] wlan0: authenticated
[  477.888194] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  477.891966] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  477.891970] wlan0: associated
[  499.136695] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  507.785304] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  507.787264] wlan0: authenticated
[  507.787307] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  507.792296] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  507.792301] wlan0: associated
[  526.014087] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  527.126209] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  527.128153] wlan0: authenticated
[  527.128189] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  527.132472] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  527.132479] wlan0: associated
[  548.036910] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  564.232891] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  564.237542] wlan0: authenticated
[  564.237591] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  564.241426] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  564.241437] wlan0: associated
[  585.959719] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  847.853778] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  847.855769] wlan0: authenticated
[  847.855810] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  847.860065] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  847.860069] wlan0: associated
[  869.383761] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[  876.236134] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[  876.238073] wlan0: authenticated
[  876.238116] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[  876.242660] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[  876.242667] wlan0: associated
[  897.326120] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[ 1081.970113] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[ 1081.972503] wlan0: authenticated
[ 1081.972539] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[ 1081.976796] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[ 1081.976801] wlan0: associated
[ 1101.911923] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
[ 1109.561481] wlan0: authenticate with 00:26:5a:f0:f8:98 (try 1)
[ 1109.563412] wlan0: authenticated
[ 1109.563453] wlan0: associate with 00:26:5a:f0:f8:98 (try 1)
[ 1109.567305] wlan0: RX AssocResp from 00:26:5a:f0:f8:98 (capab=0x431 status=0 aid=1)
[ 1109.567312] wlan0: associated
[ 1129.856118] wlan0: deauthenticating from 00:26:5a:f0:f8:98 by local choice (reason=3)
```


Hope it helps you finding whats wrong. 

Thank you very much for your time, I do appreciate it a lot. In fact, I am starting to learn quite a few things about Linux, and that's a good thing, isn't it?

---

### Post by wildmanne39 on 2011-07-27
Hi, have a look at this link I believe it is post 17 where I give instructions on what may fix this problem. Try what the post says and let me know if it fixes your problem.
[http://ubuntuforums.org/showthread.php?p=11093299#post11093299](http://ubuntuforums.org/showthread.php?p=11093299#post11093299)
Thank you

---

### Post by Sedgewick on 2011-07-28
I got it to work!

Actually, I tried reinstalling Ubuntu yesterday. This time, I did it while I had a wired connection to my router, and it worked like a charm. I now have an automatic connection, no need to enter my DNS servers. 


Thank you all for your help.

---

### Post by wildmanne39 on 2011-07-28
Hi, your welcome! glad you got it fixed.

---

