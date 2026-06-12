---
title: "Getting nowhere with audio"
date: 2011-12-29
forum: Multimedia Software
---

### Post by Chrus on 2011-12-29
I'm trying to set up a Mythbunntu media PC, but getting audio working is doing my head in. And not having audio on a media PC is going to be a bit of a problem. I've never been a big fan of trying to get sound out of linux, I like when it just works... But in this case, nothing I try is giving me any results.

Im running Mythbuntu 10.10, (I gave up on 11.04 and 11.10 because they were a bit buggy and refused to boot at times) I've just done a clean install and run apt-get update/upgrade. I've got a Gigabyte GA-E350N-USB3 Mini-ITX Motherboard. I would like to get audio out over HDMI if possible. Have tried 3.5mm, but no luck there either.

lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

I cant help but think theres another important piece of information I should be giving... but i cant for the life of me think of what it could be.

Anyway... Anyone have any advice on how to get sound working? Happy to provide any more detail that may be needed.

Thanks

---

### Post by MoreOrLess on 2011-12-29
> I cant help but think theres another important piece of information I should be giving...
What video driver are you using? ;)
Only fglrx/Catalyst supports HDMI audio on RadeonHD APU's right now. If you're using that driver, have you selected the HDMI audio device for output?

---

### Post by Chrus on 2011-12-29
Thanks MoreOrLess

I've tried without updating the driver, which obviously didn't work. Tried updating the drivers (System > additional drivers) and no joy there either.

Just DL'd and installed the latest fglrx driver (8.92) from the AMD website. Nothing there either.

Probably an extreamly stupid question (and im going to kick myself when you answer)... but where do I select HDMI as the audio output?

---

### Post by MoreOrLess on 2011-12-29
It depends on what desktop environment you're using. Mythbuntu probably has its own control center.

---

### Post by Chrus on 2011-12-29
Well here's an interesting little piece of something.

If i go into VLC and change the audio settings in there, I get sound. Setting Output Module to 'ALSA audio output' and Device to 'HD-Audio Generic: ATI HDMI (hw:0,3)' works. Obviously this only gives sound for VLC and nothing else.

Now to figure out how to make that the default.

FYI: Mythbuntu still uses Gnome, just with a Myth interface that is started on login, and with auto login set, you dont usually see the desktop... But its still there if needed.

---

### Post by MoreOrLess on 2011-12-29
If you only want the HDMI audio, then just disable the mobo audio in the BIOS.

---

### Post by Chrus on 2011-12-29
SUCCESS!

Turns out I just needed to install pulseaudio and pavucontrol (Pulse Audio Volume Control).

Pavucontrol has the option to select which output to use as the default.

This doesnt mean I hate audio in linux any less. But i did at least learn about the relationship between Alsa and Pulse.

Thanks for the help MoreOrLess. Much appreciated.

---

### Post by inobe on 2011-12-29
how did you figure this out?

---

### Post by Chrus on 2011-12-30
> **inobe said:**
> how did you figure this out?

I was reading a thread about someone only getting stereo out of HDMI, and someone suggested installing pavucontrol because that would give the option to select which output is used (ie: HDMI Stereo or HDMI 5.1).

So I started looking into what pavucontrol was/does. Looked somewhat relevant. Gave it a go... and it worked.

---

