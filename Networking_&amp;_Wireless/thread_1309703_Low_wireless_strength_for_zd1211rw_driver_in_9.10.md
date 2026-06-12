---
title: "Low wireless strength for zd1211rw driver in 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by picpak on 2009-11-01
Hi everyone, 

I've got a Retail Plus Mini Wireless USB Adapter that uses the zd1211rw driver. In Jaunty, it works perfectly. In fact, it has in every version I've tried except Karmic. In Karmic, my wireless strength only stays at 40%. If I boot back into Jaunty's 2.6.28 kernel, it's 100%.

Here's the output of lsusb:

```
Bus 001 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

and lsmod:

```
Module                  Size  Used by
input_polldev          11912  0 
video                  25872  0 
output                 11008  1 video
lp                     17156  0 
sisfb                 251988  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
arc4                    9856  2 
snd_seq_midi           14336  0 
ppdev                  15620  0 
ecb                    10752  2 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10496  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
zd1211rw               52740  0 
mac80211              217592  1 zd1211rw
cfg80211               38288  2 zd1211rw,mac80211
psmouse                61972  0 
serio_raw              13444  0 
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
sis_agp                15360  1 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
shpchp                 40212  0 
agpgart                42696  1 sis_agp
usbhid                 42336  0 
sis900                 28288  0 
mii                    13312  1 sis900
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```


I've seen lots of problems in Karmic with wireless drivers not working at all, but that's not happening to me, it just has a weak signal. The router is just across the room, so that's not it.

*EDIT* According to this bug report, I'm not the only one with this problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445989](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445989)

Specifically this post:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445989/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445989/comments/6)

I also tried the latest kernel at [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/) and that stuck me at 0%. Any ideas?

---

### Post by s.dalas on 2009-11-01
take a look here... [http://ubuntuforums.org/showthread.php?t=1307667]("http://ubuntuforums.org/showthread.php?t=1307667")

---

### Post by picpak on 2009-11-01
Thanks! Right-clicking Network Manager > Connection Information shows the speed as 54 Mb/s and not 1 anymore, but it still stays at 40%.

Here's the output of ifconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"mine"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:A4:03:1B:C9   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/100  Signal level=48/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Any more suggestions?

---

### Post by s.dalas on 2009-11-01
have you tried with NDISwrapper? i have seen different posts talking about "slower internet in Karmic". i will search for them again and see if i find something...

---

### Post by picpak on 2009-11-01
I gave ndiswrapper a try. I downloaded my wireless drivers from the manufacturer's site, installed ndisgtk and installed them through System > Administration > Windows Wireless Drivers. After I installed them it said it was "Unable to see if hardware is present", but afterwards it tells me that the hardware is present. Still no changes to the wireless strength, however. 

I installed the XP drivers for good measure. Should I go for Vista? XP's drivers are named zd1211bu and Vista's are named netathrusb, for what it's worth. Would that make a difference?

---

### Post by s.dalas on 2009-11-01
Hmmm, i have seen posts which confirm that there is a driver difference. For some users vista didn't work, they roll back to xp and they are ok. Some others need the vista while xp is not working...
No new idea from me till now. sorry. but i will keep looking...

---

### Post by picpak on 2009-11-01
After a restart, the ndiswrapper driver only sticks around 50-70%. If I switch back to zd1211rw, it's 100%. This is with XP's, haven't tried it with Vista's.

I may just stick with Jaunty's kernel, but this would be great to fix.

---

### Post by baizon on 2009-12-29
Same problem, after upgrade from 9.04 to 9.10 the signal strength changed from ~80% to ~20% :( 
Hope this will be fixed with Ubuntu 10.04.

---

### Post by cookdav on 2009-12-29
Thinking out loud:
Hmmm...are these 'erroneous' signal-strength values coming from
the driver itself, or maybe from the 'network manager'?

One way to find out, would be to install 'wicd' as your
'network manager' replacement, and then see if the low-values
are still shown?

[I much prefer 'wicd' as a network-manager for wifi, but
it takes a little getting familiar with how to configure
and use it...like any somewhat complex tool.] :)

---

### Post by baizon on 2009-12-29
> **cookdav said:**
> Thinking out loud:
Hmmm...are these 'erroneous' signal-strength values coming from
the driver itself, or maybe from the 'network manager'?

One way to find out, would be to install 'wicd' as your
'network manager' replacement, and then see if the low-values
are still shown?

[I much prefer 'wicd' as a network-manager for wifi, but
it takes a little getting familiar with how to configure
and use it...like any somewhat complex tool.] :)

I've tested Wicd yesterday. Still the same problem so it must be a driver problem.

Edit (4.01.2010):
Just upgraded to 10.4 Beta 1. Before the last update my signal strength was ~27%, now it is ~17% :(

---

