---
title: "No line-in/mic capture by software, but sound plays directly through"
date: 2010-03-12
forum: Multimedia Software
---

### Post by RascallHunter on 2010-03-12
Hello. I have a problem with trying to capture sound through the input jacks on my computer. The sound plays through from the inputs to the output, and it's volume is controlled by alsa mixer, but no programs can pick up the stream, including the PulseAudio and Gnome Volume controls.

I have tried many of the suggestions to be found in these forums for sound issues, including removing Pulse, configuring the model in alsa-base.conf, and messing with every setting I can find.

Here are the outputs from the commands from the troubleshooting guides:
```

lspci -v | less

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio 
Controller (rev 01)
        Subsystem: Intel Corporation Device d601
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at 63100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

http://www.alsa-project.org/db/?f=aa57662afa504a2c300bae26714850e1f77b4e84



sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Details of the computer:
E-Machines (gateway?) T5212
Dual core 2.6Ghz Intel Pentium D Processor 805
Intel Motherboard
1GB DDR2 RAM
Ubuntu release 9.10
Linux Kernel 2.6.31-20-generic
GNOME 2.28.1

Any help or suggestions are appreciated.
All the best,
Reuben Bailey

---

### Post by chaanakya_chiraag on 2010-03-12
Do you still have PulseAudio Volume Manager?  If so, does it say dummy output?

---

### Post by chaanakya_chiraag on 2010-03-12
If PulseAudio says it can only see dummy output, then try this:
```
sudo killall pulseaudio
sudo pulseaudio --system --daemon
```
and see if PulseAudio can now see the device.

---

### Post by RascallHunter on 2010-03-12
I do still have the volume control, and it shows the card. I have sound from all programs on the computer, but they can not seem to find the stream coming in from the input jacks.

---

### Post by chaanakya_chiraag on 2010-03-12
What exactly do you mean by "find the stream"?  Do you mean you cannt record anything?

---

### Post by RascallHunter on 2010-03-12
@chaanakya_chiraag Results of commands...
```

reuben@reuben-desktop:~$ sudo killall pulseaudio
sudo: unable to resolve host reuben-desktop
[sudo] password for reuben: 
reuben@reuben-desktop:~$ sudo pulseaudio --system --daemon
sudo: unable to resolve host reuben-desktop
W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!

```Yes, I am not able to record the audio from the input jacks with any software on the computer, but I can hear it through the speakers which are plugged into the speaker jack of the same (only) sound card.

---

### Post by chaanakya_chiraag on 2010-03-12
After running the above commands, try recording something.  Does it work?

---

### Post by chaanakya_chiraag on 2010-03-12
You have to make sure the recording application is using PulseAudio (or ALSA in the case of Audacity).

---

### Post by RascallHunter on 2010-03-12
Audacity is set to use ALSA: Pulse for recording. The level monitor shows nothing when monitoring the sound card (as set by the sound preferences) or (using the PulseAudio applet) it is set to pull from the monitor of the internal Audio Analog Stereo stream. When I select either my headphone mic (usb) or my web cam mic (also usb) I get sound on the level monitor.

I'm beginning to think that for some reason ALSA does not like the card very much and so it doesn't pass things on from the inputs.

---

### Post by chaanakya_chiraag on 2010-03-12
Yeah...basically, alsa doesn't recognize that your soundcard has an input. That's why it's not working.

---

### Post by mocha on 2010-03-13
Try this modules option line in your /etc/modprobe.d/alsa-base.conf file, reboot then try capturing.  I had problems with similar hardware, I think the position_fix=1 is what fixes the capture.  If it fixes the problem file a bug so the devs can add your hardware to needing the positon_fix.

```
options snd-hda-intel power_save=0 power_save_controller=N position_fix=1 enable=yes
```

---

### Post by RascallHunter on 2010-03-13
Thank you Mocha! That seems to have done the trick!
I need to file the bug report with the ALSA folks, right?
Thanks again!

All the best,
Reuben Bailey

---

### Post by mocha on 2010-03-13
> **RascallHunter said:**
> Thank you Mocha! That seems to have done the trick!
I need to file the bug report with the ALSA folks, right?
Thanks again!

All the best,
Reuben Bailey

Glad that helped.  Actually, file the bug on launchpad for the alsa-driver package.  There is some devs there that seem to pay attention to these issues fairly quickly.  Make sure you give them the output of "sudo lspci -vvnn" for the audio hardware section so they have all the info.

---

### Post by RascallHunter on 2010-03-14
Bug report filed at the following link:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/538895](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/538895)
Thank you both again for your help.
All the best,
Reuben Bailey

---

### Post by RascallHunter on 2010-03-15
The fix seems to be a combination of setting the model to 6stack-dig and adding the position fix in the /etc/modprobe.d/alsa-base.conf file.
```

options snd-hda-intel model=6stack-dig
options snd-hda-intel power_save=0 power_save_controller=N position_fix=1 enable=yes

```

---

### Post by Nordstroemen on 2010-03-16
I have the exact same problem as Rascall.. but im a newb, and dont really understand what im supposed to do? Could one of you, Rascall or Mocha, spell it out for me in easy understandable writing (for dummies)..? :D

It would be much appreciated

thx

---

### Post by RascallHunter on 2010-03-16
Nordstroemen,

First of all, welcome to Ubuntu!

To help you with the problem, we first need some information about your computer.
open a terminal (Applications > Accessories > Terminal if you are using Gnome) and enter the following commands:

```

grep "^Codec\|^Vendor Id\|^Subsystem Id\|^Revision Id" /proc/asound/card*/*codec*{,/*}

```I recommend copying and pasting that into your terminal. The shortcut keys will not work in the terminal, but a right-click with the mouse should.

It should result in 4-5 lines of code that look something like this:

```

grep: /proc/asound/card*/*codec*/*: No such file or directory
/proc/asound/card0/codec#3:Codec: Realtek ALC883
/proc/asound/card0/codec#3:Vendor Id: 0x10ec0883
/proc/asound/card0/codec#3:Subsystem Id: 0x8086d601
/proc/asound/card0/codec#3:Revision Id: 0x100002

```   If the results are exactly match the last four lines above, then your hardware is the same as mine and the fix should work for you. If they don't match exactly, then it may or may not work.

The fix for me consisted of two things. I originally could not hear sound from the speakers when an input was fed into one of the jacks. This was fixed with the model quirk (model=6stack-dig). The second piece was getting alsa to pass the data stream on to Pulse! using the position fix.

The following four statements should make the 2 fixes plain:

-If neither the position fix or the model are present, no sound comes through the 
speakers (plugged into the speaker out jack) when there is input.

-If the position fix is there but the model is not, the result is the same.

-If the model is there but no position fix, I can hear sound from the speakers and 
control the volume with the ALSA mixer, but no other software picks up the stream.

-If both model and position fix are present, I can hear the sound directly from 
the speakers and all software picks up the stream.

If you can already hear sound from speakers plugged into a jack on the sound card, and can control volume and mute through GNOME ALSA Mixer (Applications > Sound & Video > GNOME ALSA Mixer)(if it's not there, it can be installed using the package manager - type ALSA in the quick search bar and look for the gnome-alsamixer package), then you may just need the position fix line shown below.

These two items are fixed by editing the /etc/modprobe.d/alsa-base.conf configuration file. This is done through the terminal and gedit as follows:

First, open the configuration file as root (sudo) with gedit:

```

sudo gedit /etc/modprobe.d/alsa-base.conf

```A dialog box will open, asking you for your password. After you enter it, gedit will open with the alsa-base.conf file loaded.

Copy and paste one or both of the following 2 lines at the end of the file, depending on what you need to fix:

```

options snd-hda-intel model=6stack-dig
options snd-hda-intel position_fix=1 enable=yes

```Save the file and exit gedit.

Now reboot your computer and see if you can record sound.

Hopefully this is helpful to you. If you have further questions, please ask.
All the best,
Reuben Bailey

---

### Post by Nordstroemen on 2010-04-06
Hey Reuben.. sry that I havent had the chance to reply (family issues) and thank you for your effort.. thx!
I dont have the exact same hardware as you.. but has actually by now worked my way around the problem.. Simply purged Pule entirely and now only rely on Alsa.. skype works --> Im happy.

Will try your advice out event though, at least to try to understand a bit more about how Ubuntu is working. 

again thank you very much for your effort

Best

- Nordstroemen

---

### Post by Ryland on 2010-04-22
I am haveing the same problem with snd-hda-intel for a AD1989B chip on a Asus P5Q board. If I could just find out that it is possible to record sound in with this chip and module I will keep working at it. Unfortunatly all the posts I have followed so far don't actually confirm it is possible.

---

