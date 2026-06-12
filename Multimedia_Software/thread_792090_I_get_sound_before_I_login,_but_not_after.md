---
title: "I get sound before I login, but not after"
date: 2008-05-12
forum: Multimedia Software
---

### Post by IcedDante on 2008-05-12
I'm working with a relatively new installation of Ubuntu sporadically and I cannot remember if sound ever worked on it because I was using this box for development. Check it:

A while ago I had a problem occur where I went to System->Administration and the Synaptic Package Manager was not there. I don't know why this happened, but fixing it involved adding myself to the admin group using "usermod" as is detailed in this post:

[**http://ubuntuforums.org/showthread.php?t=703998**]("http://ubuntuforums.org/showthread.php?t=703998")

I wonder if the cause of that problem is causing my sound problems now.

What is happening is that when I boot up Ubuntu, firstly it takes a ridiculously long time to start (compared to when I first installed it where it started up super quick) and seems to just "hang" at a black screen for a while.

When I am finally presented with a login screen I hear those beautiful bongo drums clap, but once I login, I get no sound. If I click on the Volume Control icon I get a:
**No volume control GStreamer plugins and/or devices found.**

Going to System->Preferences->Sound and clicking on test for any option I get:
**audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.**

aplay -l confirms that "**no sound cards are found**"
and lspci -v returns several devices but I'm not sure if any of them are my sound card (I'll include the output in the next post if it will help). 

I have a feeling that the sound not working after I login may have something to do with a permissions setting that I can fix. Any ideas?

Thanks for any help in advance.

---

### Post by IcedDante on 2008-05-12
Here is the unwieldy (but edited: I deleted some of the lines about buses and memory ports and the like) output from **lspci -v**
```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02) (prog-if 00 [UHCI])

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation Latitude C640
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at 3a000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: Cirrus Logic Crystal WMD Audio Codec
        Flags: bus master, medium devsel, latency 0, IRQ 5

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: PCTel Inc Dell Inspiron 2100 internal modem
        Flags: bus master, medium devsel, latency 0, IRQ 5

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 00e3
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 7 8)
        Subsystem: Dell Unknown device 00e3
        Capabilities: <access denied>

02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
        Subsystem: Dell Unknown device 00e3
        16-bit legacy interface ports at 0001

02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
        Subsystem: Dell Unknown device 00e3
        16-bit legacy interface ports at 0001

```

---

### Post by IcedDante on 2008-05-13
I saw another post for someone that owned my model Laptop (Dell Latitute c510) that reported that everything worked OOTB for them except for sound. No information on how/if they fixed this problem. Any help you all could provide would be appreciated- let me know if you need any more information from me.

---

### Post by RealPSL on 2008-05-14
By adding yourself to the admin group I am suspecting that you removed yourself from the audio group which is required for your sound to work. You can tell by typing the ```
groups
```command which will list your groups. If you are only in the admin group then that is definitely your problem. To fix I recommend the following

System > Administration > Users and Groups. Enter your password. Highlight your user and click properties. Select the User privileges tab. Check all the privileges you need including audio. Log off and log in and you should have sound.

---

### Post by IcedDante on 2008-05-16
> **RealPSL said:**
> By adding yourself to the admin group I am suspecting that you removed yourself from the audio group which is required for your sound to work. 

System > Administration > Users and Groups. Enter your password. Highlight your user and click properties. Select the User privileges tab. Check all the privileges you need including audio. Log off and log in and you should have sound.

Thanks for the advice, but when I went to User Privileges both for myself and for root the list was empty! I clicked 'OK' to finish, and it seemed to have wiped out all my group settings and Ubuntu is unusable. This seems to be out of the scope of Multimedia- so I'll shift over to a new thread. 

thanks for your help!

---

