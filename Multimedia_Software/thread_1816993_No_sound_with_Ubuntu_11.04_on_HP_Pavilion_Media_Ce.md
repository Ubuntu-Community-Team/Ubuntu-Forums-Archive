---
title: "No sound with Ubuntu 11.04 on HP Pavilion Media Center"
date: 2011-08-02
forum: Multimedia Software
---

### Post by Chaos7703 on 2011-08-02
Hello everyone! =)

My neighbor has an HP Pavilion a1214n "HP Media Center PC." (Originally using Windows XP) The computer stopped working and gave her a "Code Purple" error.  She asked me to see if I could fix it for her.  After researching I became apparent that I may not be able to fix it for her.  I asked what she uses it for & she said she just uses the internet to play games, etc. So I told her I might install Ubuntu if I couldn't get it fixed (seemed like a perfect solution;).  I couldn't fix HP so I downloaded & installed Ubuntu 11.04 along side XP last night (8/1/2011).  I Gave Ubuntu ~130GB of space & left the broken XP with some space (just in case).

Everything seems to be working fine EXCEPT:

[LIST=1]
[*]there's no sound,
[*]the MP3 file I copied to the system to test is opening (with no sound)  and playing at about 5x normal speed (in both Banshee & Movie Player),
[*]Trying to test a DVD opens Movie Player and gives me:
>  "Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed"(It's a plain out-of-the-box from Walmart DVD movie.)
[*]The display randomly seems to "forget"/mess up
For example: I can't see all of #3 above after I cut & pasted it into this list and windows sometimes have "holes" through them (to what ever is below)
[/LIST]

The sound problem is my first concern.  I tried to go through the "Comprehensive Sound Problem..." sticky, but the linked pages are not working correctly or as expected/described. (I posted a reply to it detailing what I found wrong).

What I get from steps one & two:
>  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
> lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fe00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at fd00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at fc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fb00 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at fa00 [size=8]
    I/O ports at f900 [size=4]
    I/O ports at f800 [size=8]
    I/O ports at f700 [size=4]
    I/O ports at f600 [size=16]
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: medium devsel, IRQ 255
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350] (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Device 2462
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at de00 [size=256]
    Expansion ROM at fddc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc RV710/730
    Subsystem: XFX Pine Group Inc. Device aa38
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Device 0003:000f
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 20
    Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ef00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Device 1acb:e102
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at ec00 [size=256]
    Memory at fdefe000 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at fdec0000 [disabled] [size=128K]
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

02:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a22
    Flags: bus master, medium devsel, latency 32, IRQ 20
    Memory at fdefd000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ee00 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100
(I included the entire output because I don't know what else besides the "Audio Device: ATI ..." might be relevant)

Step three asks to look on a website for a driver for my chipset.  The audio information doesn't look like "chipset information" (maybe I'm wrong).   It looks like a card name/type.

I ran (almost) all system tests & submitted the results.
I have run the updater & installed all updates.

Any help is greatly appreciated by me & my neighbor (she just a little old lady that wants to play her games hehehe)
Chaos7703 - Todd

---

### Post by cbennett926 on 2011-08-02
Have you downloaded the correct Mp3 codecs? MP3 playback never works upon initial installation.

---

### Post by lkjoel on 2011-08-02
For the DVD, it's actually quite simple to fix.
Type in a Terminal window:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install libdvdcss2 non-free-codecs
```

For the sound, try Sound Troubleshooting in my signature.

---

### Post by Chaos7703 on 2011-08-03
Hello again

I did not install any codecs (manually) before.  I told the installer to install the 3rd party codecs (or whatever the bottom checkbox was on the installer), I connected it to the internet & also told it to download any updates during the install.  I also noticed that Firefox said I needed to update Flash, so I went ahead and let it update Flash.  That's the state the computer was in when I post the first post above.

I performed the DVD fix above and it did give me video when I put the DVD in.  However, the video also play at *at least* 5 times normal speed.  (With no sound)

Looking at the BIOS setup menu I changed the "Onboard audio" to "Enabled" rather than "Auto".  That gave me three sound cards listed.  GNOME ALSA Mixer right now has only one tab titled: "ATI r6xx HDMI" with a checked checkbox labeled "IEC958" at the bottom of the screen. 

I found the "matrix" page with the vendor list at: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) so I tried to work through the "Comprehensive Sound Problem Solutions Guide: ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449))

I also tried working through the "Sound Troubleshooting" ([http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/](http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/))

Then I tried to work through this "Sound Troubleshooting" ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting))

At this point it won't even try to play an mp3 file anymore, but it did just play the DVD at the correct speed (with no sound) and I have absolutely no idea what is or isn't installled anymore.  I don't know what I could or should add to this post that might help clarify or give you additional information. :(

I hope you'll bare with me.  As far as Ubuntu/Linux goes I'm a noob.  I'm a programmer, but when it comes to operating systems etc I don't know much more than the general concepts. :confused:

Let me know of any information I can give to help clarify the situation. 

Thanks again,
Chaos7703 - Todd

---

### Post by lkjoel on 2011-08-03
Could you give me the URL that this command gives you?
```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh

```

---

### Post by Chaos7703 on 2011-08-03
THAT looks like a pretty convenient script there.

[http://www.alsa-project.org/db/?f=ad65448b11c05afb0e30b44639f2d52edaeb7678](http://www.alsa-project.org/db/?f=ad65448b11c05afb0e30b44639f2d52edaeb7678)

Thanks again.

Ps.  There is no personal information/settings on the computer yet.  I was planning on just reinstalling Ubuntu again last night, but I thought perhaps it would be better to see what you thought first.

I noticed that the report at the URL above is pretty empty.  I thought I'd mention that I have no objection to reinstalling if that would be an easier route.

---

### Post by lkjoel on 2011-08-03
Try this in a Terminal window:
```
sudo usermod -aG audio `whoami`

```
And reboot.
Then could you give me the output of:
```
aplay -l
sudo aplay -l

```

---

### Post by Chaos7703 on 2011-08-03
Should the reboot take a long time? I rebooted after performing the first command and I have been waiting about eight minutes so far.  It does not seem like the computer is doing anything, but I do not want to interrupt it.

---

### Post by Chaos7703 on 2011-08-03
I'm not totally sure if this information is correct or accurate.  When I rebooted the computer it took at least 30 minutes before I got the desktop on the screen.  Then the mouse would work, but I could not do anything.  Right clicking & left clicking didn't do anything.  The screen kept going black randomly and when it would come back up, different parts of the desktop would be "missing."  The screensaver didn't seem to be working, because I left it & waited about another 45-60 minutes for it to "stabilize" and hopefully respond.  It never did; so I had to hold the power button until it finally shut off.

When I restarted it, it acted as if it was doing the same thing.  After leaving the "Ubuntu" startup screen for ~10 minutes, I force restarted it again.  This time it booted "normally" and executed the commands.

> aplay -l
aplay: device_list:240: no soundcards found...
mary@mary-LakePort:~$ sudo aplay -l
[sudo] password for mary: 
aplay: device_list:240: no soundcards found...
mary@mary-LakePort:~$ 
Thanks again for the help.  I hope it's not as annoying on your end as it is on mine.
Todd

---

### Post by lkjoel on 2011-08-03
Type this into a Terminal window:
```
echo "snd-hda-intel" | sudo tee -a /etc/modules

```Then reboot (again).
Then could you still give me the output of:
```
aplay -l
sudo aplay -l

```

---

### Post by Chaos7703 on 2011-08-03
mary@mary-LakePort:~$ aplay -l
aplay: device_list:240: no soundcards found...
mary@mary-LakePort:~$ sudo aplay -l
[sudo] password for mary: 
aplay: device_list:240: no soundcards found...
mary@mary-LakePort:~$

---

### Post by lkjoel on 2011-08-03
Try this:
```
echo "options snd-hda-intel model=hp" | sudo tee -a /etc/modprobe.d/alsa-base.conf

```
Reboot, and give me the output of:
```
aplay -l
sudo aplay -l

```

---

### Post by Chaos7703 on 2011-08-03
aplay -l
aplay: device_list:240: no soundcards found...
mary@mary-LakePort:~$ sudo aplay -l
[sudo] password for mary: 
aplay: device_list:240: no soundcards found...
mary@mary-LakePort:~$

---

### Post by lkjoel on 2011-08-03
Could you give me the output of these commands?
```
sudo cat /etc/modules
sudo cat /etc/modprobe.d/alsa-base.conf

```

---

### Post by Chaos7703 on 2011-08-03
mary@mary-LakePort:~$ sudo cat /etc/modules
[sudo] password for mary: 
Sorry, try again.
[sudo] password for mary: 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-hda-intel
mary@mary-LakePort:~$

---

### Post by lkjoel on 2011-08-04
Could you give me the output of the second command too?

---

### Post by Chaos7703 on 2011-08-04
Sorry.  Can't believe I missed that.

mary@mary-LakePort:~$ sudo cat /etc/modprobe.d/alsa-base.conf
[sudo] password for mary: 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=hp
mary@mary-LakePort:~$

---

### Post by lkjoel on 2011-08-04
Could you give me the output of these commands?
```
sudo modprobe snd-hda-intel
aplay -l
sudo aplay -l

```

---

### Post by cosine352 on 2011-08-04
type > gnome-volume-control in a terminal 
then click on the "Hardware" tab and chose the "Internal Audio". I guess it is now set for the "HDMI" and that is why it is not working.

---

### Post by Chaos7703 on 2011-08-06
My apologies, yesterday I was unable to get the computer to start.  It got stuck in a loop starting BIOS over & over & over.  The live disk kept failing with some kind of error and when I tried to use the Ulitimate Boot CD the keyboard would only work "occasionally." So I couldn't really do ANYTHING with it.  I was too busy today, but I haven't abandoned the issue.  Tomorrow I will try again, but I worry that either the hard drive or motherboard is going... ???

Thanks again for the help.  I will post back if I get results or decide the computer is dead.

---

### Post by lkjoel on 2011-08-06
That might be a problem with GRUB.

---

### Post by Chaos7703 on 2011-08-17
Sorry for the delayed response.  I was unable to get the computer to do anything other than give me error messages. I tried to run some diagnostics using the Ultimate Boot CD, but the USB keyboard stopped working most of the time and when it did work, it didn't work correctly.  I swapped it out with a PS2 keyboard which would work; however, every diagnostic I tried would give me a "compression error."  I burned a copy of the newest UBCD version, but it gave the same errors.  When I put the live Ubuntu CD in, it stops and gives me an error after loading for a couple of minutes. It seems that either the motherboard, BIOS, or both is shot and the computer is dead :-({|=, but all this is above my head.

I'm willing to mess with it some more if someone believes they know what the problem is.

Thanks again for your time & efforts.
Todd

---

