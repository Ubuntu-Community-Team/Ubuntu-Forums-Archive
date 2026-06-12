---
title: "Native instruments Audio 6 not working properly in Ubuntu 14.04"
date: 2015-01-04
forum: Multimedia Software
---

### Post by ximo on 2015-01-04
Hi

I have recently reinstalled ubuntu 14.04 after some time of not using any linux distro and im am having issues with the following soundcard.

Native Instruments Audio 6.

I used to have it working correctly in ubuntu 12.04 with the .asoundrc file from here: 


[http://www.native-instruments.com/forum/threads/audio-6-linux-support.136907/](http://www.native-instruments.com/forum/threads/audio-6-linux-support.136907/)


But now, while the sound card is detected the channel configuration seems to be different. I am trying to call in alsa the pcms t6_pair1, t6_pair2 or t6_pair3 and it returns an error. Like if the device doesnt exists. Also when i  use alsa mixer on the device (hw:2,0)[COLOR=#333333] I see the Direct Thru Inputs and Line Ins (mentioned as Outputs...), I can't see the outputs (A, B and Main) and it doesnt detect any inputs.

[/COLOR]Anyone know how i could get this soundcard to work properly again in 14.04?

To me it looks like the usb-sound driver in alsa has been modified since 12.04 where it worked properly (or something of the sorts)..... maybe reload an older driver into the kernel?

Thx

---

### Post by Rob Sayer on 2015-01-06
This looks like the best thing I can find ....

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Native_Instruments](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Native_Instruments)

... and I would consider that non newbie stuff.  It doesn't say it's for a particular distro/release because it assumes you know how to deal with it.

---

### Post by ximo on 2015-01-06
Well, the usb-audio module is loaded as it does detect the sound card (and another usb card i have works correctly).....

Actually i made progress with the .asoudrc, it just doesnt load it but it does load from /etc/asound.conf. So i can now acces the pairs i want from aplay.

The poblem is with alsamixer, it just displays the phono and pass through switches (which i can correctly control with amixer) and no volume controls for either input or output. It seems both capture and playback pcms are muted and i cant get them to unmute.

------------------
amixer -c T6 contents
numid=3,iface=MIXER,name='Direct Thru Channel A'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=4,iface=MIXER,name='Direct Thru Channel B'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=5,iface=MIXER,name='Phono Input Channel A'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=6,iface=MIXER,name='Phono Input Channel B'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=2,iface=PCM,name='Capture Channel Map'
  ; type=INTEGER,access=r----R--,values=6,min=0,max=36,step=0
  : values=0,0,0,0,0,0
  |     | chmap-fixed=FL,FR,FC,LFE,RL,RR

numid=1,iface=PCM,name='Playback Channel Map'
  ; type=INTEGER,access=r----R--,values=6,min=0,max=36,step=0
  : values=0,0,0,0,0,0
  |     | chmap-fixed=FL,FR,FC,LFE,RL,RR

ximo@ximo-ubuntu:~$ amixer -c T6 cset numid=1 36,36,36,36,36,36
amixer: Control hw:2 element write error: Operation not permitted

ximo@ximo-ubuntu:~$ amixer -c T6 cset numid=2 36,36,36,36,36,36
amixer: Control hw:2 element write error: Operation not permitted

-----------------------------------------------

Dont know why it does not allow me to change the volumes in the capture or playback pcm... so they are stuck at 0.

---

### Post by Yellow Pasque on 2015-01-09
Do you have pulseaudio installed? Because Ubuntu 14.04 comes with pulseaudio and that asound file goes around pulseaudio. 

> amixer: Control hw:2 element write error: Operation not permitted
You probably need to put your user in the audio group if you are trying to do that..

---

### Post by ximo on 2015-01-09
yeah i have pulse audio installed, but i can correctly call the duplex pairs in the asound through alsa be it with aplay or xwax (final goal)... It just doesnt reproduce or capture any sound, so its like muted. Well i dont think its exactly muted, alsa mixer ( and even the pulseaudio mixer who does see the card) just dont detect any input or output devices. amixer doesnt detect any controls besides the direct thru and phono switches, well the amixer -contents comand does detect the playback and capture channel maps. but thats what i cant get to modify. Which i obviously tried to do as root too (sudo), with the same result.

---

### Post by Yellow Pasque on 2015-01-09
Hmm. Well, I would try the latest kernel. Maybe these fixes are applicable:
[https://github.com/torvalds/linux/commit/01cb156edbbd4e6c4fd8db0d05f18c62c424f9aa](https://github.com/torvalds/linux/commit/01cb156edbbd4e6c4fd8db0d05f18c62c424f9aa)
[https://github.com/torvalds/linux/commit/da6d276957ea56b9514aa5c8d885edf22f0b3e65](https://github.com/torvalds/linux/commit/da6d276957ea56b9514aa5c8d885edf22f0b3e65)

[https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc3-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc3-vivid/)

---

### Post by ximo on 2015-01-10
I have tried updating to the highest stable kernel 3.18.1... but i hadnt seen those fixes, gona give it a shot i guess i dont loose anything..... coz i even tried downgrading the kernel to previous releases and it still didnt work.

---

### Post by ximo on 2015-01-10
Ok im just posting to say i solved this, ut was a faulty usb port causing all the trouble. I guess this card just doesnt have any volume controls for alsa mixer.....

I got a hold of another laptop and with a fresh instalation of trusty it worked off the bat with the asound.conf file.


any mod can just close the thread and edit the title to solved.

---

