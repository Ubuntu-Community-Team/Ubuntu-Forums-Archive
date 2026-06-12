---
title: "GA-MA78GM-US2H HDMI Audio Problems"
date: 2009-06-24
forum: Multimedia Software
---

### Post by agentsmith23 on 2009-06-24
I am having trouble getting audio out using hdmi on this motherboard. I have tried using different distros and the only one that audio fullt worked on was mandriva however I ran into some really bad issues with mythtv under mandriva so I decided to come back to ubuntu and replicate what mandriva was doing. I am still a linux newbie so please bare with me if more info is needed please just ask and I will gladly get it for you.

Under Ubuntu when I bring up the volume control and select the device HDA ATI HDMI (Alsa Mixer) I have two tabs available (Switches and Sound Theme). Switches has IEC958 available and it is checked. This is pretty much the same way it was in Mandriva except with the volume controller that was used in that distro there was an area whee I could select a master input and I had two choices HDMI or Analog. By default the IEC958 switches were off and the HDMI out was muted but just by selecting the switches and unmuting the HDMI out audio worked perfectly in mandriva. How can I get it to do the same in Ubuntu?

I ran lspci in both mandriva and it Ubuntu and it came back identical.

Here is the lspci out from ubuntu:

```
dnd@dnd-htpc:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by agentsmith23 on 2009-06-25
Anyone? Is there anyway to just check how the audio is setup under mandriva and then repeat it under ubuntu?

Thanks,
Dave

---

### Post by agentsmith23 on 2009-06-26
bump
please help

I have been able to replicate the gui part of what mandriva is doing but I don't have the option of selectiong the HDMI output.

---

### Post by carmaa on 2009-10-31
*bump*

---

### Post by maydog on 2009-10-31
I have the same motherboard and was able to successfully get all the sound routed through HDMI by compiling the latest catalyst video and realtek sound drivers for the 889A and creating a .asoundrc file.

Use "aplay -l" to find out what device the hdmi is and then create an asoundrc file like this.

pcm.!hdmi {
    type hw
    card 1
    device 0
}


pcm.!default {
   type plug
   slave { 
	pcm "hdmi"
	}	
}

This seemed to work great for me, I have since installed a NVIDIA card to try getting VPDAU to work so I no longer use the setup as it seems that the two drivers do not work well together.

Good luck

---

