---
title: "NEwBIE: M-Audio Delta 1010 LT trouble"
date: 2010-05-10
forum: Multimedia Software
---

### Post by Greg Zell on 2010-05-10
Hi,

quite good at Windows, I made the step and switched to Ubuntu two days ago...

As expected, this Linux-World is very new and strange for me.

I encounter many problems, the most pressing now is the lack of my Ubunto-PC to make use of my M-Audio Delta 1010 LT Soundcard.

I installed ALSA package yesterday, but there's still no sign of my Soundcard to be found. 

sudo aplay -l delivers:

aplay: device_list:223: keine Soundkarten gefunden ... (no soundcards found)




lspci -v | less delivers: 

01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. Device d63b
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 9c00 [size=32]
        I/O ports at 9800 [size=16]
        I/O ports at 9400 [size=16]
        I/O ports at 9000 [size=64]
        Capabilities: <access denied>

What now? This is a great studio-soundcard and I want to keep it!

What can I do to solve this? Please don't forget, I am as new as can be to Ubuntu, so please take that into account, when answering.

Thanks in advance!

Greg

---

### Post by cchhrriiss121212 on 2010-05-10
Firstly the delta series is fully supported by alsa, so you can get it working eventually. 
What version are you using? You should not need to install alsa, as Ubuntu comes with it.
Here is what my lspci -v shows (bold text mine):
```
01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. Device d633
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at dc00 [size=32]
    I/O ports at d880 [size=16]
    I/O ports at d800 [size=16]
    I/O ports at d480 [size=64]
    Capabilities: <access denied>
    [B]Kernel driver in use: ICE1712
    Kernel modules: snd-ice1712[/B]
```
For some reason, your system is not loading the kernel modules for the card. See step 4 in [this guide]("http://ubuntuforums.org/showthread.php?t=205449").

---

### Post by Greg Zell on 2010-05-10
On a sidenote: I just tried to install Java. There is this damned Java-license-agreement, I can't get rid of, and which blocks further use of the terminal:

at the End of this license-agreement there is "<Ok>. What to do with it? "Enter/Return" doesn't work. Typing "Ok" doesn't work, typing "<Ok>" doesn't work.

How do I accept this bloody thing. Even such an easy thingy as that suddenly makes hour long trouble.

I start feeling desperate. 

Please help me!

Greg

---

### Post by Greg Zell on 2010-05-10
Thanks cchhrriiss,

If I type   [SIZE=2]sudo modprobe snd-
[/SIZE]     , I get: FATAL: Module snd_ not found.

Also I wouldn't know what exactly I need to type behind the "snd_"

---

### Post by cchhrriiss121212 on 2010-05-10
OK, I should have made that clearer. The guide says this:
> [SIZE=2]Now, press the **TAB** key **BEFORE** pressing the **ENTER** key to see a list of modules. Try to find the module that matches the driver you found in step 3.[/SIZE]
But seeing as we know that you are using an ice1712 card, you can just type:
```
sudo modprobe snd-ice1712
```
Which should mean that your card is now running, and you can make sure by using aplay -l. Then proceed with the rest of step 4.

Regarding java, you seem to be taking the difficult route of installing things through the terminal which is not neccessary. Open synaptic package manager and search for ubuntu-restricted-extras, which will install java and a bunch of other useful codecs. If you want anything installed, then use synaptic, terminal use should only be required for odd problems like this sound one.

---

### Post by Greg Zell on 2010-05-10
[FONT=Arial]thanks for your help!
issue not solved though :-([/FONT]

sudo modprobe snd-ice1712 delivers: "FATAL: Module snd_ice1712 not found."

aplay -l delivers: "aplay: device_list:223: keine Soundkarten gefunden ..." = no soundcard found

Thanks for the hint on installing things easier via synaptic package manager. Will do in the future, But now the Java installation process is already running. Any idea how I get this damned licence agreement to disappear? As I wrote above, it wants a confirmation from me. There is this <Ok> at the end of the licence agreement. What to do with it? Mouse click doesnt help. Typing "Ok" doesn't help, typing "<Ok>" doesn't help. I'm not a complete idiot with computers normally, but this drives me nuts, slowly.
I feel like 25 years ago, hacking my first DOS commandlines here. ;-)

---

### Post by cchhrriiss121212 on 2010-05-10
What is displayed when you type in "sudo modprobe snd-" and press tab? You should be given a list of drivers. Could you also mention what release you are using, as it is helpful for solving this.

The java install I would try entering y.

---

### Post by Greg Zell on 2010-05-11
Thanks for helping, Cchhrriiss!  I dropped the idea of using Ubuntu yesterday night. It's just not my cup of tea to learn a new OS. I want things I need to do on my computer to run smoothly and the Ubuntu experience I got is the opposite. So, for the time being, I'll stick with XP and give Ubuntu another try, when I have the time and space and patience. Now is not the right moment, I need things to get done...

---

### Post by cchhrriiss121212 on 2010-05-11
No problem, it took me a week or two of casual use to get to grips with things and I think the same is true for most users. Remember to check the forums if/when you return.

---

### Post by EzeKB on 2010-07-13
Hi! I'm getting just the same, problem here and so far didn't get any better. Still no sound :(
I'm also a newbie running away from both Windows and MacOS after years of fighting against all it's problems, so please be patient, just yesterday I learned how to open a terminal window... 8-[
I'm a Sound Engineer and Musician so it sould mean a lot to me to get my sound working. ;)
Thanks a lot!

---

### Post by cchhrriiss121212 on 2010-07-13
Hi EzeKB, could you post the output of "aplay -l" and "lspci -v" like the first poster? Just paste the commands without the quotes into a terminal window and press enter.

---

### Post by EzeKB on 2010-07-14
Hi! Thanks for the help!
Here we go:
> 
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: M1010LT [M Audio Delta 1010LT], dispositivo 0: ICE1712 multi [ICE1712 multi]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: VT82xx [HDA VIA VT82xx], dispositivo 0: VT1708 Analog [VT1708 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: VT82xx [HDA VIA VT82xx], dispositivo 1: VT1708 Digital [VT1708 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

and (this is a long one):

> 
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, medium devsel, latency 8
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller (prog-if 20)
    Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
    Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: dfb00000-dfbfffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: da000000-ddffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: dfe00000-dfefffff
    Prefetchable memory behind bridge: 00000000dfd00000-00000000dfdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372 (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at fc00 [size=8]
    I/O ports at f800 [size=4]
    I/O ports at f400 [size=8]
    I/O ports at f000 [size=4]
    I/O ports at ec00 [size=16]
    I/O ports at e800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device 5002
    Flags: bus master, medium devsel, latency 32
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at e400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at e000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 32, IRQ 22
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at dffff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
    Subsystem: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
    Flags: medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
    Subsystem: VIA Technologies, Inc. Device 337e
    Flags: bus master, medium devsel, latency 32
    Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
    Subsystem: Giga-byte Technology Device e000
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at d000 [size=256]
    Memory at dfffe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
    Flags: fast devsel
    Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00008000-00009fff
    Memory behind bridge: dfa00000-dfafffff
    Prefetchable memory behind bridge: 00000000df900000-00000000df9fffff
    Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
    Subsystem: XFX Pine Group Inc. Device 230b
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at da000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at bc00 [size=128]
    [virtual] Expansion ROM at dd000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidia-173, nvidiafb, nouveau

04:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46) (prog-if 10)
    Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 17
    Memory at dfaff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at 9c00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

04:05.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. Device d63b
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at 9800 [size=32]
    I/O ports at 9400 [size=16]
    I/O ports at 9000 [size=16]
    I/O ports at 8c00 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: ICE1712
    Kernel modules: snd-ice1712

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
    Subsystem: Giga-byte Technology Device a004
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


I hope it helps, Thanks again! :D

---

### Post by cchhrriiss121212 on 2010-07-15
The soundcard is recognised so that means you just need to set the volume levels using alsamixer in a terminal (they are often muted by default). There is also a program called envy24control which you can download from synaptic package manager in a package called alsatools, it is a more advanced version of alsamixer designed for your soundcard.
As you are a musician I take it you will be using the jackd sound server as well?

---

### Post by EzeKB on 2010-07-16
Thanks Chris, but I couldn't get any sound, using envy24 or the ALSAmix can't figure out how to make it work. It's frustrating! ](*,)
I also can't configure the video right, some boots it fails mounting and ask me to skip, cancel or ignore, but don't know why or what does it mean, trying to fix this problems I don't know how but I ended up running XUBUNTU. All the things that I hated in all my windows user years, happend together and the worst part is that the same day I installed UBUNTU, also Installed Win7 and win runs smohhthly without a single problem. I hate the very first idea of propietary software, I want to support free software, but it just doesn't work for me. I give up! :cry:
Thanks for helping me, I appreciate.

---

### Post by lidex on 2010-07-18
Stop scaring 'em, chris!! ;)

---

### Post by cchhrriiss121212 on 2010-07-19
> **lidex said:**
> Stop scaring 'em, chris!! ;)
It must be something I said:(

To anyone else with this card, the problems you will face are due to pulseaudio/ALSA configuration and they have been around for [some time]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442").
I think most users with an ice1712 card have learned to either remove pulse (which is fairly redundant anyway), or edit a few system files. Not a great solution when you consider that it has been a problem for so long.

---

