---
title: "No sound after updating - tired re-installing pulseaudio"
date: 2013-09-30
forum: Multimedia Software
---

### Post by Wiking on 2013-09-30
Hi after updating I have no sound after reading some info I've tried purging pulseaudio, re-installing it and nothing. I've looked in alsamixer and the speakers are not muted, I also believe I've selected the right audio card in the Phonon.

I've tried the following commands and some variations:


[LIST]
[*]Remove alsa-base and pulseaudio:
[/LIST]
  ```
[INDENT] sudo apt-get remove --purge alsa-base pulseaudio
 [/INDENT]
```  
[LIST]
[*]Reinstall alsa-base and pulseaudio:
[/LIST]
  ```
[INDENT] sudo apt-get install alsa-base pulseaudio
 [/INDENT]
```  
[LIST]
[*]For them to load:
[/LIST]
  ```
[INDENT] sudo alsa force-reload
 [/INDENT]
```

After rebooting I still have no sound.

I've also tried editing some configuration files but when I open them they're empty.

Info about my card:

```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
```

```
0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc0800000 irq 50


```
[ATTACH]246637[/ATTACH][ATTACH]246638[/ATTACH][ATTACH]246639[/ATTACH]

---

### Post by SeijiSensei on 2013-09-30
I have a persistent issue with 13.04 where Phonon selects the wrong output device each time I restart.  Take a look in System Settings > Multimedia > Phonon > Audio Hardware Setup and look at the "Connector" entry.  On my machine it comes up with "Analog Output" when I log in, but I need to switch it to "Speakers" to get it to send the audio out the headphone connector to my stereo system.  What's really annoying is I cannot figure out what file keeps this setting so I cannot make it permanent.  

Anyway, give that a try and see if it helps.

---

### Post by Yellow Pasque on 2013-10-01
```
What's really annoying is I cannot figure out what file keeps this setting so I cannot make it permanent.
```
~/.kde/share/config/phonondevicesrc looks promising...

---

### Post by Yellow Pasque on 2013-10-01
@OP: have you tried this?: [https://wiki.ubuntu.com/PulseAudio#Resetting_User_Configuration](https://wiki.ubuntu.com/PulseAudio#Resetting_User_Configuration)

---

### Post by SeijiSensei on 2013-10-01
> **Temüjin said:**
> ~/.kde/share/config/phonondevicesrc looks promising...

Thanks.  I looked at that file before and again just now and don't see any entry that controls the "Connector" preference, though the entries in that file are admittedly somewhat obscure like "index."  I don't see any entry for that setting in ~/.config/kde.org/libphonon.conf or ~/.config/kde.org/Phonon-Xine.xine.conf either.

This isn't the first time I've had problems with settings in KDE not persisting through a reboot.  Back in 9.04 I participated in a [bug report thread]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/368977") where printer configurations were lost upon a reboot.

---

### Post by Wiking on 2013-10-01
> **Temüjin said:**
> @OP: have you tried this?: [https://wiki.ubuntu.com/PulseAudio#Resetting_User_Configuration](https://wiki.ubuntu.com/PulseAudio#Resetting_User_Configuration)

Thanks that fixed the problem. I'll be sure to bookmark that page for future updates and upgrades.

```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by thomassisson on 2013-11-27
I originally started with Ubuntu 12.04 and sound worked, but I have had the same issue since an issue in 12.10. I even built PulseAudio from source. Finally, I found a reference on an OpenSuse website to alsa-firmware package that is not automatically installed. Ubuntu does not have alsa-firmware but has a package called alsa-firmware-loader. I installed it and it also installed fxload.

My specific problem after trying every solution out there was that I had sound immediately after login, but it would go away after five to ten minutes.

For me, this fixed the problem in Kubuntu 12.10. I don't know why sound has to be such a pain, but it is. No one solution works for everyone, but I hope this helps those who have yet to get sound working.

If I have lucked upon a solution that resolves sound problems for that small percentage that consistently have a problem, I hope the developers take note. It may then be a good idea to add alsa-firmware-loader as a dependency. I suspect this may be a common issue for those with at least one of the following: a Toshiba, an Acer, a hybrid gpu where the video and sound are not the same manufacturer, and a Conexant sound card.

---

