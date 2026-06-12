---
title: "Skype video white screen and high CPU 9.04 Jaunty"
date: 2009-05-01
forum: Multimedia Software
---

### Post by bluenova on 2009-05-01
Hi all,

I had an issue after upgrading to 9.04 whereby video in Skype would only display a white screen and CPU usage would shoot up to 100%

The issue seemed to be the driver Skype was using although it worked fine in 8.10

The solution was to force the correct driver...

```
cd /usr/bin
sudo gedit ./runSkype
```

Add the text...

```

#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Make it executable...

```
sudo chmod a+x ./runSkype
```

Then run Skype with...

```
runSkype
```

---

### Post by jasidog on 2009-05-07
Hmm, doesn't work for me. Still at 100% cpu usage. Wasn't trying to use video. 

Lots of errors - 

```
jasidog@boxer-box-nix:~$ runSkype
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

RtApiAlsa: underrun detected.

ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

RtApiAlsa: underrun detected.

ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.


RtApiAlsa: underrun detected.

ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

RtApiAlsa: underrun detected.

```

---

### Post by Lex92 on 2009-05-07
> **jasidog said:**
> hmm, doesn't work for me. Still at 100% cpu usage. Wasn't trying to use video. 

Lots of errors - 

```
jasidog@boxer-box-nix:~$ runskype
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)

rtapialsa: Underrun detected.

Alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)

rtapialsa: Underrun detected.

Alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)

rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.


Rtapialsa: Underrun detected.

Alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm.c:2205:(snd_pcm_open_noupdate) unknown pcm cards.pcm.hdmi
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)
alsa lib pcm_bluetooth.c:1569:(audioservice_expect) bt_get_capabilities failed : Input/output error(5)

rtapialsa: Underrun detected.

```


+1:(

---

### Post by kodiakz on 2009-05-09
Thanks for that, my Microdia cam runs now like charm with skype. First I had to get it running with the manual [[COLOR="Blue"]here[/COLOR]]("http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1").

---

### Post by unc0nn3ct3d on 2009-05-10
Solution doesn't solve problem.. In fact /usr/local/bin/skype was already configured to force load that driver

Hope this helps:

[http://blog.netflowdevelopments.com/2009/05/10/fixing-alsa-underrun-erorrs-associated-with-pulseaudio-and-typically-skype-in-ubuntu/](http://blog.netflowdevelopments.com/2009/05/10/fixing-alsa-underrun-erorrs-associated-with-pulseaudio-and-typically-skype-in-ubuntu/)

Summary:

    * edit ~/.pulse/daemon.conf (or /etc/pulse/daemon.conf if you run as system)
    * Hash out realtime-scheduling and realtime-priority
    * Unhash high-priority and nice-level
    * set nice level to 3 (not -3 or -11 for that matter)

---

### Post by unc0nn3ct3d on 2009-05-11
With skype to skype and skype in I am having no problems but just with skypeout I am getting stuttering audio still at the hands of the underrun.  It doesn't cut out completely like before so I am still ahead but my cpu sits at 99% while in a call.. If I give Skype higher priority it does help but not terribly much.

Gah!

Searching around the skype forums netting me a solution:

Put this in your ~/.asoundrc file

# Part I directly from ALSA Dmix Wiki

pcm.paul { # paul is my name, you can use your name, just make sure you use it below too
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"    
        period_time 0
        period_size 1024
        buffer_size 8192
       #format "S32_LE"
       #periods 128
        rate 44100
    }
}

pcm.dsp0 {
    type plug
    slave.pcm "paul"
}

# This following device can fool some applications into using pulseaudio
pcm.dsp1 {
    type plug
    slave.pcm "pulse"
}

ctl.mixer0 {
    type hw
    card 0
}


pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
}

---

### Post by sayantandas on 2009-05-24
thanks a lot.. it works a charm

---

### Post by code_linux on 2009-06-04
Thank you. Video works fine on Skype! ;)

---

### Post by cyrinda on 2009-06-09
hi for me works just set up all sound devices in skype pref., not let it be default ... then skype sleeps in taskbar really .. srr for my english

---

### Post by fiveacez on 2009-06-10
> **unc0nn3ct3d said:**
> 
Put this in your ~/.asoundrc file

# Part I directly from ALSA Dmix Wiki


I'm a Ubuntu noob, so I have 2 Questions: 
1) Where is "~/.asoundrc"?  If it's supposed to be in home, I don't have it (does installing this through apt-get affect this?)
2)  I'm confused by the ALSA Dmix Wiki...can someone show me the code for this?

---

### Post by mfarewell on 2009-06-22
> **fiveacez said:**
> I'm a Ubuntu noob, so I have 2 Questions: 
1) Where is "~/.asoundrc"?  If it's supposed to be in home, I don't have it (does installing this through apt-get affect this?)
2)  I'm confused by the ALSA Dmix Wiki...can someone show me the code for this?

You just create the file with that name in your home directory e.g. ```
gedit ~/.asoundrc
``` and then add the text suggested from the post. If you log out and login again you should see an option "paul" in the skype sound settings (unless you have modified the profile to your name), select this and hopefully it will work. I must say it doesn't work for me and I abandoned it. But maybe it is OK for you. I have currently followed [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) in the hopes that it will resolve it. I have also tried killing the bluetooth service as this seems to be causing a crash in skype. You are not alone in hoping this gets resolved soon!

See Also:
[https://bugs.launchpad.net/bugs/361615](https://bugs.launchpad.net/bugs/361615)
[https://bugs.launchpad.net/bugs/386817](https://bugs.launchpad.net/bugs/386817)
[http://forum.skype.com/index.php?showtopic=306381&st=0](http://forum.skype.com/index.php?showtopic=306381&st=0)

---

