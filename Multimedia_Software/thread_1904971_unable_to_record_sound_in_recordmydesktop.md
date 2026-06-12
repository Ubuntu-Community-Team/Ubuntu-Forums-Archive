---
title: "unable to record sound in recordmydesktop"
date: 2012-01-05
forum: Multimedia Software
---

### Post by iuval on 2012-01-05
I am able to record sound in sound recorder, but not in recordmydesktop. Already tried the procedures in the sticky threads. Everything seems fine, but no sound input. I tried all possible (eight) combinations, enabling and disabling the 3 sliders for mic, and two capture (why 2?) sliders in ALSA. The audio device in the gui to recordmydesktop is DEFAULT. The sound quality box is cheked (I tried unchecking it too). I also tried running from command line. What is the problem?

---

### Post by iuval on 2012-01-05
More information:

iuval@iuval-LT27:~$ lspci -nn | grep '\[04[80][13]\]'
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
iuval@iuval-LT27:~$ echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)

---

### Post by iuval on 2012-01-05
I am not using a jack, but the internal microphone.

---

### Post by iuval on 2012-01-07
I set the audio channels to 2 instead of 1, and it worked.

---

