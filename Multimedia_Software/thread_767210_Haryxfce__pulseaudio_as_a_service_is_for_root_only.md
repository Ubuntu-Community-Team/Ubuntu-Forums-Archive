---
title: "Hary/xfce : pulseaudio as a service is for root only ;-("
date: 2008-04-25
forum: Multimedia Software
---

### Post by manatlan on 2008-04-25
I'd dist-upgraded from gutsy to hardy. No trouble
I use mainly XFCE4, and it seems that pulseaudio is only available under gnome-session, because it seems it replace ESd in the core.

SO under xfce4, pulseaudio is not activate ...
when i run "pulseaudio" in a terminal ... all seems works.

But i'd like to be able to run it as a service. So i edited the /etc/init.d/pulseaudio, to be able to start the service when session start. (on hardy, the service pulseaudio is not activated, because, like a say before, it's integrated in the esg/gnome)

So, under xfce/hardy, the pulseaudio start now as a service, and all audio applications reach to play audio thru pulse audio (mpd, totem, ...)

But because as a service, it's started as root ... all pulseaudio utilities are not able to connect to pulse (paplay, pavucontrol, pavumeter ...), by saying "connection refused : access denied" ... (note: if i run "sudo pavumeter" : it can't connect too !!?!)
(If i start pulseaudio under a terminal, without root rights, all this tools reach to connect)

So, how can I do to be able to run pulseaudio as a service, and to be able to use pulseaudio tools in the same time ???

please help
I had googled a lot, but found nothing ...

---

### Post by stevodude on 2008-05-22
I to would like to know how to do this.

Have" ubunut 8.04
Pulseaudio
MPD running as a service when pc starts.
now I cannot hear any music play when I connect using mpd clients (ie ncmpc) until I log into gnome...

This is an unsatisfactory way to run an audio engine specially on linux...
should be as a startup daemon service.

---

### Post by Cyan_Fire on 2009-01-19
Did you figure it out? If not, you need to add users to the pulse-access group to be able to connect to pulseaudio, as documented [here]("http://pulseaudio.org/wiki/SystemWideInstance").

Also, you shouldn't modify the init script itself but instead the settings in /etc/default/pulseaudio.

---

