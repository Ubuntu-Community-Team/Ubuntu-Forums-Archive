---
title: "after Jaunty upgrade, no sound exept from OSS"
date: 2009-04-23
forum: Multimedia Software
---

### Post by Roland123 on 2009-04-23
ubuntu 9.04

After upgrade from 8.10 to 9.04 sound stopped working on autodetect

when selecting system -> preferences -> sound -> autodetect, then no sound comes from speaker.

When selecting HDA Intel ALC883 ALSA and pressing test, i get an error: could not open device for playback.

Sound works only when OSS is selected.

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v
```
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)                                                                                    
        Subsystem: COMPAL Electronics Inc Device 0017                                        
        Flags: bus master, fast devsel, latency 0, IRQ 22                                    
        Memory at d2500000 (64-bit, non-prefetchable) [size=16K]                             
        Capabilities: <access denied>                                                        
        Kernel driver in use: HDA Intel                                                      
        Kernel modules: snd-hda-intel   
```

When using OSS, flash seems to have no sound and amarok 2 doesn't make any sound either.

Any ideas how to overcome this issue?

I appreciate any help you can give me.


Problem solved: [LINK]("http://ubuntuforums.org/showpost.php?p=7152097&postcount=25")

---

### Post by darweth on 2009-04-23
Same issues with these specs.  OSS only thing that works.  Worked fine in Intrepid.

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Intel Corporation Device 0107
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e400 [size=256]
	I/O ports at e080 [size=64]
	Memory at febff800 (32-bit, non-prefetchable) [size=512]
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

```

---

### Post by FaceLeg on 2009-04-23
Same issue here

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ea
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fea78000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

No sound in VLC, MPlayer, Exaile, Amarok2 ...

Thought I had broken something, reinstalled Jaunty - still no joy.

EDIT:

If I use "Sound playback" with gnome-sound-properties and select "HDA Intel VT1708B Analog (ALSA) and attempt to test the audio I get the message:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

Testing all other all others except for OSS results in no message or sound.  Testing OSS results in sound, but audio applications are still silent, though they do not complain about anything (no errors).

---

### Post by mozychan on 2009-04-24
I'm not getting sound either, but unlike you guys I can't even get oss to work.  Here's my situation:

```
mozychan@mozychan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

mozychan@mozychan-laptop:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3600
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Hewlett-Packard Company Device 3600
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2310000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

I am able to get sound with headphones...  Any ideas?

-moose

---

### Post by FaceLeg on 2009-04-24
> **mozychan said:**
> I'm not getting sound either, but unlike you guys I can't even get oss to work.  Here's my situation:

I am able to get sound with headphones...  Any ideas?

-moose

By "work" I mean that when I press test the tone sounds.  There is still no sound elsewhere ...

You mean sound works with headphones for you?  How much - just the tone or everything?

---

### Post by mozychan on 2009-04-24
> **FaceLeg said:**
> By "work" I mean that when I press test the tone sounds.  There is still no sound elsewhere ...

You mean sound works with headphones for you?  How much - just the tone or everything?

um yeah, the oss test doesn't work for me.

everything works with the headphones.  startup sound, flash videos, music... you name it.

speakers still work in windows...

-moose

---

### Post by rcarlton on 2009-04-24
no sound from the Ubuntu RC a couple of days ago, and none from the Kubuntu official release today.   

This is a recurring problem, I have had it working with 8.10 pretty successfully, but this upgrade is silent.  

I get the same error messages and silent Test as noted above.

---

### Post by OobNosferatu on 2009-04-24
Just upgraded to Ubuntu 9.04 and I get no sound whatsoever, and also have the same audio error as above.

Here's my situation:

```
sudo lshw -c multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_i

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

It was working fine under Ubuntu 8.10

:(

---

### Post by bastubis on 2009-04-24
Slightly off-topic but in case it's any help to anyone else having a similar problem with the Intel HD 82801H Audio Controller - this seems to default to pretty much everything being turned off and not visible in Alsamixer. Sorry if teaching people to suck eggs, but did everyone hit 'preferences' in Alsamixer, select everything then turn everything you need on? 

It was all fine in Intrepid, but after clean Jaunty installation I had sound on the front speaker but nothing on the side jacks (no side mic or headphones). Turned on 'side' in Alsamixer but side jacks didn't work until I turned on 'surround'.

---

### Post by FaceLeg on 2009-04-24
> **bastubis said:**
> Slightly off-topic but in case it's any help to anyone else having a similar problem with the Intel HD 82801H Audio Controller - this seems to default to pretty much everything being turned off and not visible in Alsamixer. Sorry if teaching people to suck eggs, but did everyone hit 'preferences' in Alsamixer, select everything then turn everything you need on? 

It was all fine in Intrepid, but after clean Jaunty installation I had sound on the front speaker but nothing on the side jacks (no side mic or headphones). Turned on 'side' in Alsamixer but side jacks didn't work until I turned on 'surround'.

Thanks!

I had turned *everything* up in gnome-sound-preferences, but didn't know about alsamixer. 

I had a look in there - everything was on.  So I switched "indepen" off on a whim - lucky I didn't have my headphones on or I'd be partially deaf - it worked!

:)  

See attached screenshot highlighting relevant section:

Terminal, type "alsamixer".  Press right until you find the circled option, turn it from on to off.  Test.

Hopefully this works for more people!

Thanks bastubis!

---

### Post by Roland123 on 2009-04-24
When running "alsamixer" in terminal I only see pulseaudio master volume control, to see others "alsamixer -c 0"

Volumes in gnome-sound-preferences and alsamixer are all OK.

I don't have experience in troubleshooting audio problems, could this be somekind of **pulseaudio** problem?

When selecting HDA Intel ALC883 Analog (ALSA) and pressing test, i get an error: [SIZE="4"]**could not open device for playback.**[/SIZE]

---

### Post by TheSlipstream on 2009-04-24
> **FaceLeg said:**
> 
Hopefully this works for more people!

I suspect it'll only work for your Via chip, I have a Realtek and it gives no option of 'Independ'. I'm amazed this wasn't fixed...how did Canonical miss this huge bug?

---

### Post by darweth on 2009-04-24
Yep. I have turned up and on every little thing alsamixer provides.  I don't even have the "indepen" option described above.  :)  I've tried every combo and setting possible and still only OSS sound.

---

### Post by OobNosferatu on 2009-04-24
Ditto here too. Is everyone who has an intel soundcard having this problem? Mine is onboard..

FYI using 64 bit Jaunty on P-6860FX (Laptop)

---

### Post by markitoxs on 2009-04-24
Hello guys,

Same problem here. However, one difference, when I use the pulseaudio applet volume meter for playback, I can see that there is some sound being played, however, very low, so low it cannot even be heard.

If you see my attachments, you will see that all the leves/switched are set to normal... I am running out of inspiration, any ideas? anyone?

**lspci | grep Audio**

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Koant on 2009-04-24
> **bastubis said:**
> Slightly off-topic but in case it's any help to anyone else having a similar problem with the Intel HD 82801H Audio Controller - this seems to default to pretty much everything being turned off and not visible in Alsamixer. Sorry if teaching people to suck eggs, but did everyone hit 'preferences' in Alsamixer, select everything then turn everything you need on? 

It was all fine in Intrepid, but after clean Jaunty installation I had sound on the front speaker but nothing on the side jacks (no side mic or headphones). Turned on 'side' in Alsamixer but side jacks didn't work until I turned on 'surround'.

Ah! Simple as that! Thanks a lot.

---

### Post by Axel-P on 2009-04-24
Also getting problems with sound!

So my speakers don't work, but with earphones everything is ok. Also when I shut down (and I have my earphones pluged-in) I can hear a sort of static noise, as if it doesn't shut downs my earphones :S

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3602
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Please help :(!

P.S. I have tried the solutions posted in this thread, not getting any result

---

### Post by forestwalkerjoe on 2009-04-24
ok guys.. this worked for me when i was in Intrepid 810 and has basically worked in my New Jaunty 904 upgrade. 
I have one small issue.. but i think its understanding the Pulse audio set up.. when i have music on desktop.. i , in past, could roll over and hear a clip of the song.. that doesn't work anymore.. and i have to force it to chose my VLC player instead of some other default.. but you can change defualts in the system. 
USE these changes.. and you might find better LUCK
 ```

http://ubuntuforums.org/showthread.php?t=789578
```

or 
 ```
https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760
```

These worked for me.. i hope they work for you. follow carefully.. dont do the work on a 804 that is for 810 or 904. 
If any one knows how to properly set up pulse audio.. let me know. my pulse audio applet closes every time  log off.. and i have to RESET IT each time. So i have no start up sounds and no roll overs.. but if i open any music.. it now plays.. and the flash player in FF browser now plays audio and video too. 
just Smashin all them bugs. 

FWJ

---

### Post by tomsa on 2009-04-24
I'm also having sound problems, but mine are the opposite- sound from internal speakers, but none from the headphone jack!!

Here's some info:

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
^[[6~card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: ATI Technologies Inc Device 1234
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: cfd00000-cfefffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8440 [size=8]
	I/O ports at 8434 [size=4]
	I/O ports at 8438 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8400 [size=16]
	Memory at f0309000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0304000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0305000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0306000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0307000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0308000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0309400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Gateway 2000 Device 0565
	Flags: 66MHz, medium devsel
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8420 [size=16]
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=0e, subordinate=13, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at cfdf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9000 [size=256]
	Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Subsystem: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at cfdec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Device 0565
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	I/O ports at a000 [size=256]
	Memory at f0200000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

Any ideas on how to fix this would be very welcome!

TS

---

### Post by lisle-adam on 2009-04-25
I had a problem like the ones posted in this thread after I upgraded from intrepid to jaunty.  Then I happened to find the kernel module(s) for intel HDA weren't there, though they are apparently enabled in the config file under /boot directory.  I don't know if it's just me.

Anyway I tried rebuilding the kernel from the source from main repo, confirming that the modules were surely built and placed, and audio started work again.

---

### Post by markbl on 2009-04-25
Many responses here are from people not experiencing the same issue as the OP. Linux sound is complicated and there seems to be a multitude of unrelated issues that can occur.

I had the same problem as the OP, i.e. had no sound but could hear the test tone if I selected OSS in the gnome sound menu. Sound had worked fine on intrepid. At one point, after installing a few pulseaudio packages etc, I found that even selecting OSS just gave me an error message. I also later noticed that I could SEE sound playing in the pulseaudio volume meter but just could not hear it.

Today I fixed the problem but unfortunately can't say here exactly how I did it. I thought I'd post here what I played around with because I know how frustrating and time consuming this problem can be.

In short, I installed gnome-alsamixer and played around with it and the curses alsamixer merely selecting (un-muting) everything I could find(!).
I ran the curses alsamixer with "alsamixer -c0" otherwise it would just see the pulse device. Suddenly sound plays fine. Sorry I can't be more exact!

---

### Post by viocudinti on 2009-04-26
My SOLUTION was to MUTE (!) the headphones ... suddenly there was sound in speakers.

---

### Post by ktenney on 2009-04-26
Similiar problems here, alsamixer didn't offer any help, when I installed and ran gnome-alsamixer I could see the 'mute' boxes, most of which were checked, when unchecked, problem solved.

Thanks,
Kent

---

### Post by jack_spratt on 2009-04-26
I have very similar problem to the OP.

I upgraded from kubuntu 8.10 to jaunty and now I have no sound.

I have tried adding the suggested line to the end of alsa-base.conf, but it made no difference.

I have tried installing three different guis for alsa volume levels and messed with them and no change.

I don't know what to try next and I really really need sound.

Can anyone make any other suggestions?

---

### Post by Roland123 on 2009-04-26
> **viocudinti said:**
> My SOLUTION was to MUTE (!) the headphones ... suddenly there was sound in speakers.

Thanks dude, it helped. Now i have sound in all programs :). (exept amarok2 don't know what bothers it.)

Installing gnome-alsamixer and MUTE'ing all channels and after that UNMUTE'ing helped to fix the sound issue. 

PS! I don't know what exactly fixed the issue. Here is one of the other things I did before that MUTE trick.

* [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) << pulseaudio setup guide - no success after this guide

---

### Post by babuu on 2009-04-26
> **Roland123 said:**
> 
* [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) << pulseaudio setup guide - no success after this guide

Thanks a bunch! That guide did it for me. Since I upgraded from Intrepid I only followed Part A, and even though I didn't manage to follow through since pavucontrol wouldn't launch, sound was already fixed. Puh :)

---

### Post by darweth on 2009-04-26
None of the solutions above worked for me but something did!!!!

Disable the Multicast/RTP sender.  And in volume control playback, click the down arrow at the far right of any stream.  Move stream to the "Intel" or whatever sound chip.  Everything came on for me immediately.

---

### Post by jonah_sao on 2009-04-27
I found a solution that worked for me here:

[https://bugs.launchpad.net/pulseaudio/+bug/315809](https://bugs.launchpad.net/pulseaudio/+bug/315809)

Basically the solution was to creating a missing symbolic link

sudo ln -s /etc/init.d/alsa-utils /etc/rc2.d/S26alsa-utils

---

### Post by shankhs on 2009-04-28
No help guys I somehow made amarok2 to work but vlc is still not giving any sound.

---

### Post by jonbing on 2009-04-29
I had a very similar problem to those with ATI cards (not the OP), who only had sound in the speakers:

card 0: SB [HDA ATI SB] STAC92xx

I solved the problem by adding the adding the following line to /etc/modprobe.d/alsa-base.conf (I have a HP Pavillion):

options snd-hda-intel enable=1 index=0 model=hp-m4

---

### Post by OobNosferatu on 2009-04-30
I gave up. Switched back to 8.10, will wait for the next release... because I was experiencing boot up problems too - I had /home on a different hard drive and for some reason it just wouldn't mount it after every third boot or so.. :/

---

### Post by chek2fire on 2009-05-01
> **darweth said:**
> None of the solutions above worked for me but something did!!!!

Disable the Multicast/RTP sender.  And in volume control playback, click the down arrow at the far right of any stream.  Move stream to the "Intel" or whatever sound chip.  Everything came on for me immediately.

Thanks this solved my problem :D

---

### Post by tomsa on 2009-05-01
I'm re-installing intrepid as we speak! The bug in my signature makes sound unusable except through the built in speakers.  It doesn't matter if I use regular headphones, or USB headphones.  Sound in Ubuntu for me is pretty borked right now.

---

### Post by forestwalkerjoe on 2009-05-02
ok , since the day i upgraded.. i have had some sort of sound issue.. we now have music playing.. Flash clips playing in youtube.. I was even able to get the Roll over effects working so if i go to music folder and mouse over songs , i can get a sound bite.. all that is finaly working.. with a lot of tweeking to get it there.. but to the date.. i still DONT have system sounds.. NO LOG IN LOG OFF.. in Start up.. none of that works.. i have tested in System Pref Sounds.. and none of the TEST buttons make sounds either.. is this a PULSE AUDIO thing? or sound server is looking in the wrong place? Please some one.. give me a heads up on sound server .. i used the ALSA suggestions a page back.. and the PULSE AUDIO config fix page.. and that is why i have what i have now.. that and the fact that some settings revert after boot.. to MUTE. 

ANY IDEAS? 

thanks 

FWJ

---

### Post by GH68 on 2009-05-05
My problem seemed to be exactly the same as what most of you describe, i.e. I had sound only from OSS after upgrading to Jaunty. Then I found out that this only seemed to be the case for my own login name (which also was the login from which I made the upgrade). My problem was solved by replacing the .pulse folder in my directory with one from a user for which the sound worked. Remember to change ownership of the folder, and you also have to log out and log in again to update the settings. If you are the only user on your computer, you may create a new one to see if sound works for that one.

Good luck, whatever your problems might be!

---

### Post by vernsh on 2009-05-07
My first post so please bear with me.  I am triple booting ubuntu, windows xp and windows 7 beta.  My SB-Xfi card works fine in windows but there are apparently issues with Linux in general with xfi when using the default ALSA. ALSA does not even recognize my card. I was able to install the OSS v4 package which gives me sound for cds and movies but no desktop sound.  I understand these sounds utilize ALSA but is there a way to convert the alsa sounds to oss?

---

### Post by daveysan on 2009-05-11
vernsh - To use OSS (which is the only thing I can get working in Jaunty) I did the following:

System->Preferences->Sound.

I selected OSS from each of the pull downs and now I get sound for most of my apps. Hope this helps ...

---

### Post by GH68 on 2009-05-11
> **daveysan said:**
> vernsh - To use OSS (which is the only thing I can get working in Jaunty) I did the following:

System->Preferences->Sound.

I selected OSS from each of the pull downs and now I get sound for most of my apps. Hope this helps ...

Daveysan,

I also *thought* that I only could get OSS working in Jaunty, but following the procedure that I described in my latest post above enabled me to use Pulseaudio. Trying to fix all settings manually, following the recommendations in this thread, just didn't help. It may not work for you, but maybe worth to give a try.

---

### Post by daveysan on 2009-05-11
Thanks GH68. I thought your post may have worked for me, but I don't really know anyone else using Ubuntu (aka the poor unenlightened :) ). Perhaps you could attach your working directory as a zip file?

I have managed to get Pulse working now for most of my apps, which is nice. I happened to read somewhere on one of this forum's posts (can't find it now, else I would credit the author) that when the Pulse Audio Volume Controller was displayed (playback tab), you could dynamically alter the stream used for playback which could help. I opened the gui - when I tried to play sound through Ryhthmbox, an entry for Rhythmbox appeared in the playback tab. I clicked on the "down arrow" (on the right of the entry) and selected "move stream" to a different entry - and I got sound. Bliss :P This method then worked for most of my apps so I am a happy bunny once again.

But thanks for your post. It's people like you that give this forum a good name.

---

### Post by GH68 on 2009-05-12
daveysan,

I'll see what I can do as soon as I have time (right now I'm not at my Ubuntu computer). Another idea, instead of trying to use my files, would be to create a new user on your computer and check if Pulseaudio give any sound for that user. If so, copy the .pulse directory (and possibly other files/directories?) to you own home directory.

Just to clarify exactly what problem I had, so we are not thinking of different problems:
1. Pulseaudio worked flawlessly in Ubuntu 8.10
2. After upgrading to 9.04 there was no sound, and I only got it to work by selecting "OSS" in System->Preferences->Sound
3. I tried to adjust all settings in the volume control etc according to the hints in this thread but ended up with no change.
4. I copied the .pulse directory from another user on the *same* computer to my own home directory. (Please note that I was the only user for which Pulseaudio stopped working, I don't know if it had anything to do with the fact that I upgraded to 9.04 from my own account).
5. After step 4, I could again change to Pulseaudio in System->Preferences->Sound, and I had sound working for all applications.

Good luck!

---

### Post by martinkellner on 2009-05-12
I don't have that option. Is there any way to make it visible?

---

### Post by robertj20112 on 2009-05-15
> **darweth said:**
> None of the solutions above worked for me but something did!!!!

Disable the Multicast/RTP sender.  And in volume control playback, click the down arrow at the far right of any stream.  Move stream to the "Intel" or whatever sound chip.  Everything came on for me immediately.
Thanks!  I've tried many suggestions but this one was the only one which worked for me.

---

### Post by forestwalkerjoe on 2009-05-22
Ok.. I am not a really experienced guy in here.. there are a thousand things i have not the first clue how to do. BUT.. i was able to get Most types of sound ON.. WITH THE EXCEPTION.. which i need help with, of system sounds. 
I can not recall the terminal work that i did that opened this next comment up.. but some HELP file showed me how to write a code and it would tell me the status of my sound system. there was a line that said ESound Deamon ; OFF. every thing else i can find has been turned on. 
 I am in a Wubi within XP windows.. 904 version.. and Upgrade from my 810. 
At first there was no sounds at all. 
I checked the volume control.. set up Pulse audio.. which means i messed arround in pulse audio.. since i know nothing.. opened up the Alsamixer and tried turning every thing up and On.. did the alsamixer -Dhw:0 trick.. 
Tried messing with pavucontrol and all else i could think of. the Pulse audio config help page really DID a lot of the work.. which got sounds on.. just still NO sounds for startup or log off.. Pideon IM sounds come on.. but again.. no system sounds. 
here is my sound set up. as far i as i understand how to show that. 
lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
if there are other codes that show more and give better suggestions as to how to proceed.. let me know..and i'll post them. 
this is one of those things were learning has disadvantages.. If you dont know what is wrong.. then pretty much.. others will not know how to help you FIND out what is wrong or Find out what to do to fix it. 
Can some of you more GURU types who understand Sound.. give me some clues on what to SHOW.. so we can FIND the issue? or if there is a work arround? i dont want to mess  arround on my own ignorance too long.. or i could mess up the bit of progress i already have. 

Funny.. I tend to help others to install duel booted or now WUBI of Ubuntu on their systems.  I am not completely useless.. but since i did get the newest disk of 904 in the mail.. i have held back on trying to do wubi installs of this distro till i am sure i understand the sound issues.  am trying to make a good impression. 
So far.. i have helped install 810 quite a few times.. with Very few real issues.. other than they dont have good enough graphics card to run Compiz. which is a bummer.. cause Compiz is a Deal MAKER most of the time. 

thanks for helping.. if i can solve this it will really restore my faith in this Upgrade. 

FWJ

---

### Post by bhaumik_thacker on 2009-05-22
Hi everyone,

I am a newbee in using ubuntu. I installed 9.04 and then installed all the required codecs. I was facing the same problem as you people. I messed around with the volume control.

I can here the audio but the problem is the balance is not right.
My left speaker has all the audio, while the right one is blank.
And this is the problem with both, the headphones as well as the speakers in the TFT. They worked before the upgradation perfectly fine.

Checked all the volume levels, tried changing them. Still the same.

aplay -l
-----------------------------------------------------------------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
-----------------------------------------------------------------------------------

lspci -v
-----------------------------------------------------------------------------------
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device a201
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 92100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
-----------------------------------------------------------------------------------

pulseaudio
------------------------------------------------------------------------------------------------------- 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
-----------------------------------------------------------------------------------------------------


Also, I face the problem of a very loud static while shutting down.

---

### Post by forestwalkerjoe on 2009-05-26
yeah.. i have figured i have the same issue. there are a lot of sound config issues in 810 and 904. as far as i can tell.. its all fixable.. but requires a bit of hunt a poke to get it done. I have all sounds EXCEPT OGG sounds.. which DO play if i find the file itself and hit Play.. but will give me that LOUD static you talk of.. IF i run it from a system. 
I have NO SYSTEM sounds.. but i have all others. NO Log on / Log off start up sounds. Unless i hunt them down and click directly.. then i either get LOUD static or the correct sound. 

i know its gotta be some sort of sound config conflict.. but i am just NOT a sounds type of guy.. i would like to see some one with a few brain cells and history with sounds in ubuntu.. help me track it down. i am sure if ya'all can do that.. then we can post the solves for many others.. help me out please?


RJ

---

### Post by forestwalkerjoe on 2009-05-29
hey thracker.. 
I didnt read all of your posts.. but.. some thing that helped me get at least general play for MP3 and flash was to open alsamixer. 
Open a Terminal.. looks like a ms dos.. and type **alsamixer**. Use your arrows to move about.. and turn UP or ON all things that are related to playing PC sounds. 
there is also some little tweaks you can do from here: [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems")
Be sure to look at the Alsa Update compile.. not just the older one. 

and here:[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

this one is really a good one for 904.. so follow it cleanly.. and then if all else fails.. use the appendix at the bottom to trouble shoot and post your information for a solve. 
My only need now.. is i have Some system sounds.. still cant figure out why my system doesnt like to play the Start up and shut down system sounds. I can find them IN my system and click and play them.. and i have the CLICK and THUMP of opening and closing programs now.. but no log ON and Log Off sounds. Very strange. ALL other sounds.. video in FF , MP3's , DVD'S , all of it.. plays just fine now.. even the Roll Over sound bites i could not get at the first install of 810 and upgrade TO 904 work now. 
This could be an ALSA MIXER miscompile.. or a Pulse audio glitch.. or misconfig on my part. Some times there are files that done compile upon a Downloaded upgrade. So check the links above.. it takes a little reading.. and following the plan.. but you should be able to get your sounds up and running. TRY to set up your Alsa mixer.. Make sure IN volume you dont have JACK checked.. and use the Pulse audio set up.. it seems to work wonders for others.. at least i have seen that be true. 
OH.. and BTW.. you have your settings such.. that if i click on your name, there is no way to leave you a private message or answer to any questions.. unless its posted in Forum itself. Some have their reasons for that.. but for me, if i am trying to leave a help for a problem, I'll post and Post to the private message as well.. so they know its there or can get better personal help from a one to one. 


FWJ

---

### Post by bhaumik_thacker on 2009-06-12
hi all,

thank you joe for the links. they were a gret help.

the problem with my sound was that the balance wasnt right and alsamixer needed changes in its controls.

me being a newbee, couldnt figure out alsamixer but the links were great help.


(although, i m not facing any sound issues as you all. strange but true. i will try to regularly visit this thread to learn more about sound in ubuntu.)

thanks a lot everyone. these are the links that can explain alsamixers from the scratch.

---

### Post by kfrancart on 2009-06-24
Finally working, thanks to this tread! Had same errors as many here...

Worked in 8.10 stopped after upgrade to 9.04. Changed to OSS from Default (ALSA not working) in Sound Preferences, Test button beeped but no sounds under Sounds tab - All sound events sounded like scratching.

Some of my audio apps would work if they had the ability to override the Default and allow me to choose OSS. 

Installed Gnome ALSA Mixer using the Synaptic Package Manager (searched for ALSA) found PCM Slider was all the way down and the Capture slider was also all the way down. The PCM slider wasn't muted, there is no mute button, it was just turned down all the way. Did not see this slider in Alsamixer only in the Gnome Alsa Mixer.

Many thanks to those who persevered on this thread!

---

### Post by forestwalkerjoe on 2009-07-02
I am not sure.. but i think what is left of my issue with sound.. is related to the fact that i did a downloaded upgrade from 810 to 904. 
I think that some of my sound config is set up based off the 810 settings and i have NO idea how to reset these sound configs so that the natural 904 defaults will take over. I am sure that part of this RESET to Default will bug me.. because I'll have to redo all of it.. and find what made it work all over again.Most of my sound issues have been solved over time.. with the exception that Start up and Log off/Shut down sounds dont work. when  hit the Pulse audio icon there are settings at the top.. IN mine.. there are multiple choices.. instead of only one. I think there is a choice conflict.. it doesnt know what to do for the local sound server. or some thing. ANY have clues how to solve this? ask more questions if you want to know more.

---

### Post by MadEarThInk on 2009-08-03
> **GH68 said:**
> daveysan,

I'll see what I can do as soon as I have time (right now I'm not at my Ubuntu computer). Another idea, instead of trying to use my files, would be to create a new user on your computer and check if Pulseaudio give any sound for that user. If so, copy the .pulse directory (and possibly other files/directories?) to you own home directory.

Just to clarify exactly what problem I had, so we are not thinking of different problems:
1. Pulseaudio worked flawlessly in Ubuntu 8.10
2. After upgrading to 9.04 there was no sound, and I only got it to work by selecting "OSS" in System->Preferences->Sound
3. I tried to adjust all settings in the volume control etc according to the hints in this thread but ended up with no change.
4. I copied the .pulse directory from another user on the *same* computer to my own home directory. (Please note that I was the only user for which Pulseaudio stopped working, I don't know if it had anything to do with the fact that I upgraded to 9.04 from my own account).
5. After step 4, I could again change to Pulseaudio in System->Preferences->Sound, and I had sound working for all applications.

Good luck!
This worked for me as well.  Nice find and thanks.

---

### Post by Apollo2366 on 2009-08-04
Wow! This is awesome! Thanks for this. I was having immense problems with pulseaudio and ALSA, so I had switched to OSS, but by turning up "PCM" and turning "Independ" I get all my old functionality back! Here's the thread I started for my problem: [http://ubuntuforums.org/showthread.php?t=1229317](http://ubuntuforums.org/showthread.php?t=1229317) All my setup info is in there.

---

