---
title: "headset works, usb speakers do not"
date: 2009-10-12
forum: Multimedia Software
---

### Post by cyberstump on 2009-10-12
Hello All,

I have been getting fairly upset while messing around with my old speakers here.  Sound has always worked out of my desktop headphone jack, but when I attempted to plug my usb speakers in nothing comes out (not even the initial boot up sounds).

While my machine is booting, a sharp little bit of static comes through the speakers, which leads me to believe that they are hooked up correctly. I am using ubuntu 9.04, have attempted to search the forums and use anything that looked like it may work but have had no success.  

Everything else out there that I found did not account for the headphones working but not the speakers.  usually it was the other way around.  

And it may also be important to note that I am a total noob.  I have been using ubuntu exclusively for about a year, and this is the first time that I havent been able to eventually get something to work.  Thanks in advance, and I appreciate all of the help that the linux gurus have provided for people like me :)

---

### Post by cyberstump on 2009-10-12
some other info... 

1.) I do not understand alsa what-so-ever :)

2.) output for aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


3.) output for lspci

00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:07.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by marshmallow1304 on 2009-10-12
Check Volume Control (right-click on the speaker icon in the tray) and make sure Device is set correctly.

---

### Post by cyberstump on 2009-10-12
> **marshmallow1304 said:**
> Check Volume Control (right-click on the speaker icon in the tray) and make sure Device is set correctly.
I have seen in other posts that some people were looking to make sure that their "usb audio device" was tagged.   I dont seem to have that option anywhere. I have searched around through everything in the system>pref>sound, and came up short.  I messed around with the stuff under the volume control icon like to suggested, and still to no avail.

thanks for the speedy reply though!  That was great :)

Still struggling....  I know that there is a way to fix it, and I just need to be patient.  Problem is, I lack patients....

---

### Post by LorisMaria on 2009-11-09
It has been one of my biggest pains, the USB speakers. I finally fixed it today.

Not sure if your problem is the same as mine, but here are the steps that fixed it:

- Click on the speaker icon and then "Volume control..."
- Look at the Device field (on the top of the box) and make sure it's showing USB Audio. If this option is not available, then you might have a bigger issue... or you can always unplug it and plug it again. Works for me most of the time.
- Then you'll see only one sound level controller (PCM). It'll be set to the lowest level, so you just raise it to a volume you think is comfortable.
- Then, to make sure you can control USB volume through the speaker icon on the tray, click on the "Preferences" button, still on the Volume Control panel. 
- Select USB Audio, so when you move the slider on the tray, it'll be in relation to USB and not speaker audio.

Hope this works for you too!

---

