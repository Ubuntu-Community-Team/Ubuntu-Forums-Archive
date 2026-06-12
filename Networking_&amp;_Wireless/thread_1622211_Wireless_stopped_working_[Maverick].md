---
title: "Wireless stopped working [Maverick]"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by sombrancelha on 2010-11-15
Hello,

I'm using Maverick and since yesterday, my wireless hasn't been working. It was working before with Maverick and I don't recall doing any updates that might have changed wireless configurations.

By "doesn't work" I mean it doesn't recognizes any networks, as if the wireless was turned off (there's this button on laptops, but it's turned on). I had that problem some time ago, but rebooting solved the problem, which, now, didn't.

My laptop is a HP dv6420la.

Where to start?

---

### Post by LeMeun on 2010-11-15
hep,

often the command in the terminal:

sudo ifconfig (see what interface is up)

followed by

sudo iwconfig (check your wifi cards)

just copy past the output in this thread

---

### Post by sombrancelha on 2010-11-15
Output of sudo ifconfig:
```

eth0      Link encap:Ethernet  Endereço de HW 00:1b:24:d9:d7:58  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:20 Endereço de E/S:0x6000 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:312 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:312 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:23824 (23.8 KB) TX bytes:23824 (23.8 KB)

```

Output of sudo iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```

---

### Post by LeMeun on 2010-11-15
is ubuntu under virtual box?

what about the output of this commands:
sudo ifconfig -a

sudo lsusb

sudo lsmod

---

### Post by sombrancelha on 2010-11-15
Ubuntu is not under virtual box.

Output of sudo ifconfig -a:
```

eth0      Link encap:Ethernet  Endereço de HW 00:1b:24:d9:d7:58  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:20 Endereço de E/S:0x6000 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:120 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:120 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:9072 (9.0 KB) TX bytes:9072 (9.0 KB)

vboxnet0  Link encap:Ethernet  Endereço de HW 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

output of sudo lsusb:
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

output of sudo lsmod:
```

Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
nvidia               9329739  41 
joydev                  8735  0 
snd_hda_codec_conexant    29736  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
r852                    9536  0 
sm_common               3285  1 r852
snd                    49006  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   34905  2 r852,sm_common
hp_wmi                  5191  0 
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
mtd                    18877  2 sm_common,nand
soundcore                880  1 snd
psmouse                59033  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_nforce2             5179  0 
serio_raw               4022  0 
agpgart                32011  1 nvidia
k8temp                  3132  0 
video                  18712  0 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
sdhci_pci               6339  0 
firewire_ohci          21106  0 
sdhci                  15890  1 sdhci_pci
firewire_core          46643  1 firewire_ohci
sata_nv                19420  3 
led_class               2633  1 sdhci
forcedeth              49433  0 
crc_itu_t               1383  1 firewire_core
pata_amd                8746  0 

```

---

### Post by sombrancelha on 2010-11-16
Today when I turned the computer on, the internet just started working again... Weird...

---

### Post by LeMeun on 2010-11-16
could you type lspci

Sorry i though you had a usb wifi adapter --> lsusb (list usb connected)
lspci will list the cards

What wifi card do you have? which driver did you install?

---

### Post by sombrancelha on 2010-11-16
Output of lpsci:
```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

My wifi card is a Broadcom Corporation BCM4312 802.11a/b/g (rev 02), I'm not sure what is my driver...

PS: As my post was just one minute before yours, I don't know if you saw that it's now working, although I didn't change anything...

---

### Post by LeMeun on 2010-11-16
for the button issue could you type: 
sudo rfkill list

Just in case and let's hope someone else will come help us a bit :)

---

### Post by LeMeun on 2010-11-16
weird but your card show up in the lspci
**03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)**

try the sudo rfkill list 
while is working and post it like that we have a record of it and once the problem occure again (if it does!) please retype the 
sudo rfkill list command and post it.

In the mid time, enjoy your surf ;)

---

### Post by sombrancelha on 2010-11-16
Output of sudo rfkill list:
```

0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by LeMeun on 2010-11-16
good should be like that all the time, if the Hard blocked turn to yes it means that your button is messing around. Soft blocked turn yes is a software blocking i guess

---

### Post by sombrancelha on 2010-11-16
The problem is back.

I noticed that, while the internet was working, the light indicator of the "wireless blocking button" was blue. Now, it's orange. I don't know if that means it's a problem in the button, though...

I've tried the same commands as before, and I have two differences:
lpsci doesn't list my wifi card anymore
sudo rfkill list has a blank output.

---

### Post by LeMeun on 2010-11-17
try pushing the button until it turn bleu again and wait a while (1 or 2 mins) then check if u got back ur internet.
If not try lspci and look for ur card if not there, reboot
see if the light still blue and if the internet is back.

I have a similar thing on my MSI laptop, if i don't use it for a while when i start it the wireless is off is need to push the button to turn it on and usually ubuntu react automatically and bring my interface alive.

I hope you don't have a hardware problem

---

### Post by LeMeun on 2010-11-17
> **sombrancelha said:**
> 

[COLOR="Red"]**My laptop is a HP dv6420la.**[/COLOR]



Anyone with a similar laptop and similar issue?
Any suggestions will be great

---

### Post by sombrancelha on 2010-11-17
I can't get the blue light back, no matter how long or hard I push the button :(

---

### Post by Snicko on 2010-11-17
> **sombrancelha said:**
> I can't get the blue light back, no matter how long or hard I push the button :(

I have the same problem and I cant find any solution to this problem, it's Ubuntu 10.10 that has a problem with this. It should work with Ubuntu 10.04 but i rather wait until there is a fix for this. I think you can disconnect the network button but who wanna do that? I want to solve this problem without touching the hardware.

---

### Post by kiki298 on 2010-11-17
Hey, have a similar laptop to you, dv2500, and a similar problem. But I got it fixed! Went lurking and found this suggestion.

> **Forte125 said:**
> I think I found a solution:

sudo rfkill unblock wifi

Did that, my wireless light came on right away, but I had to restart before I could use the wireless card. Hope it works for you!

---

### Post by Snicko on 2010-11-17
> **kiki298 said:**
> Hey, have a similar laptop to you, dv2500, and a similar problem. But I got it fixed! Went lurking and found this suggestion.



Did that, my wireless light came on right away, but I had to restart before I could use the wireless card. Hope it works for you!
Is it possible that your Wireless network only was software blocket?

What was your output on:
```
rfkill list all
```

---

### Post by kiki298 on 2010-11-17
I have no idea if the code I enter changed anything, but right now, the output is:

 hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I'm assuming since I unblocked the wifi, something previously said yes, but I don't know since I never checked. Are you have the same problem? Maybe just try it out and see if it fixes anything :)

---

### Post by sombrancelha on 2010-11-17
> **kiki298 said:**
> Hey, have a similar laptop to you, dv2500, and a similar problem. But I got it fixed! Went lurking and found this suggestion.

[QUOTE=Forte125;9969573]I think I found a solution:

sudo rfkill unblock wifi

Did that, my wireless light came on right away, but I had to restart before I could use the wireless card. Hope it works for you![/QUOTE]

No success, this command doesn't change anything.

Snicko, are you on 10.04 or did you find a workaround?

---

### Post by sombrancelha on 2010-11-19
I guess downgrading is the way? :(

Would it be a not so important issue, I could live with it and wait for a fix, but no internet is quite problematic...

---

### Post by voncrane on 2010-12-04
> **kiki298 said:**
> Hey, have a similar laptop to you, dv2500, and a similar problem. But I got it fixed! Went lurking and found this suggestion.



Did that, my wireless light came on right away, but I had to restart before I could use the wireless card. Hope it works for you!

"sudo rfkill unblock wifi" worked for me as well....wireless light turned blue from orange but i also had to restart before i could view and connect to my wireless router...

---

### Post by sombrancelha on 2010-12-04
sudo rfkill unblock wifi didn't work for me, when I was having the problem.

However, around a week ago it "magically" started working again, and since then I haven't had any issues. I did all upgrades asked by Ubuntu.

---

