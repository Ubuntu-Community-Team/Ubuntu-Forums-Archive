---
title: "Alfa awus050nh can't surf"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by krolikbunny on 2010-07-04
i use ubuntu 10.04 and cannot surf with my Alfa Awus 050nh.It works perfectly with aircrack-ng but i want to use it to surf.
```
nirvana@nirvana-USB:~$ uname -r
2.6.32-23-generic

```Now i use second card for surfing

[HTML]nirvana@nirvana-USB:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:620 (620.0 B)  TX bytes:620 (620.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:f1  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80:xx:20e:xxxx:fe76:25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12709354 (12.7 MB)  TX bytes:2584373 (2.5 MB)
[/HTML]i followed Jano's tutorial on aircrack forum but it didn't solve a problem
[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

and removed the rt2800usb module and replugged usb device
[HTML]nirvana@nirvana-USB:~$ sudo rmmod rt2800usb rt2x00usb rt2x00lib mac80211 cfg80211
ERROR: Module mac80211 is in use by ath5k
ERROR: Module cfg80211 is in use by ath5k,mac80211,ath
nirvana@nirvana-USB:~$ lsmod |grep rt
rt2870sta             461811  0 
snd_mpu401_uart         5617  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_rawmidi            19056  6 snd_seq_virmidi,snd_emu10k1,snd_wavefront,snd_usb_lib,snd_mpu401_uart,snd_seq_midi
gameport                9089  4 emu10k1_gp,ns558
snd                    54148  26 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_wavefront,snd_cs4236,snd_wss_lib,snd_ac97_codec,snd_usb_audio,snd_opl3_lib,snd_mpu401,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                31724  2 ttm,drm
parport_pc             25962  1 
parport                32635  3 ppdev,parport_pc,lp
[/HTML] and still i can't connect to my router(WPA key)

Any help or hints?

---

