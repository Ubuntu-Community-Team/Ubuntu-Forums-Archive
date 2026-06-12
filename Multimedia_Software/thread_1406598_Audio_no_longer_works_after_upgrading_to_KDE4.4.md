---
title: "Audio no longer works after upgrading to KDE4.4"
date: 2010-02-14
forum: Multimedia Software
---

### Post by Hellraizer on 2010-02-14
[COLOR="Red"]*//Solved the audio problems, read the ending of the post.*[/COLOR]

Hi.


I upgraded to KDE 4.4 on my Kubuntu 9.10 (64bit). The upgrade didn't go so good, I thought, there were some dependency issues that I managed to solve with the -f option. After that, everything was working... for a while. When I started up the computer today I got a box saying
KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Capture: HDA Intel (ALC889A Analog)
Output: HDA Intel (ALC889A Analog)

When I go to System Settings -> Multimedia, HDA Intel (ALC889A Analog) is on top of the list (the preferred device) but it is grayed out.

I tryed to playing some media with mplayer and the audio worked fine. There is no audio for programs like Amarok, however.

I tryed inspectin the problem with the help of Ubuntu SoundTroubleshooting Guide:

aplay /usr/share/sounds/alsa/Front_Center.wav
Audio plays fine

fgrep -ie 'audio' /etc/group
audio:x:29:bubba


sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


find /lib/modules/`uname -r` | grep snd
bunch of items with the ending .ko come up, guess its fine?

lspci -v | less
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f8100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
Check the output here: [http://www.alsa-project.org/db/?f=26a35a979ff6f86fd0979db6e95f87160b66093c](http://www.alsa-project.org/db/?f=26a35a979ff6f86fd0979db6e95f87160b66093c)



I'm a bit worried about the upgrade to kde4.4 I did, I was told that using -f was not such a good idea. It didn't install updates with just apt-get upgrade, however, so thats why I used it. For some time, everything seemed to work fine, until today when I booted up the computer and got the audio problem.
Will I be having problems because of this in the future? 'apt-get check' doesn't give any errors at the moment. I really like KDE4.4 better than KDE4.3.2, it has fixed some issues I had with 4.3.2.


But what about the audio problems? Why did it stop working all of a sudden? It still works for programs like Mplayer, no errors in the log or anything there. But why does KDE report the audio devices as 'removed'?

Kernel: 2.6.31-19-generic


Hellraizer


**[COLOR="Red"]EDIT:[/color]**

Audio works again after booting into older kernel (2.6.31-14-generic) and then booting into newer (2.5.31-19). But still, is it a good idea to use this system or will I have problems in future because of the whole upgrade dependency mess?

---

### Post by mfraser on 2010-03-13
I think this is what I'm getting too, but I'm running KDE 4.3.2 on Kubuntu 9.10.

A few weeks ago I started having popups appear saying that no audio drivers could be found and defaulting to . After rebooting the computer, sound was OK again.

This then went away, but came back again yesterday. This is when I noticed that it was only KDE apps that weren't playing audio - MPlayer and VLC worked fine.

This morning when I tried, it took 3 attempts to get sound working with Amarok.

Linux Rachael 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

---

