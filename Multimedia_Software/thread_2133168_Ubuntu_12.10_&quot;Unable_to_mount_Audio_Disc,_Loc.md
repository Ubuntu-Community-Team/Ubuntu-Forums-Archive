---
title: "Ubuntu 12.10 &quot;Unable to mount Audio Disc, Location is not mountable&quot;"
date: 2013-04-07
forum: Multimedia Software
---

### Post by bquade on 2013-04-07
I bought this machine in December. I was never able to play DVDs, but I had been able to play audio CDs until recently. I hadn't played any CDs for about a month, and now I get a message that says, "Unable to mount Audio Disc, Location is not mountable". I can still mount data disks, just not audio ones. And I can play video and audio streaming on the Internet, but not from a CD.

I ran the speaker test and they work fine.

My sound card is found.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT1802 HP [VT1802 HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And the sound card appears to be activated.
```
$ echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)

```

I tried adding an /etc/asound.conf file with the following contents (which I think is correct), and then rebooting, but it still says audio disks are not mountable.
```
pcm.!default {
      type plug slave.pcm {
            type hw card 0 device 2
      }
}

```

I've done every sound troubleshooting guide I could find that might apply to Ubuntu 12.10, but nothing works. And it looks like this is an old Ubuntu bug going back at least 3 or 4 years. I'm about ready to give up on Linux as anything other than a development and server system.

---

