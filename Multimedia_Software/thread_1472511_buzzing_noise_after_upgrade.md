---
title: "buzzing noise after upgrade"
date: 2010-05-04
forum: Multimedia Software
---

### Post by suomaf on 2010-05-04
Hey guys,

Did a fresh install of 10.04 and there is an annoying buzzing noise. It does not seem to go away even when I am moving the mouse and I have tried everything on the sound preferences. The card was working in 9.10.

```

lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


```

```

 cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 22


```

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I am using a acer e-machine if that is useful for anyone. Does anyone know what I should try?

Thanks

---

### Post by Alan James on 2010-05-04
I have had the same thing happen after lots of trouble shooting found it to be that my mic line was turned all the way up. Use the "alsamixer" command to check if all of your settings are set correctly.

---

### Post by suomaf on 2010-05-04
Thanks for the reply, still no good.. played with just about every setting.. the buzzing is constant through out. Its only when I adjust the settings.. it seems to "buzz-tick" Any ideas?

---

### Post by suomaf on 2010-05-04
oopps... I replaced the wires and it worked... typical software engineer.. its always the software's problem first. <bonks self>

---

### Post by alejandro.mc on 2010-05-29
I replaced the wires and the problem is still there..

H E L P

---

### Post by alejandro.mc on 2010-06-01
Help

---

### Post by alejandro.mc on 2010-06-01
Doing a LOOOOOTTTTT of digging I found this:



"


Open up alsamixer and lower your PCM value. This will fix the distortion issue.

Next...

To fix this problem, you'll need to change the settings file found in /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common (To the #$##$ who put the config files here on Ubuntu, put them somewhere in /etc.)

Under [Element PCM] you'll need to tweak some settings

[Element PCM]
switch = mute
volume = zero
override-map.1 = all
override-map.2 = all-left,all-right

You might use "ignore" versus "zero", but PulseAudio in its infinite wisdom will set PCM to 100 on reboot.



"


That is from:

[http://www.reddit.com/r/linux/comments/bzhx2/](http://www.reddit.com/r/linux/comments/bzhx2/)







Apparently it got fixed. I'll keep testing.

---

### Post by superbullock on 2010-06-03
I'm still having buzzing issues after changing settings under [Element PCM] any other ideas?

---

### Post by alejandro.mc on 2010-06-04
Did you:

sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common

and changed and saved "Element PCM volume" to zero??

After doing that you are suppose to restart, then lower the PCM bar in the program Gnome ALSA Mixer (do you have it installed? the GUI is useful - not the console version that lacks features..), and leave the rest (front, center, etc.) maxed out, you should use from that on the Master bar and the remote control of the speakers to change volume..

That should fix it..

Cheers!

Alejandro
Buenos Aires
Argentina

---

