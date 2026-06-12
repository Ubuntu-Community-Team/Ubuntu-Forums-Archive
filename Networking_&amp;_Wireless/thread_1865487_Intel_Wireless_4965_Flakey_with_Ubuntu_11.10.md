---
title: "Intel Wireless 4965 Flakey with Ubuntu 11.10"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by Smylers on 2011-10-20
Hi. I'm also having wireless problems with 11.10. Often it won't connect at all, and when it does it's very slow and drops the connection after a short time. It worked fine as Oneiric Alpha 3 (which was a new install) through to and including Beta 2; it was only upgrading from Beta 2 to the final release which broke things.

This is my wireless card (as reported by lspci):

> 0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
        Subsystem: Intel Corporation Device [8086:1121]
        Kernel driver in use: iwl4965

Here's the interface (as reported by iwconfig):

> wlan0     IEEE 802.11abgn  ESSID:off/any

Here are the syslog entries of a failed connection:

> NetworkManager[671]: <info> Activation (wlan0) starting connection 'number 17 1'
NetworkManager[671]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
NetworkManager[671]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager[671]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager[671]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager[671]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager[671]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager[671]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
NetworkManager[671]: <info> Activation (wlan0/wireless): connection 'number 17 1' has security, and secrets exist.  No new secrets needed.
NetworkManager[671]: <info> Config: added 'ssid' value 'number 17'
NetworkManager[671]: <info> Config: added 'scan_ssid' value '1'
NetworkManager[671]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
NetworkManager[671]: <info> Config: added 'auth_alg' value 'OPEN'
NetworkManager[671]: <info> Config: added 'psk' value '<omitted>'
NetworkManager[671]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager[671]: <info> Config: set interface ap_scan to 1
NetworkManager[671]: <info> (wlan0): supplicant interface state: disconnected -> scanning
wpa_supplicant[951]: Trying to authenticate with 00:24:17:e0:a9:3b (SSID='number 17' freq=2442 MHz)
kernel: [ 7220.384125] wlan0: authenticate with 00:24:17:e0:a9:3b (try 1)
NetworkManager[671]: <info> (wlan0): supplicant interface state: scanning -> authenticating
kernel: [ 7220.584122] wlan0: authenticate with 00:24:17:e0:a9:3b (try 2)
kernel: [ 7220.784107] wlan0: authenticate with 00:24:17:e0:a9:3b (try 3)
kernel: [ 7220.984093] wlan0: authentication with 00:24:17:e0:a9:3b timed out

rfkill lists no blocks.

iwlist scan sometimes reports ‘No scan results’ for wlan0, and sometimes lists a few access points. NetworkManager always lists them.

/etc/modprobe.d/ doesn't contain any files starting iw*.

Things I've tried which don't seem to work:

[LIST]
[*] disabling IPv6 -- following the instructions on [http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal)
[*] reconfiguring my router to use WEP instead of WPA/WPA2
[*] modprobe iwl4965 11n_disable=1
[*] modprobe iwl4965 nohwcrypt=1
[*] iwconfig wlan0 power off
[/LIST]

Thanks for any help you can offer.

---

### Post by shubham1 on 2011-10-20
try to use other net connectors wicd etc

---

### Post by Smylers on 2011-10-20
> **shubham1 said:**
> try to use other net connectors wicd etc

Thanks for the suggestion. Unfortunately it doesn't seem to help. Wicd complains that the password is wrong (it isn't), with similar syslog entries to using NetworkManager, trying 3 times to authenticate then timing out. On a network without a password Wicd reports not being able to get an IP address.

But I'm not familiar with Wicd, so perhaps there's something I'm missing with it. I installed [FONT="Courier New"]wicd[/FONT] and [FONT="Courier New"]wicd-gtk[/FONT] then ran [FONT="Courier New"]wicd-gtk -n[/FONT], scanned for networks, used ‘Properties’ to specify the WPA password, then pressed ‘Connect’. Anything else I should be doing?

Or has anybody got any other suggestions?

---

### Post by jawilljr on 2011-10-21
I just did a clean install of Oneiric 11.10... guess what? My iwl4965 is working flawlessly... no problems.


Here is my lspci -nnk:

```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
	Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
	Kernel driver in use: iwl4965
	Kernel modules: iwl4965
```

Jerry

---

### Post by F0r90tteN on 2011-10-24
got the same problem with intel 4965ag card.

@jawilljr, were you able to connect to wireless during the clean install? when i tried the clean install, i found out that i couldn't connect to the wireless in live cd also so i didn't go on with the install...

---

### Post by jawilljr on 2011-10-24
> **F0r90tteN said:**
> got the same problem with intel 4965ag card.

@jawilljr, were you able to connect to wireless during the clean install? when i tried the clean install, i found out that i couldn't connect to the wireless in live cd also so i didn't go on with the install...

Yes...

Here is my iwconfig

```
wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  [color=red]Frequency:5.18 GHz[/color]  Access Point: C0:C1:C0:38:4F:32   
          [color=red]Bit Rate=144.4 Mb/s[/color]   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:95  Invalid misc:42   Missed beacon:0
```

And below is my iperf test:

```
jawilljr@jawilljr:~$ iperf -c kjawhtpc -r
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to kjawhtpc, TCP port 5001
TCP window size: 78.9 KByte (default)
------------------------------------------------------------
[  5] local 192.168.1.7 port 45551 connected with 192.168.1.3 port 5001
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-10.0 sec  99.5 MBytes  83.4 Mbits/sec
[  4] local 192.168.1.7 port 5001 connected with 192.168.1.3 port 58180
[  4]  0.0-10.0 sec   115 MBytes  95.9 Mbits/sec
```

Below is "cat /etc/lsb-release

```
jawilljr@jawilljr:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
```

And "sudo lshw -C network":

```
jawilljr@jawilljr:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:b5:98:8f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.0.0-12-generic firmware=228.61.2.24 ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f6000000-f6001fff
```

Could it be better... yes, but I am happy.

Jerry

---

### Post by F0r90tteN on 2011-10-26
Ok, update on the problem...

When I brought my laptop to office this morning (where i did the upgrade from 11.04 to 11.10) i was able to connect to both two of wireless networks in the office! (one access point, Zyxel WPA3205 and one wireless adsl modem, USR Wireless MaxG ADSL Gateway)

I am really confused now. Why can't I connect to wireless at home (D-link DSL-2640T)? Any suggestions?

---

### Post by stewacide on 2011-10-28
I have Intel wifi that's also being flaky with my D-link wifi. That could be the common link.

---

### Post by jony121 on 2011-11-05
Hi all. Having the same problem. Worked amazing in 11.04.
lspci -v

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation PRO/Wireless 4965 AG or AGN
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fa000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwl4965
	Kernel modules: iwl4965

I have a netgear router.

I chose to upgrade distribution rather than install fresh. When I get the time I will burn off a CD and check if it works in the live environment. Might be a problem with the upgrade.

---

### Post by hanzz on 2011-11-08
Hi all,

is there any update on this issue? I have the same problem.

Wireless worked flawlessly on 11.04, (amd64), after upgrade to 11.10 oneiric my wireless connection keeps making problems ...

basically it is connected to the wavelan all the time but the connection seems to get "stuck" and slows down to nearly zero - next request/click works normal again, then it hangs again ...

hansp@kodos:~$ lspci -nvn | grep -i net
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)


I tried with Live-CD of 11.10 and after uptime of some hours I had the same issues with the running live-CD system so I guess a fresh-clean install won't help.


I can workaround the issues when selecting the old 2.6 kernel at boot time so somehow it has to be related to kernel 3.0  ... 

Recently I have to boot windows7 when I need to work without problems on my laptop and this is really, really SAD !

---

### Post by jony121 on 2011-11-12
agreed, was reading around. apparently 3.0 causing a few wireless problems. Don't know where to find the bug reports. Just keep your fingers crossed and hope someone fixes it by design or mistake. Unless anyone here is a kernel hacker with experience in coding wireless drivers?

---

### Post by wildmanne39 on 2011-11-12
Hi, have a look at this link it might help.
[http://ubuntuforums.org/showthread.php?t=1859558&page=3](http://ubuntuforums.org/showthread.php?t=1859558&page=3)
Post 21.
Thank you

---

### Post by jony121 on 2011-11-16
> **wildmanne39 said:**
> Hi, have a look at this link it might help.
[http://ubuntuforums.org/showthread.php?t=1859558&page=3](http://ubuntuforums.org/showthread.php?t=1859558&page=3)
Post 21.
Thank you

That WORKED!!! Why did that work! YAY! :D

HAHA, I AM USING THE INTERNET!

---

### Post by OwnSurname on 2012-02-07
Didn't work for me. I've a fresh install on a Dell Latitude D630, having the same Intel 4965 wireless. Connection works fine until it drops down, and once is dropped, the network (wlan0) is down, and I don't know how to bring it up again. Any help is really appreciated, because the only workaround at the moment is to restart the computer.

---

### Post by Smylers on 2012-02-08
> **OwnSurname said:**
> Didn't work for me.

Yeah, none of the suggestions have worked for me either (I'm the original poster).

> **OwnSurname said:**
> the only workaround at the moment is to restart the computer.

Even that doesn't reliably work for me.

My workaround is to plug an external wi-fi adapter into a USB slot; that's been working absolutely fine.

---

### Post by Bartender on 2012-03-08
> **Smylers said:**
> My workaround is to plug an external wi-fi adapter into a USB slot; that's been working absolutely fine.

What's the model of USB adapter you're using?

---

### Post by kirusoft on 2012-03-14
If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

---

### Post by nipper77 on 2012-04-18
> **kirusoft said:**
> If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

Tried this myself on my Fujitsu Siemens Amilo Pro v3405 and didn't work. On the sudo rmmod -f iwlagn command I got - ERROR: Removing 'iwlagn' : no such file or directory -

And with the power off command I got - Operation not supported. 


Somebody please help with this, I've tried every solution I've come across on here and nothing works at all. Starting to lose all hope in Ubuntu 11.10 for this issue.

---

### Post by wildmanne39 on 2012-04-18
Hi, it probably did not work because you may not have the same driver, please post the output of: 
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by nipper77 on 2012-04-24
Ok here you go, sorry for delay in getting back. 


cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux niall-AMILO-Pro-Edition-V3405 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

```

lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
0a:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Fujitsu Technology Solutions Device [1734:10c1]
	Kernel driver in use: 8139too

```

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12d1:1c1f Huawei Technologies Co., Ltd. 
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"3MobileWiFi-e976"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 80:B6:86:6E:E9:76   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:150   Missed beacon:0

```

rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod
```
Module                  Size  Used by
cdc_ncm                17199  0 
usbnet                 25214  1 cdc_ncm
usb_storage            44173  0 
uas                    17699  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
binfmt_misc            17292  1 
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
joydev                 17393  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  509519  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
psmouse                73673  0 
serio_raw              12990  0 
arc4                   12473  2 
iwl3945                73360  0 
iwl_legacy             71499  1 iwl3945
mac80211              393421  2 iwl3945,iwl_legacy
cfg80211              172427  3 iwl3945,iwl_legacy,mac80211
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
8139too                23283  0 
8139cp                 22636  0 

```

Thanks

---

### Post by wildmanne39 on 2012-04-24
Hi, your driver is not the same as the one in this post and your power management is already off so let's add a parameter to your driver.

Please do:
```
sudo rmmod -f iwl3945

sudo modprobe iwl3945 swcrypto=1
```
this is just for one this boot so do not reboot after you run the commands and let us know if it is working better if it is we will need to make it permanent.
Thanks

---

### Post by nipper77 on 2012-04-24
Not sure if there's any point in carrying out that command at the moment as wireless has suddenly decided to start working again. Can't get my head around this at all.

---

### Post by wildmanne39 on 2012-04-24
Hi, those commands in most cases make it more stable and faster.
Thanks

---

### Post by nipper77 on 2012-04-25
Ok, tried it there and it didn't seem to work. Certainly no wireless became available but I will  try it again. 

Another thing, my mouse pad now seems to be intermittently cutting out which is new. Seems Ubuntu just doesn't like the hardware on this laptop as I'm having issues with the built in wireless adapter, any external stick I try to use and the mouse pad.

---

### Post by wildmanne39 on 2012-04-25
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by nipper77 on 2012-04-27
Ok here is the output as requested. Still no luck yet anyway but I did notice that after running the
 *sudo modprobe iwl3945 swcrypto=1* command the device status switched from 'device disabled by hardware switch' to 'device not ready' so maybe there's just another command that needs to be run at that point to get things going.


```
niall@niall-AMILO-Pro-Edition-V3405:~$ cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10" 
Linux niall-AMILO-Pro-Edition-V3405 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux 
niall@niall-AMILO-Pro-Edition-V3405:~$ lspci -nnk | grep -iA2 net 
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02) 
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001] 
	Kernel driver in use: iwl3945 
	Kernel modules: iwl3945 
0a:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
	Subsystem: Fujitsu Technology Solutions Device [1734:10c1] 
	Kernel driver in use: 8139too 
niall@niall-AMILO-Pro-Edition-V3405:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
niall@niall-AMILO-Pro-Edition-V3405:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11abg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
           
niall@niall-AMILO-Pro-Edition-V3405:~$ rfkill list all 
1: phy1: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 

niall@niall-AMILO-Pro-Edition-V3405:~$ lsmod 
Module                  Size  Used by 
iwl3945                73360  0  
bnep                   17923  2  
rfcomm                 38408  0  
bluetooth             148839  10 bnep,rfcomm 
parport_pc             32114  0  
ppdev                  12849  0  
snd_hda_codec_si3054    12864  1  
snd_hda_codec_realtek   254163  1  
snd_hda_intel          24262  2  
snd_hda_codec          91859  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0  
snd_rawmidi            25241  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
binfmt_misc            17292  1  
i915                  509519  3  
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
joydev                 17393  0  
drm_kms_helper         32889  1 i915 
snd_timer              28932  2 snd_pcm,snd_seq 
drm                   192194  4 i915,drm_kms_helper 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
i2c_algo_bit           13199  1 i915 
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
video                  18908  1 i915 
psmouse                73673  0  
serio_raw              12990  0  
soundcore              12600  1 snd 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
arc4                   12473  2  
iwl_legacy             71499  1 iwl3945 
mac80211              393421  2 iwl3945,iwl_legacy 
cfg80211              172427  3 iwl3945,iwl_legacy,mac80211 
lp                     17455  0  
parport                40930  3 parport_pc,ppdev,lp 
8139too                23283  0  
8139cp                 22636  0  
ahci                   21634  3  
libahci                25727  1 ahci 
niall@niall-AMILO-Pro-Edition-V3405:~$  

```

---

### Post by wildmanne39 on 2012-04-27
Hi, please explain the problem with your connection sometimes it works sometimes it does not or is it slow.

Try the command with the zero on the end instead of the 1.
```
sudo rmmod -f iwl3945

sudo modprobe iwl3945 swcrypto=0
```
if that does not help reboot and try this:
```
sudo rmmod -f iwl3945

sudo modprobe iwl3945 disable_hw_scan=0

```
Thanks

---

### Post by nipper77 on 2012-04-28
Yeh the problem is that ubuntu has a problem with the wireless adapter. The vast majority of the time, when I boot into Ubuntu, wireless doesn't work and I get the message 'wireless disabled by hardware switch'. Very very occasionally when I boot up wireless is available, there seems to be no reason for this, it just seems to work on its own terms. As I said that command you gave to run changes the status from 'wireless adapter disabled by hardware switch' to 'device not ready'. So it's got nothing to do with the speed of the wireless connection, when it does decide to work performance is fine. 

Anyway I'll try those new commands you've given me and see how it goes.

---

### Post by wildmanne39 on 2012-04-28
Hi, when it will not connect post the output of:
```
rfkill list all
```
Thanks

---

### Post by nipper77 on 2012-05-01
Tried both of those new commands you gave me and get the same thing; it changes from 'wireless disabled by hardware switch' to 'device not ready' but still no wireless available.

Here's the output from 'rfkill list all' as requested:

```

niall@niall-AMILO-Pro-Edition-V3405:~$ rfkill list all 
1: phy1: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 

```

Thanks.

---

### Post by wildmanne39 on 2012-05-03
Hi, please post the output of:
```
nm-tool
cat /var/lib/NetworkManager/NetworkManager.state
sudo iwlist scan
dmesg | egrep 'iwl|firm|radio|switch|wlan0'
```
Thanks

---

### Post by nipper77 on 2012-05-03
What's the chances that 12.04 will have this resolved? I'm tempted to upgrade and see what happens.

---

### Post by wildmanne39 on 2012-05-03
Hi, not likely but you can try if you want.
Thanks

---

### Post by nipper77 on 2012-05-03
Ok, as per usual every time you ask me to do something I log onto Ubuntu and wireless is available, sod's law they call it. So at this very moment I'm on Ubuntu and wireless IS available. I've decided to give you an output of rfkill list all just so you can see it while wireless is functioning (not sure if it makes any difference). What I did notice was that 'phy' is at 0 here whereas it was at 1 when wireless wasn't functioning.

```

niall@niall-AMILO-Pro-Edition-V3405:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
niall@niall-AMILO-Pro-Edition-V3405:~$ 

```

And here's the output from the latest set of commands you provided. Again just to stress wireless IS working at this point so I presume that will affect the output.

```
niall@niall-AMILO-Pro-Edition-V3405:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
niall@niall-AMILO-Pro-Edition-V3405:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [eircom78720383] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        00:13:02:80:67:8A

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *eircom78720383: Infra, C8:6C:87:50:49:39, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:0A:E4:B8:99:79

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


niall@niall-AMILO-Pro-Edition-V3405:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
niall@niall-AMILO-Pro-Edition-V3405:~$ sudo iwlist scan
[sudo] password for niall: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C8:6C:87:50:49:39
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"eircom78720383"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f9a4d0040
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000E656972636F6D3738373230333833
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706494520010D14
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

niall@niall-AMILO-Pro-Edition-V3405:~$ dmesg | egrep 'iwl|firm|radio|switch|wlan0'
[   21.623636] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.623642] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.623722] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.623739] iwl3945 0000:02:00.0: setting latency timer to 64
[   21.663998] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   21.664016] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.664170] iwl3945 0000:02:00.0: irq 43 for MSI/MSI-X
[   21.705928] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   23.716988] Console: switching to colour frame buffer device 160x50
[   26.072737] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   26.141987] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.434838] wlan0: authenticate with c8:6c:87:50:49:39 (try 1)
[   34.436613] wlan0: authenticated
[   34.437131] wlan0: associate with c8:6c:87:50:49:39 (try 1)
[   34.439969] wlan0: RX AssocResp from c8:6c:87:50:49:39 (capab=0x431 status=0 aid=2)
[   34.439978] wlan0: associated
[   34.449145] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.728060] wlan0: no IPv6 routers present
niall@niall-AMILO-Pro-Edition-V3405:~$ 

```

---

### Post by nipper77 on 2012-05-03
So sorry but if you need me to run those commands again when wireless is not available just let me know.

---

### Post by wildmanne39 on 2012-05-03
Hi, yes I really do need them when you can not connect but here is a few things to do that usually helps.

In your router change your encryption to wpa2 only and not mixed if that option is available also while in there set your wirless speed to g only and see if that helps.
Thanks

---

### Post by nipper77 on 2012-05-04
Ok well when I logged on first thing this morning wireless was again unavailable so here's the output as requested:

```
niall@niall-AMILO-Pro-Edition-V3405:~$ nm-tool 
 
NetworkManager Tool 
 
State: disconnected 
 
- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            iwl3945 
  State:             unavailable 
  Default:           no 
  HW Address:        00:13:02:80:67:8A 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points  
 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            8139too 
  State:             unavailable 
  Default:           no 
  HW Address:        00:0A:E4:B8:99:79 
 
  Capabilities: 
    Carrier Detect:  yes 
    Speed:           10 Mb/s 
 
  Wired Properties 
    Carrier:         off 
 
 
niall@niall-AMILO-Pro-Edition-V3405:~$ cat /var/lib/NetworkManager/NetworkManager.state 
 
[main] 
NetworkingEnabled=true 
WirelessEnabled=true 
WWANEnabled=true 
WimaxEnabled=true 
niall@niall-AMILO-Pro-Edition-V3405:~$ sudo iwlist scan 
[sudo] password for niall:  
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Interface doesn't support scanning : Network is down 
 
niall@niall-AMILO-Pro-Edition-V3405:~$ dmesg | egrep 'iwl|firm|radio|switch|wlan0' 
[   21.959553] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s 
[   21.959559] iwl3945: Copyright(c) 2003-2011 Intel Corporation 
[   21.959641] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   21.959658] iwl3945 0000:02:00.0: setting latency timer to 64 
[   21.999946] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels 
[   21.999951] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG 
[   22.000128] iwl3945 0000:02:00.0: irq 43 for MSI/MSI-X 
[   22.094425] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs' 
[   24.208984] Console: switching to colour frame buffer device 160x50 
niall@niall-AMILO-Pro-Edition-V3405:~$  



```

In the meantime I'll see how I can go about changing those router settings. 

Thanks

---

### Post by wildmanne39 on 2012-05-04
Hi, let's see if this fixes it.
```
gksudo gedit /etc/rc.local
```
Add these three lines above exit 0:
```
rmmod -r iwl3945
rfkill unblock all
modprobe iwl3945
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

### Post by nipper77 on 2012-05-06
No it didn't work I'm afraid, unless I'm doing something wrong but I can't see what that might be.

---

### Post by wildmanne39 on 2012-05-06
Hi, do:
```
gksudo gedit /etc/rc.local
```
then copy the contents here please.
Thanks

---

### Post by nipper77 on 2012-05-06
Here you go:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rmmod -r iwl3945
rfkill unblock all
modprobe iwl3945
exit 0

```

---

### Post by wildmanne39 on 2012-05-06
Hi, this is an issue that some people have had with the device and driver.

Did you change your router setting to just wpa2?

Install wicd and remove network manager in that order then setup wireless and see if it works.

Also set IPV6 to disable and use IPV4 only.
Thanks

---

### Post by baditaflorin on 2012-05-09
> **jony121 said:**
> That WORKED!!! Why did that work! YAY! :D

HAHA, I AM USING THE INTERNET!

Ubuntu 12.04. This solution worked for me too.

[http://ubuntuforums.org/showpost.php?p=11350040&postcount=21](http://ubuntuforums.org/showpost.php?p=11350040&postcount=21)

I reported the bug in like 3 or 4 locations. Not the internet is as fast as it would be on cable. 

Report the bug also, so tht this gets fixed :)

---

### Post by nipper77 on 2012-05-15
> **wildmanne39 said:**
> Hi, this is an issue that some people have had with the device and driver.

Did you change your router setting to just wpa2?

Install wicd and remove network manager in that order then setup wireless and see if it works.

Also set IPV6 to disable and use IPV4 only.
Thanks

Sorry haven't been able to look at this for a while, it's exam season here and I'm pretty busy. Just a couple of things:

1) I presume you're referring to the router supplied by my ISP. If so wouldn't that only resolve the issue locally. As in when I look to use wireless elsewhere, in the college library for example, it would make no difference.

2) Also as there are other machines working off that router I'm reluctant to change it as I don't want to cause issues elsewhere.

3) Most important, I seem to have found a strange little work around to do with dropbox. It goes as follows:

If I boot into the Windows XP partition, open the dropbox folder and create or delete a folder then restart the laptop and boot into Ubuntu wireless is somehow available. However if I boot into Ubuntu and make the change in there and then restart, wireless remains unavailable. I've tested this about 10 or more times now and everytime it works so it's a remarkable coincidence if that is the case. 

At the same time I can't see how Ubuntu would know that a change had been made on the windows partition but maybe there's something in the startup script for Dropbox that forces wireless on when it notices a change. I've no idea and I know it makes little sense but it does seem to work. Any ideas if the resolution is in there somewhere?

---

