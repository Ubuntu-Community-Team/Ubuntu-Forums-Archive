---
title: "I can't turn on the wireless ?"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by markonato on 2009-06-26
First of all I would like to sya that I'm totaly begginer with Linux. I just downloaded and somehow instal a new ubuntu 9.04. I have a problem because my wireless wont work. I have a button on my laptop which is not responding to mu presing, it wont light. It works perfect under windows but here just wont work. I read some instruktions but all of them requares to get some upgrade or something, but how can I do then when i cant get on network?? I can't use cable eather. The only thing I can do is that I can download from windows and then try to instal it in linux, if this can work somehow...
I have one more question and its regarding the graphict. Is it normaln that I can only use 800X600 resolution? The icons are big and picture is not very smooth, or maybe its just the way it is. Ok anyway I would like the answer on my first question I can deal with this resolution. Thank to all

---

### Post by X_Splinter on 2009-06-26
Try write in the console:

```
sudo ifconfig wlan0 up
```

---

### Post by Sub101 on 2009-06-26
The resolution is probably because you arent using the drivers, which would normally be downloaded but arent as you don't yet have internet up.

Do you know what wireless card you are using? 

What does iwconfig return?

---

### Post by markonato on 2009-06-26
I just tried "ifconfig wlan0 up" and o got this "ERROR while getting interface flags: No such device
"
I'm using Atheros card, I mean in windows that what is say.

---

### Post by X_Splinter on 2009-06-26
> **markonato said:**
> I just tried "ifconfig wlan0 up" and o got this "ERROR while getting interface flags: No such device
"
I'm using Atheros card, I mean in windows that what is say.

So it is as Sub101 said you dont have the drivers installed. You must connect to the internet in order to install them.

---

### Post by wojox on 2009-06-26
Open Console 

```
 sudo iwconfig
```

---

### Post by markonato on 2009-06-26
Ok, so somehow if i get a cable connection it should work? And if cable connection work, how I instal drivers then?

---

### Post by X_Splinter on 2009-06-26
> **markonato said:**
> Ok, so somehow if i get a cable connection it should work? And if cable connection work, how I instal drivers then?

First copy paste what shows when you type in the console
```
sudo iwconfig
```

---

### Post by markonato on 2009-06-26
sudo iwconfig  

    
lo          no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



this is what i got

---

### Post by markonato on 2009-06-26
On this forum i found some commands, i run them and this is what i got. Just thought maybe it can be usefull?..

lspci



00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge:
 Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)






iwconfig wlan0


wlan0     No such device








lsmod



binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
joydev                 18368  0 
ndiswrapper           193436  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
acer_wmi               24260  0 
sdhci_pci              15232  0 
led_class              12036  1 acer_wmi
k8temp                 12416  0 
serio_raw              13316  0 
sdhci                  23940  1 sdhci_pci
pcspkr                 10496  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
forcedeth              61712  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit








iwlist scan


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


pan0      Interface doesn't support scanning.



sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...

---

### Post by markonato on 2009-06-26
No one can help me with this??

---

### Post by X_Splinter on 2009-06-26
> **markonato said:**
> No one can help me with this??

I can't but I pretty sure someone can, just wait for reply

---

### Post by wojox on 2009-06-26
Here follow the instructions on this link
[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

---

