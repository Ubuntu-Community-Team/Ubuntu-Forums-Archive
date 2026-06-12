---
title: "WTH? Network Manager has lost Wireless option"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2010-04-28
Karmic Koala, Acer Aspire 1

So I've been using the wireless networking in this laptop for a month, no problem. But a few minutes ago I plugged a second monitor into the port on the side of the laptop, did a System > Preferences > Display and the main screen, on the laptop, went blank except for a non-responsive cursor. The secondary screen never lit up. So after futzing around a bit, and getting no response, I powered the laptop off and re-booted it. Primary screen returned.

But Network Manager shows no entry for Wireless, just Wired Network, Disconnect, and VPN. I checked System > Preferences > Network Connections > Wireless and all my usual access points are still listed. 

Do I need to launch some daemon or something?

---

### Post by mikewhatever on 2010-04-28
Any wireless related buttons/switches there? Perhaps it's simply turned off? If not, the outputs of *ifconfig* and *lsmod* might help.

---

### Post by Rocket J Squirrel on 2010-04-28
Thanks for helping. 

The laptop has a wireless on/off switch (which I just discovered because I've never touched it before). The little wireless lamp on the top is not lit, and sliding the switch over doesn't light it. Maybe the switch broke? I can't tell without disassembly, so we'll leave that aside for the moment because maybe Ubuntu needs to do something to activate the wireless thingy, so here are the outputs you suggested we look at:
```
jackelliott@TheJackUbuntuNetbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:6c:5a:20  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe6c:5a20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13610 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:10089049 (10.0 MB)  TX bytes:2274376 (2.2 MB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108084 (108.0 KB)  TX bytes:108084 (108.0 KB)
```

```
jackelliott@TheJackUbuntuNetbook:~$ lsmod
Module                  Size  Used by
hidp                   14268  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
btusb                  11856  4 
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
dm_crypt               12928  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
cfg80211              132712  0 
led_class               4096  0 
atl1c                  31456  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
ramzswap                8880  1 
xvmalloc                5180  1 ramzswap
lzo_decompress          2620  1 ramzswap
lzo_compress            2300  1 ramzswap
```

See anything useful there?

---

### Post by Rocket J Squirrel on 2010-04-28
I should mention that I've got a LAN cable connected to the laptop right now until I figure out why the wireless isn't working.

---

### Post by mikewhatever on 2010-04-28
It looks like the problem is that no wireless module is loaded. I think Acers have wireless by Atheros, cat you confirm by posting the output of the following: 
```
sudo lshw -C network
```

---

### Post by Rocket J Squirrel on 2010-04-28
Thank you for your help. 

Yes, the Acer uses Atheros -- I know because it took a lot of work debugging and backporting to get the wireless working in the first place. After it was working, it survived numerous shutdowns and a complete system restore a couple weeks ago. I'd do that again if my live CD (USB) was more up to date but I've put in a lot of changes since then and don't want to have to recreate them. Anyway, here's the output the suggested command, I hope it provides clues:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo lshw -C network
[sudo] password for jackelliott: 
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:57100000-5710ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:6c:5a:20
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:55000000-5503ffff ioport:2000(size=128)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

### Post by mikewhatever on 2010-04-28
Right, the module name appears to be ath9k, so try manually loading it with *sudo modprobe ath9k*, the wireless shold come to life, if successful.

---

### Post by Rocket J Squirrel on 2010-04-28
Thank you for your help. The thing didn't come to life, here's what happened:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo modprobe ath9k
[sudo] password for jackelliott: 
WARNING: Error inserting pcmcia_core (/lib/modules/2.6.31-20-generic/kernel/drivers/pcmcia/pcmcia_core.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting compat (/lib/modules/2.6.31-20-generic/updates/compat/compat.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-20-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.31-20-generic/updates/cw/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Here's the tail of dmesg:
```
[12104.602150] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
[12104.602161] ath: Unknown symbol wiphy_apply_custom_regulatory
[12104.602394] ath: disagrees about version of symbol freq_reg_info
[12104.602399] ath: Unknown symbol freq_reg_info
```

Looks pretty obscure and highly complicated, to me. I hope this is useful to someone!

---

### Post by mikewhatever on 2010-04-28
Obscure indeed, and seems completely unrelated to the second monitor. Have you tried just rebooting again? The info I googled earlier suggested linux-backports-modules-karmic was needed for Atheros in 9.10. Do you know if you have it installed?

```
dpkg -l | grep linux-backports-modules-karmic
```

---

### Post by Rocket J Squirrel on 2010-04-28
Thank you for helping.

No telling if the second monitor had anything to do with this, or whether it was a problem lurking around until the reboot. I'll get to that second monitor thing after I clear up this thing. 

Yes, I did try rebooting the machine when I saw that the wireless wasn't working. Just in case. But it made no difference. 

I did install the karmic backports a few weeks ago, as part of the original "let's go Ubuntu!" troubleshooting of the wireless. Once the backports were done, the wireless was completely stable. Prior to that, it was flaky** but the light always lit** and I could connect, but the connections got slower and sloower and slooooowweeer until they stopped. 

Using your suggested command, I get:
```
jackelliott@TheJackUbuntuNetbook:~$ dpkg -l | grep linux-backports-modules-karmic
jackelliott@TheJackUbuntuNetbook:~$ 
```

Unless I miss my guess, this suggests that the machine has entirely forgotten about them.

---

### Post by mikewhatever on 2010-04-28
Yes, that output shows that the [I]linux-backports-modules-karmic
[/I] is not installed. Perhaps you could try installing it.

---

### Post by Rocket J Squirrel on 2010-04-28
Um . . . what's the syntax again?

---

### Post by Rocket J Squirrel on 2010-04-28
Thanks for helping.

Okay, I dredged up how to install the backports, and now we see they are (re)installed:

```
jackelliott@TheJackUbuntuNetbook:~$ dpkg -l | grep linux-backports-modules-karmic
ii  linux-backports-modules-karmic                  2.6.31.20.33                               Generic Linux backported drivers.
ii  linux-backports-modules-karmic-generic          2.6.31.20.33                               Backported drivers for generic kernel image
```

The wireless lamp did not come on, Network Manager still does not show the Wireless option. I rebooted, same thing.

So for the other commands, we see:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo modprobe ath9k
WARNING: Error inserting pcmcia_core (/lib/modules/2.6.31-20-generic/kernel/drivers/pcmcia/pcmcia_core.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting compat (/lib/modules/2.6.31-20-generic/updates/compat/compat.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-20-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.31-20-generic/updates/cw/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Tail of dmesg says:
```
[  157.794395] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input10
[  157.794696] generic-bluetooth 0005:045E:0700.0001: input,hidraw0: BLUETOOTH HID v1.00 Mouse [Microsoft Bluetooth Notebook Mouse 5000] on 00:26:5E:A4:DA:D5
[  346.664009] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
[  346.664026] ath: Unknown symbol wiphy_apply_custom_regulatory
[  346.664438] ath: disagrees about version of symbol freq_reg_info
[  346.664446] ath: Unknown symbol freq_reg_info
[  352.375118] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
[  352.375128] ath: Unknown symbol wiphy_apply_custom_regulatory
[  352.375363] ath: disagrees about version of symbol freq_reg_info
[  352.375368] ath: Unknown symbol freq_reg_info

```

And for the other bits:
```
jackelliott@TheJackUbuntuNetbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:6c:5a:20  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe6c:5a20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4007 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:4490075 (4.4 MB)  TX bytes:644301 (644.3 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61009 (61.0 KB)  TX bytes:61009 (61.0 KB)
```

and

```
jackelliott@TheJackUbuntuNetbook:~$ lsmod
Module                  Size  Used by
hidp                   14268  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
btusb                  11856  4 
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
dm_crypt               12928  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
psmouse                56500  0 
serio_raw               5280  0 
atl1c                  31456  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211              132712  0 
led_class               4096  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
ramzswap                8880  1 
xvmalloc                5180  1 ramzswap
lzo_decompress          2620  1 ramzswap
lzo_compress            2300  1 ramzswap
```

I realize that this is getting mighty complicated. It might be a hardware problem, and I do have a LiveUSB I can boot from. If that doesn't light the darn light then I'll take this stupid thing apart and pull the dead bug out of the switch or something. Does this sound like a reasonable course of action?

---

### Post by Rocket J Squirrel on 2010-04-28
I'd like to mention that something weird happened yesterday, see [HTML]http://ubuntuforums.org/showthread.php?t=1464001[/HTML] -- this might have installed that "lurking" problem that was just a-waitin' for a reboot to surface. The second monitor thing caused me to reboot the 'pooter.

---

### Post by mikewhatever on 2010-04-29
I think you'll need to install another backport package, linux-backports-modules-wireless-karmic-generic. ;) Reboot when done.

```
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

---

### Post by Rocket J Squirrel on 2010-04-29
Thank you for helping. 

I installed those backports along with linux-backports-modules-karmic earlier this evening before reporting back:

```
jackelliott@TheJackUbuntuNetbook:~$ dpkg -l | grep linux-backports-modules-karmic
ii  linux-backports-modules-karmic                  2.6.31.20.33                               Generic Linux backported drivers.
ii  linux-backports-modules-karmic-generic          2.6.31.20.33
```

I'm gonna boot off the LiveUSB tomorrow morning and if the Wireless thingy does not come to life I'll assume this is a hardware problem and take a mallet to it.

---

### Post by Rocket J Squirrel on 2010-04-29
Um, looks Ubuntu fixed itself. 

A few minutes ago, Update Manager presented a list of updates it wanted to install, including new flavors of backport stuff. I let it run, it asked permission to reboot, I let it reboot . . . and the frickin' wireless lamp lit up. And the access points are now accessible.

I don't know if there is any way to determine what happened and what particular update fixed it? It would be nice to add that info to this thread for folk dealing with a similar problem.

Thanks for all the help. 

I know here is a way to add SOLVED to this thread . . . looking for it . . . looking for it . . . nope, don't see it. Where's it hidden?

---

### Post by Rocket J Squirrel on 2010-04-29
Ah -- found it. Can't mark a thread as SOLVED while making a post. :P

---

