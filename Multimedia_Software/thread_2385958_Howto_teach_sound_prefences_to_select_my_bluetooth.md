---
title: "Howto teach sound prefences to select my bluetooth device once connected?"
date: 2018-02-27
forum: Multimedia Software
---

### Post by Byb on 2018-02-27
Hi
I'd like my bluetooth audio receiver (Philips EAE2700) to become the default sound output once connected. How do I do this in Ubuntu 14.04.5 ?
Whatever the connexion is established or not, */proc/asound/cards* only shows the single HDA Intel PCH inside. Although, *pacmd list-cards* shows 2 cards available, the internal Intel always at index 0 and the bluetooth device at an index number that increments +1 on every new connection along with the module owner number.

```

 >>>2 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    ...
index: 11
    name: <bluez_card.0C_A6_94_85_46_E3>
    driver: <module-bluetooth-device.c>
    owner module: 35
    properties:
        device.description = "Philips AEA2700"
        device.string = "0C:A6:94:85:46:E3"
        device.api = "bluez"
        device.class = "sound"
        device.bus = "bluetooth"
        device.form_factor = "speaker"
        bluez.path = "/org/bluez/462/hci0/dev_0C_A6_94_85_46_E3"
        bluez.class = "0x240414"
        bluez.name = "Philips AEA2700"
        device.icon_name = "audio-speakers-bluetooth"
    profiles:
        a2dp: Lecture haute fidélité (A2DP) (priority 10, available: unknown)
        off: Éteint (priority 0, available: yes)
    active profile: <a2dp>
    sinks:
        bluez_sink.0C_A6_94_85_46_E3/#11: Philips AEA2700
    sources:
        bluez_sink.0C_A6_94_85_46_E3.monitor/#12: Monitor of Philips AEA2700
    ports:
        speaker-output: Haut-parleur (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
        speaker-input: Entrée Bluetooth (priority 0, latency offset 0 usec, available: no)
            properties:


```

Thank you

---

### Post by Byb on 2018-02-28
[https://askubuntu.com/questions/158241/automatically-change-sound-input-output-device](https://askubuntu.com/questions/158241/automatically-change-sound-input-output-device) works for BT too, albeit BT device wasn't/still isn't listed by [I]cat /proc/asound/cards
(per user tweak - didn't try system wide)
[/I]

---

