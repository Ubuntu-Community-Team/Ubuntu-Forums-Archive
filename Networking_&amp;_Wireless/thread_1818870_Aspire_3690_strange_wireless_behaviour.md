---
title: "Aspire 3690 strange wireless behaviour"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by shrinkinguniverse on 2011-08-05
Hi,
I'm very new to Linux, and use it on my desktop with no problems. I'm staying at my parents at the moment though, and I have been given a friends old Aspire 3690 (so I can't rule out faulty hardware) and thought I'd use it to continue my Ubuntu adventures. A bit of info: installed 11.04, and have installed all the updates suggested by the update manager. Its duel booted with WinXP.

The problem I'm having is this:
When I'm downstairs, no wireless networks are detected. Upstairs I can connect to my parents wireless, and see all the others in the area. If I take the laptop downstairs after turning it on upstairs it works fine (seeing and connecting to wireless networks) until I next restart it. I wouldn't mind but I don't have a battery for the computer so have to use an extension cord to bring it downstairs after turning it on. Additionally turning it on downstairs and taking it upstairs does not allow me to view wireless networks.

I am at a total loss as to why being upstairs would affect the ability of the computer to see all nearby wireless connections. At first I thought it must be signal strength or intererrance or something, but when using windows xp I have no problems at all, which means it must be software related, right? If I plug in a belkin usb wireless dongle with ubuntu I can see all the wireless networks for both the belkin and antheros (the internal wireless card) and the antheros one connects successfully but I'm unable to load any web pages. Unplugging the belkin sometimes crashes the laptop but usually just allows me to continue being 'connected'. Reconnecting doesn't help.

Searching the forum I found this [http://ubuntuforums.org/showthread.php?t=1546065&highlight=aspire+3690+wireless](http://ubuntuforums.org/showthread.php?t=1546065&highlight=aspire+3690+wireless) which looks like it may be a similar problem? But I don't know how to implement the suggested solution, and I'm not convinced it is the same cause anyway.

Any help would be greatly appreciated. I'd love to get the internal card working as I'd like to use this computer for university. I'm reasonably computer savvy but have next to no knowledge of Linux. If you have the time to write a short explanation of what any steps you suggest is doing, I would appreciate it, because I'd like to learn something new as much as fix the problem.

---

### Post by smuthavarapu on 2011-08-05
Can You check if there any other wireless devices at downstairs, which is causing this issue. I guess i had similar problem with my wireless mouse vs modem channel. When i change the channel to 2 then it resolve that issue. 

Try changing the channel of the modem and try again

---

### Post by wildmanne39 on 2011-08-05
Hi, you can try this command and if it works we will need to make it persistent.

Also unplug your wired connection if you have one and disconnect the usb adapter, you can only use one connection at a time.

Run the command but do not restart your computer after you run it.
```
sudo rmmod -f acer-wmi
```
Thank you

---

### Post by shrinkinguniverse on 2011-08-06
Hi,
Thank you both for your replies. Typically, since reading your replies I've not had any problems. I'm sure they'll reoccur I'll let you know if that command words wildmanne.

Smuthavarapu, we've got various other wireless devices, there's a wireless hard drive, a TV (with wireless access) and I pick up about 5 nearby wireless access points and one wireless LAN direct access (I think that's the right word for it). I don't have access to the router settings though, and my dad doesn't want me messing with the settings as he's only just got it all working. I know there's no risk of breaking things really, but it's not something I can influence. I'll take the laptop to a friends house and test it there for a while (once it stops working again), as that might give an idea of whether it's interference.

---

### Post by shrinkinguniverse on 2011-08-08
Hi,
As predicted the problem returned with the same symptoms. I tried the command wildmanne suggested (sudo rmmod -f acer-wmi) and got a message saying there was no module by that name. I don't know the significance of this result though.

I've not had chance to try the wireless at a friends yet, but thought the result of wildmanne's suggestion may be useful.

Thanks again for any help!

---

### Post by wildmanne39 on 2011-08-08
Hi, post the results of these commands please: run them while you can not connect.
```
sudo lshw -C network
``` 
```
nm-tool
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
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by shrinkinguniverse on 2011-08-08
Both 'enable networking' and 'enable wireless' options were ticked. I've left the command that produced the output at the top of each code block.


```
tesla@tesla-Aspire-3690:~$ sudo lshw -C network
[sudo] password for tesla: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 0
:16:d4:52:13:ee
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:d0010000-d0011fff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:83:14:17
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:d0000000-d000ffff
```


```
tesla@tesla-Aspire-3690:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:16:D4:52:13:EE

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:16:CF:83:14:17

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```



```
lspci -nn | grep 0280
```
gave no response.

```
tesla@tesla-Aspire-3690:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
```
tesla@tesla-Aspire-3690:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
tesla@tesla-Aspire-3690:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ath5k                 144412  0 
ath                    19141  1 ath5k
snd_seq_midi           13132  0 
mac80211              257001  1 ath5k
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
pcmcia                 39671  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  3 ath5k,ath,mac80211
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450934  3 
drm_kms_helper         40745  1 i915
b44                    35301  0 
drm                   180037  4 i915,drm_kms_helper
ssb                    45942  1 b44
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```

---

### Post by wildmanne39 on 2011-08-08
Hi,run these commands please, also while it will not connect to your network.
```
sudo iwlist scan
```
```
dmesg | grep wlan0
```
```
dmesg | grep ath
```
```
lsmod | grep ath
```
Thank you

---

### Post by shrinkinguniverse on 2011-08-08
Here are the results:

```
tesla@tesla-Aspire-3690:~$ sudo iwlist scan
[sudo] password for tesla: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```


```
tesla@tesla-Aspire-3690:~$ dmesg | grep wlan0
[   23.853023] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```


```
tesla@tesla-Aspire-3690:~$ dmesg | grep ath
[    0.518229] device-mapper: multipath: version 1.2.0 loaded
[    0.518234] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.946927] ath5k 0000:06:02.0: enabling device (0000 -> 0002)
[   22.946954] ath5k 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   22.947027] ath5k 0000:06:02.0: registered as 'phy0'
[   23.728619] ath: EEPROM regdomain: 0x63
[   23.728625] ath: EEPROM indicates we should expect a direct regpair map
[   23.728630] ath: Country alpha2 being used: 00
[   23.728632] ath: Regpair used: 0x63
[   23.804876] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
```


```
tesla@tesla-Aspire-3690:~$ lsmod | grep ath
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
```

---

### Post by wildmanne39 on 2011-08-08
Hi, try this and if it works we will need to blacklist it.
```
sudo rmmod -f acer_wmi
```
Thank you

---

### Post by shrinkinguniverse on 2011-08-08
Thanks for sticking with me with this. I got the same result as last time, though I remembered to save the exact wording this time:

```
tesla@tesla-Aspire-3690:~$ sudo rmmod -f acer_wmi
[sudo] password for tesla: 
ERROR: Removing 'acer_wmi': No such file or directory
```

---

### Post by wildmanne39 on 2011-08-08
Hi, run this command again and post the complete results please do not edit.
```
iwconfig
```
Thank you

---

### Post by shrinkinguniverse on 2011-08-09
Hi,
I've not knowingly edited any of my responses, however it's not impossible that I may have missed something out. Here's the result:

```
tesla@tesla-Aspire-3690:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

---

### Post by shrinkinguniverse on 2011-08-09
Note: It didn't ask for a password as I originally mistyped the command. So I already had sudo access.

Thanks again

---

### Post by wildmanne39 on 2011-08-09
Hi, try this please:
```
sudo ifup wlan0

sudo iwlist scan

```
post the results here.
Thank you

---

### Post by shrinkinguniverse on 2011-08-10
here are the results, doesn't look very useful I'm afraid:

```

tesla@tesla-Aspire-3690:~$ sudo ifup wlan0
[sudo] password for tesla: 
Ignoring unknown interface wlan0=wlan0.
tesla@tesla-Aspire-3690:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by aleoo on 2011-08-16
I have the same problem..I've read this discussion.
My results are the same except this

#" lsmod | grep ath
ath_pci               183044  0 
wlan                  224640  1 ath_pci
ath_hal               398701  1 ath_pci
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211 "

I have an Aspire 3680, I post my issue in this other thread as well:
[http://ubuntuforums.org/showthread.php?t=1744331&highlight=weirdly](http://ubuntuforums.org/showthread.php?t=1744331&highlight=weirdly)

Can anyone help me?

---

### Post by joner101 on 2011-08-24
Hi All, Another Acer Aspire 3690 owner with the same woes.
I installed Ubuntu 11.04 about 10 days ago. I have no dual boot. Just Ubuntu.
I have done all the tests as listed in this post and my results are identical to those posted.
I'm loving the system and it's open source environment, but without the wireless, I may have to switch back to a Windows system. (Which I'd rather not do...)
Anyway, any help would be much appreciated, as I only have a short LAN cable and my router is tucked away in the corner of our living room, so using the laptop while staring at a blank wall is starting to take it's toll.  :(
Many Thanks,
Joner

---

### Post by shrinkinguniverse on 2011-08-25
Has anyone tries their Aspire 3690 with 10.04 instead? I'm assuming it's not recommended to use the older versions of Ubuntu incase there are security flaws etc.?

---

### Post by joner101 on 2011-08-25
Can't say that I have. This is my first experience of Ubuntu. Is there much of a difference? Can you still get previous versions?
If I'm honest, I will try for a few more weeks to persevere with the problem. After that, I will probably consider other options.

---

### Post by wildmanne39 on 2011-08-25
> **shrinkinguniverse said:**
> Has anyone tries their Aspire 3690 with 10.04 instead? I'm assuming it's not recommended to use the older versions of Ubuntu incase there are security flaws etc.?

Hi, I am sorry that it has taken me so long to get back to you I have been very sick.

Please run this command, I may have had the syntax incorrect before.
```
sudo rmmod -f acer-wmi
```
Unplug your wired and usb connection first and see if it fixes your problem, if it does we will need to blacklist it and please do not restart your computer after you run the command.
Thank you

---

### Post by joner101 on 2011-08-26
Hi There,
Thanks for the reply and I'm sorry to hear you have been unwell. I hope you're on the road to recovery.
Anyway, I tried your command in terminal and the following was returned:
[FONT=Courier New]ERROR: Removing 'acer_wmi': No such file or directory[/FONT]
Any ideas?
Joner

---

### Post by wildmanne39 on 2011-08-26
Hi, lets start at the beginning, please post the outcome of these commands, you can copy them to a usb jump drive if you need to then paste them here on the system that has internet. 
```
lspci -nn | grep 0280
```
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

---

### Post by joner101 on 2011-08-26
OK, here goes. I'm actually using the Acer Aspire 3690, but hard wired via LAN.

Anyway, the terminal results are as follows:

  	 	 	 	 	 	  [FONT=DejaVu Sans Mono, monospace][SIZE=2]joner101@Aspire-3690:~$ [/SIZE][/FONT][COLOR=#0000ff][FONT=DejaVu Sans Mono, monospace][SIZE=2]lspci -nn | grep 0280[/SIZE][/FONT][/COLOR][FONT=DejaVu Sans Mono, monospace][SIZE=2] [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]06:02.0 Network controller [[/SIZE][/FONT][COLOR=#ff0000][FONT=DejaVu Sans Mono, monospace][SIZE=2]0280[/SIZE][/FONT][/COLOR][FONT=DejaVu Sans Mono, monospace][SIZE=2]]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) [/SIZE][/FONT]
 

 

 [FONT=DejaVu Sans Mono, monospace][SIZE=2]joner101@Aspire-3690:~$ [COLOR=#0000ff]sudo lshw -C network[/COLOR] [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2][sudo] password for joner101:  [/SIZE][/FONT]
   [FONT=DejaVu Sans Mono, monospace][SIZE=2]*-network:0              [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]description: Ethernet interface [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]product: BCM4401-B0 100Base-TX [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]vendor: Broadcom Corporation [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]physical id: 1 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]bus info: pci@0000:06:01.0 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]logical name: eth0 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]version: 02 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]serial: 00:16:d4:ac:f5:6b [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]size: 100Mbit/s [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]capacity: 100Mbit/s [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]width: 32 bits [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]clock: 33MHz [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.104 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]resources: irq:21 memory:d0000000-d0001fff [/SIZE][/FONT]
   [FONT=DejaVu Sans Mono, monospace][SIZE=2]*-network:1 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]description: Network controller [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]vendor: Broadcom Corporation [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]physical id: 2 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]bus info: pci@0000:06:02.0 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]version: 02 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]width: 32 bits [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]clock: 33MHz [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]capabilities: bus_master [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]configuration: driver=b43-pci-bridge latency=64 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]resources: irq:22 memory:d0002000-d0003fff [/SIZE][/FONT]
   [FONT=DejaVu Sans Mono, monospace][SIZE=2]*-network DISABLED [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]description: Wireless interface [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]physical id: 2 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]logical name: wlan0 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]serial: 00:19:7d:43:d7:82 [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]capabilities: ethernet physical wireless [/SIZE][/FONT]
        [FONT=DejaVu Sans Mono, monospace][SIZE=2]configuration: broadcast=yes driver=b43 driverversion=2.6.38-11-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg [/SIZE][/FONT]
 

 

 [FONT=DejaVu Sans Mono, monospace][SIZE=2]joner101@Aspire-3690:~$ [COLOR=#0000ff]iwconfig[/COLOR] [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]lo        no wireless extensions. [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2] [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]eth0      no wireless extensions. [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2] [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]wlan0     IEEE 802.11bg  ESSID:off/any   [/SIZE][/FONT]
           [FONT=DejaVu Sans Mono, monospace][SIZE=2]Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    [/SIZE][/FONT]
           [FONT=DejaVu Sans Mono, monospace][SIZE=2]Retry  long limit:7   RTS thr:off   Fragment thr:off [/SIZE][/FONT]
           [FONT=DejaVu Sans Mono, monospace][SIZE=2]Power Management:off [/SIZE][/FONT]
           [FONT=DejaVu Sans Mono, monospace][SIZE=2] [/SIZE][/FONT]
 

 [FONT=DejaVu Sans Mono, monospace][SIZE=2]joner101@Aspire-3690:~$ [COLOR=#0000ff]rfkill list all[/COLOR] [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]0: phy0: Wireless LAN [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]	Soft blocked: no [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]	Hard blocked: no [/SIZE][/FONT]
 

 

 [FONT=DejaVu Sans Mono, monospace][SIZE=2]joner101@Aspire-3690:~$ [COLOR=#0000ff]lsmod [/COLOR][/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]Module                  Size  Used by [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]parport_pc             32111  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]ppdev                  12849  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_hda_codec_realtek   255882  1  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]arc4                   12473  2  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]binfmt_misc            13213  1  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_hda_intel          24113  2  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_hwdep              13274  1 snd_hda_codec [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_pcm                80042  2 snd_hda_intel,snd_hda_codec [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]i915                  451033  3  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]b43                   296610  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_seq_midi           13132  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_rawmidi            25269  1 snd_seq_midi [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]pcmcia                 39671  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]mac80211              257001  1 b43 [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_seq_midi_event     14475  1 snd_seq_midi [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]joydev                 17322  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]drm_kms_helper         40745  1 i915 [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]gspca_vc032x           32072  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_timer              28659  2 snd_pcm,snd_seq [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]gspca_main             27894  1 gspca_vc032x [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]drm                   184164  4 i915,drm_kms_helper [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]cfg80211              156212  2 b43,mac80211 [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]yenta_socket           27230  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]i2c_algo_bit           13184  1 i915 [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]pcmcia_rsrc            18292  1 yenta_socket [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]videodev               75143  1 gspca_main [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]soundcore              12600  1 snd [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]snd_page_alloc         14073  2 snd_hda_intel,snd_pcm [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]psmouse                73312  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]serio_raw              12990  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]video                  18951  1 i915 [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]lp                     13349  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]parport                36746  3 parport_pc,ppdev,lp [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]b44                    35301  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]sdhci_pci              13623  0  [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]ssb                    45942  2 b43,b44 [/SIZE][/FONT]
 [FONT=DejaVu Sans Mono, monospace][SIZE=2]sdhci                  22720  1 sdhci_pci [/SIZE][/FONT]
 
Have I posted these correctly? Is this what you expected to see?
Thanks again.
Joner

---

### Post by wildmanne39 on 2011-08-26
Hi, yes you did it right.
You need the firmware for the driver please run this command with the wired connection plugged in.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
now unplug the wired connection and restart your computer and it should work if it does not please post the results of these commands. 
```
dmesg | grep b43
```
```
lsmod | grep b43
```
Thank you

---

### Post by joner101 on 2011-08-26
What can I say.......It Works...... Chuffed would be an understatement.
Thanks for all your help.
Now I'm finally mobile with Ubuntu.
Regards,
Joner

---

### Post by wildmanne39 on 2011-08-26
Hi, your welcome! I am glad I could help.

---

