---
title: "Treat headphone and speaker jacks as two separate devices in PulseAudio"
date: 2014-06-21
forum: Multimedia Software
---

### Post by GigabyteProduction on 2014-06-21
I would like to use my headphone jack and speaker jack as two independent sinks in PulseAudio.

I would like a solution similar to [https://wiki.archlinux.org/index.php/PulseAudio/Examples#Splitting_front.2Frear](https://wiki.archlinux.org/index.php/PulseAudio/Examples#Splitting_front.2Frear) but using my headphone jack instead of one of my surround sound jacks.

I would also like to make all of my input jacks independent of each other instead of having to pic only one to use with pavucontrol.

---

### Post by SeijiSensei on 2014-06-21
Do you want to have different streams coming from each connector?  I doubt that's possible with only audio adapter.

---

### Post by GigabyteProduction on 2014-06-21
Yes, i want them to play two independent streams. I'm not using any kind of adapter, just the chipset on my motherboard. It also is possible to use the two outputs independently in Windows; I don't see why it couldn't work in alsa.

---

### Post by GigabyteProduction on 2014-07-30
bump...

---

### Post by KillEmAllx on 2014-09-05
Found any solution to this? I'm trying to switch between my headphones and speakers, both connected at the same time. I've turned off "auto-mute" in alsamixer settings because otherwise I can't get sound out of my speakers as long as the headphones are connected. Now I have sound from both devices at the same time, what's left is to mute speakers when switching audio source to headphones and vice versa.
I use indicator-sound-switcher to quickly switch audio sources btw.

---

### Post by GigabyteProduction on 2014-09-05
I haven't found a solution to this problem. I actually forgot about the problem as the friend I was setting this up for (this was part of a multiseat setup) was visiting for only a few days, so I never needed it afterwards as I always use my headset. My goal isn't to switch between them, my goal is to use them at the same time, but independently (not playing the same audio; a program coming out of headsets while another program comes out of speakers).

At least our posts bumped this, maybe someone will come along with a solution. As I've said in my original post, I do not want to use the remap-sink solution demonstrated in my link. I want to use the **front headphone jack** and the **back speaker jack** as two **independent** sinks.

---

### Post by Yellow Pasque on 2014-09-06
You would have to make sure your hardware is actually capable of it...
[https://wiki.archlinux.org/index.php/PulseAudio#Simultaneous_output_to_multiple_sinks_on_the_same_sound_card_not_working](https://wiki.archlinux.org/index.php/PulseAudio#Simultaneous_output_to_multiple_sinks_on_the_same_sound_card_not_working)

---

### Post by GigabyteProduction on 2014-09-06
This is different, though. The link you gave shows how to use multiple sinks at the same time, with the built in sinks.

```
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
        output:analog-surround-40: Analog Surround 4.0 Output (priority 700, available: unknown)
        output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (priority 760, available: unknown)
        output:analog-surround-41: Analog Surround 4.1 Output (priority 800, available: unknown)
        output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (priority 860, available: unknown)
        output:analog-surround-50: Analog Surround 5.0 Output (priority 700, available: unknown)
        output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (priority 760, available: unknown)
        output:analog-surround-51: Analog Surround 5.1 Output (priority 800, available: unknown)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 860, available: unknown)
        output:analog-surround-71: Analog Surround 7.1 Output (priority 700, available: unknown)
        output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 Output + Analog Stereo Input (priority 760, available: unknown)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5560, available: unknown)
        off: Off (priority 0, available: unknown)
```

These are the sinks I have available. There's no sink for **just my headphone port** and there's no sink for **just my speaker port**, so I couldn't add those two sinks to a pulseaudio preset. I do know my hardware is capable of this exact task I'm trying to accomplish because it's worked in Windows.

PulseAudio does see my ports as separate ports, though, so is there a way to make a sink from a port?

    ```
ports:
        analog-input-microphone-front: Front Microphone (priority 8500, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-microphone-rear: Rear Microphone (priority 8200, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: no)
            properties:
                
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-headphones"
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:
```

---

