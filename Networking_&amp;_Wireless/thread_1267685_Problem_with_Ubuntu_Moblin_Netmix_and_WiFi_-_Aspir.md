---
title: "Problem with Ubuntu Moblin Netmix and WiFi - Aspire One G5"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by newbe01 on 2009-09-16
Hello,

I have installed Ubuntu (Moblin) Netmix on my Netbook. The problem is that since a couple of days the wireless do not work anymore. It cannot find any networks. It used to work without problems a couple of days ago.

The wlan0 is loaded:

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:8d:e5:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I don't what is the problem.

The errors on demsg are these:
>  2.245054] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.245068] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c15cc0), AE_ALREADY_EXISTS
[    2.245083] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    2.246458] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.246471] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c15cc0), AE_ALREADY_EXISTS
[    2.249035] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.249050] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c15cc0), AE_ALREADY_EXISTS
[    2.249330] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.249343] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c15cc0), AE_ALREADY_EXISTS
[    2.249616] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.249628] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c15cc0), AE_ALREADY_EXISTS
[    2.249902] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.249914] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c15cc0), AE_ALREADY_EXISTS
[   19.916532] [drm:i915_setparam] *ERROR* unknown parameter 4
[   19.916613] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   21.072451] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   39.138776] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   55.442392] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  665.074713] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 2004.292881] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 3213.344789] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
[ 3223.276074] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 3888.211726] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 4578.177142] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 7594.444319] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 8825.104288] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 9124.976094] ACPI: EC: missing confirmations, switch off interrupt mode.

It let's me create (in theory) a wireless network but it does not see the current networks, which are passwordless WiFi's, which i tused to work without problems.

Any ideas?

thanks

---

### Post by cubano on 2010-04-03
I got the same problem =[ but i have a eeepc900 ( yea old).
 
 
Networks show up for me, but then i get connection failure.

---

