---
title: "Complete loos of sound"
date: 2011-09-26
forum: Multimedia Software
---

### Post by Lektorvis on 2011-09-26
I had a well functioning Natty. * 4.5.2 (x86_64-linux-gnu)

In an attempt to get a software synthesizer to function, I have had a lot of different audio programs installed.
This has resulted in that my sound is now completely gone. I have reinstalled Alsa, but without result.

```
~$ cat /proc/asound/card0/codec* | grep Codec
cat: /proc/asound/card0/codec*: No such file or directory

```

When I run: 
```
aplay -Dplughw:X,0 -fcd /musik/a.wav
```
I get this output:
```
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
aplay: main:660: error at sound opening: No such device
```

When I open the "audio settings" there is no hardware to see, no input and no programs, but the output is now "Dummy output" Stereo!
I assume that my card has been deleted or overwritten in some configuration file, but I can't figure out where or what to write.

My audio card works perfectly in Windows, it is a 'Realtek HD Audio output' 
```
~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

```

I will be grateful for any help

---

### Post by lidex on 2011-09-27
Try resetting your pulse configuration.
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Lektorvis on 2011-09-27
Thank You for your effort Lidex
In the meantime I found a solution to my hiden sound card in an other thread:
[http://ubuntuforums.org/showthread.php?t=1807595]("http://ubuntuforums.org/showthread.php?t=1807595")

---

