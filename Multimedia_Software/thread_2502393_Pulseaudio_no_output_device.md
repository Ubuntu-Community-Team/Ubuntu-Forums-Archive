---
title: "Pulseaudio no output device"
date: 2024-11-13
forum: Multimedia Software
---

### Post by jet-bundle on 2024-11-13
I have a Dell XPS laptop running Lubuntu 22.04, kernel 5.15.0-125 which recently stopped playing audio through the system speaker (it plays through headphones). I don't think there's a hardware problem, because the system speaker works if I boot into an earlier kernel. I've tried removing and reinstalling pulseaudio, but with no effect (apart from the GUI option disappearing from the Sound & Video menu).

Here are some of the things I've tried.

aplay /usr/share/sounds/alsa/Front_Center.wav   gives silence (again I can hear it through headphones).

fuser -v /dev/snd/*   gives no response at all.

pactl info

```

Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 15
Tile Size: 65472
User Name: *****
Host Name: Dell17LUB
Server Name: pulseaudio
Server Version: 15.99.1
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: auto_null
Default Source: auto_null.monitor
Cookie: 8001:c499

```

aplay -L

```

null
    Discard all samples (playback) or generate zero samples (capture)
default
    Playback/recording through the PulseAudio sound server
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
hw:CARD=sofsoundwire,DEV=2
    sof-soundwire, 
    Direct hardware device without any conversions
hw:CARD=sofsoundwire,DEV=5
    sof-soundwire, 
    Direct hardware device without any conversions
hw:CARD=sofsoundwire,DEV=6
    sof-soundwire, 
    Direct hardware device without any conversions
hw:CARD=sofsoundwire,DEV=7
    sof-soundwire, 
    Direct hardware device without any conversions
plughw:CARD=sofsoundwire,DEV=2
    sof-soundwire, 
    Hardware device with all software conversions
plughw:CARD=sofsoundwire,DEV=5
    sof-soundwire, 
    Hardware device with all software conversions
plughw:CARD=sofsoundwire,DEV=6
    sof-soundwire, 
    Hardware device with all software conversions
plughw:CARD=sofsoundwire,DEV=7
    sof-soundwire, 
    Hardware device with all software conversions
dmix:CARD=sofsoundwire,DEV=2
    sof-soundwire, 
    Direct sample mixing device
dmix:CARD=sofsoundwire,DEV=5
    sof-soundwire, 
    Direct sample mixing device
dmix:CARD=sofsoundwire,DEV=6
    sof-soundwire, 
    Direct sample mixing device
dmix:CARD=sofsoundwire,DEV=7
    sof-soundwire, 
    Direct sample mixing device
usbstream:CARD=sofsoundwire
    sof-soundwire
    USB Stream Output

```

systemctl --user status pulseaudioaplay

```
&#9679; pulseaudio.service - Sound Service
     Loaded: loaded (/usr/lib/systemd/user/pulseaudio.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2024-11-13 09:11:50 GMT; 3min 53s ago
TriggeredBy: &#9679; pulseaudio.socket
   Main PID: 1272 (pulseaudio)
      Tasks: 3 (limit: 18595)
     Memory: 7.7M
        CPU: 133ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pulseaudio.service
             &#9492;&#9472;1272 /usr/bin/pulseaudio --daemonize=no --log-target=journal

Nov 13 09:11:50 Dell17LUB pulseaudio[1272]: Could not find org.bluez.BatteryProviderManager1.RegisterBatteryProvider(), is bluetoothd started with experimental features enabled (-E flag)?
Nov 13 09:11:50 Dell17LUB pulseaudio[1272]: Failed to find a working profile.
Nov 13 09:11:50 Dell17LUB pulseaudio[1272]: Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_1f.3-platform-sof_sdw" card_name="alsa_card.pci-0000_00_1f.3-platform-sof_sdw" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes avoid_resampling=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Nov 13 09:11:51 Dell17LUB pulseaudio[1272]: Failed to find a working profile.
Nov 13 09:11:51 Dell17LUB pulseaudio[1272]: Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_1f.3-platform-sof_sdw" card_name="alsa_card.pci-0000_00_1f.3-platform-sof_sdw" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes avoid_resampling=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Nov 13 09:11:51 Dell17LUB pulseaudio[1272]: Failed to find a working profile.
Nov 13 09:11:51 Dell17LUB pulseaudio[1272]: Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_1f.3-platform-sof_sdw" card_name="alsa_card.pci-0000_00_1f.3-platform-sof_sdw" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes avoid_resampling=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Nov 13 09:11:51 Dell17LUB pulseaudio[1272]: Failed to find a working profile.
Nov 13 09:11:51 Dell17LUB pulseaudio[1272]: Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_1f.3-platform-sof_sdw" card_name="alsa_card.pci-0000_00_1f.3-platform-sof_sdw" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes avoid_resampling=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Nov 13 09:11:51 Dell17LUB pulseaudio[1272]: Tried to configure /devices/pci0000:00/0000:00:1f.3/sof_sdw/sound/card0 (alsa_card.pci-0000_00_1f.3-platform-sof_sdw) more often than 5 times in 10s

```

So there seems to be a missing profile somewhere. I'd be grateful for advice on how to reinstate this.

---

### Post by jet-bundle on 2024-11-15
Here's the response from pacmd list-cards.  Using kernel 5.15.0-125 I get "0 card(s) available.", though if I plug headphones into the USB port I get this:

```
1 card(s) available.
    index: 0
    name: <alsa_card.usb-Dell_Dell_Adapter_-_USB-C_to_3.5mm_Headphone_Jack_SA1023_230412A1UF-00>
    driver: <module-alsa-card.c>
    owner module: 30
    properties:
        alsa.card = "1"
        alsa.card_name = "Dell Adapter - USB-C to 3.5mm H"
        alsa.long_card_name = "Dell Dell Adapter - USB-C to 3.5mm H at usb-0000:00:14.0-6, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:6:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/sound/card1"
        udev.id = "usb-Dell_Dell_Adapter_-_USB-C_to_3.5mm_Headphone_Jack_SA1023_230412A1UF-00"
        device.bus = "usb"
        device.vendor.id = "413c"
        device.vendor.name = "Dell Computer Corp."
        device.product.id = "b100"
        device.product.name = "Dell Adapter - USB-C to 3.5mm Headphone Jack SA1023"
        device.serial = "Dell_Dell_Adapter_-_USB-C_to_3.5mm_Headphone_Jack_SA1023_230412A1UF"
        device.form_factor = "headphone"
        device.string = "1"
        device.description = "Dell Adapter - USB-C to 3.5mm Headphone Jack SA1023"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-headphones-usb"
    profiles:
        input:mono-fallback: Mono Input (priority 1, available: unknown)
        output:analog-stereo: Analogue Stereo Output (priority 6500, available: unknown)
        output:analog-stereo+input:mono-fallback: Analogue Stereo Output + Mono Input (priority 6501, available: unknown)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
        output:iec958-stereo+input:mono-fallback: Digital Stereo (IEC958) Output + Mono Input (priority 5501, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:mono-fallback>
    sinks:
        alsa_output.usb-Dell_Dell_Adapter_-_USB-C_to_3.5mm_Headphone_Jack_SA1023_230412A1UF-00.analog-stereo/#1: Dell Adapter - USB-C to 3.5mm Headphone Jack SA1023 Analogue Stereo
    sources:
        alsa_output.usb-Dell_Dell_Adapter_-_USB-C_to_3.5mm_Headphone_Jack_SA1023_230412A1UF-00.analog-stereo.monitor/#1: Monitor of Dell Adapter - USB-C to 3.5mm Headphone Jack SA1023 Analogue Stereo
        alsa_input.usb-Dell_Dell_Adapter_-_USB-C_to_3.5mm_Headphone_Jack_SA1023_230412A1UF-00.mono-fallback/#2: Dell Adapter - USB-C to 3.5mm Headphone Jack SA1023 Mono
    ports:
        analog-input: Analog Input (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:

```

And if I boot into kernel 5.15.0-124 instead of 5.15.0-125 I get this, without headphones:

```

1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1f.3-platform-sof_sdw>
    driver: <module-alsa-card.c>
    owner module: 7
    properties:
        alsa.card = "0"
        alsa.card_name = "sof-soundwire"
        alsa.long_card_name = "Intel Soundwire SOF"
        alsa.driver_name = "snd_soc_sof_sdw"
        device.bus_path = "pci-0000:00:1f.3-platform-sof_sdw"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sof_sdw/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "51cc"
        device.string = "0"
        device.description = "sof-soundwire"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        HiFi: Play HiFi quality Music (priority 40768, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <HiFi>
    sinks:
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_7__sink/#0: sof-soundwire HDMI / DisplayPort 3 Output
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_6__sink/#1: sof-soundwire HDMI / DisplayPort 2 Output
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_5__sink/#2: sof-soundwire HDMI / DisplayPort 1 Output
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_2__sink/#3: sof-soundwire Speaker
    sources:
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_7__sink.monitor/#0: Monitor of sof-soundwire HDMI / DisplayPort 3 Output
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_6__sink.monitor/#1: Monitor of sof-soundwire HDMI / DisplayPort 2 Output
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_5__sink.monitor/#2: Monitor of sof-soundwire HDMI / DisplayPort 1 Output
        alsa_output.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_2__sink.monitor/#3: Monitor of sof-soundwire Speaker
        alsa_input.pci-0000_00_1f.3-platform-sof_sdw.HiFi__hw_sofsoundwire_4__source/#4: sof-soundwire SoundWire microphones
    ports:
        [Out] HDMI3: HDMI / DisplayPort 3 Output (priority 700, latency offset 0 usec, available: no)
            properties:
                
        [Out] HDMI2: HDMI / DisplayPort 2 Output (priority 600, latency offset 0 usec, available: no)
            properties:
                
        [Out] HDMI1: HDMI / DisplayPort 1 Output (priority 500, latency offset 0 usec, available: no)
            properties:
                
        [Out] Speaker: Speaker (priority 100, latency offset 0 usec, available: unknown)
            properties:
                
        [In] Mic: SoundWire microphones (priority 100, latency offset 0 usec, available: unknown)
            properties:

```

I wonder if this helps to track down the problem? Thanks in advance for any suggestions.

---

### Post by jet-bundle on 2024-11-21
Today's upgrade to 5.156.0-126 has solved the problem.

---

