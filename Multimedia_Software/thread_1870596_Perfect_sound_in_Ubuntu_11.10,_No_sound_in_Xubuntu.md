---
title: "Perfect sound in Ubuntu 11.10, No sound in Xubuntu 11.10"
date: 2011-10-27
forum: Multimedia Software
---

### Post by razaz03 on 2011-10-27
The most significant input I can provide without pasting terminal commands is the above, Sound works perfectly with my Creative X-Fi soundcard in W7 and Ubuntu 11.10 (fresh install) but not Xubuntu 11.10 (fresh install), so I refuse to believe an ALSA driver doesn't exist.

I can see my volume button with Creative X-FI (Alsa mixer) and Playback: SB X-Fi Analogue Stereo (Pulse Audio Mixer) amongst others, with every option unmuted.

[COLOR=navy][U]**[SIZE=4][B]Comprehensive Sound Problem Solutions Guide** v0.5e 

[/SIZE][/B][/U][/COLOR]
[LEFT][SIZE=2]**(1)** Go to a shell and type:      Code:
     aplay -l 
[/SIZE][/LEFT]
[COLOR=navy][FONT=Verdana][SIZE=4][COLOR=Black][SIZE=2]card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7

and 

card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Amongst onboard.

[/SIZE][/COLOR][/SIZE][/FONT][/COLOR][LEFT][SIZE=2]**(2)** Type this into the shell:      Code:
     lspci -v 
[/SIZE][/LEFT]
05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 0023
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at ec00 [size=32]
    Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi

[SIZE=2]**(3)** Check to see if the ALSA driver for your sound card exists. Go to [/SIZE][[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/")[SIZE=2]  and search for your sound card (chipset) manufacturer in the dropdown  box. You'll be given a matrix of the sound cards made by the  manufacturer. Try to match the chipset you found in step 2 with the  driver([COLOR=seagreen]green hyperlink text[/COLOR]).[/SIZE]

I don't see ctxfi in the list but big deal; it works in Ubuntu 11.10.

[SIZE=2]**(4)** Now go back to the shell and type      Code:
     sudo modprobe snd-ctxfi 
[/SIZE]
[LIST]
[*][SIZE=2][COLOR=red]**Failure**[/COLOR] -You have two options[/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]Move on to **Getting the ALSA drivers from a *fresh* kernel**.  This step is easier and is recommended to users who might have been  tinkering with their sound settings and want to revert back to the way  it was just after installing **Ubuntu **(without reinstalling Ubuntu of course :wink: )[/SIZE]
[/LIST]
[SIZE=2]Move on to **ALSA driver Compilation**, if you have not done so already. If you have, please post a new thread with your problem.[/SIZE][COLOR=navy][FONT=Verdana][SIZE=4][COLOR=Black][SIZE=2]

So attempting the former part of the guide now as I've written this and don't want to lose it's format, I'll post the thread and edit it with the result.

Many thanks,

raz





Followed the guide to a tee and it doesn't work: My user was not in audio when I typed into terminal:

raz@raznix:~$ grep 'audio' /etc/group
audio:x:29:pulse

after following the guide, changing it to:

raz@raznix:~$ grep 'audio' /etc/group
audio:x:29:pulse:raz

It. Still. Doesn't. Work

Included is a screen shot I took in desperation, please help!


[/SIZE][/COLOR][/SIZE][/FONT][/COLOR]

---

### Post by razaz03 on 2011-10-27
Buuuuuump, no solution as yet and I would really appreciate any ideas!

---

### Post by 4Orbs on 2011-10-27
The problem with Xubuntu mixer is that you can select your desired sound card, but there is no method provided to turn-off the other sound cards (or sound chip). If you install either the Pulse Audio volume control or gnome-media you will then be able to disable the undesired sound devices by using the dropdown menu found in the Hardware Configuration settings of either volume control you choose to install. Open a terminal and enter either:
```
sudo apt-get install pavucontrol
```
OR:
```
sudo apt-get install gnome-media
```
then, after the installation finishes, open the sound configuration settings and turn-off all sound devices except the one you wish to use.

NOTE: Installing gnome-media will add another volume icon to your desktop panel. You can easily remove the Xubuntu mixer icon by opening the Xubuntu Settings Manager>>Sessions and Startup>>Autostart Apps and un-check the Volume Control. After reboot you will have only the single gnome-media volume icon on the panel.

---

### Post by razaz03 on 2011-10-27
> **4Orbs said:**
> The problem with Xubuntu mixer is that you can select your desired sound card, but there is no method provided to turn-off the other sound cards (or sound chip). If you install either the Pulse Audio volume control or gnome-media you will then be able to disable the undesired sound devices by using the dropdown menu found in the Hardware Configuration settings of either volume control you choose to install. Open a terminal and enter either:
```
sudo apt-get install pavucontrol
```OR:
```
sudo apt-get install gnome-media
```then, after the installation finishes, open the sound configuration settings and turn-off all sound devices except the one you wish to use.

NOTE: Installing gnome-media will add another volume icon to your desktop panel. You can easily remove the Xubuntu mixer icon by opening the Xubuntu Settings Manager>>Sessions and Startup>>Autostart Apps and un-check the Volume Control. After reboot you will have only the single gnome-media volume icon on the panel.

Dear god it's worked. Orb, you're a genius. 

I'm only grateful now but I will say one thing (that no one will ever see unless you have reply notifications): I was recommended to do my coding on Linux using the LAMP synergy.

I spent many hours troubleshooting this via the official troubleshooting pages which were neither here nor there, before you responded and I implemented your suggestion. Not many would be as patient, and with the sort of enthusiasm for linux as I. Especially coming from an already comfortable operating environment.

Nobody will ever see this but on the off-chance: Canonical need to get their act together and support Xubuntu as much Ubuntu if they value growth.

---

### Post by UndiFineD on 2012-01-24
the following link is broken
[[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/")

---

### Post by luno on 2012-02-01
I experienced a similar problem with an Acer Aspire One netbook (model AO-D250) and 11.10.  Audio works fine in Ubuntu, doesn't work at all in Xubuntu.  I'd have to consider this distro broken, since it looks like the OP and I have completely different audio hardware.

Most importantly, I installed "pavucontrol" via aptitude, configured mixer settings and now everything works.  This is an easy fix.

lspci:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

lsmod|grep snd:

snd_hda_codec_realtek   254125  1
snd_hda_intel          24262  3
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm

aplay -l:
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by hitman2k9 on 2012-02-02
Worked for me too :) thank you !

---

### Post by Dlambert on 2012-02-16
This didn't work for me....Creative SB -Xtreme (same card)

---

### Post by ShawnMilo on 2012-06-08
Thank you!

I've had so much trouble with this I switched back to Ubuntu from Xubuntu. For weeks I've been unable to solve this problem.

Using pavucontrol solved the problem for me -- finally!

---

