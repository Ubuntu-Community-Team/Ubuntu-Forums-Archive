---
title: "No sound from ISA PNP Creative Phone Blaster"
date: 2009-10-08
forum: Multimedia Software
---

### Post by waynemcdougall on 2009-10-08
I am requesting help in getting an ISA Creative Phone Blaster 28.8/33.6 PNP soundcard to produce sound using Ubuntu Karmic.

I am supplying older computer systems to members of the community who cannot afford to buy a computer or broadband. I have dozens of these Phone Blaster cards which give both sound and dial-up modems (only 33.6k). So I'm willing to put in time, rather than money.

Furthermore the sound works just fine with Windows XP and I don't want Linux to lose. I'm probably just missing something simple an obvious.

To me cat /proc/ioports suggests there may be something in there, but I don't know enough in that area.

lspnp -vvshows the state of the soundcard is Disabled. Setpnp does not work with this kernel. I do not know any other way to make it active, or even if this would be helpful.

The card is detected and the modem automatically set up correctly and works. Sound does not. The PC is a Compaq Deskpro. Ubuntu was a based install of Karmic Alpha 5, but with all upgrades applied.

What I have tried:
enabling and disabling the sound card in BIOS
trying snd-sb16 in both /etc/modules and from the command line
trying snd-sbawe in both /etc/modules and from the command line

With and without the following lines in /etc/modprobe.d/alsa-base.conf

options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5

options snd-sbawe isapnp=0

#options snd-sb16 isapnp=1


and with and without isapnp=1
and with just
options snd-sb16 isapnp=0

Those settings are the ones used by Windows XP.

I've also installed the latest (not test) version of ALSA using the script here.
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

The Phone Blaster is listed as supported by Linux here: 
[http://tldp.org/HOWTO/Hardware-HOWTO/sound.html](http://tldp.org/HOWTO/Hardware-HOWTO/sound.html)
and certainly the modem part works beautifully.

It's not listed specifically at [www.alsa-project.org](www.alsa-project.org) – on the other hand Windows XP sees it as a SB16 or SB-AWE card. 

If I put a SB16 card in this PC, it works just fine with snd-sb16 in /etc/modules and
options snd-sb16 isapnp=0

in /etc/modprobe.d/alsa-base.conf

The big difference is the SB16 card is NOT PNP.

I have tried running the alsaconf script which claims to detect a SB16 card, and creates a file with the same settings I have been adding to alsa-case.conf. It dos not help.

Attached is the output of 
uname
cat /proc/interrupts
cat /proc/dma
cat /proc/ioports
dmesg
lsmod
lspnp -vv

I am willing to try anything anyone suggests.

Uname -a
Linux freepc68-desktop 2.6.31-12-generic #41-Ubuntu SMP Wed Oct 7 18:42:46 UTC 2009 i686 GNU/Linux


cat /proc/interrupts
           CPU0       

  0:     193180    XT-PIC-XT        timer

  1:       6587    XT-PIC-XT        i8042

  2:          0    XT-PIC-XT        cascade

  3:          1    XT-PIC-XT      

  4:          1    XT-PIC-XT      

  5:          2    XT-PIC-XT      

  7:          1    XT-PIC-XT        parport0

  8:          0    XT-PIC-XT        rtc0

  9:          0    XT-PIC-XT        acpi

 11:        228    XT-PIC-XT        uhci_hcd:usb1, eth0

 12:      10571    XT-PIC-XT        i8042

 14:      33292    XT-PIC-XT        ata_piix

 15:          0    XT-PIC-XT        ata_piix

NMI:          0   Non-maskable interrupts

LOC:          0   Local timer interrupts

SPU:          0   Spurious interrupts

CNT:          0   Performance counter interrupts

PND:          0   Performance pending work

RES:          0   Rescheduling interrupts

CAL:          0   Function call interrupts

TLB:          0   TLB shootdowns

ERR:          0

MIS:          0


cat /proc/dma

 3: parport0

 4: cascade


cat /proc/ioports

0000-001f : dma1

0020-0021 : pic1

0040-0043 : timer0

0050-0053 : timer1

0060-0060 : keyboard

0064-0064 : keyboard

0070-0071 : rtc0

0080-008f : dma page reg

00a0-00a1 : pic2

00b2-00b3 : ACPI PM1b_CNT_BLK

00c0-00df : dma2

00f0-00ff : fpu

015c-015d : pnp 00:0b

0170-0177 : 0000:00:14.1

  0170-0177 : ata_piix

01f0-01f7 : 0000:00:14.1

  01f0-01f7 : ata_piix

0213-0213 : ISAPnP

0260-0261 : pnp 00:0b

02f8-02ff : serial

0376-0376 : 0000:00:14.1

  0376-0376 : ata_piix

0378-037a : parport0

037b-037f : parport0

03c0-03df : vga+

03e8-03ef : serial

03f6-03f6 : 0000:00:14.1

  03f6-03f6 : ata_piix

03f8-03ff : serial

04d0-04d1 : pnp 00:0b

0778-077a : parport0

077e-077f : pnp 00:0b

0a79-0a79 : isapnp write

0cf8-0cff : PCI conf1

1000-107f : 0000:00:0e.0

1080-109f : 0000:00:14.2

  1080-109f : uhci_hcd

10a0-10af : 0000:00:14.1

  10a0-10af : ata_piix

f800-f83f : 0000:00:14.3

  f800-f803 : ACPI PM1a_EVT_BLK

  f804-f805 : ACPI PM1a_CNT_BLK

  f808-f80b : ACPI PM_TMR

  f80c-f80f : ACPI GPE0_BLK

  f810-f815 : ACPI CPU throttle

fc00-fc0f : 0000:00:14.3

  fc00-fc07 : piix4_smbus


lspnp

00:00 PNP0a03 PCI bus

00:01 PNP0c04 Math coprocessor

00:02 PNP0200 AT DMA controller

00:03 PNP0b00 AT real-time clock

00:04 PNP0800 AT speaker

00:05 PNP0f13 PS/2 port for PS/2-style mice

00:06 PNP0303 IBM enhanced keyboard (101/102-key, PS/2 mouse support)

00:07 PNP0401 ECP printer port

00:08 PNP0501 16550A-compatible serial port

00:09 PNP0501 16550A-compatible serial port

00:0a PNP0700 PC standard floppy disk controller

00:0b PNP0c02 Motherboard resources

00:0c PNP0c02 Motherboard resources

00:0d PNP0c01 System board

01:01.00 CTL0031 Creative Labs Sound Blaster 16 or AWE-32 Plug and Play

01:01.01 CTL2011 Creative Labs IDE controller

01:01.02 CTL7fff (unknown)

01:01.03 CTL7001 Gameport Joystick

01:01.04 CTL3001 (unknown)

---

### Post by waynemcdougall on 2009-10-14
No replies? I'd hate to see Windows XP beat Linux on this card.

---

