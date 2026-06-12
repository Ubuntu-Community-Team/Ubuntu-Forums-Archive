---
title: "No sound on 10.04, works fine on 12.04 Live USB."
date: 2013-05-28
forum: Multimedia Software
---

### Post by spiritofcat on 2013-05-28
I've just bought a new PC and I'm trying to migrate my Ubuntu 10.04 installation over to it.
I've chosen to do this instead of just starting with a fresh 12.04 install since I've got a lot of things already set up the way I want them on 10.04 and I don't want to go through the drama of getting everything set up from scratch again.

I've used Clonezilla to clone the hard drive from the old machine to the new one, and for the most part it's working well.

The only problem I've noticed is that the onboard sound card of the new machine is not reporting for duty.

I've read through both these guides:
[URL="https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit"]
Sound Troubleshooting Guide[/URL]
(by Lkjoel and Wildmanne39)
[URL="https://help.ubuntu.com/community/SoundTroubleshootingProcedure"]
Sound Troubleshooting Procedure[/URL]
(by Mark Rijckenberg)

I followed the first one but with no success.
The second one seems to be only for 12.04 so I'm not sure how much help it can be to me.

Working with the first guide, I've become stuck with
```
sudo aplay -l
```
always returning
```
aplay: device_list:223: no soundcards found...
```

I've run the big command in procedure Ac:
```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
```
And received this output:
```
Sound cards recognized by the system:00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1e20] (rev 04)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1e20] (rev 04)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1e20] (rev 04)
```

but when I run
```
sudo aplay -l
```
I still get:
```
aplay: device_list:223: no soundcards found...
```

I've tried rebooting, I've tried removing, purging and reinstalling alsa and pulse. Nothing has worked.
I've used the Try Ubuntu feature from a 12.04 installation USB stick, and sound works there, so there's nothing wrong with my sound card or my speakers.

Anyone got any more things for me to try?

---

### Post by Yellow Pasque on 2013-05-28
10.04 is EOL and relatively ancient compared to your hardware. You need to try a newer kernel for updated sound modules: [http://askubuntu.com/questions/47796/can-i-update-the-kernel-of-my-10-04-lts-to-the-latest-kernel#47797](http://askubuntu.com/questions/47796/can-i-update-the-kernel-of-my-10-04-lts-to-the-latest-kernel#47797)

---

### Post by spiritofcat on 2013-05-28
> **Temüjin said:**
> 10.04 is EOL and relatively ancient compared to your hardware. You need to try a newer kernel for updated sound modules: [http://askubuntu.com/questions/47796/can-i-update-the-kernel-of-my-10-04-lts-to-the-latest-kernel#47797](http://askubuntu.com/questions/47796/can-i-update-the-kernel-of-my-10-04-lts-to-the-latest-kernel#47797)
Thanks!

I ran
```
[FONT=Ubuntu Mono]sudo apt-get install linux-image-generic-lts-backport-oneiric[/FONT]
```[FONT=Ubuntu Mono]
and
```
sudo apt-get install linux-headers-generic-lts-backport-oneiric
```[/FONT][FONT=Ubuntu Mono]
[FONT=Verdana]And once those were complete an Update Manager popped up with a bunch of packages to update.
I let it update all those packages and now I'm going to reboot and see if I've got sound.

Edit:
I'm back after rebooting, aplay -l now lists some devices, and after I un-muted it in the mixer, my speakers work!
Thanks for the help!
[/FONT][FONT=Verdana]
[/FONT][/FONT]

---

