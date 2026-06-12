---
title: "Nuforce Udac USB DAC (soundcard)"
date: 2010-11-23
forum: Multimedia Software
---

### Post by mosfidelity on 2010-11-23
Hi!

There is only one reason I cant make the switch from Windows to Ubuntu, and that is sound. I need to be able to listen to music on my headphones while using the computer. However, I have problems using my external USB DAC in Ubuntu, that works flawlessly on windows. The DAC is a NuForce uDAC 2, and it shows up in pulseaudio. I can get it to work for e few minutes, but then the sound is totally distorted - unable to listen to.

If I then restart the computer, the USB DAC does not show up in PulseAudio. Then after a couple of reboots, it's back, but plays for a couple of minutes, or not at all. Ubelievably frustrating! The USB DAC works in windows, so it is not a hardware problem.

I would be grateful for a direction towards a solution to this problem, so that I can start using Ubuntu fulltime.

Specs:
Ubuntu 10.10 (also tried Mint 10, with same results).
[NuForce USB DAC 2]("http://www.nuforce.com/hp/products/iconudac2/")
PulseAudio

---

### Post by cchhrriiss121212 on 2010-11-23
The device works in Linux [according to this]("http://www.blinkenlights.ch/ccms/misc/nuforce_udac.html") (but this is the udac and not the udac-2 which may be different). 

Could you post the output of "lsusb" and "aplay -l" from a terminal? Make sure the device is plugged in at the time.

---

### Post by mosfidelity on 2010-11-23
> **cchhrriiss121212 said:**
> The device works in Linux [according to this]("http://www.blinkenlights.ch/ccms/misc/nuforce_udac.html") (but this is the udac and not the udac-2 which may be different). 

Could you post the output of "lsusb" and "aplay -l" from a terminal? Make sure the device is plugged in at the time.

Thanks for the quick reply, cchhrriiss121212! :)

**_lsusb:_**
```
Bus 004 Device 003: ID 1e7d:30d4 ROCCAT 
Bus 004 Device 002: ID 1852:db96  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c066 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**_aplay -l:_**
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: N2 [NuForce µDAC 2], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: N2 [NuForce µDAC 2], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


When the sound stops (and Rhythmbox freezes) this error message is in the kern.log (hundreds of entries):

```
[ 2280.856226] 2:3:1: usb_set_interface failed
```

EDIT:
This message shows up in syslog also:
```
pulseaudio[2018]: alsa-sink.c: Failed to set hardware parameters: Input/output error
```

---

### Post by cchhrriiss121212 on 2010-11-23
You might just need to define it as default using ~/.asoundrc. You could try copying this (edited from the link earlier):
```
pcm.!default {
   type            plug
   slave.pcm       "softvol"   
}

pcm.softvol {
   type            softvol
   slave {
      pcm         "dmixer"      
   }
   control {
      name        "PCM"       
      card        0
       }
}

pcm.dmixer  {
   type dmix
   ipc_key 1025
   slave {
      pcm "hw:1,0"
   }
   bindings {
   0 0
   1 1
   }
}

ctl.dmixer {
   type hw
   card 1
}
```
Now open a terminal and type:
```
gedit ~/.asoundrc
```
then paste the code above and save the file. Reboot to try it out.

---

### Post by mosfidelity on 2010-11-23
> **cchhrriiss121212 said:**
> You might just need to define it as default using ~/.asoundrc.

Thank you for the help. 
I tried creating .asoundrc in my home folder with the code you provided. However, I still get distorted sound after a couple of minutes of playing music. 

This is from kern.log:
```
[  647.508928] 2:3:1: usb_set_interface failed
```

syslog:
```
pulseaudio[2005]: alsa-sink.c: Failed to set hardware parameters: Input/output error
```

user.log:
```
pulseaudio[2005]: module-alsa-card.c: Failed to find a working profile.
pulseaudio[2005]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="2" name="pci-0000_04_00.1" card_name="alsa_card.pci-0000_04_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
pulseaudio[2005]: module-alsa-card.c: Failed to find a working profile.
pulseaudio[2005]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="3" name="pci-0000_05_00.1" card_name="alsa_card.pci-0000_05_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
pulseaudio[2187]: pid.c: Daemon already running.
pulseaudio[2005]: ratelimit.c: 3 events suppressed
pulseaudio[2005]: ratelimit.c: 96 events suppressed
pulseaudio[2005]: ratelimit.c: 31 events suppressed
pulseaudio[2005]: ratelimit.c: 31 events suppressed
pulseaudio[2005]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
pulseaudio[2005]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_usb_audio'. Please report this issue to the ALSA developers.
pulseaudio[2005]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
pulseaudio[2005]: alsa-sink.c: Failed to set hardware parameters: Input/output error
pulseaudio[2005]: last message repeated 2 times
```

Is there anything else I could try to fix this?

I really appreciate the help.

---

### Post by cchhrriiss121212 on 2010-11-23
I'm not sure, but it looks unlikely. It is not able to define a profile, and the device uses the generic USB ALSA driver which means you can't set one manually. 
Searching around on Google I see this consensus: the uDAC works but the uDAC2 does not.

If you have the time you could try using it on a system without pulse (I have seen reports it causes distorted output in some devices), but that would just be a guess.

---

### Post by mosfidelity on 2010-11-25
I've sent an email to NuForce, asking them if they know about any solutions to this. Crossing my fingers!

---

### Post by RonnieBiggs on 2011-01-08
new informations?

---

### Post by chowanec on 2011-01-14
Hey all,

I have a similar problem.  I also have the NuForce uDac2.  It shows up in lsusb:
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 004: ID 1852:db96  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

It's the "db96" one -- confirmed by plugging and replugging.

And in aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: N2 [NuForce µDAC 2], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: N2 [NuForce µDAC 2], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And -- here's where it gets weird for me.  I cannot hear ANYTHING via Amarok and PulseAudio.  When opening PulseAudio Volume Control:
Playback -> Amarok: I can select the nuForce from the drop down.
Output Devices: Shows the nuForce left and right channels and the levels -- i.e. I can see the "music" but I cannot hear it. 
Configuration Tab: I have tried EVERY POSSIBLE configuration here to no effect.  My choices are: 
[LIST]
[*]Analog Stereo Duplex
[*]Analog Stereo Output + Digital Stereo (IEC958) Input
[*]Analog Stereo Output
[*]Digital Stereo (IEC958) Output + Analog Stereo Input
[*]Digital Stereo (IEC958) Output + Digital Stereo (IEC958) Input
[*]Digital Stereo Duplex (IEC958)
[*]Analog Stereo Input
[*]Digital Stereo (IEC958) Input
[/LIST]

I cannot choose a specific device WITHIN Amarok -- it only indicates Pulse Audio.

Any ideas? I've googled for two days looking around for solutions and have come up pretty dry.  Works on my Windows laptop and I like how this thing sounds... :P  Would love to find a way to hook it up to my media PC...

---

### Post by earwax on 2011-02-20
Hi,
Have the same problem with udac2, so i bought the older udac in stead. However the same problem turned upp. Sound got distorted after a few minutes, firefox went down and Rythmbox froze. 

Using Ubuntu 10.04 LTS  - Lucid Lynx

Any help? Can still return the newly bought older udac so I&#7743; happy for prompt reply...

---

### Post by Jondice on 2011-04-07
> **mosfidelity said:**
> Hi!

There is only one reason I cant make the switch from Windows to Ubuntu, and that is sound. I need to be able to listen to music on my headphones while using the computer. However, I have problems using my external USB DAC in Ubuntu, that works flawlessly on windows. The DAC is a NuForce uDAC 2, and it shows up in pulseaudio. I can get it to work for e few minutes, but then the sound is totally distorted - unable to listen to.

If I then restart the computer, the USB DAC does not show up in PulseAudio. Then after a couple of reboots, it's back, but plays for a couple of minutes, or not at all. Ubelievably frustrating! The USB DAC works in windows, so it is not a hardware problem.

I would be grateful for a direction towards a solution to this problem, so that I can start using Ubuntu fulltime.

Specs:
Ubuntu 10.10 (also tried Mint 10, with same results).
[NuForce USB DAC 2]("http://www.nuforce.com/hp/products/iconudac2/")
PulseAudio

I just wanted to confirm I have this problem with the NuForce uDAC-2; I haven't had the opportunity to test yet in other distros.

---

### Post by jchedstrom on 2011-11-18
Using Ubuntu 11.04 and 11.10 the uDAC 2 works fine... mostly. Running for a few hours in an old AMD 5400+ rig works fine. Running on my newer sandy bridge Intel i5-2500K on GIGABYTE GA-H67MA-UD2H-B3 motherboard has worked for months except for some weirdness.

When I first bought it I was constantly swapping it with some other USB DACs for comparison on my Sandy Bridge rig. Sometimes it would become distorted after running for a few minutes. Sometimes it would start distorted. Sometimes it would only become distorted after moving the Left/Right balance to an extreme. I was never able to figure out why or what exactly remedied the situation. After settling on the uDAC 2  it hasn't given me problems for the last few months, but today I did some more swapping for some amp tests and the problem WOULD NOT GO AWAY on my newer Intel rig after moving to a left balance extreme. Finally I discovered a repeatable solution. Plug it into USB2.0 slot = distorted. Plug it into USB3.0 slot = good. I'm not sure what I've been plugged into for the last few months, but this fixed my problem. 

Here's a USB2.0 port dmesg output. Recognized correctly but using "ehci_hcd". Audio is heavily distorted:
```
[  892.184350] usb 1-1.3: new full speed USB device number 7 using ehci_hcd
[  892.316050] usb 1-1.3: config 1 has an invalid interface number: 3 but max is 2
[  892.316055] usb 1-1.3: config 1 has an invalid interface number: 3 but max is 2
[  892.316058] usb 1-1.3: config 1 has an invalid interface number: 3 but max is 2
[  892.316061] usb 1-1.3: config 1 has an invalid interface number: 3 but max is 2
[  892.316064] usb 1-1.3: config 1 has no interface number 2
[  892.335087] input: NuForce, Inc. NuForce µDAC 2 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input11
[  892.335169] generic-usb 0003:1852:DB96.0008: input,hidraw0: USB HID v1.00 Device [NuForce, Inc. NuForce µDAC 2] on usb-0000:00:1a.0-1.3/input0

```

Here's a USB3.0 port dmesg output. Recognized correctly but using "xhci_hcd". Audio is perfect:
```
[  901.977867] usb 3-1: new full speed USB device number 3 using xhci_hcd
[  902.112014] usb 3-1: config 1 has an invalid interface number: 3 but max is 2
[  902.112020] usb 3-1: config 1 has an invalid interface number: 3 but max is 2
[  902.112023] usb 3-1: config 1 has an invalid interface number: 3 but max is 2
[  902.112025] usb 3-1: config 1 has an invalid interface number: 3 but max is 2
[  902.112029] usb 3-1: config 1 has no interface number 2
[  902.114988] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[  902.127931] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[  902.140927] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[  902.174846] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[  902.175949] input: NuForce, Inc. NuForce µDAC 2 as /devices/pci0000:00/0000:00:01.0/0000:01:00.0/usb3/3-1/3-1:1.0/input/input12
[  902.176033] generic-usb 0003:1852:DB96.0009: input,hidraw0: USB HID v1.00 Device [NuForce, Inc. NuForce µDAC 2] on usb-0000:01:00.0-1/input0
[  902.187817] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[  902.200786] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[  902.213755] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[  902.357416] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.359415] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.361393] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.363373] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.365397] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.367392] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.369387] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.371356] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.373378] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
[  902.375346] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint

```

P.S.  For other budget minded audiophiles out there I have the following tip. Although I kept the uDAC 2 which is an impressive USB DAC. If you're budget conscious I also highly recommend the cheaper Behringer UCA222. It has a ****** (though usable) volume nob but has a stereo mic-in and optical out which is nice. Honestly I found it difficult to tell the difference on either $150 Beyerdynamic 250 headphones or my ~$2000 speaker setup.

---

### Post by Welly Wu on 2012-09-03
I have a System76 Lemur Ultra Thin (lemu4) and Ubuntu 12.04.1 64 bit Long Term Service along with a NuForce Icon uDAC-2 HP. I also have the Ultimate Ears Ue-10 PRO custom in ear monitors, Grado SR-60i headphones, and Sennheiser HD-650 headphones with the Cardas Headphone Replacement Cable. I have no problems whatsoever. I used Clementine and I switched to Rhythmbox and I finally switched to Banshee. I can get my .FLAC and .MP3 files to play flawlessly. It provides full, rich, balanced stereo sound output.

---

