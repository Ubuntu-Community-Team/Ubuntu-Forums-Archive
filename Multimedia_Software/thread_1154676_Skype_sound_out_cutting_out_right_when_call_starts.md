---
title: "Skype sound out cutting out right when call starts"
date: 2009-05-10
forum: Multimedia Software
---

### Post by unc0nn3ct3d on 2009-05-10
This problem comes and goes but today it isn't going away so I figure I'll ask around for help.

So what happens is that skype appears to be working, I make a call, can hear it ringing and as soon as the phone gets picked up(using skypeout) the sound cuts out completely for skype and STAYS off until I reload alsa and restart pulseaudio.  
If I try to close skype it just hangs there indefinitely, I am forced to kill the process in terminal just to shut it down.  When I restart it the lack of sounds persists and will persist unti I reload alsa and restart pulse.

All other sound applications are functioning beautifully and are unaffected by this.


This is the error log I am getting with skype:

[QUOTE]ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)


RtApiAlsa: underrun detected.

ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)


Problem solved:

[http://blog.netflowdevelopments.com/2009/05/10/fixing-alsa-underring-erorrs-associated-with-pulseaudio-and-typically-skype-in-ubuntu/](http://blog.netflowdevelopments.com/2009/05/10/fixing-alsa-underring-erorrs-associated-with-pulseaudio-and-typically-skype-in-ubuntu/)

Summary:

    * edit ~/.pulse/daemon.conf (or /etc/pulse/daemon.conf if you run as system)
    * Hash out realtime-scheduling and realtime-priority
    * Unhash high-priority and nice-level
    * set nice level to 3 (not -3 or -11 for that matter)

---

