---
title: "Audio worked on initial installation but has stopped; &quot;no valid device and/or elemen&quot;"
date: 2014-11-17
forum: Multimedia Software
---

### Post by Linus_Drumbler on 2014-11-17
I've gone through the sticked troubleshooting options but I can't seem to get this to work. I installed Ubuntu yesterday and everything works great except for the sound. It worked when I first installed, and it works on a live CD, but now it's not working.

Here is a relevant command from the troubleshooting docs.

```

$ echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
Sound cards recognized by the system:
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
Sound cards recognized by ALSA:
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
Sound cards recognized by ALSA, and activated:
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)


```

Alsamixer lists both these sound cards and they are unmuted, while pavucontrol's output devices tab lists only a "dummy output" while sound is playing.

---

