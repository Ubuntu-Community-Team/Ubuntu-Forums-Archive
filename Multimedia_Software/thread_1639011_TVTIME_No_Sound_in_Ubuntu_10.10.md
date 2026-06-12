---
title: "TVTIME No Sound in Ubuntu 10.10"
date: 2010-12-06
forum: Multimedia Software
---

### Post by kistareddyd on 2010-12-06
[SIZE=3]kista@kista-ubuntu:~$ arecord -l 
**** List of CAPTURE Hardware Devices ****
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 1: Intel ICH - MIC ADC [Intel ICH7 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 2: Intel ICH - MIC2 ADC [Intel ICH7 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 3: Intel ICH - ADC2 [Intel ICH7 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

=====================================================[/SIZE] [SIZE=3]

mixer: Can't open mixer pcm:0, mixer volume and mute unavailable.[/SIZE] [SIZE=3]
mixer: Can't open device pcm, mixer volume and mute unavailable.
Thank you for using tvtime.
kista@kista-ubuntu:~$ tvtime --mixer=pcm:1
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/kista/.tvtime/tvtime.xml
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL pcm:1
mixer: attach error: No such file or directory
mixer: Can't open mixer pcm:1, mixer volume and mute unavailable.
mixer: Can't open device pcm, mixer volume and mute unavailable.
videoinput: Aspect ratio: 0.915254
Thank you for using tvtime.[/SIZE]

---

### Post by kistareddyd on 2010-12-06
[SIZE=3][COLOR=Blue]$ lspci | grep SAA
[/COLOR][/SIZE] [SIZE=3][COLOR=Blue]It will output something like that : [/COLOR][/SIZE]
 [SIZE=3][COLOR=Blue]04:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
[/COLOR][/SIZE] [SIZE=3][COLOR=Blue]**04:08.0** is the *address* of your card. [/COLOR][/SIZE]
 
[LIST]
[*][SIZE=3][COLOR=Blue] Then, the following command [/COLOR][/SIZE]
[/LIST]
 [SIZE=3][COLOR=Blue]$ LANG=C pactl list | grep -A2 'Source #' | grep 'Name: ' | cut -d" " -f

ex: $ LANG=C pactl list | grep -A2 alsa

now select your tv card alsa_input.pciXXXXXXXXXXXXXXX

follow below steps
[/COLOR][/SIZE] [SIZE=3][COLOR=Blue]will list all source detected by Pulseaudio. [/COLOR][/SIZE]
[SIZE=3][COLOR=Blue]For example, on my computer: [/COLOR][/SIZE]
 [SIZE=3][COLOR=Blue]alsa_input.pci-0000_04_08.0.analog-stereo
alsa_output.pci-0000_00_10.1.analog-stereo.monitor
alsa_input.pci-0000_00_10.1.analog-stereo
[/COLOR][/SIZE] [SIZE=3][COLOR=Blue]The source name to use is **the one with the right PCI address**.  Here the third one: alsa_input.pci-0000_**04_08.0**.analog-stereo [/COLOR][/SIZE]
 
[LIST]
[*][SIZE=3][COLOR=Blue] Edit the file /etc/pulse/default.pa with your favorite text editor: [/COLOR][/SIZE]
[/LIST]
 [SIZE=3][COLOR=Blue]# gedit /etc/pulse/default.pa
[/COLOR][/SIZE] [SIZE=3][COLOR=Blue]Add the following line at the end of the file (replacing source with the one you found): [/COLOR][/SIZE]
 [SIZE=3][COLOR=Blue]load-module module-loopback source=alsa_input.pci-0000_04_08.0.analog-stereo
[/COLOR][/SIZE] 
[LIST]
[*][SIZE=3][COLOR=Blue] Restart Pulseaudio [/COLOR][/SIZE]
[/LIST]
 [SIZE=3][COLOR=Blue]$ pulseaudio -k[/COLOR][/SIZE]

---

### Post by tedrampart on 2010-12-08
I wish this made more sense to me, I'm having the no sound problem.

I get an error after your second command:
$ LANG=C pactl list | grep -A2 'Source #'
Connection failure: Connection refused

am I doing something wrong?

---

### Post by kistareddyd on 2010-12-10
[SIZE=3][COLOR=Blue]$ LANG=C pactl list | grep -A2 alsa[/COLOR][/SIZE]

---

