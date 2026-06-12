---
title: "Can't record sound (microphone)"
date: 2009-03-30
forum: Multimedia Software
---

### Post by TBTsjG89 on 2009-03-30
Hi Everybody!

I'm having a lot of trouble trying to get my microphone to work (including suicidal thoughts](*,)). I've read a lot on the topic, but I'm still unable to fix it.
When I speak in the microphone, I can hear my voice coming from the speakers, and I'm also able to set the volume.
But when it comes to recording, all programs are deaf.
I have attached a screenshot of my current settings hoping that you could help me find a solution.
Any help would be much appreciated!
Thanks in advance,

Mr krey

---

### Post by TBTsjG89 on 2009-04-02
Please, somebody help before my topic disappears!
Any help would be most welcome.

Mr. krey

---

### Post by vegetarianshrimp on 2009-04-02
Is it an internal mic, or is it a mic you bought that you connect to your computer via a cord? Also, what make and model is your computer? Hopefully I can help you once I get this information. :)

---

### Post by TBTsjG89 on 2009-04-04
Thanks for your reply, it's an external mic, plugged into my onboard soundcard.
This is what *sudo lspci -v* says about my soundcard:
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


---

### Post by vegetarianshrimp on 2009-04-04
Open the volume control, click preferences, make sure Mic boost, capture, and imput source are selected. In the Playback tab, increase the volume on Mic boost. In Recording tab, Increase the capture volume, and click the mic at the bottom so it's not "X"ed out. In the Otions tab, the Input Source should either be mic or line, I'm not sure, so try both.

Hope that helps! I'm kind of a newb myself, so it might not :(
-vegetarianshrimp:)

---

### Post by Hue_Blue on 2009-04-04
I am also having the same problems. I wish I was here to help but I unfortunately am in need of help myself. I am using Ubuntu 9.04 on a Compaq Presario sr5233wm I can give more info if you need it. I have tried installing a list of things to fix this that was said in a forum that i now cannot find to refrance (Sorry) . Here is what i have: 

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci -v | less 

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Hewlett-Packard Company Device 2a59
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fc000000-febfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Device 2a59
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fbdf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fbf00000-fbffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
        Subsystem: Hewlett-Packard Company Device 2a59
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at b880 [size=32]
        Kernel driver in use: uhci_hcd

---

### Post by Hue_Blue on 2009-04-04
I have opened all up in gui and all are turen up but boost

---

### Post by Hue_Blue on 2009-04-06
I have managed to fix this by changing my preferred sound to alsa and unmute the mic and then changed the mic to front mic in volume control options

---

### Post by TBTsjG89 on 2009-04-08
I had to reinstall my system, and the microphone *magically* started working. Thanks for your help!

mr_krey

---

