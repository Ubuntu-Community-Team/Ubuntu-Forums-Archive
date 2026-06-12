---
title: "Problems with the ATI Radeon HD 2400 HDMI Audio"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by johntash on 2007-11-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/151374](https://bugs.launchpad.net/ubuntu/+bug/151374) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Alright.  So we just went out and purchased an ATI Radeon HD 2400 graphics card mainly because it had a built-in hdmi port with sound.   

I got Xorg and Xgl working using the latest drivers from ATI (7.11 released on Nov. 21,2007).

I installed Alsa 1.0.15 since I saw in the changelog it said something about adding support for audio through hdmi on the R600 cards, but it's still not recognized.

Here's **lspci **
```
-cut-
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c3
05:00.1 Audio device: ATI Technologies Inc Unknown device aa10

```

**cat /proc/asound/cards**
```

 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 17

```

Sound will still work if I use the motherboard's sound, but it won't come through the hdmi cable on the graphics card.

Does anyone else have this card, ATI Radeon HD 2400, and have video and sound working through it?

If not, what other card is available that actutally can play sound through hdmi?

---

### Post by Yellow Pasque on 2007-11-26
Try:
```
sudo update-pciids
```
and THEN run lspci.

Not sure what to tell you after that. I have my integrated 690G HDMI detected through OSSv4, so if you can't find a solution with ALSA, keep that in mind as a possible alternative.

---

### Post by markoloka on 2007-11-26
You need to install drivers for it. I have 2400hd and i'm writing this using it. 
I recommend this way...as it's easiest way to install:
"Script:

[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

I would just download the script, press cntr+alt+f1 and get to the terminal. Then change it into a executable as root, then just run it. It did all the magic and I had the latest driver installed.

sudo chmod +x ./install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh

To get Xv working, just type

sudo aticonfig --overlay-type=Xv in a terminal and restart your system."
Info taken from ubuntuforums.org and phoronix forum.

Edit note:
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7059 Release

But lspci still don't know about my card. Unknown device blaah blaah.

---

### Post by Yellow Pasque on 2007-11-26
> But lspci still don't know about my card. Unknown device blaah blaah.
Did you try the sudo update-pciids command?

---

### Post by johntash on 2007-11-26
Thanks for both of your guys' help.   

**markoloka**:  Do you have sound working through the hdmi cable as well?   I looked at the script and it looked like it just installed the new drivers for the video which I had working already..  I'll try the script anyway in just a minute.


**Temüjin**:  After running update-pciids, lspci still shows it as an unknown device.  I'm installing OSSv4 right now to see if OSS will help any.

---

### Post by johntash on 2007-11-26
Okay.  I disabled the motherboards onboard sound in the bios.  Now no sound cards are detected.

I installed OSSv4 using [this link]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60") from Temüjin's signature.  It installed and started up fine, but still doesn't detect the ATI card as having sound..

Output of **ossinfo**
```
Version info: OSS 4.0 (b1009/200711131254) (0x00040003)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 (bawls-desktop)

Number of audio devices:        0
Number of audio engines:        0
Number of MIDI devices:         0
Number of mixer devices:        0


Device objects
 0: osscore0 OSS core services
 1: ossusb0 USB audio core services
 2: vmix0 OSS transparent virtual support

MIDI devices (/dev/midi*)

Mixer devices (/dev/mixer*)

Audio devices

```

And when I try to run ossmix, I get 
```
SNDCTL_MIX_NREXT: No such device or address
```

**lspci -v **
```

05:00.1 Audio device: ATI Technologies Inc Unknown device aa10
        Subsystem: VISIONTEK Unknown device aa10
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fe210000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint IRQ 0
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

```

Video through HDMI still works fine
**$ fglrxinfo**
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7059 Release
```


Any other ideas?

---

### Post by trr135 on 2008-03-09
Has there been any update on this? I am having a similar issue and wondered if you could share any fixes.

---

