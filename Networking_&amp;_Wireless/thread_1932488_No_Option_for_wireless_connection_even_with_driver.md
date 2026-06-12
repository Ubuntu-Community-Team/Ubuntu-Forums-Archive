---
title: "No Option for wireless connection even with drivers"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by aamir147 on 2012-02-27
I am trying to configure a Ralink Rt3090 wireless card and have the drivers for it as well as ndisgtk installed. Nothing has seemed to work for me. I do have access to an ethernet connection sometimes but I do not know what to do. I am a complete noob at Linux. Also I used Wubi to install if that matters. 
Thanks

---

### Post by praseodym on 2012-02-27
Hi,

for this device you dont need ndisgtk, uninstall ndiswrapper completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
Check the device, kernel, and drivers loaded:

```
lspci -nnk | grep -iA2 Ralink
uname -a
lsmod
```

---

### Post by phillipmaloney on 2012-02-27
on the forums page at the upper right hand corner there is a search box. type in ralink 3090 and there are 148 results scroll down and find one marked solved and that should help you out. sorry i can't help you. i use a different card.

---

### Post by aamir147 on 2012-02-27
> **phillipmaloney said:**
> on the forums page at the upper right hand corner there is a search box. type in ralink 3090 and there are 148 results scroll down and find one marked solved and that should help you out. sorry i can't help you. i use a different card.

I tried many solved forums and it led to the option of wifi disappearing. other solutions didn't work for me.

---

### Post by aamir147 on 2012-02-29
Ok do I removed ndiswrappergtk as well as rebooted multiple times, still I dont have an option that allows me to enable wireless. The latest drivers are installed for my card. The card works perfectly in windows but not even an enable option in ubuntu. also when I run a network card check the card shows up as unclaimed.

---

### Post by praseodym on 2012-02-29
Which driver did you install? Please show the outputs from above, plus

> egrep 'rt3|rt2' /etc/modprobe.d/*
cat /etc/modules

---

### Post by aamir147 on 2012-02-29
> **praseodym said:**
> Which driver did you install? Please show the outputs from above, plus

I was unable to run the last piece of code you gave me successfully however, I attached a screenshot of my latest driver in ubuntu package manager.

> aamir@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h Processor Root Complex [1022:1705]
	Subsystem: Advanced Micro Devices [AMD] Family 12h Processor Root Complex [1022:1705]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9648]
	Subsystem: Lenovo Device [17aa:3971]
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1714]
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 12h Processor Root Port [1022:1709]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 12h Processor Root Port [1022:170b]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7804]
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:12.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: ehci_hcd
00:13.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 13)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
	Subsystem: Lenovo Device [17aa:397b]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lenovo Device [17aa:f101]
	Kernel modules: rt2800pci
aamir@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
aamir@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   18436  2
rfcomm                 47946  0
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0
ppdev                  17113  0
vesafb                 13809  1
joydev                 17693  0
binfmt_misc            17540  1
rts5139               351143  0
snd_hda_codec_realtek   330769  1
uvcvideo               72711  0
videodev               92992  1 uvcvideo
acer_wmi               23948  0
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_hdmi     32040  1
snd_hda_intel          33390  2
snd_hda_codec         104931  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73882  0
serio_raw              13166  0
k10temp                13166  0
i2c_piix4              13301  0
snd_seq_midi           13324  0
snd_rawmidi            30547  1 snd_seq_midi
ideapad_laptop         13871  0
snd_seq_midi_event     14899  1 snd_seq_midi
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
fglrx                2967808  87
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19412  0
wmi                    19256  1 acer_wmi
snd                    68266  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  1
libahci                26861  1 ahci
r8169                  52788  0


If this doesn't make sense then I copied the contents into a word document in ubuntu however word doesn't read it natively.

---

### Post by praseodym on 2012-03-01
Load the regular driver:

> sudo modprobe -v rt2800pci

---

### Post by aamir147 on 2012-03-02
> **praseodym said:**
> Load the regular driver:

I ran the script above however it did not work, I have attached the sreenshot to show what happened. I believe it ran correctly but still no option to enable wireless yet.

Edit: Do you think I should Uninstall and reinstall the drivers to see if that works?

---

