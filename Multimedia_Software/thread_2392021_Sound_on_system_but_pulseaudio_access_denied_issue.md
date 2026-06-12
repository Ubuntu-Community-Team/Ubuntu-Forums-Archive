---
title: "Sound on system but pulseaudio access denied issue"
date: 2018-05-15
forum: Multimedia Software
---

### Post by 76mpaul on 2018-05-15
Hi everyone, 

I'm having an issue with pusleaudio and alsa since many days that give me some headaches...
I've sound on my system, no problems with that (both firefox and spotify works) but I've issues in the syslog that lead some software (snips in that case) to not load.

The command 'tail -f /var/log/syslog' give me the following result :
```
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: Home directory not accessible: Permission denied
May 15 22:54:01 paulm-serveur pulseaudio[12853]: [autospawn] core-util.c: Home directory not accessible: Permission non accordée
May 15 22:54:01 paulm-serveur pulseaudio[12853]: [autospawn] lock-autospawn.c: Impossible d'accèder au verrou autonome.
May 15 22:54:01 paulm-serveur pulseaudio[12853]: [pulseaudio] main.c: Failed to acquire autospawn lock
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: ALSA lib pcm_route.c:867:(find_matching_chmap) Found no matching channel map
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: Home directory not accessible: Permission denied
May 15 22:54:01 paulm-serveur pulseaudio[12856]: [autospawn] core-util.c: Home directory not accessible: Permission non accordée
May 15 22:54:01 paulm-serveur pulseaudio[12856]: [autospawn] lock-autospawn.c: Impossible d'accèder au verrou autonome.
May 15 22:54:01 paulm-serveur pulseaudio[12856]: [pulseaudio] main.c: Failed to acquire autospawn lock
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused
May 15 22:54:01 paulm-serveur snips-audio-server[12849]: Home directory not accessible: Permission denied
```

And 'journalctl -b -r  _COMM=pulseaudio' :
```
mai 15 22:58:03 paulm-serveur pulseaudio[13842]: [pulseaudio] main.c: Failed to acquire autospawn lock
mai 15 22:58:03 paulm-serveur pulseaudio[13842]: [autospawn] lock-autospawn.c: Impossible d'accèder au verrou autonome.
mai 15 22:58:03 paulm-serveur pulseaudio[13842]: [autospawn] core-util.c: Home directory not accessible: Permission non accordée
```

So I wandered arround the web, follow countless of topics and tutorials, purge and reinstall pulse, alsa ... But nothing seams to works...
As you may asks, here are the permissions of my home folder :
```
root@paulm-serveur:/home/paulm# ls -la /home
total 12
drwxr-xr-x  3 root  root  4096 mai    5 18:05 .
drwxr-xr-x 24 root  root  4096 mai   11 21:23 ..
drwxr-xr-x 28 paulm paulm 4096 mai   15 22:41 paulm
root@paulm-serveur:/home/paulm#
```

My user is part of the following groups :
```
paulm@paulm-serveur:~$ groups
paulm sys adm cdrom sudo audio dip video plugdev lpadmin pulse pulse-access sambashare _snips pulse-rt
```

I add few modification on the pulse config :
[LIST]
[*]/etc/pulse/daemon.conf
[LIST]
[*]daemonize = yes 
[/LIST]
  
[*]/etc/pulse/default.pa
[LIST]
[*]load-module module-alsa-sink device=hw:1,7
load-module module-alsa-source device=hw:0,3 
[/LIST]
    
[/LIST]
And my asound.conf is :
```
pcm.!default {
    type pulse
    hint.description "Default Audio Device"
}
ctl.!default {
    type pulse
}

pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}
```

My sound output is an HDMI port on a nvidia card.

Is there anything I've missed or seems to be out of place in my config ?

Thanks for your help,

Regards, 

76MPaul

---

### Post by Yellow Pasque on 2018-05-17
It looks like snips wants access to the sound device, but can't get it because of pulseaudio. I'm not familiar with snips, but I would look for a way to get it to play nicely with pulseaudio.

---

### Post by 76mpaul on 2018-05-20
Thanks for your answer and sorry for my late reply. 

I don't know if it's really a snips related issue as i can't use the "aplay" function...

```
root@paulm-serveur:/home/paulm# aplay test.wav
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connexion refusée


aplay: main:722: erreur à l'ouverture audio: Connexion refusée
```

---

### Post by Yellow Pasque on 2018-05-20
So pulseaudio is not running? You may need to get more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

I'm not sure why you are manually loading "load-module module-alsa-sink". The pulseaudio documentation recommends you use "module-udev-detect" to detect the devices for you. I'm also not sure what you are doing with asound.conf as the default configuration is already setup to use pulse.

---

### Post by 76mpaul on 2018-05-21
It's what I can't understand... 

Here are the logs from your shared links :
[http://www.alsa-project.org/db/?f=2be97caa0638bdeeff1c9749b7239b84aded325b](http://www.alsa-project.org/db/?f=2be97caa0638bdeeff1c9749b7239b84aded325b)

and pulse : 
```
(   0.000|   0.000) E: [pulseaudio] main.c: Daemon startup failed.
```

What bother me is that pavucontrol is working well and I've sound. From the alsa log it seems that pulse is running. However not from the pulseverbose log...
And I can't understand why the Daemon startup failed...

---

### Post by Yellow Pasque on 2018-05-22
> And I can't understand why the Daemon startup failed... 
IIRC, you get this message if you try to start pulseaudio and it's already running.

---

