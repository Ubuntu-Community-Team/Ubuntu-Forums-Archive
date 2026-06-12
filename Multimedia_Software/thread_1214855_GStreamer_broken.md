---
title: "GStreamer broken"
date: 2009-07-16
forum: Multimedia Software
---

### Post by Zyrshnikashnu on 2009-07-16
All of my GStreamer apps (Totem, Banshee, etc) have ceased functioning properly. Totem plays back video at only a few frames per second and plays no audio and Banshee will not play music. Before I installed the xine backend, Amarok also did not play music.

This started just a few days ago. I'm not sure what I did to change it. The only major change I can think of is adding the kubuntu-experimental and kubuntu-backports repositories to my sources.list so I could upgrade Amarok and Konversation.

Any ideas on where to start?

---

### Post by vinutux on 2009-07-16
downgrade all gstreamer plugins to jaunty fix your problem

for that open synaptic select all gstreamer plgins P**[COLOR="DarkGreen"]akage menu>Force version[/COLOR]** and select to jaunty version and apply


.

---

### Post by Zyrshnikashnu on 2009-07-16
A simple restart fixed it, oddly enough. Now I look like an alarmist. ;)

I'll keep the forced version trick in mind, though.

---

### Post by Zyrshnikashnu on 2009-07-16
SCRATCH THAT

It regressed again. I checked Synaptic for downgrades, but I only have the current versions installed, anyway. Looks like GStreamer was unaffected by the KDE upgrade.

Another thing I noticed: This problem seems to go hand-in-hand with an issue wherein closing a Firefox tab with a Flash video open causes the browser to lock up.

---

### Post by jetta on 2009-07-16
> **vinutux said:**
> downgrade all gstreamer plugins to jaunty fix your problem

for that open synaptic select all gstreamer plgins P**[COLOR="DarkGreen"]akage menu>Force version[/COLOR]** and select to jaunty version and apply


.

hi vinutux, im newbie here, i had the same problem too with amarok, i want to follow the step that u are telling us, but can u tell me the step by step to  do 'force version'. i select gstreamer plugins then open the package menu but the 'force version menu' still cant be selected.
thanx in advance and sorry for my bad english.

---

### Post by vinutux on 2009-07-17
> **jetta said:**
> hi vinutux, im newbie here, i had the same problem too with amarok, i want to follow the step that u are telling us, but can u tell me the step by step to  do 'force version'. i select gstreamer plugins then open the package menu but the 'force version menu' still cant be selected.
thanx in advance and sorry for my bad english.

[B][COLOR="DarkGreen"]Force Version fix is only for that people who installed or upgrade gstreamer plugins from un-official repos.... like mediubuntu.
[/COLOR][/B]

upgrade to some new apps from thirdparty sites or from PPA causing installing diffrent gstreamer versions...that broke stable workable gstreamer system..if you are not installing anything from other repos this fix is not for you....you have some other problems.

Anyway make is clear.....give more infos about your problem help us to fix it........:P

---

### Post by jetta on 2009-07-17
hi gus, i've fix my problem with amarok. fyi check this thread..
[http://ubuntuforums.org/showthread.php?t=1138252&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1138252&highlight=amarok)
cheers..

---

### Post by jetta on 2009-07-17
> **vinutux said:**
> [B][COLOR="DarkGreen"]Force Version fix is only for that people who installed or upgrade gstreamer plugins from un-official repos.... like mediubuntu.
[/COLOR][/B]

upgrade to some new apps from thirdparty sites or from PPA causing installing diffrent gstreamer versions...that broke stable workable gstreamer system..if you are not installing anything from other repos this fix is not for you....you have some other problems.

Anyway make is clear.....give more infos about your problem help us to fix it........:P

thanx for ur explaination:)

---

### Post by vinutux on 2009-07-18
> **jetta said:**
> thanx for ur explaination:)

welcome.........bro :D

---

