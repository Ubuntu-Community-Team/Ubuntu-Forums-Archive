---
title: "USB sound card (m-audio mobile pre) not recognized"
date: 2009-10-23
forum: Multimedia Software
---

### Post by JC Cheloven on 2009-10-23
I'm trying to use the M-Audio Mobile Pre audio card, which seems to be supported in alsa as for 
[http://alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://alsa-project.org/main/index.php/Matrix:Vendor-MAudio)

It appears as a usb device: ```
jc@emachin:~$ lsusb
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0763:2804 [COLOR="Red"]Midiman M-Audio MobilePre DFU[/COLOR]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
But it isn't recognized by alsa (the NVidia is the internal one):
```
jc@emachin:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: ALC888 Analog [ALC888 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```
```
jc@emachin:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 21
```
Also, the lsmod command doesn't show anything I can recognize as a kernel module for that card (I'd perhaps expect "snd-usb-audio"...)
Finally, I did a search through the outout of dmesg, and can't find any instance of the words "snd" or "audio". What is worse, I can't find the word "error" either. 

I realize it's a difficult one. Any ideas would be appreciated.

---

### Post by AutoStatic on 2009-10-24
You need to install the madfuload package. This package will fetch the right firmware for your device so the snd-usb-audio module can make use of your M-Audio device.

---

### Post by JC Cheloven on 2009-10-24
> **AutoStatic said:**
> You need to install the madfuload package. This package will fetch the right firmware for your device so the snd-usb-audio module can make use of your M-Audio device.

Thank you for pointing me in the right direction. But I don't find my way around as yet (perhaps I don't understand madfuload?). Here's what I did:

- Installed mafuload with synaptic. Plugged my usb card. No improvement: only the internal soundcard is seen by "aplay -l" or in /proc/asound/cards. The related records in dmesg after plugging in, are: > [  664.140030] usb 2-1: new full speed USB device using ohci_hcd and address 2
[  664.381977] usb 2-1: configuration #1 chosen from 1 choice

- I see with lsmod that no module "snd-usb-audio" is loaded, even after reboot. I tried loading it with "sudo modprobe snd-usb-audio". Now lsmod shows here and there some references to snd-usb-audio, but "aplay -l" again shows only the internal card.

- Reading [this thread]("http://ubuntuforums.org/showthread.php?p=5300948"), I realize that what we're triyng to do is to run the firmware that would be used in a windows install. I don't know if the thread applies to jaunty (it is reported as to work in intrepid, though). I also found that the firmware file for my card is ma004103.bin, which I've got. I've tried to run madfuload from command line, trying to supply the firmwware file above. But the help of madfuload is so scarce that I didn't manage to run it properly (always says "please supply a firmware file", for every combination of the "-f" and "-D" specifiers I've tried).

- Also from that post, I saw that an udev rule is expected to be created in /etc/udev/rules.d/42-madfuload.rules, but there isn't such.

- I tried unistall from synaptic and to complile madfuload [from here]("http://sourceforge.net/projects/usb-midi-fw/files/madfu-firmware/1.2/madfuload-1.2.tar.gz/download"), but it fails because "I need udev version 057 or later". Strange enough, as I think jaunty comes with a later version.

Any thougts, please? Perhaps about the command-line madfuload bit?

---

### Post by AutoStatic on 2009-10-24
Unfortunately I do not own such a device myself so I can't play around with madfuload.
As for the udev rules, those have been moved to /lib/udev/rules.d since Jaunty, so you could check there.

---

### Post by JC Cheloven on 2009-10-26
In fact, I should have carrying on reading the mentioned thread, as in post #23 another user has added pertinent and updated (jaunty) info. He got working an usb soundcard of the same family as mine. One of the half a dozed for which madfuload applies, indeed.

Unfortunately, I've been unable to get mine working, despite my very good feelings looking at that post. I did everything the other user did, but no avail. Perhaps there is something different/unexpected in my soundcard (it is from the times when the MobilePre was launched, more than 10 years ago I think). Modern MobilePres are reported as to work out of the box in ubuntu, so there must have been some evolution in the hardware.

I've also tried many other distros this weekend (most of them in live cd mode), bun none does accept my soundcard. These are: 
[INDENT]64studio
Mepis7.8
Mandriva2009
Fedora8
Opensuse (this one don't even see my internal soundcard)
Puppy4
Musix
UbuntuStudo8.04 (is the recommended one)
Knoppix (yes, in my despair I even tried that)
[/INDENT]

So I'm leaving my efforts. 
I can either keeping my hardware and using it just fine under windows, or buying a supported usb soundcard. As I like free software too much, perhaps it is time to make a brave resolution and throw away my previous soundcards (this mobilepre and a tascam fw1804, which is excelent, but never will work under linux). Anyone interested? 

@autostatic:  Thank you very much. Your pointings were clear and useful. And I keep best memories from dutch people, since an intercourse we had with the Utrechtsch Studenten Concert by 2000 :-)

---

