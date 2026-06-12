---
title: "Wireless not finding a network after Kernel update"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by Reded on 2011-12-11
Hey all,

I ran my usual daily update-check, and saw there was a Linux Kernel upgrade. I've done one of these before so I knew from back then that I have to redo my wireless card driver afterwards, so I went ahead.

I recompiled/installed my wireless drivers, but this time they don't work. Maybe I missed something, but in Network manager, no networks appear under the wireless card at all. The networks are there, I can connect to them using a USB dongle (That works 'out of the box' as they say).

Some info that usually gets asked:

lspci:

01:07.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R

ifconfig:

ra0       Link encap:Ethernet  HWaddr c8:3a:35:c7:42:a0  
          inet6 addr: fe80::ca3a:35ff:fec7:42a0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4639 (4.6 KB)  TX bytes:0 (0.0 B)
          Interrupt:17 

iwconfig:

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod:


Module                  Size  Used by
rfcomm                 47946  0 
rt3562sta             990799  1 
snd_hrtimer            12744  1 
vesafb                 13809  1 
snd_hda_codec_hdmi     32040  1 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
ppdev                  17113  0 
rt2x00lib              50325  2 rt73usb,rt2x00usb
snd_hda_intel          33390  4 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              462092  2 rt2x00usb,rt2x00lib
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
fglrx                2928969  295 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199587  2 rt2x00lib,mac80211
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53746  0 
edac_mce_amd           23709  0 
snd                    68266  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 13057  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             36962  1 
binfmt_misc            17540  1 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
sata_nv                32305  0 
pata_amd               14121  2 
forcedeth              67563  0 

sudo lshw -C network


  *-network               
       description: Wireless interface
       product: RT3060 Wireless 802.11n 1T/1R
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: ra0
       version: 00
       serial: c8:3a:35:c7:42:a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA

iwlist scan:

ra0       No scan results

Ubuntu 11.10 64-bit, 3.0.0-14-generic x86_64

Restart network command didn't do anything - returned 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 

Thanks for any help!

---

### Post by Redcard on 2011-12-11
From what I've been told, you're lucky you ever got this to work.  If you figure it out, let me know, I have a card with the same chipset.

---

### Post by Reded on 2011-12-11
I got it to work quite nicely, with a few bumps and scrapes. Power Management was impossible to turn off until I made a few adjustments in the .dat file, I'll dig out the thread I used to get it working if you want :p

---

### Post by TBABill on 2011-12-11
You also have 2 drivers active...rt73usb and rt3562sta. I'd blacklist one and see if the system works better unless you know you need both active.

---

### Post by Reded on 2011-12-11
I'm not sure if the usb one is for my USB dongle or not, I'll try it and if it kills it then I know ;)

EDIT:

Didn't kill my USB dongle, but didn't improve the wireless card either :(

---

### Post by TBABill on 2011-12-11
When you blacklisted one, did you save and restart, or at least ```
sudo modprobe -r xxxx
``` with xxxx being both drivers, then modprobe the one you want to use by ```
sudo modprobe xxxx
```

---

### Post by TBABill on 2011-12-11
I asked the above because you have to make sure you disable the one you don't want active unless you leave your current session and restart or go through the disable/re-enable routine.

---

### Post by Reded on 2011-12-12
I'm not sure what you mean 'both cards', I only have one card in! The other one's a wireless dongle, and I'd rather have that working as well as my wireless card :(

---

### Post by TBABill on 2011-12-12
I corrected that response above to say "drivers" instead of "cards". Not sure why I used the term cards...apologies for that.

---

### Post by Reded on 2011-12-12
Should've known ;)

Tried that (And I did do that already it seems) Still not found my network - and I've restarted a couple of times since then.

---

### Post by Reded on 2011-12-13
Still unfixed. Really don't like using my USB dongle as it's fairly old and worn-out!

---

### Post by Reded on 2011-12-13
FIXED!

My .DAT file had the wrong country code in it. Another human error disguised as a software failure ;)

---

