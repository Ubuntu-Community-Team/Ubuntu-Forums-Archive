---
title: "Getting MIDI to work"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by slugkilla on 2006-06-03
Hi, I have a cmi 8738 sound card and a psr-195 yamaha keyboard. I don't know what I have to do to get It to work. I just keep getting this JACK message.
> 19:26:09.214 Patchbay deactivated.
19:26:09.305 Statistics reset.
19:26:09.474 Startup script...
19:26:09.474 artsshell -q terminate
19:26:09.521 MIDI connection graph change.
19:26:10.179 Startup script terminated with exit status=256.
19:26:10.180 JACK is starting...
19:26:10.180 /usr/bin/jackd -R -dalsa -dhw:0 -r48000 -p128 -n2 -S -H -M
19:26:10.194 JACK was started with PID=5658 (0x161a).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|hwmon|hwmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 128 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
19:26:10.447 MIDI connection change.
19:26:10.460 MIDI connection graph change.
19:26:12.464 Server configuration saved to "/home/josh/.jackdrc".
19:26:12.465 Statistics reset.
19:26:12.670 Client activated.
19:26:12.671 Audio connection change.
19:26:12.685 Audio connection graph change.
19:26:12.686 XRUN callback (1).
19:26:14.684 XRUN callback (376 skipped).
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler
19:26:15.437 Shutdown notification.
19:26:15.438 Client deactivated.
19:26:15.440 JACK was stopped successfully.
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
19:26:18.110 MIDI connection graph change.
19:26:18.133 MIDI connection graph change.
19:26:18.333 MIDI connection change.
19:26:31.178 MIDI connection graph change.
19:26:31.214 MIDI connection change.
19:26:46.928 MIDI connection change.


and here is the link to my orginal thread 
[http://ubuntuforums.org/showthread.php?t=171829](http://ubuntuforums.org/showthread.php?t=171829)

thanks for any help

---

### Post by .t. on 2006-06-04
What exactly are you aiming to do with MIDI, and what are you trying to get to work?

What is the message above, and the situation that produces it, preventing you from doing?

---

### Post by slugkilla on 2006-06-05
hey,
I'm trying to connect an old keyboard to my sound card via a MIDI cabble. Once I have it connected, I plan to link it to a soft synth like Zyn and link that to Ardour so that I can play cool songs with the keyboard and record them to the hard drive. Jack does not seem to know that my keyboard is there. It could be that the jack is not setup correctly.In the jack setup area, I'm not sure what setting to select is the interface section. 
Here are the options listed under interface, input, and output:
hw:0     C-Media PCI CMI8738-MC6
hw:0,0  C-Media PCI DAC/ADC
hw:0,1  C-Media PCI 2nd DAC
hw:0,2  C-Media PCI IEC958
hw:1   MPU-401 UART
(default)

the in/out and interface is really the main things I need to change. Thanks

---

### Post by jcg_bzh on 2006-06-05
I Slugkilla, i'm a french user of dapper and i try to activate the midi port ot my sound card with a CMI8738. I try since two weeks and it is the hell for me. Can you give me an explaination of your configuration of your Ubuntu to activate this port please.

I have this:

cat /proc/asound/card0/midi*
MPU-401 MIDI 0-0

Output 0
  Tx bytes     : 0
Input 0
  Rx bytes     : 0

But when i try to connect the MPU401 port in jackd the connection dont work

---

### Post by slugkilla on 2006-06-05
When I try that command, the return says that there is no file of directory. hmmmmm, this could be one of my problems.

Edit: what does 'cat /dev/sndstat' give you. I got this:

cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux ubuntu 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0x9000, irq 209
MPU-401 UART at 0x330, irq 10

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
1: MPU-401 UART MIDI

Timers:
7: system timer

Mixers:
0: CMedia PCI
1: mixer10

---

### Post by jcg_bzh on 2006-06-06
You are the MPU401 port enable and not me, can you explain to me how to activate it...

cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux Dapper 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738 (model 37) at 0xa400, irq 209

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: MPU-401 MIDI 0-0

Timers:
7: system timer

Mixers:
0: CMedia PCI

---

### Post by jcg_bzh on 2006-06-06
It's ok for me i have resolved my trouble with this settings:

cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux Dapper 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0xb000, irq 177
C-Media PCI CMI8738 (model 37) at 0xa000, irq 209

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)
1: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: MPU-401 MIDI 0-0
1: MPU-401 MIDI 1-0

Timers:
7: system timer

Mixers:
0: CMedia PCI
1: CMedia PCI

I can play with my masterkeyboard in midi and make links with jackd.

---

### Post by slugkilla on 2006-06-06
How did you do that?? thanks

---

### Post by jcg_bzh on 2006-06-06
I make that like a badboy, i am not sure of the operation then i make a backup immediatly with partimage to keep my configuration.....

1- I removed the PCI sound card
2- I desactivated the onboard soud chipset in hardware
3- I removed alsa-base (sudo apt-get --purge remove alsa-base) & alsa-source
4- Reboot & stop
5- I replaced the PCI card on & reactivated the onboard chipset
6- Install alsa-source & sudo dpkg-reconfigure alsa-source (with reply -yes-yes-all)
7- Install alsa-base & sudo dpkg-reconfigure alsa-base
8- Reboot
9- Sudo apt-get install libesd-alsa0
10- Sudo gedit /etc/asound.conf (place this in it)

pcm.card0 {
type hw
card 0
}
 
pcm.!default {
type plug
slave.pcm "dmixer"
 
}
 
 
pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}

11- Sudo /etc/init.d/alsa-utils restart
12- Reboot & don't forget to view alsamixer -c0 & alsamixer -c1

My ~/.asoundrc

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card CMI8738MC6
defaults.ctl.card CMI8738MC6
defaults.pcm.device 0
defaults.pcm.subdevice -1

pcm.cmipci {
type hw
card 0
}

ctl.cmipci {
type hw
card 0
}

My configuration of Jackd

[http://img121.imageshack.us/img121/3830/capture4wu.png](http://img121.imageshack.us/img121/3830/capture4wu.png)
[http://img327.imageshack.us/img327/7526/capture23pm.png](http://img327.imageshack.us/img327/7526/capture23pm.png)

I hoppe this solution will work fine for you.

---

### Post by slugkilla on 2006-06-06
Thanks for all that info :) I'll try that right now.

---

### Post by slugkilla on 2006-06-06
Thanks for all the help, but It still is giving me problems:

> 20:16:49.868 Patchbay deactivated.
20:16:50.045 Statistics reset.
20:16:50.227 Startup script...
20:16:50.227 artsshell -q terminate
20:16:50.285 MIDI connection graph change.
20:16:50.570 Startup script terminated with exit status=256.
20:16:50.571 JACK is starting...
20:16:50.571 /usr/bin/jackd -R -P25 -dalsa -dhw:0 -r44100 -p256 -n2 -S -i2 -o2
20:16:50.587 JACK was started with PID=6764 (0x1a6c).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|256|2|44100|2|2|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 256 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
20:16:50.790 MIDI connection change.
20:16:52.805 Server configuration saved to "/home/josh/.jackdrc".
20:16:52.807 Statistics reset.
20:16:52.857 Client activated.
20:16:52.858 Audio connection change.
20:16:52.871 Audio connection graph change.
20:16:59.924 MIDI connection graph change.
20:17:00.099 MIDI connection change.
20:18:21.952 Audio connection graph change.
20:18:21.987 MIDI connection graph change.
20:18:22.035 Audio connection change.
20:18:22.036 MIDI connection change.
20:18:31.772 Audio connection change.
20:18:47.586 MIDI connection change.
20:18:59.774 MIDI connection change.
20:18:59.775 XRUN callback (1).
delay of 13194.000 usecs exceeds estimated spare time of 5414.000; restart ...
20:19:05.332 MIDI connection change.
20:19:05.334 XRUN callback (2).
delay of 14712.000 usecs exceeds estimated spare time of 5409.000; restart ...

I do not understand this at all :( The XRUN happened when I tried to connect the MIDI port to Zyn. After following your steps, every thing stayed the same, It was the pic of the settup that got me where I am now. I think I'm on the right track now. Does this look like my Keyboard is bad? or do I still not have things setup right? Thanks again

---

### Post by bwanab on 2006-06-06
[QUOTE=slugkilla]Hi, I have a cmi 8738 sound card and a psr-195 yamaha keyboard. I don't know what I have to do to get It to work. I just keep getting this JACK message.



and here is the link to my orginal thread 
[http://ubuntuforums.org/showthread.php?t=171829](http://ubuntuforums.org/showthread.php?t=171829)

thanks for any help[/QUOTE]

Hi Slugkilla,
It looks to me like you've simply got your jack connection parameters way too aggressive. When you lauch qjackctl, go to setup and try setting the Frames/Period to something like 512 and the Periods/Buffer to 4. If that works, you can try to tighten it up some. From your jack log, jack is shutting down as soon as you try to do something because it can't keep up.

---

### Post by jcg_bzh on 2006-06-08
What is the news ??? Have you resolved you trouble ??? Do you want some copy of my systeme files ???

---

### Post by slugkilla on 2006-06-08
Yeah, I have tried everything. I still can't get things to work. I think my keyboard is incompatible. I'll have to wait for a yardsale with a nice keyboard. Thanks for all the help. If you still have stuff for me to try, it would be very much appreciated.

---

### Post by panki on 2007-01-27
OK guys.. here's how I solved this (after 2 days of bullfighting with my machine)

I wanted to connect my Roland Synth to my CMI midi port.. So

If you have a  C-Media PCI CMI8738-MC6, 

and when you do 

cat /dev/sndstat 

you get

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

then you need to put this line at the end of /etc/modprobe.d/alsa-base

options snd-cmipci mpu_port=0x330 fm_port=0x388

Then, on the Console, type modprobe snd-seq

you should see the mpu-401 on qjackctl (apt-get install qjackctl jackd  <-- if you dont have it)

Please note that this is on Edgy.

---

