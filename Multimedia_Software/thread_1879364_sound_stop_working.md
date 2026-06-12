---
title: "sound stop working"
date: 2011-11-11
forum: Multimedia Software
---

### Post by masuch on 2011-11-11
Hi,

I have lost sound on Oneiric 64bit couple of days ago.
In Windows it works properly.

Following this URL to find problem:
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

I have reported results from 'alsa-info' script on URL:
[http://www.alsa-project.org/db/?f=0d95bc76ad9b99af5c0a33106f0561d641b22883](http://www.alsa-project.org/db/?f=0d95bc76ad9b99af5c0a33106f0561d641b22883)

$ aplay -l
  # **** List of PLAYBACK Hardware Devices ****
  # card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  #   Subdevices: 1/1
  #   Subdevice #0: subdevice #0
  # card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  #   Subdevices: 1/1
  #   Subdevice #0: subdevice #0
  # card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  #   Subdevices: 1/1
  #   Subdevice #0: subdevice #0
  # card 2: Generic_1 [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  #   Subdevices: 0/1
  #   Subdevice #0: subdevice #0

$ lspci -nn | grep '\[04[80][13]\]'
  # 00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
  # 03:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]
  # 04:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]

final overview:
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
03:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]
04:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
03:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]
04:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]
Soundcards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
03:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]
04:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa80]


Could somebody please help how to fix it ?
thanks for any clue
M.

---

### Post by wildmanne39 on 2011-11-11
Hi, I am not an expert on your issue but at the link did you perform prcedure Af then Ag?
Thank you

---

### Post by masuch on 2011-11-11
> **wildmanne39 said:**
> Hi, I am not an expert on your issue but at the link did you perform prcedure Af then Ag?
Thank you

the last paragraph is procedure Ac.
attached file is script - I am sorry I could not find it where is it located in that documentation.
!!! please rename attached file - do not use tar !!!

---

### Post by shantiq on 2011-11-11
three weeks into using oneiric i am still having sound problems


most times it does not start automatically


i have to go to Systems Monitor


and kill pulse

the setting i see when i open SM is pulseaudio   ```
uninterruptible
```


sometimes i have to kill it 3 or 4 times before it kicks in


it starts to works when SM shows pulseaudio   ```
 sleeping 
``` 


i keep a musicplayer on top to test it as i go



**so maybe** try this    you can also go commandline with


```
pulseaudio   --killall
```    and also monitor on player


not ideal i know  :KS:KS:KS   and i have ranted elsewhere about it :KS:KS


Best of luck

---

### Post by wildmanne39 on 2011-11-11
Hi, procedure Af and Ag is there, I helped in the writing of the guide and I was just there, it is after a lot of pictures.
Thank you

---

### Post by masuch on 2011-11-11
I have found it in documentation finally.
alsa-info.sh script for generating is located in Appendix D.

---

### Post by masuch on 2011-11-11
> **shantiq said:**
> three weeks into using oneiric i am still having sound problems


most times it does not start automatically


i have to go to Systems Monitor


and kill pulse

the setting i see when i open SM is pulseaudio   ```
uninterruptible
```


sometimes i have to kill it 3 or 4 times before it kicks in


it starts to works when SM shows pulseaudio   ```
 sleeping 
``` 


i keep a musicplayer on top to test it as i go



**so maybe** try this    you can also go commandline with


```
pulseaudio   --killall
```    and also monitor on player


not ideal i know  :KS:KS:KS   and i have ranted elsewhere about it :KS:KS


Best of luck


I just killall pulse audio 
and tried to change all sound card devices 
but did not work :-(
and after tens of seconds pulseaudio was back :-)

---

### Post by masuch on 2011-11-11
Hi,

where did you get system monitor? I am using xfce desktop. I could not find it.

---

### Post by masuch on 2011-11-11
> **wildmanne39 said:**
> Hi, procedure Af and Ag is there, I helped in the writing of the guide and I was just there, it is after a lot of pictures.
Thank you

When I run alsa-info.sh it said:
 Please inform the person helping you.

but I did not find how to do it. Could you help me please how inform somebody and where ?

thank you.

---

### Post by MoreOrLess on 2011-11-11
> and after tens of seconds pulseaudio was back
You should probably set autospawn to no, either for all users in /etc/pulse/daemon.conf or for your user in ~/.pulse/daemon.conf (remember to remove the leading ';' if editing the /etc/ file).

---

### Post by shantiq on 2011-11-11
> where did you get system monitor? 


well on Oneiric it is under Applications/System Tools

---

### Post by shantiq on 2011-11-11
> **MoreOrLess said:**
> You should probably set autospawn to no, either for all users in /etc/pulse/daemon.conf or for your user in ~/.pulse/daemon.conf (remember to remove the leading ';' if editing the /etc/ file).



hi there can you explain a bit more??


autospawn is not present in the file you describe  > /etc/pulse/daemon.conf


```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
; deferred-volume-safety-margin-usec = 8000
; deferred-volume-extra-delay-usec = 0
```


[B]Can anyone see anything in there that would explain sound not starting automatically on loadup ?    it only does load up once out of three or four times


[/B]   thanx 




the second one    > ~/.pulse/daemon.conf   is simply empty

---

### Post by MoreOrLess on 2011-11-11
It's client.conf, not daemonconf (sorry, doing it from memory since i don't use pulse).

---

### Post by shantiq on 2011-11-12
nothing there either blank page:KS

---

### Post by MoreOrLess on 2011-11-12
/etc/pulse/client.conf

---

### Post by shantiq on 2011-11-12
ok moreorless found it


will report on how it changes things:KS

```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for PulseAudio clients. See pulse-client.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; default-sink =
; default-source =
; default-server =
; default-dbus-server =

[B] autospawn = no
[/B]; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; auto-connect-localhost = no
; auto-connect-display = no
```

---

### Post by shantiq on 2011-11-12
does nothing better that i can see so set it back to what it was


Could you explain what the change was supposed to do and how


Thanx    shan

---

### Post by MoreOrLess on 2011-11-12
OP was complaining about pulseaudio running after kill. It was just supposed to stop that..

---

### Post by masuch on 2011-11-13
I compared results from working sound Ubuntu instance with NOT working sound Ubuntu instance on the same computer generated by:
[http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
and found no problem.

functional Ubuntu instance:
[http://www.alsa-project.org/db/?f=3726d50bdda546409148f703d3c0eeda226a074f](http://www.alsa-project.org/db/?f=3726d50bdda546409148f703d3c0eeda226a074f)

NOT functional Ubuntu instance:
[http://www.alsa-project.org/db/?f=0d95bc76ad9b99af5c0a33106f0561d641b22883](http://www.alsa-project.org/db/?f=0d95bc76ad9b99af5c0a33106f0561d641b22883)

Could please somebody help me found where could be the problem ?

thanks in advance.

---

### Post by masuch on 2011-11-13
Hi,

I would like to thank you to all of you who tried to help.
Finally I have found the problem, which was in my default xfce desktop manager - where I switched on:
Session and Startup -> Advanced -> Launch KDE services on startup.

(my bad habits from windows to click on anything what looks interesting)

cheers,
M.

P.S. If is there anybody who understand why it behaves like that (if there is some other KDE sound daemon conflicting current or whatever else it caused), please do not hesitate to share information.

---

