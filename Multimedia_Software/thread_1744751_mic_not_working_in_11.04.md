---
title: "mic not working in 11.04"
date: 2011-04-30
forum: Multimedia Software
---

### Post by ep6 on 2011-04-30
So yeah..yesterday i updated 10.10 to 11.04 and since then my mic doesnt get recognized anymore.
At soundpreference's input i only have 1 option which were 3 before i updated to 11.04 , anyone know how to fix this ?
thanks in advance.

---

### Post by christhecoolboy on 2011-04-30
> **ep6 said:**
> So yeah..yesterday i updated 10.10 to 11.04 and since then my mic doesnt get recognized anymore.
At soundpreference's input i only have 1 option which were 3 before i updated to 11.04 , anyone know how to fix this ?
thanks in advance.

I have the same problem on my Ubuntu Machine, I put my post up ([HERE]("http://ubuntuforums.org/showthread.php?t=1743791")), The Problem that I have is that my computer had Mic before I switched over to ubuntu 11.04 and since switching over, it does not work...

On my settings, I can see a thing called "Internal Audio Analogue Stereo" , it's audio feed is a hissing static noise, to prove this, open terminal and type "alsamixer" in terminal without the quotes and move the right arrow key to the 'Mic' and Press M, you should hear a loud hissing sound, if you do, then you have the exact same as me and I need a solution too... Press M again to mute it and press ESC to close alsamixer...

---

### Post by lidex on 2011-04-30
On an upgrade, the first thing to suspect is old config files (cruft). Try removing old pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

Next this:
> Changing default subdevice configuration

    Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default.

        Open the pulseaudio record meter (pavumeter --record)
        Talk into your chosen device while you carry out the process and watch the meter.
            Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. 

        Use alsamixer -c n (where n is your sound card number, probably 0)
            Press F4 to get to the capture console
            Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up.
            Check the first input source is switched to your chosen plug (Mic, in my case) 
        At this point, you should see the record meter bouncing in response to your voice.
        I found that I had to repeat this procedure each time I wanted to use the Mic, even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized until it was repeated.
        This also works if you use the "Options" tab in the standard mixer app to do the same thing. 

---

### Post by nikunjbadjatya on 2011-05-04
Thanks, 
It fixed my mic problem. (HDA Intel - HP Pavillion DV6000 - Ubuntu 11.04 )

---

### Post by nowtejas on 2011-05-05
I did a fresh install of Ubuntu 11.04 last week and since then my microphone only produced a hissing sound and didn't record any real sound.

I have fixed this issue with a easy step, in terminal, went to ALSAMIXER and there in the source selected "Internal Mic 1" something that was not shown in the GNOME Volume Control > Preferences.

And then I had to turn the recording volume down a little and BINGO it worked perfectly, producing clear sounds. :)

Good luck fellas!! :)

---

### Post by aum11 on 2011-05-06
Thanks that fixed the mic problem on a Dell 1558 studio with the following:

$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

