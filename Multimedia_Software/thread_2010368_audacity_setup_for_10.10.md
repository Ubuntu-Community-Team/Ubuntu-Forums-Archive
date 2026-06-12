---
title: "audacity setup for 10.10"
date: 2012-06-25
forum: Multimedia Software
---

### Post by aparolin on 2012-06-25
greetings all;
i am having probs. with the setup for audacity on ubuntu 10.10.
my review:
i went to applications; ubuntu software center; sound/audio and loaded audacity.

audacity device toolbar shows ALSA pulse for both output/input device
output level slider works; 
but input level slider is grey;
it says "cannot control input level use system mixer"

i am able to listen to internet radio but the recorder doesnt work...
i am stumped
any suggestions? or links to follow.
searched in forums; but there are a lot of different paths to take and not sure which would fit my needs.


much appreciated;
thanx

---

### Post by ajgreeny on 2012-06-25
You need to use pulseaudio-volume-control to do what you want, and it may not even be installed; I can't remember if it is in 10.10.

Look in sound and video menu for it; if it's not there install **pavucontrol** package and open it from the menu.  Now with audacity recording you will see in the Recording tab an ebtry for audacity and in my system I need to set the **Record stream from** to "monitor of internal audio - - -" and also set the capture level and so on in the other tabs.

See my screenshot which may help you more.

---

### Post by aparolin on 2012-06-25
thx aj;
i downloaded only the pulse audio vol control and is part of apps along with audacity.

these are my screenshots

/home/aparolin/Desktop/audacity.png

/home/aparolin/Desktop/pavucontrol -v.png

/home/aparolin/Desktop/pavucontrol -rpng

/home/aparolin/Desktop/pavucontrol -o.png

/home/aparolin/Desktop/pavucontrol -i.png

/home/aparolin/Desktop/pavucontrol -c.png

there were also pulseaudio: 
device choser
manager
volume meter

these were not installed:

what next?

[IMG]file:///home/aparolin/Desktop/audacity.png[/IMG][IMG]file:///home/aparolin/Desktop/pavucontrol%20-v.png[/IMG]

---

### Post by aparolin on 2012-06-25
haha;
need to figure out screenshots....

---

### Post by aparolin on 2012-06-25
maybe this shows screenshots[ATTACH]220240[/ATTACH]

[ATTACH]220241[/ATTACH]

[ATTACH]220242[/ATTACH]

[ATTACH]220243[/ATTACH][IMG]file:///home/aparolin/Desktop/audacity.png[/IMG]

---

### Post by aparolin on 2012-06-25
also:

---

### Post by aparolin on 2012-06-25
and

---

### Post by aparolin on 2012-06-25
many thanx aj;

figured it out;
start playing music to speakers;
open audacity from applications;
push record button on audacity; 
then open pulseaudio vol control from applications;
goto top recording tab, then change box at right to 'monitor of internal audio analog stereo'

bingo
works perfect

---

### Post by mörgæs on 2012-06-25
Good, please mark the thread 'solved'.

Also, 10.10 is out of support. It's recommended to install one of the supported releases.

---

