---
title: "Sound Card Detection Failed - No Driver? Help!"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by jamier on 2006-05-28
Hi I'm trying to get sound working on an older HP Pavilion for my 7 year old son. I've spent quite a bit of time on it now. It's got this wierd sound card that is built into a modem card. I think I've found out all the information possible on the thing, but can't find a driver for it on [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) Is there anything else I should/can do? Or am I just out of luck. The card works find under Windows - but I can't stand the idea of my son on that OS...  :)

I'm a relative newbie to Linux, although I have done two other installations, and I use it almost daily at work.

Here is all the info that I could find. Perhaps someone will be able to help. I really appreciate it!
Jamie.

Full Debug info attached and also listed here (minus dmesg):
----------------------------------------------------------------------------------------------
From physical card:
CONEXANT
Riptide(tm)RACCO10
D7400-12
B94177.3
9949 KOREA
ARM

MODEL NO. 90079
  REN: 0.68
Smart Modular Technologies

----------------------------------------------------------------------------------------------------------------------------------------------

From Windows:
Conexant Audio
PCI slot 2 (pci bus 1, device 2, function 2)
Unimodem Half-Duplex Audio Device

----------------------------------------------------------------------------------------------------------------------------------------------

lspci -v:
0000:01:09.0 Multimedia audio controller: Rockwell International: Unknown device 4310
        Subsystem: Risq Modular Systems, Inc.: Unknown device 4310
        Flags: bus master, fast Back2Back, medium devsel, latency 64, IRQ 5
        I/O ports at 2400 [size=64]
        Capabilities: <available only to root>

----------------------------------------------------------------------------------------------------------------------------------------------

lspci:
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:01:09.0 Multimedia audio controller: Rockwell International: Unknown device 4310
0000:01:09.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
0000:01:09.2 Input device controller: Rockwell International: Unknown device 4312
0000:01:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

----------------------------------------------------------------------------------------------------------------------------------------------

aadebug:
ALSA Audio Debug v0.1.0 - Sun May 28 09:08:26 PDT 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux ubuntu-intel 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Warning: /proc/asound does not exist
This indicates that ALSA is not installed correctly
Check various logs in /var/log for a clue as to why

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

CPU -------------------------------------------------------
model name      : Pentium III (Coppermine)
cpu MHz         : 535.618

RAM -------------------------------------------------------
MemTotal:       125476 kB
SwapTotal:      369452 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:01:09.0 Multimedia audio controller: Rockwell International: Unknown device 4310

----------------------------------------------------------------------------------------------------------------------------------------------

cat /proc/version:
Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006

---

