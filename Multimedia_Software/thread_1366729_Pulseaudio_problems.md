---
title: "Pulseaudio problems"
date: 2009-12-28
forum: Multimedia Software
---

### Post by sparky8251 on 2009-12-28
I recently obtained a new modem for my dial-up service. It turned out to be a conexant chipset and after I installed the drivers for it using the guide here:

[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

My audio broke. I have tried many things and have even purged and reinstalled pulseaudio on my system. After I reinstalled pulse audio the mixer shows up but no audio. The sound preferences are showing a only one output device called "Dummy Output." I Tried the comprehensive sound troubleshooting guide here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

When I try the command: "aplay -l" I get the error: "aplay: device_list:221: no soundcard found...[FONT=monospace]"
I follow the next step and type in the command: "lspci -v" and my soundcard is found but I have no idea what my chipset is. Here is the output for my sound card:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8249
    Flags: bus master, slow devsel, latency 64, IRQ 3
    Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 
Enable-

If anyone could provide a solution to my problem, even if it means getting rid of pulseaudio I would love to try it.
[/FONT]

---

### Post by sparky8251 on 2009-12-29
bump

---

### Post by VertexPusher on 2009-12-29
> **sparky8251 said:**
> When I try the command: "aplay -l" I get the error: "aplay: device_list:221: no soundcard found..."
This is not a PulseAudio problem but an ALSA problem. Your card does appear in the PCI device list, so there must be something wrong with your ALSA installation.

---

### Post by sparky8251 on 2009-12-29
I just reinstalled my ALSA server to no avail. Could someone provide a way to remedy this problem? It's driving me crazy, for 3 days I've had no audio.

---

### Post by sparky8251 on 2009-12-29
Nevermind. Fixed the problem by reinstalling the ALSA drivers from source.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

