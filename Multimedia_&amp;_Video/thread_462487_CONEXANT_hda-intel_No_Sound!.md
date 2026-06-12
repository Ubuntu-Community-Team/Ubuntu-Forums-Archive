---
title: "CONEXANT hda-intel No Sound!"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by exspiro on 2007-06-02
i have just recently installed ubuntu and cannot get any sound output
ive looked at many many docs and tried many of them, to no avail.

here is the output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help is greatly appreciated!

---

### Post by diebels on 2007-06-02
That's the same output as I get with a working conexant hda-intel formerly known as cxt5047 now as CX20551 (Waikiki).

Try running alsamixer and unmute stuff.

If not working download and compile latest alsa release candidate from alsa website. Improved sound quality a lot for me.

I guess you need to install linux-headers-generic and build-essential.

Unpack with tar xjf alsa-driver-1.0.14rc4.tar.bz2
cd alsa-driver-1.0.14rc4
configure --with-cards=hda-intel
make
sudo make install
sudo /etc/init.d/alsasound restart

---

### Post by exspiro on 2007-06-02
diebels-

thanks for the quick response.

i have everything unmuted in alsamixer
the latest alsa release 
and performed the steps you outlined.

still. no sound.  what else could it possibly be?

thanks again

---

### Post by diebels on 2007-06-02
Strange, what kind of mixers do you have in alsamixer?

Get some information about what sound card you have:
lspci -s $(lspci | grep -i audio | cut -f 1 -d ' ') -v
lspci -s $(lspci | grep -i audio | cut -f 1 -d ' ') -v -n

---

### Post by exspiro on 2007-06-02
lspci -s $(lspci | grep -i audio | cut -f 1 -d ' ') -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>




lspci -s $(lspci | grep -i audio | cut -f 1 -d ' ') -v -n

00:1b.0 0403: 8086:27d8 (rev 02)
        Subsystem: 1179:ff31
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by diebels on 2007-06-03
The subsystem number should be a uniqe identifier for your card 1179:ff31

There is one comment in this open bug report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/83015](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/83015) with your card.

Possible workarounds: using model=3stack module parameter and changing index in /etc/modprobe.d/alsa-base.

Maybe make a new file to prevent problems with dpkg when upgrading stuff. All files in /etc/modprobe.d/ should be read anyway.

sudo gedit /etc/modprobe.d/snd-hda-intel-custom and insert:
options snd-hda-intel model=3stack index=0

reboot or run sudo /etc/init.d/alsasound restart

Edit: I think maybe we are on a wrong track here.
Alsamixer is working.
Sound applications are playing without errors?
Can you recheck the unmuting in alsamixer and paste the output of the command "amixer"

---

### Post by exspiro on 2007-06-03
sound applications seem to be playing audio as i can see the tracks moving forward and the eq moving etc.

aslamixer is definitely not muted.

here is the output:

amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 24 [80%] [on]
  Front Right: Playback 24 [80%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Line-In',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic Bypass',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'ExtMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]

thanks much.

---

### Post by diebels on 2007-06-03
Have you tried the headphone output?

Try different options for model, maybe model=toshiba. Find different models in alsa-driver-1.0.14rc4/alsa-kernel/Documentation/ALSA-Configuration.txt where you unpacked it.

In alsamixer press [tab] twice to get all controls and unmute all capture controls as well, in case there is some mismapping.

Maybe something is wrong with acpi, paste output of dmesg | grep -i acpi

Also you can try acpi=off boot parameter in case you have a acpi problem.
Edit /boot/grub/menu.lst
add acpi=off to the end of the kernel line
Mine looks like: kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=676f4a3b-d3b2-4e4a-8edc-87ce7b4a6990 ro splash locale=nb_NO

Yours have different UUID and locale, so don't change any of that.

You'll need to reboot to see if it helps. And acpi=off is not a permanent solution, since you could get some overheating problems. It's just trying to locate the cause of the problem.

---

### Post by exspiro on 2007-06-03
EDIT: there is no sound in the mic jack, and there are several kernel lines do i add the acpi=off to each and every one? 

EDIT2: when i added acpi=off to each line, and rebooted, got lots of errors, and didnt boot into gui, just text interface.  reedited file, took them out, and worked fine.

everything is unmuted in alsamixer.

i added acpi = off to the kernal line, rebooted, still no sound.

here is the output:

dmesg | grep -i acpi

[    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fe9b000 (ACPI data)

[    0.000000]  BIOS-e820: 000000007fe9b000 - 000000007ff00000 (ACPI NVS)

[    0.000000] ACPI: RSDP (v000 TOSQCI                                ) @ 0x000f7610

[    0.000000] ACPI: RSDT (v001 TOSQCI TOSQCI00 0x06040000  LTP 0x00000000) @ 0x7fe941d7

[    0.000000] ACPI: FADT (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x7fe9ae20

[    0.000000] ACPI: MADT (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x7fe9ae94

[    0.000000] ACPI: HPET (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x7fe9aefc

[    0.000000] ACPI: MCFG (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x7fe9af34

[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x7fe9af70

[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x7fe9afd8

[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7fe94217

[    0.000000] ACPI: DSDT (v001 TOSQCI   Denver 0x06040000 MSFT 0x03000000) @ 0x00000000

[    0.000000] ACPI: PM-Timer IO Port: 0x1008

[    0.000000] ACPI: Local APIC address 0xfee00000

[    0.000000] ACPI: 2 duplicate APIC table ignored.

[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])

[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)

[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

[    0.000000] ACPI: IRQ0 used by override.

[    0.000000] ACPI: IRQ2 used by override.

[    0.000000] ACPI: IRQ9 used by override.

[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000

[    0.000000] Using ACPI (MADT) for SMP configuration information

[   26.880989] ACPI: Core revision 20060707

[   26.906148] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

[    0.122049] ACPI: bus type pci registered

[    0.151236] ACPI: Interpreter enabled

[    0.151238] ACPI: Using IOAPIC for interrupt routing

[    0.151562] ACPI: PCI Root Bridge [PCI0] (0000:00)

[    0.152759] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO

[    0.154181] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.157765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]

[    0.158062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]

[    0.158280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]

[    0.158497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]

[    0.159093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]

[    0.159575] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11

[    0.159787] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)

[    0.160000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11

[    0.160207] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)

[    0.160413] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.

[    0.160619] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.

[    0.160827] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11

[    0.161033] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)

[    0.220635] pnp: PnP ACPI init

[    0.222505] pnp: PnP ACPI: found 10 devices

[    0.222509] PnPBIOS: Disabled by ACPI PNP

[    0.222601] PCI: Using ACPI for IRQ routing

[    0.254420] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16

[    0.254449] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17

[    0.254480] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16

[    0.254509] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18

[    0.254551] ACPI: PCI Interrupt 0000:0a:04.0[A] -> GSI 17 (level, low) -> IRQ 17

[    1.290542] ACPI: (supports S0 S3 S4 S5)

[    2.496871] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]

[    2.497052] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]

[    2.497259] ACPI: CPU0 (power states: C1[C1] C2[C2])

[    2.497672] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]

[    2.497839] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]

[    2.498087] ACPI: CPU1 (power states: C1[C1] C2[C2])

[    3.052000] ACPI: Thermal Zone [THRM] (56 C)

[    3.384000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19

[    3.488000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20

[    3.592000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18

[    3.696000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16

[    3.800000] ACPI: PCI Interrupt 0000:0a:04.1[A] -> GSI 17 (level, low) -> IRQ 17

[    3.852000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19

[    4.116000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20

[    4.784000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16

[   19.592000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16

[   19.596000] ACPI: PCI Interrupt 0000:0a:04.3[A] -> GSI 17 (level, low) -> IRQ 17

[   19.612000] ACPI: PCI Interrupt 0000:0a:04.2[A] -> GSI 17 (level, low) -> IRQ 17

[   19.672000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17

[   20.176000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21

[   26.828000] ACPI: Power Button (FF) [PWRF]

[   26.828000] ACPI: Lid Switch [LID]

[   26.828000] ACPI: Power Button (CM) [PWRB]

[   26.968000] ACPI: Battery Slot [BAT1] (battery present)

[   27.012000] ACPI: AC Adapter [ACAD] (on-line)

[   27.172000] ibm_acpi: ec object not found

[   27.220000] pcc_acpi: loading...

---

### Post by diebels on 2007-06-03
Then I'm almost out of ideas..

To sum it up:
You had a Toshiba laptop with windows installed and sound working, and installed Ubuntu on it.
All mixers are unmuted.
You can't find any error messages related to alsa, audio or acpi.
All sound and video applications behave like sound is working.
There is no sound in speakers, headphone, line out or mic.

You have posted #3139 on alsa bugtracker. Probably some developers looking into it soon.

You could also try the latest alsa snapshot: [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)

Edit: Don't think acpi is the problem, but you could try when you are booted up with acpi off
aplay /usr/share/sounds/login.wav

---

### Post by Cresho on 2007-06-03
I have the solution.


I can record audio in my audacity and also record audio and video through the xdtv software.

anyway, make sure you have the line in capture activated or microphone activated or checked mark or what ever.  and the most important setting is the ADC Capture.  this needs to be on!

---

### Post by exspiro on 2007-06-03
is this solution for sound output?

---

### Post by DamienSturdy on 2007-06-04
I too am having this same issue
I've updated Alsa, even downgraded it, upgraded it again, Tried every option inside Modprobe.D/Alsa-base etc...

I simply cannot get sound out of this card.

One thing though- when you run a test sound- and press the headphones to your head in a QUIET ROOM, you can hear a sine wave, extremely extremely quiet.

You cannot turn of ACPI since the Nvidia display driver seems to stop responding and Ubuntu cannot start the X-server.

This leaves me with no sound at all....

---

### Post by diebels on 2007-06-04
exspiro: Did you try the newest alsa-driver?

It's stable 1.0.14 now and [http://www.alsa-project.org/changes/v1-0-14rc4--v1-0-14.txt](http://www.alsa-project.org/changes/v1-0-14rc4--v1-0-14.txt) says two toshiba cards similar to yours, with your problem are fixed. So maybe you're lucky.

---

### Post by exspiro on 2007-06-05
do i need to remove the previous drivers and then install.

i installed and still no sound.

i may try a fresh install and then install the drivers, because there might be some problem with the many many changes i have made to settings in ubuntu as of now.

what do you think?

---

### Post by DamienSturdy on 2007-06-06
The new Alsa driver still fails to function despite several Toshiba and connexant fixes.

I am forced to go back to solo windows... Shame- all that MMS and stuff looks pretty damn sweet....

---

### Post by DamienSturdy on 2007-06-18
Any news on this? ubuntu is damn awesome in other areas, I need audio to work as i'm going to need to port some software over to Linux- including sound.

---

### Post by eric_c351 on 2007-07-12
I'm having the same problem.  Has anyone found an answer for this?

---

### Post by davidsrsb on 2007-07-13
by default audacity uses OSS, not alsa and OSS only seems to be a common issue with Feisty

---

### Post by Schadenfroh on 2007-11-19
> **eric_c351 said:**
> I'm having the same problem.  Has anyone found an answer for this?

Same issue here with my Toshiba P105 (Conexant Waikiki).

---

