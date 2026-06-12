---
title: "Linux audio with Audient iD44 MKII stopped working"
date: 2024-07-17
forum: Multimedia Software
---

### Post by M.Vilenius on 2024-07-17
I recently (~half a year ago) got back to Linux after a long break. I have an Audient iD44 MKII audio interface and until yesterday it worked "plug-n-play". Today I did an update which seems to have broken things.

First some possibly critical information:
Lenovo ThinkBook 16p Gen 4
Ubuntu 22.04.4 LTS
Kernel 6.5.0-44-generic
GNOME 42.9

I no longer have the option for Audient iD44 stereo analog output available in my Ubuntu Sound settings. In fact, I only had my laptop input and output (sof-hda-dsp) and HDMI monitor output (HDMI/DisplayPort - HDA NVidia) available.

Now I've been going into rabbit hole of ALSA, Pulseaudio (which I was somewhat familiar with), and PipeWire (which is completely new to me) documentation and forum posts online with no luck.

After looking into things, removing, reinstalling and restarting pipewire I got Multichannel Audient input and output (Audient iD44 Multichannel) to appear for a while (it's again gone), but still no stereo analog output, which was there before the update.

***inxi -aA*** shows the following:

```
Audio:
  Device-1: Intel vendor: Lenovo driver: sof-audio-pci-intel-tgl
    alternate: snd_hda_intel,snd_sof_pci_intel_tgl bus-ID: 00:1f.3
    chip-ID: 8086:51ca class-ID: 0401
  Device-2: NVIDIA vendor: Lenovo driver: snd_hda_intel v: kernel pcie:
    gen: 3 speed: 8 GT/s lanes: 8 link-max: gen: 4 speed: 16 GT/s
    bus-ID: 01:00.1 chip-ID: 10de:22be class-ID: 0403
  Device-3: Audient iD44 type: USB driver: hid-generic,snd-usb-audio,usbhid
    bus-ID: 3-9.4:9 chip-ID: 2708:000b class-ID: fe01
  Sound Server-1: ALSA v: k6.5.0-44-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 1.0.7 running: yes
```

***aplay -l*** gives me:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: iD44 [Audient iD44], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: sofhdadsp [sof-hda-dsp], device 0: HDA Analog (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: sofhdadsp [sof-hda-dsp], device 1: HDA Digital (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: sofhdadsp [sof-hda-dsp], device 3: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: sofhdadsp [sof-hda-dsp], device 4: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: sofhdadsp [sof-hda-dsp], device 5: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


With ***pactl list cards*** I can see the following:

```
Card #116
Name: alsa_card.usb-Audient_Audient_iD44-00
Driver: alsa
Owner Module: n/a
Properties:
api.acp.auto-port = "false"
api.acp.auto-profile = "false"
api.alsa.card = "1"
api.alsa.card.longname = "Audient Audient iD44 at usb-0000:00:14.0-9.4, high speed"
api.alsa.card.name = "Audient iD44"
api.alsa.path = "hw:1"
api.alsa.use-acp = "true"
api.dbus.ReserveDevice1 = "Audio1"
device.api = "alsa"
device.bus = "usb"
device.bus-id = "usb-Audient_Audient_iD44-00"
device.bus_path = "pci-0000:00:14.0-usb-0:9.4:1.0"
device.description = "Audient iD44"
device.enum.api = "udev"
device.icon_name = "audio-card-analog-usb"
device.name = "alsa_card.usb-Audient_Audient_iD44-00"
device.nick = "Audient iD44"
device.plugged.usec = "5350297026"
device.product.id = "0x000b"
device.product.name = "Audient iD44"
device.serial = "Audient_Audient_iD44"
device.subsystem = "sound"
sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9.4/3-9.4:1.0/sound/card1"
device.vendor.id = "0x2708"
device.vendor.name = "Audient"
media.class = "Audio/Device"
factory.id = "14"
client.id = "36"
object.id = "105"
object.serial = "116"
object.path = "alsa:pcm:1"
alsa.card = "1"
alsa.card_name = "Audient iD44"
alsa.long_card_name = "Audient Audient iD44 at usb-0000:00:14.0-9.4, high speed"
alsa.driver_name = "snd_usb_audio"
alsa.mixer_name = "USB Mixer"
alsa.components = "USB2708:000b"
alsa.id = "iD44"
device.string = "1"
Profiles:
off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
output:multichannel-output+input:multichannel-input: Multichannel Duplex (sinks: 1, sources: 1, priority: 101, available: yes)
output:multichannel-output: Multichannel Output (sinks: 1, sources: 0, priority: 100, available: yes)
pro-audio: Pro Audio (sinks: 1, sources: 1, priority: 1, available: yes)
input:multichannel-input: Multichannel Input (sinks: 0, sources: 1, priority: 1, available: yes)
Active Profile: input:multichannel-input
```

With ***pactl list sinks*** I can see the internal audio and the HDMI sinks, but nothing with the Audient. Should a stereo analog sink be configured for the Audient? How and where? Or is there something else missing?

I tried to add Virtual Sinks for the Audient Pro-Audio as per here: [https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Virtual-Devices#virtual-sinks](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Virtual-Devices#virtual-sinks) and here [https://www.reddit.com/r/archlinux/comments/wahggl/wireplumber_remap_usb_audio_interface/](https://www.reddit.com/r/archlinux/comments/wahggl/wireplumber_remap_usb_audio_interface/)
I could then see the output in the Ubuntu Sound settings, but no sound... In fact, after setting up Pro-Audio in ```
pavucontrol
``` for the Audient, even the integrated sound didn't work.

I also tried older kernel (6.5.0-41 and 6.5.0-35) but those didn't want to even boot correctly...

After faffing about the whole day ***pactl list cards*** doesn't show
```
output:multichannel-output+input:multichannel-input: Multichannel Duplex (sinks: 1, sources: 1, priority: 101, available: yes)
output:multichannel-output: Multichannel Output (sinks: 1, sources: 0, priority: 100, available: yes)
input:multichannel-input: Multichannel Input (sinks: 0, sources: 1, priority: 1, available: yes)
``` anymore under "Profiles" (only pro-audio and off remain)...

---

### Post by euol on 2024-08-05
If you have verified that PipeWire is the active audio server, you can use pavucontrol to configure audio profiles and add virtual sinks if needed. Verify ALSA detects the device with aplay -l and reload ALSA with sudo alsa force-reload

---

### Post by 909mjolnir on 2024-08-07
One typically helpful sound app is qasmixer which I think comes from qastools.  I always install it because it gives a quick set of on/off switches (round buttons) and faders (volume level controls).  
Be sure to set the display from the "View" menu so you can see everything.  Come back here if you need help with the "hw:card" (hardware:soundcard) types of settings.  

qasmixer looks something like this:
[img]https://ia801002.us.archive.org/4/items/Linux-DAW-Extra-Help/QasMixerSettings.png[/img]

---

### Post by bobunderwood99 on 2024-08-07
I'd be concerned that inxi doesn't show PulseAudio as running.

---

### Post by M.Vilenius on 2024-08-22
> **bobunderwood99 said:**
> I'd be concerned that inxi doesn't show PulseAudio as running.

bobunderwood99, you're right to be concerned! Thank you for noticing that.

For some reason the PulseAudio service seems to be running but non-responsive. Trying to restart it didn't work, but after killing it with ```
pulseaudio -k
``` and starting it, I now got my Audient back in my sound settings. Now only as multichannel output, so I still need to figure out how to get it work in normal stereo mode.

But it also looks like I have to kill and start PulseAudio now after every restart...

---

### Post by M.Vilenius on 2024-08-22
OK, I got a virtual stereo sink working now based on these instructions:
[https://wiki.archlinux.org/title/PulseAudio/Examples#Remapping_select_audio_sources](https://wiki.archlinux.org/title/PulseAudio/Examples#Remapping_select_audio_sources)

Now it just seems that PulseAudio freezes after some time and I need to restart it :/ Not very convenient.

---

### Post by M.Vilenius on 2024-08-22
And disabling (commenting out) "load-module module-suspend-on-idle" in /etc/pulse/default.pa seems to have fixed the freezes. Thanks all for helping!

---

