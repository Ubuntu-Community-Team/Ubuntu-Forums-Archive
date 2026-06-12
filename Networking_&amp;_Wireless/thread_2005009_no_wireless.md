---
title: "no wireless"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by Pedroski55 on 2012-06-16
I have never been able to connect to the wireless network at home, not for a year. I wonder if anyone can solve this.
My computer sees my wireless network. Also, wireless works on an open wireless network at school, so I rule out a hardware fault.
NetworkManager says I am connected to ChinaNet-Qqtn. I have entered the wep key printed on the router.

But if I disable dsl, I have no connection. So the wireless is not connected.

Here is some info:
pedro@pedro-bedro:~$ iwconfig
ppp0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ChinaNet-Qqtn"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:87:30:24:7C:21   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

eth0      no wireless extensions.

pedro@pedro-bedro:~$ 

wlan0     Link encap:Ethernet  HWaddr b4:74:9f:77:53:89  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b674:9fff:fe77:5389/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7628 (7.6 KB)  TX bytes:25328 (25.3 KB)

pedro@pedro-bedro:~$ 


Any tips as to how I might get it working??

---

### Post by wildmanne39 on 2012-06-16
Hi, start by taking the dash out of your network name and tell us if that helps.
Thanks

---

### Post by chili555 on 2012-06-16
Your faithful assistant wants to know what wireless card he has; Intel?```
lspci -nn | grep 0280
```

---

### Post by Pedroski55 on 2012-06-16
pedro@pedro-bedro:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
pedro@pedro-bedro:~$ 

What is wrong with a dash?? It was Ubuntu that put the dash there!!

---

### Post by wildmanne39 on 2012-06-16
Hi, a lot of times a connection can be made easier without any special characters.

I recommend that you remove the dash then if it does not connect post the output of:
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
lsmod
nm-tool
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Pedroski55 on 2012-06-16
Excuse my ignorance, but I don't know how to change the computer's name!

pedro@pedro-bedro:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux pedro-bedro 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 athlon i386 GNU/Linux

---

### Post by Pedroski55 on 2012-06-16
pedro@pedro-bedro:~$ iwconfig
ppp0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ChinaNet-Qqtn"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:87:30:24:7C:21   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0

eth0      no wireless extensions.

---

### Post by Pedroski55 on 2012-06-16
pedro@pedro-bedro:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Pedroski55 on 2012-06-16
pedro@pedro-bedro:~$ lsmod
Module                  Size  Used by
snd_hda_codec_conexant    52516  1 
sp5100_tco             13495  0 
joydev                 17393  0 
pppoe                  17513  2 
pppox                  13158  1 pppoe
arc4                   12473  2 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
rtl8192ce              75491  0 
rtl8192c_common        69519  1 rtl8192ce
snd_seq_midi_event     14475  1 snd_seq_midi
rtlwifi                95804  1 rtl8192ce
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
psmouse                72919  0 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
parport_pc             32114  0 
snd                    62064  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
bnep                   17830  2 
shpchp                 32325  0 
k10temp                12990  0 
soundcore              14635  1 snd
cfg80211              178679  2 rtlwifi,mac80211
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
bluetooth             158438  10 rfcomm,bnep
i2c_piix4              13093  0 
toshiba_acpi           18158  0 
radeon                733693  3 
sparse_keymap          13658  1 toshiba_acpi
video                  19068  0 
wmi                    18744  1 toshiba_acpi
mac_hid                13077  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0 
ums_realtek            17920  0 
uas                    17828  0 
usb_storage            39646  1 ums_realtek
pedro@pedro-bedro:~$

---

### Post by Pedroski55 on 2012-06-16
pedro@pedro-bedro:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ChinaNet-Qqtn] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        B4:74:9F:77:53:89

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ChinaNet-Qqtn:  Infra, 30:87:30:24:7C:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA
    iTV-Qqtn:        Infra, 30:87:30:24:7C:22, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0  [DSL connection 1] ---------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:26:6C:B1:AE:88

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         180.110.186.92
    Prefix:          32 (255.255.255.255)
    Gateway:         58.213.239.19

    DNS:             218.2.135.1
    DNS:             61.147.37.1

---

### Post by Pedroski55 on 2012-06-16
Correct me if I am wrong, but isn't the problem just the wireless dns set to DNS:             192.168.1.1

Do you think, if I change that it will work? If so, how to do that??

---

### Post by wildmanne39 on 2012-06-16
Hi, click on the internet icon in the top right corner of the screen then edit connections>wireless>change SSID.

Copy and paste for accuracy the following:

```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```

A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```

Proofread, save and close gedit, then reboot.
Thanks

Also please put all information asked for in one post using code tags by hitting the # sign in the window that you type into for future reference.
Thanks

---

### Post by Pedroski55 on 2012-06-16
Sorry, but I am a bit confused here.

Step 1 : Edit Connections > Wireless > ChinaNet-Qqtn

Step 2: Paste 'gksudo gedit /etc/modprobe.d/rtl8192ce.conf' in the field SSID ?? I don't think you mean that!

I ran gksudo gedit /etc/modprobe.d/rtl8192ce.conf in a terminal, and entered the code you suggested 'options rtl8192ce swenc=1'

Can you please clarify??

---

### Post by wildmanne39 on 2012-06-16
Hi, where it says ssid just take the dash out of the network name then close network settings.

Then paste the second command in the terminal and small window will open type your user password and you will not see it as you type so when you are done hit enter and bigger window will open paste the line that I said to paste in my last post into the file, [COLOR="black"][COLOR="Red"]Proofread, save and close gedit, then reboot.[/COLOR][/COLOR]
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
Also please post the contents of this file after you reboot:

Thanks

---

### Post by Pedroski55 on 2012-06-17
Didn't do the job. Still can't connect. Are you sure it's not the dns??

Here the contents of the file:    options rtl8192ce swenc=1

Also, the name ChinaNet-Qqtn must be coming from the wifi router. If I change the SSID field and remove the - my computer still only sees ChinaNet-Qqtn

---

### Post by wildmanne39 on 2012-06-17
Hi go back into the network settings and make all of your settings match the screenshots settings that I attach and that will change the dns server to google which works great, and a few other things.

Then open your browser and type 192.168.0.1 and hopefully that will open your settings to your router and take out the dash in your SSID you will also need to take it out of network manaqer again, then look for security settings and change your encryption to just wpa2 not wpa or mixed or wep if you have that setting, then change the N speed to just b/g speed because this driver is having issues with N speed.
Thanks

---

### Post by Pedroski55 on 2012-06-17
can't access 192.168.0.1it times out. Have to leave this for today, I'll try again tomorrow, thanks very much for trying!!

---

### Post by wildmanne39 on 2012-06-17
Hi, make sure you have a wired connection to your router then try, also the numbers may be a little different for your router if you find those do not work look at your documentation to find the numbers that do.
Thanks

---

### Post by Pedroski55 on 2012-06-18
Today's attempt: I undid the things you told me to do, now I can access 192.168.1.1, which is the useradmin of my router, as it says on the back of it. Trouble is it is in Chinese, so I will have to wait until my girlfriend comes, as my Chinese is not so good.

You suggest we change the SSID to something  without a -   ???? I'll try that. I still can't connect to the net via wireless. I wonder what the trouble might be??

---

### Post by wildmanne39 on 2012-06-18
Hi, what changes did you undo? 

I would not think that the wep key is printed on the router, it should generate a key when you set it up or you can generate a new key but you should try wpa2 only not wep or wpa or wpa/wpa2 if possible it will work best.
Thanks

---

### Post by Pedroski55 on 2012-06-18
On the back of the router it says: WPA-PSK   jsfg3zpb
Also, this key works if I start Windows. However, when I start Windows, which is not often, I also so have to make the dsl connection, or pretend to, even if the cable is not plugged in. Only then do you get a wireless connection. Why is that?

Any more tips?? I would really like to know what's wrong here. Something up with NetworkManager maybe?

---

### Post by wildmanne39 on 2012-06-18
Hi, we will check a few more things but some routers just will not work with linux.

Please post the output of:
```
nm-tool
sudo iwlist scan
iwlist chan
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/resolv.conf
lsmod | grep rtl
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by Pedroski55 on 2012-06-18
Here is a pic from 192.168.1.1

---

### Post by wildmanne39 on 2012-06-18
Hi, from what I could read it looked good except I for the dash in the network name.
Thanks

---

### Post by Pedroski55 on 2012-06-18
Sorry, this was in answer to your question 'what did you get rid of', I didn't see it this morning.
I got rid of the wired connections ipv4 DNS setting 8.8.8.8

Have to go to work soon, I will try out your suggestions and post later. Thanks!

---

### Post by wildmanne39 on 2012-06-18
Hi, okay please post the information that I asked for in post 22.
Thanks

---

### Post by Pedroski55 on 2012-06-19
I'm thinking that you need this info from my house, but I have time at the mo. Also, if you wouldn't mind, I have a bigger problem, I will post another thread, and send you a link in a pm. 
Ok, I am at school, connected to an open wireless network jiao202 The ouptut follows:

pedro@pedro-bedro:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [room101] ------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:26:6C:B1:AE:88

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         58.192.76.45
    Prefix:          24 (255.255.255.0)
    Gateway:         58.192.76.254

    DNS:             58.192.72.2


- Device: wlan0  [jiaoA 202] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        B4:74:9F:77:53:89

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *jiaoA 202:      Infra, 00:0F:E2:4E:62:28, Freq 2412 MHz, Rate 11 Mb/s, Strength 61

  IPv4 Settings:
    Address:         192.168.1.22
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.250

    DNS:             192.168.1.250


pedro@pedro-bedro:~$

---

### Post by Pedroski55 on 2012-06-19
pedro@pedro-bedro:~$ sudo iwlist scan
[sudo] password for pedro: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:E2:4E:62:28
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"jiaoA 202"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b727f9094
                    Extra: Last beacon: 792ms ago
                    IE: Unknown: 00096A69616F4120323032
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C

eth0      Interface doesn't support scanning.

pedro@pedro-bedro:~$ ^C

---

### Post by Pedroski55 on 2012-06-19
I'm sorry, you said post it all in one thingy, but I thought it might be easier to check each individual command this way.
pedro@pedro-bedro:~$ iwlist chan
lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency=2.412 GHz (Channel 1)

eth0      no frequency information.

pedro@pedro-bedro:~$

---

### Post by Pedroski55 on 2012-06-19
pedro@pedro-bedro:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
pedro@pedro-bedro:~$

---

### Post by Pedroski55 on 2012-06-19
pedro@pedro-bedro:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
pedro@pedro-bedro:~$

---

### Post by Pedroski55 on 2012-06-19
pedro@pedro-bedro:~$ lsmod | grep rtl
rtl8192ce              75491  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95804  1 rtl8192ce
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              178679  2 rtlwifi,mac80211
pedro@pedro-bedro:~$

---

### Post by Pedroski55 on 2012-06-19
pedro@pedro-bedro:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n75
Jun 19 12:06:06 pedro-bedro kernel: [   12.067618] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 19 12:06:06 pedro-bedro kernel: [   12.067634] rtl8192ce 0000:02:00.0: setting latency timer to 64
Jun 19 12:06:06 pedro-bedro kernel: [   12.741537] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Jun 19 12:06:06 pedro-bedro kernel: [   12.744122] rtlwifi: wireless switch is on
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <info> (wlan0): using nl80211 for WiFi device control
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192ce' ifindex: 3)
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <info> (wlan0): now managed
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 12:06:06 pedro-bedro NetworkManager[761]: <info> (wlan0): bringing up device.
Jun 19 12:06:06 pedro-bedro kernel: [   12.807651] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
Jun 19 12:06:07 pedro-bedro NetworkManager[761]: <info> (wlan0): preparing device.
Jun 19 12:06:07 pedro-bedro NetworkManager[761]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 19 12:06:07 pedro-bedro kernel: [   13.150669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 12:06:07 pedro-bedro dbus[538]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jun 19 12:06:07 pedro-bedro kernel: [   13.152391] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 12:06:07 pedro-bedro dbus[538]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jun 19 12:06:07 pedro-bedro NetworkManager[761]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlan0, iface: wlan0)
Jun 19 12:06:07 pedro-bedro NetworkManager[761]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 19 12:06:07 pedro-bedro NetworkManager[761]: <info> wpa_supplicant started
Jun 19 12:06:07 pedro-bedro NetworkManager[761]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 19 12:06:07 pedro-bedro NetworkManager[761]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 19 12:06:07 pedro-bedro kernel: [   13.317619] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
Jun 19 12:06:07 pedro-bedro NetworkManager[761]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) starting connection 'jiaoA 202'
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0/wireless): connection 'jiaoA 202' requires no security.  No secrets needed.
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 12:06:09 pedro-bedro NetworkManager[761]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun 19 12:06:10 pedro-bedro wpa_supplicant[907]: Trying to authenticate with 00:0f:e2:4e:62:28 (SSID='jiaoA 202' freq=2412 MHz)
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 19 12:06:10 pedro-bedro wpa_supplicant[907]: Trying to associate with 00:0f:e2:4e:62:28 (SSID='jiaoA 202' freq=2412 MHz)
Jun 19 12:06:10 pedro-bedro kernel: [   16.385999] wlan0: authenticate with 00:0f:e2:4e:62:28 (try 1)
Jun 19 12:06:10 pedro-bedro kernel: [   16.387752] wlan0: authenticated
Jun 19 12:06:10 pedro-bedro kernel: [   16.388538] wlan0: associate with 00:0f:e2:4e:62:28 (try 1)
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 19 12:06:10 pedro-bedro kernel: [   16.398286] wlan0: RX AssocResp from 00:0f:e2:4e:62:28 (capab=0x401 status=0 aid=4)
Jun 19 12:06:10 pedro-bedro kernel: [   16.398296] wlan0: associated
Jun 19 12:06:10 pedro-bedro kernel: [   16.399396] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 19 12:06:10 pedro-bedro wpa_supplicant[907]: Associated with 00:0f:e2:4e:62:28
Jun 19 12:06:10 pedro-bedro wpa_supplicant[907]: CTRL-EVENT-CONNECTED - Connection to 00:0f:e2:4e:62:28 completed (auth) [id=0 id_str=]
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> (wlan0): supplicant interface state: associating -> completed
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'jiaoA 202'.
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 19 12:06:10 pedro-bedro NetworkManager[761]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 19 12:06:10 pedro-bedro dhclient: Listening on LPF/wlan0/b4:74:9f:77:53:89
Jun 19 12:06:10 pedro-bedro dhclient: Sending on   LPF/wlan0/b4:74:9f:77:53:89
Jun 19 12:06:10 pedro-bedro dhclient: DHCPREQUEST of 192.168.1.22 on wlan0 to 255.255.255.255 port 67
Jun 19 12:06:13 pedro-bedro dhclient: DHCPREQUEST of 192.168.1.22 on wlan0 to 255.255.255.255 port 67
Jun 19 12:06:13 pedro-bedro NetworkManager[761]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 19 12:06:13 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 19 12:06:13 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 19 12:06:14 pedro-bedro NetworkManager[761]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 19 12:06:15 pedro-bedro NetworkManager[761]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 19 12:06:15 pedro-bedro NetworkManager[761]: <info> Policy set 'jiaoA 202' (wlan0) as default for IPv4 routing and DNS.
Jun 19 12:06:15 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) successful, device activated.
Jun 19 12:06:15 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 19 12:06:21 pedro-bedro kernel: [   27.160035] wlan0: no IPv6 routers present
Jun 19 12:06:30 pedro-bedro NetworkManager[761]: <info> (wlan0): IP6 addrconf timed out or failed.
Jun 19 12:06:30 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 19 12:06:30 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 19 12:06:30 pedro-bedro NetworkManager[761]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
pedro@pedro-bedro:~$

---

### Post by wildmanne39 on 2012-06-19
Hi, as I mentioned in my 5th post this is the method for posting information in a thread, post the outcome here by clicking on new reply and click # then paste the information between the brackets, and put it all in one page.

I would disable the encryption at home and see if you can connect, see if it will let you remove the dash in your router settings and network manager.
Thank you

---

### Post by Pedroski55 on 2012-06-22
Hi again! I opened 192.168.1.1 entered the useradmin name and password. I tried to change ChinaNet-Qqtn to remove the -

But: The system comes back and says, all ssid must start with   ChinaNet-    It will not accept any , or any other ssid!

That was not what I expected!

Also, I installed Ubuntu on a friend's laptop, and she also cannot access the wireless network. So the problem does not lie just with my laptop. We know it works, as Windows can access the wireless, no problem. The thing with windows is, you have to make the dsl connection, even if the cable is not plugged in, only then will the wireless work. Strange huh??

Here's the thing: if I disable wireless in Network Manager, I cannot connect to 192.168.1.1, presumably because it is not assigned?? The router is up and running.
Why can't I connect to it? I presume because, in the dsl connection, the dns is 218.2.135.1 That nameserver can't find 192.168.1.1, so it gives up. 
If I enable wireless, it has dns 192.168.1.1 , and somehow finds itself!
Any suggestions?

I tried ping, first with wireless disabled, then enabled.
pedro@pedro-bedro:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4032ms

pedro@pedro-bedro:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=5.61 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2.42 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=2.03 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=2.10 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=2.22 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 2.034/2.879/5.616/1.376 ms

---

### Post by wildmanne39 on 2012-06-22
Hi, I am afraid my only other suggestion is to try wicd.

[COLOR="Red"]You must install wicd before you remove network manager:[/COLOR]

Please do:
```
sudo apt-get install wicd
```
Then:
```
sudo apt-get purge network-manager network-manager-gnome
```

[COLOR="Red"]Make sure you have a wired connection in case you need it.[/COLOR]
You have to setup your wireless manually I believe, set dhcp needs to be dhclient, dns server and IPv6 like in the screenshots earlier in this thread and see if that helps, because wicd handles encryption better then network manager.
Thanks

---

