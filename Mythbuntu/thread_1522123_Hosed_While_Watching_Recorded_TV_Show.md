---
title: "Hosed While Watching Recorded TV Show"
date: 2010-07-01
forum: Mythbuntu
---

### Post by GraysonPeddie on 2010-07-01
Version info:
Ubuntu 10.04 + MythTV 0.23 (not using Mythbuntu)
MythTV backend is in my server; I use my HTPC as a MythTV frontend.

While watching Star Trek - The Next Generation (We'll Always Have Paris), which I've recorded, MythTV got hosed with audio buffer overflow and I can't get out of it without finding a process using htop and kill it. What I mean by "hoses" is it will not respond at all. htop shows that mythfrontend is using about 100% of the CPU resources. During normal playback CPU usage is no greater than 5%.

This happens because when my backend records a TV show, it recorded a loss of signal. The backend did not freeze during the recording, but the frontend did. I'm not sure if it's equivalent to unplugging a cable from my CM-4221 antenna, though, but MythTV frontend is like this when it can't compensate for the loss of signal. I have no idea what I'm talking about, but this is the way I think about it. Anyway, let's get in with the logs.

```
grayson@htpc:~$ mythfrontend > mythtv_problem.txt
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
^CSignal: Interrupt
Ungrabbing XVideo port: 131
Segmentation fault
grayson@htpc:~$ 
```

I have attached a text file as it's very large.

So anyway, up until 18:15:56.866, it is working okay before it starts to cause problems 30 seconds later in. Then, I get a stream of message about the audio buffer overflow.

What can I do? I can restart the video again, but then I'll have to skip 30 seconds ahead a couple of times and skip back 5 seconds almost right after the time when MythTV-frontend got hosed with a bunch of audio buffer overflow errors.

I have a question. Can't MythTV frontend just play the video and pick up the audio when the audio signal comes back onliine?

Here is my computer specs:

AMD Athlon X2 4050e CPU
ECS A780GM-A Ultra
750GB Hard Drive (with Windows Vista Ultimate 64-Bit and Ubuntu 64-Bit)
Ubuntu kernel: 2.6.32-23-generic

LSPCI:

```
grayson@htpc:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:05.0 Multimedia audio controller: Creative Labs SB X-Fi
grayson@htpc:~$ 
```

---

### Post by willebanks on 2010-07-02
Just curious...has the problem been occurring all along or did it just start happening?

Did you just update to Lucid?

Just wondering if a file or files have become corrupted.

My 2 cents!

Will

---

### Post by uncle hammy on 2010-07-02
I have had the odd time where a recording got a bad section, and the frontend just can't deal with it when playing back.  To get around it, I simply advance to just before the position it dies at, and do a 30 second skip ahead over it.

---

### Post by GraysonPeddie on 2010-07-02
I just installed a fresh copy of Ubuntu 10.04.

Also, not only this happens in the recording, this also happens when I watch Live TV and fiddle with an antenna when I change its angle or find a "sweet spot" (meaning, when moving it to a different location). I must note, however, that MythTV will take me back to the main menu when there is a loss of signal (with an error message displayed). But sometimes, it will hose/lock up and cause the CPU usage to go up to 100%. (I do have an antenna for testing (Terk FDTV1A), which is what I'm using before I give it to my loved one, so I already have an antenna that is stationary (Channel Master 4221 -- used indoor/stationary.) In case there's a bad section in my recorded video, it will only hose/lock up and that's about it.

For watching live TV, I really don't know why the frontend can hose/lock up when it should just give me an error message.

My guess is, to prevent your recordings from having bad sections where it'll just lock up, you have to have your antenna setup properly and that you get a very strong signal above 80%. 70% might be okay, but if the signal strength drops down to 60% or lower, you'll probably have bad sections in your recording.

I also seen this happen in Karmic, too.

---

