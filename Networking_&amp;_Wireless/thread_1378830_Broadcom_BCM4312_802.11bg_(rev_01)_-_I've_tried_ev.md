---
title: "Broadcom BCM4312 802.11b/g (rev 01) - I've tried everything!"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by The Glidd on 2010-01-11
I've tried to pursue some of the advice on some of the other threads with no luck, including the one that says it's a tutorial for my card.  At thie stage, I think I've done so many things to the settings on the computer that I can't make heads or tails of anything.  Network manager detects no wireless and hardware drivers won't load STA or b43.  If no one can help, can I just reinstall 9.1, keeping my user data?  Should I just buy a new computer?  
[B]
1. Dell Inspiron 1545[/B]
[B]
2. Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)[/B]

3. 
[B]
ifconfig:[/B]

eth0      Link encap:Ethernet  HWaddr 00:25:64:49:af:58  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe49:af58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5661849 (5.6 MB)  TX bytes:775071 (775.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7586774 (7.5 MB)  TX bytes:7586774 (7.5 MB)
[B]
iwconfig: [/B]

lo        no wireless extensions.

eth0      no wireless extensions.

[B]4. lsmod - I don't know how to refine this search
[/B]
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
b44                    28620  0 
mii                     5212  1 b44
joydev                 10272  0 
snd_hda_codec_idt      59844  1 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
ssb                    44868  1 b44
pcmcia                 36808  1 ssb
pcmcia_core            35792  2 ssb,pcmcia
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
lib80211                6528  0 
dell_wmi                2564  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
psmouse                56500  0 
serio_raw               5280  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52576  0 
sky2                   46560  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

[B]5. dsmeg - this looks like wireless info:
[/B]
[   29.871410] wl: module license 'MIXED/Proprietary' taints kernel.
[   29.871414] Disabling lock debugging due to kernel taint
[   29.872197] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   29.872199] wl: Unknown symbol lib80211_get_crypto_ops
[   29.892266] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.892281] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   29.896121] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   29.896124] wl: Unknown symbol lib80211_get_crypto_ops

[B]6. Network configuration:
[/B]
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
[B]
7. iwlist scan[/B]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
[B]
8. Ubuntu 9.1[/B]

[B]9. Kernel - 2.6.31-16-generic i686

10. restarting the network:
[/B]
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK

---

### Post by PRC09 on 2010-01-12
I am asuming that you have a wired connection that is working and connected as you need that in order to activate the wireless drivers.If not post back as there are instructions for activating the drivers from the cd....



[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by PRC09 on 2010-01-12
If no wired connection then try post #1.....

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by efflandt on 2010-01-12
I just set up 64-bit Ubuntu 9.10 on a 1545 recently, although, I no longer have the laptop now to refer to (it is 1700 miles away).  You appear to have an ethernet connection, so if that is connected, you should be able to go to System > Administration > Hardware Drivers and activate Broadcom STA (you don't need the wadcutter one which may interfere with STA).  Once that is activated and you reboot, **sudo lspci -v** should show it using the **wl** module, and you should be able to configure SSID and security for it with Network Connections (once you disconnect ethernet or uncheck "connect automatically" for Wired Auto eth0).

If you do not have a network connection Broadcom STA is on the 9.10 CD, so you could insert that, bring up Synaptic and check the CD to add it to the repository, hit the reload icon in Synaptic (ignore the missing network respositories), then activate Broadcom STA from System > Administration > Hardware Drivers.  Not sure if you need to reboot, but after you get connected you can uncheck the CD from the repositories and refresh Synaptic for latest packages from the websites.

Actually it worked when I initially booted 64-bit Ubuntu 9.10 from a USB drive (WD Passport) that previously had Broadcom STA activated for an older work Dell with BCM4311.  But the BCM4312 in the 1545 works much better (stronger signal).  Note that it will show up as an eth device and it may flip flop which device number it is.  But network manager seems to be able to find it.

PS: Now that I relook at that other post, maybe it did work when I installed Broadcom STA from CD because I did first install bcmwl-kernel-source from the CD before activating Broadcom STA.  But I was not sure if that was actually needed (it was not needed when activating Broadcom STA from a network, but activating Broadcom STA may have added that package).

---

### Post by The Glidd on 2010-01-12
> **PRC09 said:**
> If no wired connection then try post #1.....

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)


Ethernet works fine.  No issues this whole time.  I'm hunching that the real trouble is between STA and b43.  Could there be a conflict between the two, competing for wireless control?

Everything I've read to this point suggests using STA, but how?

---

### Post by The Glidd on 2010-01-12
> **efflandt said:**
> I just set up 64-bit Ubuntu 9.10 on a 1545 recently, although, I no longer have the laptop now to refer to (it is 1700 miles away).  You appear to have an ethernet connection, so if that is connected, you should be able to go to System > Administration > Hardware Drivers and activate Broadcom STA (you don't need the wadcutter one which may interfere with STA).  Once that is activated and you reboot, **sudo lspci -v** should show it using the **wl** module, and you should be able to configure SSID and security for it with Network Connections (once you disconnect ethernet or uncheck "connect automatically" for Wired Auto eth0).

If you do not have a network connection Broadcom STA is on the 9.10 CD, so you could insert that, bring up Synaptic and check the CD to add it to the repository, hit the reload icon in Synaptic (ignore the missing network respositories), then activate Broadcom STA from System > Administration > Hardware Drivers.  Not sure if you need to reboot, but after you get connected you can uncheck the CD from the repositories and refresh Synaptic for latest packages from the websites.

Actually it worked when I initially booted 64-bit Ubuntu 9.10 from a USB drive (WD Passport) that previously had Broadcom STA activated for an older work Dell with BCM4311.  But the BCM4312 in the 1545 works much better (stronger signal).  Note that it will show up as an eth device and it may flip flop which device number it is.  But network manager seems to be able to find it.

PS: Now that I relook at that other post, maybe it did work when I installed Broadcom STA from CD because I did first install bcmwl-kernel-source from the CD before activating Broadcom STA.  But I was not sure if that was actually needed (it was not needed when activating Broadcom STA from a network, but activating Broadcom STA may have added that package).

I went to hardware drivers (I've done this several times).  I see b43 and STA.  STA is filled in green and the bottom says. "This driver is activated but not currently in use."  I remove it, then reactivate.  I reboot, and the same thing is mentioned within hardware drivers.  I tried to set up the wireless, network manager isn't showing any wireless capability.  There's only a dialog for the ethernet.

Here are the results of lspci -v.  I'm not sure what all this means.

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Dell Device 000c
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 22-00-dd-ff-ff-5f-4f-b1
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb, wl

Also, what are you suggesting?  Can I add re-add Broadcom STA from the live CD (thus wiping the slate clean)?  Should I burn a CD and then re-install?  I'm on 9.1 after having 'upgraded' from 9.04.

---

### Post by The Glidd on 2010-01-12
That was interesting.  I tried to activate b43 from Hardware Drivers.  Network manager sprang to life and detected all sorts of networks just like the good old days, but no pages would load in the browser.  I can't help but still think this is a conflict between b43 and STA.

---

### Post by PRC09 on 2010-01-12
From the number of posts of people having issues after upgrading vs a clean install it could be any number of problems.It would probably be easier time wise to just do a clean install and start fresh.Why spend hours and hours on a problem when you can do a fresh install and be up and running in an hour.I have set up quite a few Dells with the broadcom chipsets and never had any problems with them,only clean installs mind you and using the b43. Just my opinion.......

---

### Post by The Glidd on 2010-01-13
> **PRC09 said:**
> From the number of posts of people having issues after upgrading vs a clean install it could be any number of problems.It would probably be easier time wise to just do a clean install and start fresh.Why spend hours and hours on a problem when you can do a fresh install and be up and running in an hour.I have set up quite a few Dells with the broadcom chipsets and never had any problems with them,only clean installs mind you and using the b43. Just my opinion.......

Agreed, enough of this.  

I just tried to boot from liveCD for kicks.  The wireless didn't work there either.  

How do you suggest I proceed?  If I try a fresh install, will it write on top of my current installation?  Do I have to set up another partition?  Will my files in /Home be safe through it all?  

Should I forget about 9.1 and reinstall 9.04, which had no wireless issues?

---

### Post by Popky on 2010-02-07
I have HP laptop, but the same Broadcom and unfortunately the same problem.
I am still looking for solution. I did the clean installation for twice.
I don't know if it help, but i remember, that a few months ago i tried to allow the STA broadcom driver and it works. Then i maybe do some changes, but don't know what changes. now i am having the same problem. If someone will be able to solve that problem, please answer or write me an e-mail. Thank you, everyone.

---

### Post by bkratz on 2010-02-07
> **Popky said:**
> I have HP laptop, but the same Broadcom and unfortunately the same problem.
I am still looking for solution. I did the clean installation for twice.
I don't know if it help, but i remember, that a few months ago i tried to allow the STA broadcom driver and it works. Then i maybe do some changes, but don't know what changes. now i am having the same problem. If someone will be able to solve that problem, please answer or write me an e-mail. Thank you, everyone.




This thread was about that specific card (the low power version of the BCM4312   (14e4:4315) with complete directions in post 7.

[http://ubuntuforums.org/showthread.php?p=8539988#post8539988](http://ubuntuforums.org/showthread.php?p=8539988#post8539988)

---

### Post by icc97 on 2010-02-15
I have an HP 6375s laptop.  So I finally got mine working after getting to the stage of having b43 driver activated, but it would not detect any networks.  This link got me this far: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx). Possibly I could have edited the network connections and added my wireless network manually.  A shame that I did not know that a SSID is simply the name of the network and that's all that you need to configure.  Anyway, I gave up on the b43 driver and activated the Broadcom STA driver instead.  After a restart there was no change - no wireless networks detected.  I then removed the wired ethernet connection and restarted.  This time the Wireless card started correctly (the Wireless light went from orange to blue just before the log-in screen indicating its on) and detected the local networks.

Now that its working I thought it might be useful to see a set of correct configurations:

[B]ifconfig:

[/B]eth0      Link encap:Ethernet  HWaddr 00:22:64:6f:94:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:21:00:87:a8:34  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe87:a834/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1441 errors:0 dropped:0 overruns:0 frame:88
          TX packets:1574 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1261966 (1.2 MB)  TX bytes:336731 (336.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

[B]
iwconfig
[/B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   

**lspci -vnn | grep 14e4:**
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)[B]

lshw -C network:[/B]
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:22:64:6f:94:5b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:53100000-53103fff ioport:3000(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:87:a8:34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:52000000-52003fff

Not sure if it will help anyone, but I hope so.

---

### Post by northd_tech on 2010-02-16
> **icc97 said:**
> I have an HP 6375s laptop.  So I finally got mine working after getting to the stage of having b43 driver activated, but it would not detect any networks.  This link got me this far: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx). Possibly I could have edited the network connections and added my wireless network manually.  A shame that I did not know that a SSID is simply the name of the network and that's all that you need to configure.  Anyway, I gave up on the b43 driver and activated the Broadcom STA driver instead.  After a restart there was no change - no wireless networks detected.  I then removed the wired ethernet connection and restarted.  This time the Wireless card started correctly (the Wireless light went from orange to blue just before the log-in screen indicating its on) and detected the local networks.


Hi icc97,

Since you've got a working Broadcom 4312 WiFi using the STA driver, the scientist/"tester" in me would like you to run a few experiments- if you're willing.

1.  Restart the computer about 5 times (complete power down- maybe even unplug it) and see if the STA 4312 wireless still works (each restart).  If you've got a dual/multiple boot system- maybe mix booting into Windoze/etc. a couple of times mixed in with those 5 shutdowns.

2.  With the 4312 WiFi running under Ubuntu- plug that ethernet cable back in and then run some diagnostics on the ethernet connection, and then see if the WiFi still works.

2.A. Maybe [physically] switch off the WiFi and see if the ethernet still works.

2.B.  Switch the WiFi back on and see if the wireless will connect.

2.C.  Leave the ethernet cable plugged in and restart the computer and see if you can get a wireless connection after the restart.

I've got a "method behind the madness" above- but I would rather get the honest impressions of the posters here on this thread to see what they think the problem is (before I reveal my current hypothesis- that is related to those diagnostic steps above).

If you'd rather not experiment with your working 4312 WiFi connection- that's cool with me too- it IS YOUR computer after all, icc97. ;)

P.S.  My HP DV-98xx laptop works "breasts" with that STA driver and my Broadcom 4321AG (but **lspci** reports that as a 4328 ).  I have yet to see a cable that my NVIDIA nForce ethernet will not connect to "out of the box"- going back several years, and dozens of versions of Linux, too.

---

### Post by elkoselim on 2010-02-17
> **icc97 said:**
> I have an HP 6375s laptop.  So I finally got mine working after getting to the stage of having b43 driver activated, but it would not detect any networks.  This link got me this far: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx). Possibly I could have edited the network connections and added my wireless network manually.  A shame that I did not know that a SSID is simply the name of the network and that's all that you need to configure.  Anyway, I gave up on the b43 driver and activated the Broadcom STA driver instead.  After a restart there was no change - no wireless networks detected.  I then removed the wired ethernet connection and restarted.  This time the Wireless card started correctly (the Wireless light went from orange to blue just before the log-in screen indicating its on) and detected the local networks.

Now that its working I thought it might be useful to see a set of correct configurations:

[B]ifconfig:

[/B]eth0      Link encap:Ethernet  HWaddr 00:22:64:6f:94:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:21:00:87:a8:34  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe87:a834/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1441 errors:0 dropped:0 overruns:0 frame:88
          TX packets:1574 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1261966 (1.2 MB)  TX bytes:336731 (336.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

[B]
iwconfig
[/B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   

**lspci -vnn | grep 14e4:**
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)[B]

lshw -C network:[/B]
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:22:64:6f:94:5b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:53100000-53103fff ioport:3000(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:87:a8:34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:52000000-52003fff

Not sure if it will help anyone, but I hope so.
I have same laptop. First of all, I tried to use aircrack-ng. FAILED! :( Now, could anyone send me step by step solution for installing driver and how to make bcm4322 work with aircrack-ng.

---

### Post by northd_tech on 2010-02-20
Post #32 here is about getting a Broadcom 4322 wireless working with the Broadcom STA driver:

[http://ubuntuforums.org/showpost.php?p=8828113&postcount=32](http://ubuntuforums.org/showpost.php?p=8828113&postcount=32)

---

### Post by bkratz on 2010-02-20
> **northd_tech said:**
> Post #32 here is about getting a Broadcom 4322 wireless working with the Broadcom STA driver:

[http://ubuntuforums.org/showpost.php?p=8828113&postcount=32](http://ubuntuforums.org/showpost.php?p=8828113&postcount=32)




I don't believe (but i could be wrong, often am) that the STA driver is compatible with  aircrack-ng only the b43. See below:

 [http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)

---

