---
title: "LG tv And hdmi sound"
date: 2014-03-29
forum: Multimedia Software
---

### Post by zabalaz on 2014-03-29
hi, ive been trying to get sound from my lg tv for a couple of days now and i have failed miserably, i am using ubuntu 13.10 the tv is lg. everything works fine on my second tv so dont think its an issue with my laptop or cable, i have installed gnome alsa mixer but it doesnt look like others i have seen images of. has anyone managed to sort this out and if you have could you tell me how before i lose all sanity, thanks

---

### Post by pqwoerituytrueiwoq on 2014-03-29
is the sound chip for your hdmi on your gpu? mine is on my nvidia gpu
before 14.04 i had to change the device untill i found the working one
i did this in the configuration tab of pavucontrol

---

### Post by zabalaz on 2014-03-30
hi, ive altered my sound settings via pavucontrol to hdmi and tried it, the sound bar moves as though i should be getting sound but still nothing. im using a hp pavilion laptop with nvidia graphics. im not sure how to check my sound chip after going through so many threads. i just find it odd that it works on my toshiba tv and not on my lg tv. thanks for your help

---

### Post by zabalaz on 2014-03-30
if it helps this is the result of sudo lspci from multimedia section

  *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:d7200000-d7203fff

---

### Post by pqwoerituytrueiwoq on 2014-03-30
in my exp it is easter to disable hdmi audio and use analog by tricking the tv into thinking it is a dvi connection (not ideal for laptop)
but go to the output devices tab and make the hdmi audio default or disable analog audio on the configuration tab, audio playing apps may need a restart

---

### Post by SeijiSensei on 2014-03-30
> **zabalaz said:**
> hi, ive altered my sound settings via pavucontrol to hdmi and tried it, the sound bar moves as though i should be getting sound but still nothing. im using a hp pavilion laptop with nvidia graphics. im not sure how to check my sound chip after going through so many threads. i just find it odd that it works on my toshiba tv and not on my lg tv. thanks for your help

Look in the other tabs as well.  You may find that Output Devices is still set to analog even if you switch the overall configuration to HDMI.

I have Kubuntu 14.04 running on an HP dv6t laptop with an ATI card connected to an LG 5710 via HDMI.  Aside for the poor quality sound the TV produces, it works as expected.  I don't have an audio receiver with HDMI inputs, so I also have an analog connection from the laptop to the audio system for when I care about the quality of the sound.

---

### Post by zabalaz on 2014-03-30
hi thanks, so hdmi sound does work on lg tvs then, i dont get poor image quality just no sound at all, i think i may upgrade to ubuntu 14.04 and see if that sorts it out

---

### Post by zabalaz on 2014-03-30
hi [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") i checked output devices and the dropdown menu doesnt drop down because its only giving me one option,

---

### Post by pqwoerituytrueiwoq on 2014-03-30
perhaps you picked the wrong hdmi entry on the other tab
sometimes if you mess with it enough nothing will work and you have to reset you sound then then it works 1st try (my exp)
to reset you sound config delete [FONT=courier new]~/.config/pulse[/FONT] logout and login

---

### Post by efflandt on 2014-03-30
Are you saying that the same exact laptop and cable that work with one TV do not work for audio your LG TV? I would first look at volume level and audio settings on the TV itself. For example is **TV Speaker :On**?

I have been using a 32" 1080p HDTV as a monitor for years. I know that in earlier Ubuntu versions you had to fiddle around with some settings related to alsa or pulse audio and pick the right nvidia sound device to get HDMI audio working. But I think since 12.04 came out, it just works. I normally use analog 2.1 speaker system with subwoofer. But one time after using a wireless digital headset I unplugged the dongle for that and was quite surprised that Ubuntu automatically shifted over to audio on my HDTV. The reason that was a surprise is because I am using a DVI to HDMI cable with no other audio to the TV. So somehow my GTX 550 Ti was able to feed audio out its DVI to HDMI.

---

### Post by Yellow Pasque on 2014-03-31
> **zabalaz said:**
> im using a hp pavilion laptop with nvidia graphics.

Be more specific (model number?). Is it an Optimus laptop (one with hybrid intel/nvidia graphics)?
Post output of lspci:
```
sudo update-pciids
lspci -k
```

---

### Post by zabalaz on 2014-03-31
> **Temüjin said:**
> Be more specific (model number?). Is it an Optimus laptop (one with hybrid intel/nvidia graphics)?
Post output of lspci:
```
sudo update-pciids
lspci -k
```


hi as requested

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Device 360b
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Kernel driver in use: pcieport
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [GeForce 9200M GS] (rev a1)
    Subsystem: Hewlett-Packard Company GeForce 9200M GE
    Kernel driver in use: nvidia
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: r8169
03:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 137b
    Kernel driver in use: ath5k
reece@reece-HP-G70-Notebook-PC:~$ sudo update-pciids
Downloaded daily snapshot dated 2014-03-31 03:15:01
reece@reece-HP-G70-Notebook-PC:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Device 360b
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Kernel driver in use: pcieport
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [GeForce 9200M GS] (rev a1)
    Subsystem: Hewlett-Packard Company GeForce 9200M GE
    Kernel driver in use: nvidia
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 360b
    Kernel driver in use: r8169
03:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 137b
    Kernel driver in use: ath5k

---

### Post by zabalaz on 2014-03-31
> **efflandt said:**
> Are you saying that the same exact laptop and cable that work with one TV do not work for audio your LG TV? I would first look at volume level and audio settings on the TV itself. For example is **TV Speaker :On**?

I have been using a 32" 1080p HDTV as a monitor for years. I know that in earlier Ubuntu versions you had to fiddle around with some settings related to alsa or pulse audio and pick the right nvidia sound device to get HDMI audio working. But I think since 12.04 came out, it just works. I normally use analog 2.1 speaker system with subwoofer. But one time after using a wireless digital headset I unplugged the dongle for that and was quite surprised that Ubuntu automatically shifted over to audio on my HDTV. The reason that was a surprise is because I am using a DVI to HDMI cable with no other audio to the TV. So somehow my GTX 550 Ti was able to feed audio out its DVI to HDMI.


yes thats what i am saying, hdmi on tv works as i can watch and hear my sat box.

---

### Post by zabalaz on 2014-03-31
> **pqwoerituytrueiwoq said:**
> perhaps you picked the wrong hdmi entry on the other tab
sometimes if you mess with it enough nothing will work and you have to reset you sound then then it works 1st try (my exp)
to reset you sound config delete [FONT=courier new]~/.config/pulse[/FONT] logout and login

just want to make sure i understand correctly. you want me to delete my pulse folder in .config folder the turm off then back on laptop, will that regenerate the folder again.

---

### Post by zabalaz on 2014-04-01
sorted thanks, i updated to ubuntu 14.04 and as if by magic. boooooom

---

