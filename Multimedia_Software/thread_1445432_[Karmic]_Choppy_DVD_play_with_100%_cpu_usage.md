---
title: "[Karmic] Choppy DVD play with 100% cpu usage"
date: 2010-04-02
forum: Multimedia Software
---

### Post by chris1379 on 2010-04-02
I just did a fresh install of Ubuntu 9.10 Karmic on my Sony PCG-F580K notebook computer. This is a PIII 700 MHz computer with 384MB RAM and Neomagic 256XL+ video. Most videos play just fine except for DVD's. It drops frames like crazy and pegs the CPU at 100%. This is with VLC media player. Totem Movie Player is even worse. In contrast, I can play an Xvid video with only 60% CPU usage. I also have Win2k on here, which only uses 60% of the CPU using Cybermedia Power DVD. I didn't check the CPU usage with Hardy but It did play OK. One thing that does puzzle me is that VLC shows 15 streams under codec information. 3 of them are video using mpgv codec, 3 are audio using a52, and the rest are subtitles using spu. Htop shows vlc using 37%, X using 33%, and Pulseaudio using 10%. Disabling the audio reduces CPU usage to 90% but disabling video takes it down to 30%. I'd be happy to provide more details if someone can help me.

Thanks,
Chris

---

### Post by chris1379 on 2010-04-04
I went back to my backup of Hardy and played the DVD in VLC again. This is what I got:
CPU    55%

VLC    27%
VLC    20%
usr/bin/x    10%
So what's the difference here? I read something about MTRR configuration being a possible cause but I have no idea how I would configure it. I checked it in both Karmic and Hardy and this is what I got for Hardy:
```
~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 256MB: write-back, count=1
reg01: base=0x10000000 ( 256MB), size= 128MB: write-back, count=1
reg02: base=0xfc000000 (4032MB), size=   8MB: write-combining, count=1

```
I Think the first 2 lines in Karmic are the same but the 3rd one is missing. From what I've read, the write-combining is needed for video accelleration. How do I duplicate this in Karmic?

---

### Post by 2hot6ft2 on 2010-04-04
> **chris1379 said:**
> I went back to my backup of Hardy and played the DVD in VLC again. This is what I got:
CPU    55%

VLC    27%
VLC    20%
usr/bin/x    10%
So what's the difference here? I read something about MTRR configuration being a possible cause but I have no idea how I would configure it. I checked it in both Karmic and Hardy and this is what I got for Hardy:
```
~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 256MB: write-back, count=1
reg01: base=0x10000000 ( 256MB), size= 128MB: write-back, count=1
reg02: base=0xfc000000 (4032MB), size=   8MB: write-combining, count=1

```
I Think the first 2 lines in Karmic are the same but the 3rd one is missing. From what I've read, the write-combining is needed for video accelleration. How do I duplicate this in Karmic?
Have you tried manually adding the line to /proc/mtrr ?
```
gksu gedit /proc/mtrr
```
and copy and paste the missing line into it.
You can always remove it if it doesn't help.

---

### Post by 2hot6ft2 on 2010-04-04
Double post. Mod please remove.

---

### Post by chris1379 on 2010-04-04
No, not yet. I'm pretty good at troubleshooting, being an electronics tech, but I'm  still new to Linux. I had no idea where or how to enter the changes. I'm also trying to gather as much info from Hardy as I can before I go back. Is there anything else I should check? I don't have enough HDD space to boot Hardy and Karmic so I have to backup/restore with Clonezilla.
I also noticed that VLC has lower resources on every type of video in Hardy but it's the only program that does. Totem and Gxine still max the CPU in Hardy. I'm using VLC version 0.9.9a in Hardy but version 1.05 or 1.02 in Karmic. Could that also be the difference? I don't think I can use the older version in Karmic or the newer version in Hardy to test, can I?

Edit: I just checked with Totem in Hardy again and I was wrong. It doesn't max the CPU but uses about 90%. It's completely watchable. I also see that it uses Pulseaudio but VLC doesn't. I removed the plugin and it dropped to 65%. I'm tempted to remove pulseaudio completely but my bluetooth actually works in Karmic. Unfortuneately, I don't have enough CPU for it to work with Skype (sigh).

---

### Post by chris1379 on 2010-04-04
OK, I'm back in Karmic so I tried what you said to try. I can't edit  proc/mtrr directly as it's in use by the system and seems to change. I think I need to add the configuration somewhere and then reboot but where?

Edit: I had to enter
sudo -s
echo "base=0xfc000000 size=0x800000 type=write-combining" > /proc/mtrr

My CPU load did decrease to around 85% with Pulseaudio active and quite a few other things open so I'd have to say success. Now the question is how do I make it stick and is this entirely right. The info from lspci -vvnn is:

01:00.0 VGA compatible controller [0300]: Neomagic Corporation NM2380 [MagicMedia 256XL+] [10c8:0016] (rev 10)
    Subsystem: Sony Corporation Device [104d:8088]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+ DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 128 (4000ns min, 63750ns max)
    Interrupt: pin A routed to IRQ 9
    Region 0: Memory at fc000000 (32-bit, prefetchable) [size=32M]
    Region 1: Memory at fe800000 (32-bit, non-prefetchable) [size=4M]
    Region 2: Memory at fec00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel modules: neofb

---

### Post by chris1379 on 2010-04-14
After testing several distros, I have determined that this is a bug in the X-server or Neomagic driver. It is also present in Jaunty, Fedora, and OpenSuse. The workaround seems to be putting the line:
```

echo "base=0xfc000000 size=0x800000 type=write-combining" >  /proc/mtrr
```in /etc/rc.local. The problem is (as pointed out by others) this doesn't stick if X is restarted. I also have the issue of X using 20% CPU versus 10% in Hardy but if I can make the fix work every time X is started, I guess I'll be happy.
Since this is not an Ubuntu-specific bug, where would I file a bug report?

As a side note, I can use Skype with Bluetooth now. I just had go to Skype Options>Sound Settings and uncheck the box "Allow Skype to automatically adjust my mixer levels".

---

