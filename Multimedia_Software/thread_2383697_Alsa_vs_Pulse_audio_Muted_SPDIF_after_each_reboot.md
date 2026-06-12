---
title: "Alsa vs Pulse audio Muted SPDIF after each reboot"
date: 2018-01-28
forum: Multimedia Software
---

### Post by jean67 on 2018-01-28
Hi guys, 

Bellow is my config

I tried different things but can't fix this issue. My first question is how do we know which file is used when we open Alsamixer
I can't get this information, some people say asound with one path and other people with another ...
I want to understand where this setting is stored and what I should do to debug this kind of problem in the future

Same question for pulse audio, in the GUI there is a gap between the config of alsamixer and pulse audio.

Is there any log files that I should look first?  

Linux lnx64cert 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
cat /proc/version
Linux version 4.13.0-32-generic (buildd@lgw01-amd64-004) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.5)) #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018

cat /etc/os-release

NAME="Linux Mint"
VERSION="18.2 (Sonya)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 18.2"
VERSION_ID="18.2"
VERSION_CODENAME=sonya
UBUNTU_CODENAME=xenial

list-cards
2 card(s) available.
    index: 0
    name: <alsa_card.usb-Microsoft_Microsoft_LifeCam_VX-5000-02>
    driver: <module-alsa-card.c>
    owner module: 6
    properties:
        alsa.card = "1"
        alsa.card_name = "Microsoft LifeCam VX-5000"
        alsa.long_card_name = "Microsoft Microsoft LifeCam VX-5000 at usb-0000:00:1a.0-1.2, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:1a.0-usb-0:1.2:1.2"
        sysfs.path = "/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/sound/card1"
        udev.id = "usb-Microsoft_Microsoft_LifeCam_VX-5000-02"
        device.bus = "usb"
        device.vendor.id = "045e"
        device.vendor.name = "Microsoft Corp."
        device.product.id = "0728"
        device.product.name = "LifeCam VX-5000"
        device.serial = "Microsoft_Microsoft_LifeCam_VX-5000"
        device.form_factor = "webcam"
        device.string = "1"
        device.description = "LifeCam VX-5000"
        module-udev-detect.discovered = "1"
        device.icon_name = "camera-web-usb"
    profiles:
        input:analog-mono: Analog Mono Input (priority 2, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <input:analog-mono>
    sources:
        alsa_input.usb-Microsoft_Microsoft_LifeCam_VX-5000-02.analog-mono/#0: LifeCam VX-5000 Analog Mono
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    index: 1
    name: <alsa_card.pci-0000_01_00.0>
    driver: <module-alsa-card.c>
    owner module: 22
    properties:
        alsa.card = "0"
        alsa.card_name = "Xonar DG"
        alsa.long_card_name = "C-Media Oxygen HD Audio at 0xe000, irq 20"
        alsa.driver_name = "snd_oxygen"
        device.bus_path = "pci-0000:01:00.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "13f6"
        device.vendor.name = "C-Media Electronics Inc"
        device.product.id = "8788"
        device.product.name = "CMI8788 [Oxygen HD Audio] (CMI8786 (Xonar DG))"
        device.string = "0"
        device.description = "CMI8788 [Oxygen HD Audio] (CMI8786 (Xonar DG))"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_01_00.0.analog-stereo/#1: CMI8788 [Oxygen HD Audio] (CMI8786 (Xonar DG)) Analog Stereo
    sources:
        alsa_output.pci-0000_01_00.0.analog-stereo.monitor/#2: Monitor of CMI8788 [Oxygen HD Audio] (CMI8786 (Xonar DG)) Analog Stereo
        alsa_input.pci-0000_01_00.0.analog-stereo/#3: CMI8788 [Oxygen HD Audio] (CMI8786 (Xonar DG)) Analog Stereo
    ports:
        analog-input-front-mic: Front Microphone (priority 8500, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: unknown)
            properties:
                
        analog-input-aux: Analog Input (priority 8000, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-headphones"


sudo alsa force-reload

 
Unloading ALSA sound driver modules: snd-oxygen snd-usb-audio snd-oxygen-lib snd-mpu401-uart snd-usbmidi-lib snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-oxygen snd-usb-audio snd-oxygen-lib snd-mpu401-uart snd-usbmidi-lib snd-hwdep snd-pcm snd-rawmidi snd-seq-device snd-timer).
Loading ALSA sound driver modules: snd-oxygen snd-usb-audio snd-oxygen-lib snd-mpu401-uart snd-usbmidi-lib snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.


After reboot Alsa shows S/PDIF shows muted
    &#9500;&#9472;&#9472;&#9508;                   &#9484;&#9472;&#9472;&#9488;                   &#9484;&#9472;&#9472;&#9488;                   &#9500;&#9472;&#9472;&#9508;           Stereo Headphones FP           &#9500;&#9472;&#9472;&#9508;              Front+Surround                  &#9474;
&#9474;                       &#9474;OO&#9474;                   &#9474;MM&#9474;                   &#9474;MM&#9474;                   &#9474;MM&#9474;                                          &#9474;MM&#9474;                                              &#9474;
&#9474;                       &#9492;&#9472;&#9472;&#9496;                   &#9492;&#9472;&#9472;&#9496;                   &#9492;&#9472;&#9472;&#9496;                   &#9492;&#9472;&#9472;&#9496;                                          &#9492;&#9472;&#9472;&#9496;                                              &#9474;
&#9474;                       2<>2                                                                 100                                           100                                               &#9474;
&#9474;                    Headphone       <        S/PDIF        >   S/PDIF Loopback      Analog Input Monitor      Analog Output      Digital Input Monitor     Stereo Upmixing                  &#9474;
&#9474;                                                                                                                                                                                            &#9474;
&#9474;                                                                                                                                                

/var/lib/alsa/asound.state

Alsamixer unmute and ->
sudo alsactl store

reboot 

no change still muted after reboot

/etc/pulse $ ll
total 36
-rw-r--r--   1 root root  1201 Jan  6  2017 client.conf
-rw-r--r--   1 root root  2282 Nov 15 15:19 daemon.conf
-rw-r--r--   1 root root  5709 Nov 15 15:19 default.pa
-rw-r--r--   1 root root  2046 Nov 15 15:19 system.pa


sudo alsactl store 0
same command with -force but same issue!

List of packages installed on my system:

alsa-base                    install
alsa-tools                    install
alsa-tools-gui                    deinstall
alsa-utils                    install
gnome-alsamixer                    deinstall
gstreamer0.10-alsa:amd64            install
gstreamer1.0-alsa:amd64                install
libsox-fmt-alsa:amd64                install


gstreamer0.10-pulseaudio:amd64            install
gstreamer1.0-pulseaudio:amd64            install
libpulse-mainloop-glib0:amd64            install
libpulse0:amd64                    install
libpulsedsp:amd64                install
pulseaudio                    install
pulseaudio-module-x11                install
pulseaudio-utils                install

Thank you for your help,
Jean

---

