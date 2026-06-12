---
title: "RME HDSP 9632 setup problem"
date: 2009-07-06
forum: Multimedia Software
---

### Post by zob on 2009-07-06
Hi.
I just got myself a 2. hand HDSP 9632. I've installed it already on my XP-partition and everything works fine.

Now trying to install on linux is slightly more complicated it seems.

I've unplugged every other sound device usb and pci, I have. I've switched off the on-board sound card. So everything should be ready.

I can make it do the "test sound", with a lot of clipping though (I guess it's just way to loud), but no other sound. And I have to choose the sound card. If I choose autodetect, I don't get any sound.

Strange thing is the hdspmixer actually shows signal, but I hear nothing.

In pulseaudio it is not detected as a hardware output.

But everything looks fine to me.

```
lars@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DSP [Hammerfall DSP], device 0: RME Hammerfall HDSP 9632 [RME Hammerfall HDSP 9632]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lars@ubuntu:~$ hdsploader
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : RME Hammerfall HDSP 9632 at 0xfdef0000, irq 19

```

```
lars@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation nForce3 250Gb Host Bridge [10de:00e1] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 250Gb LPC Bridge [10de:00e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation nForce 250Gb PCI System Management [10de:00e4] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 EHCI USB 2.0 Controller [10de:00e8] (rev a2)
00:05.0 Bridge [0680]: nVidia Corporation CK8S Ethernet Controller [10de:00df] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation CK8S Parallel ATA Controller (v2.5) [10de:00e5] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation nForce3 Serial ATA Controller 2 [10de:00ee] (rev a2)
00:0a.0 IDE interface [0101]: nVidia Corporation nForce3 Serial ATA Controller [10de:00e3] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge [10de:00e2] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge [10de:00ed] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) [1002:4170]
02:09.0 Multimedia audio controller [0401]: Xilinx Corporation RME Hammerfall DSP [10ee:3fc5] (rev 9a)

```

```
lars@ubuntu:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: RME Hammerfall DSP
       vendor: Xilinx Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=RME Hammerfall DSP latency=255 module=snd_hdsp

```

As you everything looks fine, I think. Only problem is that I don't have sound. That's why I'm thinking that it's just 'cause I'm new to this card. I probably just have to click a button somewhere. Please tell me where.

Only strange things are the pulseaudio naming it null-output, and not showing hardware outputs. And in the hdspmixer I see signal in something called "out 1" and "out 2", however it makes no sound. When it does make a sound (forcing from "test sound" in the gnome sound setting - which is the only place I can get sound), it shows signal on all outs. Maybe it's a question of directing the sound to the right outs, but there doesn't seem to be a way of doing that.


Just to make it all more confusing, I did have sound the right way just once. It way right after loading the snd-hdsp module manually the first time. Then I wrote it into the /etc/modules/ and rebooted. No sound! Later I have tried to unload the module and load it manually without succes.

Please help me. Someone must know!

---

### Post by zob on 2009-07-07
Ok. Just managed to get some sound by changing the virtual wiring of the HDSP mixer. Something like changing the right outputs to the right playback channels. I does sound gooooood!

Now I can get sound from vlc and firefox/flash. But still no sound from rhythmbox. Is there somewhere you can force the output of rhythmbox.

Well. As you see. This is no longer a problem with the HDSP 9632, it's now a problem of getting all applications to use it.

Oh. Of course. Now I just have the typical pulseaudio error. I don't know why flash and vlc actually work (well vlc does because I know where the settings are to force the output to a certain card), but when I look at the pulseaudio volume control, I can see fx the songbird or rhythmbox signal under the playback tab. However as my hardware is not detected by pulseaudio, I can't move the stream to other than something called the "Null Output", which doesn't end op on my HDSP.

So now I think it's a problem of getting pulseaudio to "see" my HDSP card (at the moment I still have no other soundcard installed).

Anyone can help with pulseaudio?

---

### Post by thorgal on 2009-08-03
quickly, as I am on vacation until August 18, jack and pulseaudio are layers that talk to the ALSA driver. You will have to make pulse and jack coexist. There's a long thread about it not far away in these forums. Held og lykke :)

---

### Post by zob on 2009-08-06
Thanks Thorgal.

I'm afraid I'll have to ask you a couple of questions when you get back home. For now I have uninstalled pulseaudio. I works fine with alsa only. But it is quite annoying that alsa (in my setup) only allows one stream of sound, and I have to restart apps all the time to make them sound. I guess all of this has a solution or nobody (except fools like me) would be using linux.

---

