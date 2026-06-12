---
title: "Wireless works at home, freezes ubuntu at school?"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by skullriot on 2011-04-29
Hiya. I have the 11.04 on my eeePC 1001p. Everything works just dandy at home, internet connects just fine and has no problems. When i try to connect to my schools wifi, or any other wifi, everything either runs so slow that its impossible to do anything, or it just freezes on the loading screen.

Any ideas?

---

### Post by #1 GameMaster on 2011-04-29
I'm having the same problem with my HP G60-247CL (Atheros AR928X) except it's the reverse for me at home it runs slow (40KBPS) and at school it's fast (1.5MBPS). How is it possible for it to run fine in one place and not the other is what I'd like to know. :confused:

---

### Post by finito on 2011-04-29
> **skullriot said:**
> Hiya. I have the 11.04 on my eeePC 1001p. Everything works just dandy at home, internet connects just fine and has no problems. When i try to connect to my schools wifi, or any other wifi, everything either runs so slow that its impossible to do anything, or it just freezes on the loading screen.

Any ideas?

Just to clarify, you are talking only about the Internet and not about Browser/OS Lag?

If so it's very possible that your school's bandwidth is completely used up.

Lets say you have a 8M connection and you have 100 people trying to use it the 8M is shared on those 100 people so everyone gets 81K which translates to roughly 10Kb/s. Which is painful but you to see what the bandwidth is and also how many people there are.

In a school I would be surprised if it's anything less than 24M


Peace.

---

### Post by skullriot on 2011-04-29
its not the bandwidth that is the problem, its the computer itself. when i try to connect anywhere but the original wifi spot, it practically freezes the computer itself. I cant launch nautilus, it wont read usb drives anymore, the mouse gets stuck in one spot for a few seconds at a time then jumps 2 inches or so in the direction im trying to move it then sticks again.... 

Or it just gets stuck at the boot screen, and wont even load the desktop. it happens with auto log on enabled or disabled.

---

### Post by skullriot on 2011-04-30
I did forget to mention that it is more than likely something to do with the wireless, when i turn it off at home and come in to school, it will boot just fine and run without glitching. The problems also occur at two different friends houses, and everywhere has different routers and services... i really have no idea what could be doing this. 

thanks

---

### Post by finito on 2011-05-03
And you didn't have this problem in 10.10?

---

### Post by skullriot on 2011-07-26
I just wanted to bump this because i still haven't found a solution. Ubuntu still freezes up when i try to connect any wireless other than my home connection. Is there another wireless manager that might work?

---

### Post by lisati on 2011-07-26
A shot in the dark here. It might be good to think about the nature of the connections in each of the locations. For example, does one provide the IP address for you and the other require you to set a static IP address for your end? Does one use a proxy of some kind and the other not use a proxy?

In other words, there could be some subtle difference required in the settings required for the connections at the different locations.

---

### Post by wildmanne39 on 2011-07-26
> **skullriot said:**
> I just wanted to bump this because i still haven't found a solution. Ubuntu still freezes up when i try to connect any wireless other than my home connection. Is there another wireless manager that might work?Hi, you can try wicd it is in synaptic, other then that suggestion I do not know enough to help your further.

---

### Post by skullriot on 2011-07-26
Well the one at school is behind a cisco firewall, but my friends houses are standard connections. I don't have to set static IPs for anything. The only wireless i can access is the one I use when I install ubuntu. Mostly, I would like to not have to downgrade.

---

### Post by skullriot on 2011-07-27
Well, i'm typing this from school now. I don't know what happened, or what I did but it works now. 

The only thing i did was turn off my wifi during boot, launch WICD, tried to connect with WICD and then when that didnt work, just tried to connect with the regular wireless connection. so maybe WICD poked something into the right place. WICD couldnt obtain an IP address though. 

Anyway, problem solved somehow, but I dont know the solution.

---

### Post by skullriot on 2011-07-27
After browsing a bit, the network disconnects every 5 minutes and i have to try to connect to another network (thats one i cant access) before the school network will work again. Something with the DHCP lease i'm guessing, but i dont know anything about that stuff.

---

### Post by wildmanne39 on 2011-07-27
Hi, run these commands please in a terminal 
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
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by skullriot on 2011-07-27
the first command
```
  *-network               
       description: Wireless interface
       product: AR2427 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:e7:b0:40
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:0d:ce:b5
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f7fc0000-f7ffffff ioport:ec00(size=128){|
```

Second Command
```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR2427 Wireless Network Adapter (PCI-Express) [168c:002c] (rev 01)
```

Third
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"STUDENT_WIFI"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:57:42:98:B0   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:206   Missed beacon:0
```

Fourth
```
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: eeepc-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Finally
```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath9k                 103633  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  1 ath9k
i915                  450934  3 
ath9k_common           13611  1 ath9k
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
drm_kms_helper         40745  1 i915
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  4 i915,drm_kms_helper
uvcvideo               66851  0 
soundcore              12600  1 snd
cfg80211              156212  3 ath9k,mac80211,ath
lp                     13349  0 
videodev               75143  1 uvcvideo
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
parport                36746  3 parport_pc,ppdev,lp
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
eeepc_laptop           19417  0 
psmouse                73312  0 
sparse_keymap          13666  1 eeepc_laptop
serio_raw              12990  0 
ahci                   21591  3 
libahci                25548  1 ahci
atl1c                  36237  0 
```

This was done from school, I can do it from home if you like. The away networks are the problem really, not the home.

I appreciate the help.

---

### Post by wildmanne39 on 2011-07-27
Hi, try this command is has solved this issue for some people.
```
sudo iwconfig wlan0 power off
```
Thank you

---

### Post by skullriot on 2011-07-27
thanks, i'll get back to the network and test it tomorrow.

---

### Post by wildmanne39 on 2011-07-27
Hi, your welcome! please let us know if it worked and if it did please mark the thread solved.
Thank you

---

