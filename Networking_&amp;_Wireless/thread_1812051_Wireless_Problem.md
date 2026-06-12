---
title: "Wireless Problem"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by Skyline911 on 2011-07-25
Good evening,

I am currently staying in a holiday cottage and, for the last couple of days, have been logging on to the "on-site" wireless network without any problems.  However, when I have tried to log on today I am just getting a couple of green dots and a swirly blue circle thing and no connection.

I know the network is ok because when I reboot the laptop in windows it connects fine (that's were I am now).  Also, my children can log on ok.  I have a Dell Inspiron N5030 laptop with Ubuntu 11.04 and Windows 7 installed.  

Please don't be too technical with me as I am relatively new to all this... Thank you very much.

---

### Post by Tea4all on 2011-07-25
Did it ever work in Ubuntu? If so, did it stop working after an upgrade? The card looks like one that should work.

---

### Post by Skyline911 on 2011-07-25
Hi, Yes, it worked on Saturday evening. It worked all day yesterday as well....it just hasn't been working today.  The only thing I have done upgrade/installation-wise (as far as I know!) is to put chrome on the machine yesterday afternoon but it has worked since doing that....  Also, I've never had a problem with it at home.

---

### Post by Tea4all on 2011-07-25
Can you go to Applications > Accessories > Terminal, type:
```
sudo lspci -vv
```
```

``` and post the output?
Also ```
iwlist
```

---

### Post by nm_geo on 2011-07-25
Just to see what is available

```
sudo iwlist scan
```You might edit wireless and remove all connections but your auto (Home) ..
 I have had issues when traveling and that seemed to helped .

---

### Post by Skyline911 on 2011-07-26
When I typed in

sudo lspci -vv

it came back with

Command not found.


When I typed in 

iwlist

it came back with


Usage: iwlist [interface] scanning [essid NNN] [last] 
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 


When I typed in

sudo iwlist scan

it came back with

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:1F:CA:49:78
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Edimax AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fde55d0146
                    Extra: Last beacon: 580ms ago
                    IE: Unknown: 00094564696D6178204150
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000

---

### Post by wildmanne39 on 2011-07-26
Hi, the only thing I see is that your signal strength is weak, can you get any closer to your router?

---

### Post by Skyline911 on 2011-07-26
Hi there.  I can go a bit nearer to the main house, I guess!

Forgive me if it's a stupid question but would it not work when I have booted in Windows either if the signal was too weak?? I have tried tethering wirelessly to my phone as well with the same result :(

---

### Post by wildmanne39 on 2011-07-26
Hi, sometimes there are issues where the signal is a little weaker in ubuntu, and it is something that might can be fixed by changing drivers if the one you are using is not the best one for your card, but I am about to go to bed it is very late here.

I am not saying that is the problem just that it is a factor.

Also run these commands please it will help to fix your issue.
```
lspci -nn | grep 0280
```
```
lsmod
```
```
rfkill list all
```

---

### Post by Skyline911 on 2011-07-26
Thank you wildmanne39. Good night, sleep well.

---

### Post by Skyline911 on 2011-07-26
Still no joy.....  :(

---

### Post by wildmanne39 on 2011-07-26
Hi, run the commands in my last post and paste the output here please.
Thank you

---

### Post by Skyline911 on 2011-07-27
lspci -nn | grep 0280

0c:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)


lsmod

Module                  Size  Used by 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
ath9k                 103633  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13274  1 snd_hda_codec 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec 
mac80211              257001  1 ath9k 
i915                  450934  4 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
drm_kms_helper         40745  1 i915 
snd_timer              28659  2 snd_pcm,snd_seq 
dell_laptop            13515  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
drm                   180037  5 i915,drm_kms_helper 
ath9k_common           13611  1 ath9k 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
ath9k_hw              300328  2 ath9k,ath9k_common 
ath                    19141  2 ath9k,ath9k_hw 
cfg80211              156212  3 ath9k,mac80211,ath 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi 
uvcvideo               66851  0 
dcdbas                 14054  1 dell_laptop 
i2c_algo_bit           13184  1 i915 
soundcore              12600  1 snd 
videodev               75143  1 uvcvideo 
psmouse                73312  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
video                  18951  1 i915 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp 
ahci                   21591  3 
libahci                25548  1 ahci 
atl1c                  36237  0


rfkill list all

0: dell-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no

---

### Post by wildmanne39 on 2011-07-27
Hi, run this command please and post the out put here.
```
dmesg | grep wlan0
```
Thank you

---

### Post by peu.buntu on 2011-07-27
Hi. I have the same issue sometimes.
Like the OP, i too have Ubuntu (maverick) and win7. Also, slack13.37, but dosen't matter.
The thing is, the same connectivity issue with my wireless card, also a Atheros, just happens sometimes!
It's weird. Sometimes it just don't recognise my wifi card, others identify but do not works and others works like a charm. Usually a have to reboot even three times until it works. Also, it seems to me that if my notebook boot with the ethernet cable plugged, it makes Ubuntu don't recon the wifi either.


I have been following the instructions in this thread and more to see if some kind of error messages shows up, but until now, nothing. Right now, in on wifi on Ubuntu. Also, when dosse't work, it works on win7.

Another thing that may help. When i put win7 to hibernate and then i boot in Ubuntu, the wifi doesn't work. I figure that may be some protocol that win7 holds access to the wifi while hibernating, like to wakeup if senses a signal (mine is not setup for this).

I gonna keep following here, since it seems that the problem is with almost every notebook-ubuntu-atheros card.

Cheers from Brazil. :)

---

### Post by Skyline911 on 2011-07-27
Hi wildmanne39, Thank you for your help so far...much appreciated.

[   18.129184] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   25.547586] wlan0: authenticate with 00:1f:1f:ca:49:78 (try 1) 
[   25.550359] wlan0: authenticated 
[   25.550391] wlan0: associate with 00:1f:1f:ca:49:78 (try 1) 
[   25.553053] wlan0: RX AssocResp from 00:1f:1f:ca:49:78 (capab=0x411 status=0 aid=2) 
[   25.553057] wlan0: associated 
[   25.553839] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   25.978578] wlan0: IPv6 duplicate address fe80::21b:b1ff:feeb:f911 detected! 
[   79.465873] wlan0: deauthenticating from 00:1f:1f:ca:49:78 by local choice (reason=3) 
[   80.543281] wlan0: authenticate with 00:1f:1f:ca:49:78 (try 1) 
[   80.547565] wlan0: authenticated 
[   80.547587] wlan0: associate with 00:1f:1f:ca:49:78 (try 1) 
[   80.550196] wlan0: RX AssocResp from 00:1f:1f:ca:49:78 (capab=0x411 status=0 aid=2) 
[   80.550199] wlan0: associated 
[  146.629620] wlan0: deauthenticating from 00:1f:1f:ca:49:78 by local choice (reason=3)

---

### Post by wildmanne39 on 2011-07-27
Hi Skyline911:
Some users solved this issue by turning off "power management".
```
sudo iwconfig wlan0 power off
```
If that does not work other users uninstalled "Network Manager" and installed "WICD".

WICD can be found in "Ubuntu Software Center".

Before uninstalling "Network Manager" be sure to install "WICD" first or you will not have an internet connection to install "WICD".

Then you will need to uninstall "Network Manager". 
```
sudo apt-get remove --purge network-manager
```
Let me know if that works if it does please mark thread solved.
Thank you

---

### Post by wildmanne39 on 2011-07-27
Hi peu.buntu, I suspect that my last post will fix the OP's problem and if your 
```
dmesg | grep wlan0
```
looks like the OP's probably yours as well.

---

### Post by Skyline911 on 2011-07-27
Hi Wildmanne39.

I tried your first suggestion and the response was

Error for wireless request "Set Power Management" (8B2C) : 
    SET failed on device wlan0 ; Operation not permitted.

So I will have a go at your other suggestion.  Unfortunately, I don't think I can do this until I get home on Saturday as I cannot get online with Ubuntu at the moment to download the necessary bits and pieces! (I am currently going online with Windows and copying and pasting the various info across by rebooting my machine under the different operating system.) At that point, of course, the problem may be solved anyway as I will be returning to my home network...  

Many thanks for your input so far......

---

### Post by wildmanne39 on 2011-07-27
Hi, your welcome please keep us informed.

Try sudo in front of that command and see if it works then. 
Thank you

---

### Post by Skyline911 on 2011-08-07
Hi All,

Just to let you know that since I arrived back home, everything is working properly again on my home network... The problem just went away really but there doesn't appear to be an option to mark a thread as such so I'm marking it as solved!!!!!

Thank you for all your efforts

---

### Post by wildmanne39 on 2011-08-07
Hi, I am glad it is working.

---

