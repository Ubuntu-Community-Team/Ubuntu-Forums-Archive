---
title: "No Sound 12.04 Desktop but Sound in XBMC Frodo 12.1 over HDMI"
date: 2013-09-23
forum: Multimedia Software
---

### Post by snuffy47 on 2013-09-23
Howdy

Did a new install of 12.04 Ubuntu few months ago and also XBM.  Had problems with sound working on desktop but not XBMC.

Went through some stuff and now I have sound in XBMC but not my desktop when running You tube, Firefox, Netflix, movie player ect

It has been some time since I got back to looking at this problem and was hoping someone would point me in the right direction to get started on this ;) again

---

### Post by Yellow Pasque on 2013-09-24
> Went through some stuff 
Be more specific. It's difficult to help someone undo something when they don't tell you what needs undone.

---

### Post by snuffy47 on 2013-09-25
The problem I am having is now I can not remeber what I actually did

Been reading some of the FAQs and will try and get back on it.  Is there any outputs I could paste bin that would help identify my configuration.

---

### Post by Yellow Pasque on 2013-09-25
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by snuffy47 on 2013-09-26
It is xbmcbuntu desktop that does not have sound.  My xbmc has sound though

[http://www.alsa-project.org/db/?f=37727a8b0fc320b9380771374f97b78f032b244d](http://www.alsa-project.org/db/?f=37727a8b0fc320b9380771374f97b78f032b244d)

---

### Post by snuffy47 on 2013-09-29
Okay still having problems with sound

I have XBMCbuntu installed.  Sound works find in XBMC 

No sound in XBMCbuntu desktop or I think it is LXEubuntu but not sure here

```
smc@dsmc-GA-MA74GM-S2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
dsmc@dsmc-GA-MA74GM-S2:~$ ^C
```

this terminal command gives me white noise through left front speaker in desktop enviroment

```
 speaker-test -D plughw:0,7
```

I could really use some help here

---

### Post by snuffy47 on 2013-09-30
Okay tried this and it did not work for me

[http://ubuntuforums.org/showthread.php?t=1641771&page=2](http://ubuntuforums.org/showthread.php?t=1641771&page=2)

Going to try to update alsa now :(

Any interest here hehehe

---

### Post by robertozillioxo on 2013-11-03
I Am having the same issue. I have sound working fine through my XBMC. But  nothing to  any applications on my desktop such as chrome or firefox or VLC etc....
aslamixer shows me have my sound at 100 aplay -vv   audiofile does not play any sounds.

 cat /proc/asound/card0/codec* | grep Codec                       Codec: Realtek ALC887-VD
Codec: Intel CougarPoint HDMI

cat /proc/asound/card0/codec* | grep Codec                       Codec: Realtek ALC887-VD
Codec: Intel CougarPoint HDMI
nate@Dragon:~$ ^C
nate@Dragon:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0








[http://www.alsa-project.org/db/?f=688f13b74eee82f914b8d00acbc84a9f7ae3cca5](http://www.alsa-project.org/db/?f=688f13b74eee82f914b8d00acbc84a9f7ae3cca5)

---

### Post by snuffy47 on 2013-11-03
I am still in the same boat

If you figure it out please post

---

### Post by bs0d2 on 2013-12-21
I'm having the same issue here. It's sure strange... Audio works in XBMC, but not in XBMCBuntu??

---

### Post by sdouble on 2013-12-23
is your user in the audio group?

I'm having an issue where mpd is the only thing that works on my system.  If I want to run something like VLC or a browser with youtube, I have to run it as root.  Making sure your user is in the audio group should fix that, but it hasn't for me.  Check your user and make sure they're in the right group.

---

### Post by diyhouse on 2013-12-23
Just to add to this discussion,.. I am running a ubuntu myth setup,.. sound from Myth is fine, and works as expected,.. its is just that I get no sound with chrome. Although I can run the sound test speaker-test -Dhw:0,3 -c2,.. and white noise is produced from TV speakers...

Output from "aplay -l", is exactly as given by [COLOR=#000000]robertozillioxo, note,... so there are many similarities with my own setup....

my asound.conf file looks as follows

-rwxrwxrwx 1 root root 126 Dec 14 21:33 asound.conf

pcm.!default {
      type plug
      slave.pcm {
              type hw
              card 0
              device 3
      }
 }


I have added mylogin -user to the audio group,.. this has made no difference,.. still no sound from chrome...


Any ideas and help gratefully appreciated

[/COLOR]

---

