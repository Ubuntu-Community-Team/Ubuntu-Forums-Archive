---
title: "Can't connect to wireless networks"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by tinhnghich1993 on 2012-07-05
Hi,

When I connect to a network, it asked for the network password and kept connecting for a while and asked for my password again. Can you help me solve the problem?  I'm using Ubuntu 12.04 64 bit.

---

### Post by msammels on 2012-07-05
Hi. Does your network use DHCP?

---

### Post by tinhnghich1993 on 2012-07-05
I don't know.  Can you show me how to know that?

I can connect to wireless networks in Windows 7 or wired networks in Ubuntu.

---

### Post by msammels on 2012-07-05
OK, let me ask this. In Windows do you need to enter anything other than the wireless password? Also, are you sure you're using the right connection type? Like, is your password WEP/WPA, etc? Remember as well that passwords **are** case sensitive.

---

### Post by tinhnghich1993 on 2012-07-05
I think my password is correct. I checked it many times.

I just tried connecting to a network without password.  After connecting for a while it said
"Wireless network
Disconnected"
and continued to connect.

---

### Post by wildmanne39 on 2012-07-05
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by tinhnghich1993 on 2012-07-05
Here are the results:

```
nam@Nam:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Nam 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
nam@Nam:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1656]
	Kernel driver in use: r8169
--
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
	Kernel driver in use: iwlwifi

```

```
nam@Nam:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse

```

```
nam@Nam:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```

```
nam@Nam:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
nam@Nam:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               332672  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
hp_accel               25976  0 
fglrx                3263966  134 
psmouse                87692  0 
serio_raw              13211  0 
i915                  468737  2 
wmi                    19256  1 hp_wmi
rts_pstor             445196  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mac_hid                13253  0 
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

```

---

### Post by wildmanne39 on 2012-07-05
Hi, it says you need to turn your wireless on, so it is usually done with a key combination or physical switch, then run these commands one line at a time:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Thanks

---

### Post by tinhnghich1993 on 2012-07-06
Oh I forgot to turn wireless on before running the commands.

I tried turning it on and run the 3 commands but didn't solve the problem.  Is there any other solution for it? Thanks.

---

### Post by wildmanne39 on 2012-07-06
Hi, please post the contents of:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
post the output of:
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

### Post by tinhnghich1993 on 2012-07-06
The contents of the file in the first command: 
options iwlwifi 11n_disable=1

The output of the second command:
```
nam@Nam:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -
Jul  6 21:53:58 Nam wpa_supplicant[1074]: Trying to authenticate with 00:21:55:4f:01:d0 (SSID='RCGuests' freq=2462 MHz)
Jul  6 21:53:58 Nam kernel: [  257.746741] wlan0: direct probe to 00:21:55:4f:01:d0 (try 1/3)
Jul  6 21:53:58 Nam kernel: [  257.943521] wlan0: direct probe to 00:21:55:4f:01:d0 (try 2/3)
Jul  6 21:53:58 Nam kernel: [  258.143416] wlan0: direct probe to 00:21:55:4f:01:d0 (try 3/3)
Jul  6 21:53:58 Nam kernel: [  258.343302] wlan0: direct probe to 00:21:55:4f:01:d0 timed out
Jul  6 21:54:04 Nam wpa_supplicant[1074]: Trying to authenticate with 00:21:55:4f:01:d0 (SSID='RCGuests' freq=2462 MHz)
Jul  6 21:54:04 Nam kernel: [  263.908100] wlan0: direct probe to 00:21:55:4f:01:d0 (try 1/3)
Jul  6 21:54:04 Nam kernel: [  264.104266] wlan0: direct probe to 00:21:55:4f:01:d0 (try 2/3)
Jul  6 21:54:04 Nam kernel: [  264.304162] wlan0: direct probe to 00:21:55:4f:01:d0 (try 3/3)
Jul  6 21:54:04 Nam kernel: [  264.504090] wlan0: direct probe to 00:21:55:4f:01:d0 timed out

```

---

### Post by wildmanne39 on 2012-07-07
Hi, what does this say now:
```
nm-tool
rfkill list all
```
Is the information that you posted all that was shown with this command:
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n55
```
is should have shown 55 lines, please try it again.
Thanks

---

### Post by Zudey on 2012-07-07
I'm Sorry, I'm new on this forum, I want some help because I installed Ubuntu 12.04 in a Intel Centrino Duo Laptop but I only can connect to Internet using a wired connection and I cannot connect it to a wireless,[SIZE=2] **[COLOR=Red]"WIRELESS NETWORKS DEVICE  NOT READY"  [/COLOR]**[/SIZE][COLOR=Black]That is what appears on my screen [/COLOR]in the section of Connections upper right  Please I need your HELP!!

---

### Post by wildmanne39 on 2012-07-07
Hi Zudey, please start a new thread with a descriptive title it will make it easier for you to get the help you need and the person who started this thread to get the help they need.
Thanks

---

### Post by tinhnghich1993 on 2012-07-07
Here are the results:

```
nam@Nam:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0  [jimnetwork] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (need authentication)
  Default:           no
  HW Address:        8C:A9:82:AB:C2:1C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    jimnetwork:      Infra, 20:AA:4B:4A:FB:AF, Freq 2452 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        10:1F:74:10:63:DC

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

```
nam@Nam:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no	
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

```
nam@Nam:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n55
[sudo] password for nam: 
Jul  7 21:54:24 Nam NetworkManager[987]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul  7 21:54:24 Nam NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  7 21:54:38 Nam NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  7 21:54:38 Nam NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul  7 21:54:38 Nam NetworkManager[987]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul  7 21:54:38 Nam NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul  7 21:54:38 Nam NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul  7 21:54:38 Nam NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul  7 21:54:38 Nam NetworkManager[987]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  7 21:54:38 Nam NetworkManager[987]: <info> Activation (wlan0/wireless): connection 'jimnetwork' has security, and secrets exist.  No new secrets needed.
Jul  7 21:54:38 Nam NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  7 21:54:38 Nam NetworkManager[987]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul  7 21:54:45 Nam wpa_supplicant[1327]: Trying to authenticate with 20:aa:4b:4a:fb:af (SSID='jimnetwork' freq=2452 MHz)
Jul  7 21:54:45 Nam NetworkManager[987]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul  7 21:54:45 Nam kernel: [  126.754490] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 1/3)
Jul  7 21:54:45 Nam kernel: [  126.950600] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 2/3)
Jul  7 21:54:45 Nam kernel: [  127.150501] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 3/3)
Jul  7 21:54:45 Nam kernel: [  127.350388] wlan0: direct probe to 20:aa:4b:4a:fb:af timed out
Jul  7 21:54:51 Nam wpa_supplicant[1327]: Trying to authenticate with 20:aa:4b:4a:fb:af (SSID='jimnetwork' freq=2452 MHz)
Jul  7 21:54:51 Nam kernel: [  133.072905] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 1/3)
Jul  7 21:54:51 Nam kernel: [  133.271317] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 2/3)
Jul  7 21:54:51 Nam kernel: [  133.471205] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 3/3)
Jul  7 21:54:52 Nam kernel: [  133.671099] wlan0: direct probe to 20:aa:4b:4a:fb:af timed out
Jul  7 21:55:03 Nam wpa_supplicant[1327]: Trying to authenticate with 20:aa:4b:4a:fb:af (SSID='jimnetwork' freq=2452 MHz)
Jul  7 21:55:03 Nam kernel: [  145.083485] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 1/3)
Jul  7 21:55:03 Nam kernel: [  145.281207] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 2/3)
Jul  7 21:55:03 Nam kernel: [  145.481093] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 3/3)
Jul  7 21:55:04 Nam kernel: [  145.680997] wlan0: direct probe to 20:aa:4b:4a:fb:af timed out
Jul  7 21:55:15 Nam wpa_supplicant[1327]: Trying to authenticate with 20:aa:4b:4a:fb:af (SSID='jimnetwork' freq=2452 MHz)
Jul  7 21:55:15 Nam kernel: [  157.048963] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 1/3)
Jul  7 21:55:15 Nam kernel: [  157.247002] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 2/3)
Jul  7 21:55:15 Nam kernel: [  157.446900] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 3/3)
Jul  7 21:55:15 Nam kernel: [  157.646795] wlan0: direct probe to 20:aa:4b:4a:fb:af timed out
Jul  7 21:55:18 Nam kernel: [  159.657740] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul  7 21:55:23 Nam wpa_supplicant[1327]: Trying to authenticate with 20:aa:4b:4a:fb:af (SSID='jimnetwork' freq=2452 MHz)
Jul  7 21:55:23 Nam kernel: [  165.339545] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 1/3)
Jul  7 21:55:23 Nam kernel: [  165.538806] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 2/3)
Jul  7 21:55:24 Nam kernel: [  165.742688] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 3/3)
Jul  7 21:55:24 Nam kernel: [  165.942599] wlan0: direct probe to 20:aa:4b:4a:fb:af timed out
Jul  7 21:55:26 Nam kernel: [  167.949524] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul  7 21:55:31 Nam wpa_supplicant[1327]: Trying to authenticate with 20:aa:4b:4a:fb:af (SSID='jimnetwork' freq=2452 MHz)
Jul  7 21:55:31 Nam kernel: [  173.629656] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 1/3)
Jul  7 21:55:32 Nam kernel: [  173.826542] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 2/3)
Jul  7 21:55:32 Nam kernel: [  174.026471] wlan0: direct probe to 20:aa:4b:4a:fb:af (try 3/3)
Jul  7 21:55:32 Nam kernel: [  174.226353] wlan0: direct probe to 20:aa:4b:4a:fb:af timed out
Jul  7 21:55:34 Nam kernel: [  176.233316] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul  7 21:55:39 Nam NetworkManager[987]: <warn> Activation (wlan0/wireless): association took too long.
Jul  7 21:55:39 Nam NetworkManager[987]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul  7 21:55:39 Nam NetworkManager[987]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul  7 21:55:39 Nam NetworkManager[987]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jul  7 21:57:39 Nam NetworkManager[987]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jul  7 21:57:39 Nam NetworkManager[987]: <warn> Activation (wlan0) failed for access point (jimnetwork)
Jul  7 21:57:39 Nam NetworkManager[987]: <warn> Activation (wlan0) failed.
Jul  7 21:57:39 Nam NetworkManager[987]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jul  7 21:57:39 Nam NetworkManager[987]: <info> (wlan0): deactivating device (reason 'none') [0]

```
Thanks.

---

### Post by wildmanne39 on 2012-07-07
Hi, go into your router settings and change encryption to just wpa2 if possible it works best, then show:
```
nm-tool
```
if it does not connect.
Thanks

---

### Post by tinhnghich1993 on 2012-07-07
This is not my network so I can't change anything on it.  It is the third network I have tried.  I tried 1 network without password and had the same problem too. I don't think it is because of the network or password.

Here is the result:

```
nam@Nam:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0  [jimnetwork] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (need authentication)
  Default:           no
  HW Address:        8C:A9:82:AB:C2:1C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    jimnetwork:      Infra, 20:AA:4B:4A:FB:AF, Freq 2452 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        10:1F:74:10:63:DC

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```
Thanks.

---

### Post by wildmanne39 on 2012-07-08
Hi, we need to work on only one network and please do not try other suggestions while we are working on this it will make getting it to work a lot harder or impossible.

So you need to run these commands again from the network that you can change settings on and that you are primarily going to be using. 
```
iwconfig
rfkill list all
lsmod
nm-tool
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

### Post by tinhnghich1993 on 2012-07-12
Here are the results. The network name is mxn:

```
nam@Nam:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


```

```
nam@Nam:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```


```
nam@Nam:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
iwlwifi               332672  0 
snd_rawmidi            30748  1 snd_seq_midi
mac80211              506816  1 iwlwifi
psmouse                87692  0 
serio_raw              13211  0 
cfg80211              205544  2 iwlwifi,mac80211
rts_pstor             445196  0 
uvcvideo               72627  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
fglrx                3263966  126 
i915                  468737  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         46978  1 i915
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               25976  0 
mac_hid                13253  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 hp_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 

```

```
nam@Nam:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [mxn] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (need authentication)
  Default:           no
  HW Address:        8C:A9:82:AB:C2:1C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    AnhNgoc:         Infra, 00:D0:41:CA:02:9A, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    Rad Office:      Infra, 00:22:6B:82:F5:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    mxn:             Infra, 00:24:01:AE:DB:9E, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        10:1F:74:10:63:DC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



```

```
nam@Nam:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n55
[sudo] password for nam: 
Jul 12 07:42:07 Nam kernel: [ 1622.146533] wlan0: direct probe to 00:24:01:ae:db:9e timed out
Jul 12 07:42:09 Nam kernel: [ 1624.185460] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul 12 07:42:20 Nam wpa_supplicant[1196]: Trying to authenticate with 00:24:01:ae:db:9e (SSID='mxn' freq=2437 MHz)
Jul 12 07:42:20 Nam kernel: [ 1635.469541] wlan0: direct probe to 00:24:01:ae:db:9e (try 1/3)
Jul 12 07:42:21 Nam kernel: [ 1635.667580] wlan0: direct probe to 00:24:01:ae:db:9e (try 2/3)
Jul 12 07:42:21 Nam kernel: [ 1635.867485] wlan0: direct probe to 00:24:01:ae:db:9e (try 3/3)
Jul 12 07:42:21 Nam kernel: [ 1636.067542] wlan0: direct probe to 00:24:01:ae:db:9e timed out
Jul 12 07:42:32 Nam wpa_supplicant[1196]: Trying to authenticate with 00:24:01:ae:db:9e (SSID='mxn' freq=2437 MHz)
Jul 12 07:42:32 Nam kernel: [ 1647.439312] wlan0: direct probe to 00:24:01:ae:db:9e (try 1/3)
Jul 12 07:42:33 Nam kernel: [ 1647.637443] wlan0: direct probe to 00:24:01:ae:db:9e (try 2/3)
Jul 12 07:42:33 Nam kernel: [ 1647.837337] wlan0: direct probe to 00:24:01:ae:db:9e (try 3/3)
Jul 12 07:42:33 Nam kernel: [ 1648.037360] wlan0: direct probe to 00:24:01:ae:db:9e timed out
Jul 12 07:42:34 Nam NetworkManager[979]: <warn> Activation (wlan0/wireless): association took too long.
Jul 12 07:42:34 Nam NetworkManager[979]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 12 07:42:34 Nam NetworkManager[979]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul 12 07:42:34 Nam NetworkManager[979]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jul 12 07:42:35 Nam kernel: [ 1650.044180] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul 12 07:42:39 Nam NetworkManager[979]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 12 07:42:39 Nam NetworkManager[979]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 12 07:42:39 Nam NetworkManager[979]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 12 07:42:39 Nam NetworkManager[979]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 12 07:42:39 Nam NetworkManager[979]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 12 07:42:39 Nam NetworkManager[979]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 12 07:42:39 Nam NetworkManager[979]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 12 07:42:39 Nam NetworkManager[979]: <info> Activation (wlan0/wireless): connection 'mxn' has security, and secrets exist.  No new secrets needed.
Jul 12 07:42:39 Nam NetworkManager[979]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 12 07:42:40 Nam NetworkManager[979]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 12 07:42:52 Nam wpa_supplicant[1196]: Trying to authenticate with 00:24:01:ae:db:9e (SSID='mxn' freq=2437 MHz)
Jul 12 07:42:52 Nam NetworkManager[979]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 12 07:42:52 Nam kernel: [ 1667.090772] wlan0: direct probe to 00:24:01:ae:db:9e (try 1/3)
Jul 12 07:42:52 Nam kernel: [ 1667.287413] wlan0: direct probe to 00:24:01:ae:db:9e (try 2/3)
Jul 12 07:42:52 Nam kernel: [ 1667.487303] wlan0: direct probe to 00:24:01:ae:db:9e (try 3/3)
Jul 12 07:42:53 Nam kernel: [ 1667.687207] wlan0: direct probe to 00:24:01:ae:db:9e timed out
Jul 12 07:42:55 Nam kernel: [ 1669.718164] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul 12 07:43:00 Nam wpa_supplicant[1196]: Trying to authenticate with 00:24:01:ae:db:9e (SSID='mxn' freq=2437 MHz)
Jul 12 07:43:00 Nam kernel: [ 1675.401922] wlan0: direct probe to 00:24:01:ae:db:9e (try 1/3)
Jul 12 07:43:01 Nam kernel: [ 1675.599108] wlan0: direct probe to 00:24:01:ae:db:9e (try 2/3)
Jul 12 07:43:01 Nam kernel: [ 1675.798970] wlan0: direct probe to 00:24:01:ae:db:9e (try 3/3)
Jul 12 07:43:01 Nam kernel: [ 1675.998870] wlan0: direct probe to 00:24:01:ae:db:9e timed out
Jul 12 07:43:07 Nam wpa_supplicant[1196]: Trying to authenticate with 00:24:01:ae:db:9e (SSID='mxn' freq=2437 MHz)
Jul 12 07:43:07 Nam kernel: [ 1681.734516] wlan0: direct probe to 00:24:01:ae:db:9e (try 1/3)
Jul 12 07:43:07 Nam kernel: [ 1681.931855] wlan0: direct probe to 00:24:01:ae:db:9e (try 2/3)
Jul 12 07:43:07 Nam kernel: [ 1682.131751] wlan0: direct probe to 00:24:01:ae:db:9e (try 3/3)
Jul 12 07:43:07 Nam kernel: [ 1682.331647] wlan0: direct probe to 00:24:01:ae:db:9e timed out
Jul 12 07:43:09 Nam kernel: [ 1684.366639] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul 12 07:43:21 Nam wpa_supplicant[1196]: Trying to authenticate with 00:24:01:ae:db:9e (SSID='mxn' freq=2437 MHz)
Jul 12 07:43:21 Nam kernel: [ 1695.704291] wlan0: direct probe to 00:24:01:ae:db:9e (try 1/3)
Jul 12 07:43:21 Nam kernel: [ 1695.904662] wlan0: direct probe to 00:24:01:ae:db:9e (try 2/3)
Jul 12 07:43:21 Nam kernel: [ 1696.104578] wlan0: direct probe to 00:24:01:ae:db:9e (try 3/3)
Jul 12 07:43:21 Nam kernel: [ 1696.308540] wlan0: direct probe to 00:24:01:ae:db:9e timed out
Jul 12 07:43:23 Nam kernel: [ 1698.339474] iwlwifi 0000:0d:00.0: fail to flush all tx fifo queues
Jul 12 07:43:39 Nam NetworkManager[979]: <warn> Activation (wlan0/wireless): association took too long.
Jul 12 07:43:39 Nam NetworkManager[979]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 12 07:43:39 Nam NetworkManager[979]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul 12 07:43:39 Nam NetworkManager[979]: <info> (wlan0): supplicant interface state: authenticating -> disconnected

```

---

### Post by wildmanne39 on 2012-07-13
Hi, with the error message you have > fail to flush all tx fifo queues I recommend compat wireless in the linux-backports-modules and if that does not work upgrading your kernel, I am travelling right now so I will be slow to reply.
Thanks

---

### Post by tinhnghich1993 on 2012-07-16
Did you mean I should install linux-backports-modules-cw-3.3-3.2.0-26-generic? I tried it but couldn't solve the problem.
Thanks.

---

### Post by tinhnghich1993 on 2012-07-22
Could you please help me?

---

