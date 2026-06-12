---
title: "No sound after 13.04 upgrade"
date: 2013-04-27
forum: Multimedia Software
---

### Post by _0R10N on 2013-04-27
Hi! Last night I upgraded my ubuntu 12.10 to 13.04. This morning I found it can't reproduce any sound. The Output tab under sound settings lists "Dummy Output" as the only entry. Any ideas on how to solve this?

Regards!

---

### Post by _0R10N on 2013-04-27
I solved my self by reinstalling alsa-base and audiopulse

# apt-get remove --purge alsa-base pulseaudio
# apt-get install alsa-base pulseaudio
# alsa force-reload

and restarting

---

### Post by Freiberg on 2013-04-27
Despite it freezing on the last command, it worked!  Thank you!

---

### Post by tacopy on 2013-05-01
Previously, I had done a fresh install of 13.04.  Everything worked fine the first day (I had sound) but after the 2nd day, the sound stopped working for seemingly no apparent reason.

i entered the commands above, and now i still dont have sound but i also dont have the volume in the systray on the top right corner.

---

### Post by opulentorca on 2013-05-03
Thanks [**[COLOR=#000000]_0R10N[/COLOR]**]("http://ubuntuforums.org/member.php?u=1052866")

While I also experienced the hang on the third command and neither the test sounds play or the volume icon appears in the notifications area, I am grateful that the sound is working again.

---

### Post by opulentorca on 2013-05-04
To re-acquire the notification icon, you can enter the following in the terminal:
[I]sudo apt-get install indicator-sound
killall unity-panel-service[/I]

Courtesy of sdbillin in
from [http://ubuntuforums.org/showthread.php?t=1871144](http://ubuntuforums.org/showthread.php?t=1871144)

---

### Post by cbenagaraj on 2013-07-07
*after reinstalling  *pulseaudio, eventhough sound is not working

---

