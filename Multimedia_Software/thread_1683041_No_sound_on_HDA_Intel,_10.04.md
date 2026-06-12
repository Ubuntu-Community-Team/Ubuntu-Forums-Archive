---
title: "No sound on HDA Intel, 10.04"
date: 2011-02-06
forum: Multimedia Software
---

### Post by maiden_taiwan on 2011-02-06
I recently upgraded from Kubuntu 7.10 to 10.04, and now one of my two sound cards does not produce any sound. It is an HDA Intel on an Asus P5E motherboard. (My other card, an M Audio Delta 1010LT, works fine.) If anyone could help, that would be great.

I have tried the "Comprehensive Sound Problem Solutions Guide" at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and unfortunately nothing worked for me. Here the vital statistics:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
$ lspci -v
...
0:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Device 8277
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
...
``````
$ sudo modprobe snd-hda-intel
*(no output appears here)*
$
``````
$ cat /etc/modules
lp
sbp2
# I added this next line
snd-hda-intel
```I also tried adding various lines to the end of /etc/modprobe.d/alsa-base.conf, such as:

```
options snd-hda-intel model=3stack
```and

```
options snd slots=snd-hda-intel
options snd-hda-intel model=3stack
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```which did not help.

I also purged, removed, and reinstalled linux-sound-base, alsa-base, and alsa-utils. No change.

I rebooted after every change. It didn't help.

KDE's Multimedia settings for Audio Output all list the HDA Intel and the M Audio Delta. The HDA Intel is first for all the categories (Music, Video, etc.). Clicking the "Test" button works perfectly for the M Audio Delta but produces only silence for the HDA Intel.

KMix shows that all the HDA Intel channels are UN-muted.

I have not tried recompiling ALSA nor using drivers from alsa-project.org yet. I'm hoping there's a simpler solution (like maybe I missed a "mute" button somewhere... dream on... :-)).

Thanks for any advice....

---

### Post by maiden_taiwan on 2011-02-06
More data:

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22
 1 [M1010LT        ]: ICE1712 - M Audio Delta 1010LT
                      M Audio Delta 1010LT at 0xe000, irq 18

$ head -n 1 /proc/asound/card0/codec#0 
Codec: Analog Devices AD1988B

---

### Post by maiden_taiwan on 2011-02-07
I've discovered that if I run Amarok (mp3 player), audio begins working, both in Amarok and some other applications. But not all applications (e.g., Konsole and Emacs still don't beep when I type ctrl-G).

After a while, audio stops working. Then I run Amarok again and it starts working. Weird.

---

### Post by akwala on 2011-12-19
Have you seen this...
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

Based on the comments, many have been able to fix their audio issues following these instructions. While compiling isn't necessarily difficult, I was able to install the recommended alsa version from a PPA - see:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/#comment-631](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/#comment-631)
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

