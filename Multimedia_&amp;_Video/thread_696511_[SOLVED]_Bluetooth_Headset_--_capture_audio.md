---
title: "[SOLVED] Bluetooth Headset -- capture audio"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by divinebovine on 2008-02-14
I'm having problems getting gnome-voice-control to capture audio with my bluetooth headset.  I have it working with a usb microphone, however I'd like to use my headset.

My headset is paired and I can play audio over my bluetooth headset with "aplay -Dplug:pcm.headset test.wav".  I can also capture audio with arecord similiarly.  However when the headset is connected, I'd expect to be able to just talk and the gnome-voice-control should capture it, but thats not the case.

Also, when the headset is not connected, I'd expect the headset to connect when i push the button... It seems to do it once the first time and then never again... any suggestions?  Below is the .asoundrc file that I created to try to handle the separate capture device.

```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
    }
    capture.pcm "headset"
}

pcm.headset {
    type bluetooth
    device 00:11:22:33:44:55
    profile "auto"
}
```

---

### Post by linuxwizard on 2008-02-14
Look over these see if something will help.

[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

[https://help.ubuntu.com/community/BluetoothSetup#head-82b6734db30571f54da4ceaa7254b1b464640156](https://help.ubuntu.com/community/BluetoothSetup#head-82b6734db30571f54da4ceaa7254b1b464640156)

---

### Post by divinebovine on 2008-02-15
Thanks for the reply, I'm out of town this weekend and won't be back till Monday.  I'll see if any of those links help then.

---

### Post by Skerit on 2008-02-18
These did not help me at all, I have the same problem.

It's nice to get the headset to work but its kind of retarted to not have a control in the alsa mixer.

---

### Post by divinebovine on 2008-02-25
Alright, none of the links helped.  Somehow, my bluetooth headset connects every time i hit the button now, so thats no longer a problem.  However the gnome-voice-control applet still is not capturing the audio correctly.  When I right click on the applet and select start control, my headset connects and I can hear white noise over the speaker, however, the applet still says Idle and when I speak it never signals that its picking anything up.

---

### Post by divinebovine on 2008-02-28
Ok, it looks like I was able to get this to work finally.  Below is my ~/.asoudnrc file.  Apparently the ctl.headset section was necessary... I'm not sure what the ctl section does exactly... I assume ctl stands for control, but the alsa documentation online didn't explain what it meant and what it does.  Hope anyone else attempting this can find this useful.  Also, this allowed me to use gnome sound recorder to record with the headset too, in case anyone was wondering.


```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
    }

## USB Microphone
#    capture.pcm  {
#         type plug
#         slave.pcm "hw:1,0"
#    }

## Bluetooth headset
     capture.pcm {
          type plug
          slave.pcm "headset"
     }
}

ctl.headset {
    type bluetooth
    device 00:11:22:33:44:55
    profile "auto"
}

pcm.headset {
    type bluetooth
    device 00:11:22:33:44:55
    profile "auto"
}
```

---

