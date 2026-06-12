---
title: "Headphones and Speakers have sound"
date: 2014-01-04
forum: Multimedia Software
---

### Post by anneandypearson on 2014-01-04
I have always had this problem - sound comes out of headphones and speakers. I have tried to search forums for help in the past but none has helped me. I thought I would try again. I am trying to follow the following advice from a previous thread:

[COLOR=#000000][FONT=verdana]These instructions got the headphones jacked working like I wanted: When I plug in my headphones the speakers automatically mute, and when I unplug them the speakers come back on.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]1) Open gnome-volume-control[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2) Click on the "Output" tab.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]3) Change "Connector" to "Analog Headphones"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]4) Open gnome-alsamixer[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]5) Turn the "Front" channel up to maximum volume.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]6) Close gnome-alsamixer[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]7) Use gnome-volume-control to adjust volume/mute/unmute.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]If you want both headphones and speakers, open gnome-alsamixer and unmute the "Front" channel.

[SIZE=2]I did not have Volume Control so I installed it - I can see it but it does not open. I click it and I see a grey box for 2 seconds then nothing at all?

Any help really appreciated.[/SIZE][/FONT][/COLOR]

---

### Post by Yellow Pasque on 2014-01-05
Often, the best thing you can do is update to latest driver, especially if running Ubuntu <= 13.04
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)


If that doesn't work, give ALSA info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

