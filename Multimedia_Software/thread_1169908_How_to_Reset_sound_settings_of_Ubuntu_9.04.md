---
title: "How to Reset sound settings of Ubuntu 9.04"
date: 2009-05-25
forum: Multimedia Software
---

### Post by RafaelG on 2009-05-25
Hi, I'm new in ubuntu 9.04,  I have tow sound card Intel and external, I found a thread on this Forum to hear multiple sound using both ALSA & ESD and I moved the sound Setting of Ubuntu 9.04 but the sound on the system like when it start and the sound on Firefox like flash don't work with my second sound card (external) just with the Intel card, I will like to remove what I did or reset the default sound settings of ubuntu 9.04 how I can to do it? I live some information to get help

eligonzalez@ergg:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[B]
WHAT I DID:[/B]
                                                  HOWTO: Hear Multiple Sounds Using Both ESD & ALSA

Hello there,
This is just a clean and better organised guide of varunus's HowTo located [here]("http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound"). So primarily all the credits go to him.

This HowTo will give you instruction on enabling software mixing, to avoid application problems like Audacity needing killall esd to work as well as Skype [now Skype will no longer crash if you receive a message or a call (when it try to play sound in fact)], so let's get to work shall we ?? :razz:.


[LIST=1]
[*]We need to install libesd-alsa0 so
     Code:
     sudo apt-get install libesd-alsa0
[*]We need to create /etc/asound.conf, so
     Code:
     sudo gedit /etc/asound.conf 
Insert into it:
     Code:
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
period_size 2048    #1024
buffer_size 32768    #4096
            #periods 128
rate 48000        #44100
}
bindings {
0 0
1 1
}
}
[*]We need to change /etc/esound/esd.conf contents so:
     Code:
     sudo mv /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf 
Insert into it:
     Code:
     [esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
[*]Now **You** need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
     Code:
     gstreamer-properties
[/LIST]

---

