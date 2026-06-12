---
title: "another skype problem ubuntu jaunty"
date: 2009-08-18
forum: Multimedia Software
---

### Post by erolerten on 2009-08-18
Hi All,

Although I am not really new to ubuntu, I could not solve this problem on my own. 

I have installed skype (first tried the installer from their web site, then through medibuntu). Every time I boot up ubuntu (jaunty) and start skype, it cannot make any calls and takes very long to connect.

I have run it through terminal once and the output was:
```
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
^[[1;2AALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi

```

During this skype instance, I try to check the sound setting and skype stops responding... I have to force to quit.

When I start it a second time, everything works normal...

Here is what I have already tried to fix it:
[LIST=1]
[*]try every possible sound setting from the sound devices in skype
[*]installed skype-static
[/LIST]

None of them worked...

How can I solve this?

Thank you in advance for your help.

Erol

---

### Post by erolerten on 2009-08-18
Dear All

I have finally managed to solve the problem,

Installing Skpye-static-oss was the solution...

---

