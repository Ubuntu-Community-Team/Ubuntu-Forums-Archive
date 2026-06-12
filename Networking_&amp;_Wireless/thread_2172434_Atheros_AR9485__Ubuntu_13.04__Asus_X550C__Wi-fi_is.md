---
title: "Atheros AR9485 / Ubuntu 13.04 / Asus X550C / Wi-fi is disabled by hardware switch"
date: 2013-09-04
forum: Networking &amp; Wireless
---

### Post by jason-barnabe-gmail on 2013-09-04
I've installed Ubuntu 13.04 on my Asus X550C laptop, dual booting with Windows 8. Wi-fi works fine in Windows 8. When I ran Ubuntu from the Live CD, wi-fi worked. After installing it, wi-fi no longer works. The networking menu says "wi-fi is disabled by hardware switch". Going back to Live CD, wi-fi doesn't work any more.

There is no physical switch for the wi-fi (I assume it there was and it was off, it wouldn't have worked on Windows). Pressing the Fn-F2 combination doesn't appear to do anything in Ubuntu. On Windows 8, it correctly toggles the wi-fi on and off.

The wi-fi indicator light is on under Ubuntu, but it seems a little flaky even in Windows. I've seen it off when the wi-fi was on; when toggling wi-fi off the light remained off, and toggling it back on turned on the light.

I've tried resetting the BIOS, no help. I've tried enabling the networking from the BIOS, no help.

```
jason@jason-X550CA:~$ lspci | grep Atheros
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

``````
jason@jason-X550CA:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr ac:22:0b:1a:cf:4e  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae22:bff:fe1a:cf4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2358555 (2.3 MB)  TX bytes:143442 (143.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19182 (19.1 KB)  TX bytes:19182 (19.1 KB)


``````
jason@jason-X550CA:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

``````
jason@jason-X550CA:~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
joydev                 17377  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
uvcvideo               80847  0 
coretemp               13355  0 
arc4                   12615  2 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm_intel             132891  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
asus_nb_wmi            12854  0 
kvm                   443165  1 kvm_intel
snd_seq_midi           13324  0 
asus_wmi               24213  1 asus_nb_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
sparse_keymap          13890  1 asus_wmi
videodev              129260  2 uvcvideo,videobuf2_core
snd_rawmidi            30180  1 snd_seq_midi
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
wmi                    19070  1 asus_wmi
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i915                  600351  3 
mac80211              606457  1 ath9k
video                  19390  2 i915,asus_wmi
drm_kms_helper         49394  1 i915
rtsx_pci_ms            13011  0 
drm                   286313  4 i915,drm_kms_helper
mei                    41158  0 
memstick               16554  1 rtsx_pci_ms
mac_hid                13205  0 
cfg80211              510937  3 ath,ath9k,mac80211
i2c_algo_bit           13413  1 i915
psmouse                95870  0 
microcode              22881  0 
soundcore              12680  1 snd
serio_raw              13215  0 
lpc_ich                17061  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         17475  0 
r8169                  67446  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25731  3 
libahci                31364  1 ahci

``````
jason@jason-X550CA:~$ sudo lshw -C network
[sudo] password for jason: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:d2:24:04:a3:0a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 0a
       serial: ac:22:0b:1a:cf:4e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.1.111 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

``````
jason@jason-X550CA:~$ iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down


``````
jason@jason-X550CA:~$ lsb_release -d
Description:    Ubuntu 13.04

``````
jason@jason-X550CA:~$ uname -mr
3.8.0-19-generic x86_64

```
```
jason@jason-X550CA:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
jason@jason-X550CA:~$ sudo rfkill unblock all
jason@jason-X550CA:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

dmesg doesn't look like it says anything related. Restarting networking makes me lose all my windows and be left with a blank screen, but doesn't have any error messages.

---

### Post by jason-barnabe-gmail on 2013-09-09
No one has any suggestions for me? I got this laptop specifically to put Ubuntu on it to support development of my Firefox extension Stylish [http://addons.mozilla.org/en-US/firefox/addon/stylish/](http://addons.mozilla.org/en-US/firefox/addon/stylish/). It's kind of a kick in the pants to not have Wifi working on it.

---

### Post by Sam_Whitlock on 2013-09-09
I have this exact same laptop, with this exact same problem, but I haven't had time to try anything out yet.

This appears to be [a known bug with this wireless card]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971809"), but I haven't had time to try the upstream kernel module yet (for ath9k). [This comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971809/comments/63") from that thread outlines how to do this. It seems to fix this issue for Atheros AR9485 chips, but I'm hoping that it doesn't have to do with something *else* in this laptop!

If you can wait about a month until 13.10 comes out, this fix should be integrated (if it isn't already?).

---

### Post by jason-barnabe-gmail on 2013-09-09
Actually, when I tried my laptop again today, Wifi was working! After some testing, I found that it starts working only after I suspend and awaken the laptop. Do you see the same behaviour with yours?

Perhaps 13.10 would fix this, but this has turned into a major inconvenience into a slight inconvenience, so I don't want to mess around with patches that might break it all over again.

---

### Post by Sam_Whitlock on 2013-09-10
I haven't tried this, but I definitely will. I'd rather wait for it to come out with 13.10 (in only about a month now!).

This seems like a reasonable fix because apparently the power management stuff is what is causing difficulties with this card (at least according to the handful of forum / SE posts I've seen).

---

### Post by Sam_Whitlock on 2013-09-10
The method you suggested (putting it to sleep and then waking up again) works for me too! Thanks for posting this seemingly obvious easy quick-fix (e.g. "Did you try turning it off and on again?" :o).

---

### Post by QDmzmk7 on 2013-10-13
Also worked for me (putting it to sleep and then waking up again). Does anyone know if this is a problem with the Atheros AR9485 card or the motherboard /wifi switch (fn f2) on my Asus X550C. I hear Intel wifi cards work well with Ubuntu... I will buy one in a heartbeat if that will solve the problem. All other fn function (volume, screen brightness, etc) work fine with Unbuntu...I just can't turn the wifi on execpt by putting it to sleep and then waking it up again. Even then, the wifi light never comes on, but it works. :p

---

### Post by varunendra on 2013-10-18
> **jason-barnabe-gmail said:**
> After some testing, I found that it starts working only after I suspend and awaken the laptop.

> **Sam_Whitlock said:**
> The method you suggested (putting it to sleep and then waking up again) works for me too!

@ Jason, Sam,

If you are still facing the same issue, please try the workaround suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=2181558") which specifically addresses this very same issue. It is safe to try and you can revert it anytime you wish by just deleting a conf file that is created to fix it.

QDmzmk7 has already followed the same fix and it worked for them, as it has for others having the same issue.

The Fn+F2 still doesn't work but a workaround to that is also suggested in post #2 of the thread.

Above all, if it works for you, I'd suggest to submit a bug report against it or add yourselves to the "Affected" list if someone has already submitted it.

---

