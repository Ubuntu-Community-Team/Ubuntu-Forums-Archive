---
title: "Amarok commands work pasted in terminal but not in bash script"
date: 2017-10-26
forum: Multimedia Software
---

### Post by accounts0 on 2017-10-26
This is my original script [1] which I thought was working until I discovered it doesn't work in every case.

For example if there's different values from its previous session- a different track in the playlist, its volume isn't 100%,. the window is open- it won't change its volume, hide, or start playing the track the script adds to the playlist. 

So then I started tinkering & found I can successfully execute the commands in a terminal user session, but not from the script, which I edited [2] to try to make it work- but it won't.

As it stands I have to be sure that Amarok is minimized to the system tray, & has its volume at 100% prior to running the script since it doesn't work. I've been using it for months now thinking it was working- maybe it was, & something happened in such a way that I never noticed the change.

Google has troubles similar but the solutions I find are related to specific commands, different than the qdbus ones I use here. Any way I look at it I need help. 

[1]
[http://sebsauvage.net/paste/?96c634eb1f0449de#hcykuIDvH6IWfjJwil6mr1/6EebtZBva8z/gm7JsMUI=](http://sebsauvage.net/paste/?96c634eb1f0449de#hcykuIDvH6IWfjJwil6mr1/6EebtZBva8z/gm7JsMUI=)

[2]
[http://sebsauvage.net/paste/?66a571380e000025#RQZvsS1DtLSU+tCxiq97C4oAbq9tx+QWs4mKxTWkT5s=](http://sebsauvage.net/paste/?66a571380e000025#RQZvsS1DtLSU+tCxiq97C4oAbq9tx+QWs4mKxTWkT5s=)

---

### Post by accounts0 on 2017-11-05
bump

---

### Post by accounts0 on 2017-12-01
bump

---

### Post by uRock on 2017-12-02
Maybe post the outputs within code tags here, so people don't have to click multiple links to get the full picture?

---

### Post by vasa1 on 2017-12-02
> Paste does not exist, has expired or has been deleted.As uRock suggested paste here between code tags. If it's too long, try pastebin.

---

### Post by accounts0 on 2017-12-13
Original:

```
#!/bin/bash
killall amarok
sleep 15
amixer -D pulse sset Master 17%
sleep 5
#exec /usr/bin/amarok --debug -l "/home/user/Music/WebRadio/SomaFM_GrooveSalad.pls"
#exec /usr/bin/amarok -l "/home/user/Music/WebRadio/SomaFM_GrooveSalad.pls"
exec /usr/bin/amarok -l "/home/user/Music/WebRadio/SomaFM_Christmas_Lounge.pls"
sleep 3
qdbus org.kde.amarok /Player org.freedesktop.MediaPlayer.VolumeSet 100
sleep 2
qdbus org.kde.amarok /amarok/MainWindow org.qtproject.Qt.QWidget.hide

```



Current:

"AmarokAutoStartDelayedI.sh"

```
#!/bin/bash
sleep 30
killall amarok
screen -dm sh ~/Scripts/AmarokAutoStartDelayedII.sh
amixer -D pulse sset Master 33%
exec /usr/bin/amarok -l /home/user/Music/WebRadio/SomaFM_Christmas_Lounge.pls
```

"AmarokAutoStartDelayedII.sh"

```
#!/bin/bash
sleep 5
qdbus org.kde.amarok /Player org.freedesktop.MediaPlayer.VolumeSet 100
qdbus org.kde.amarok /amarok/MainWindow org.qtproject.Qt.QWidget.hide

```

---

