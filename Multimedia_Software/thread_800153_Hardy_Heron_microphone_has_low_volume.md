---
title: "Hardy Heron: microphone has low volume"
date: 2008-05-19
forum: Multimedia Software
---

### Post by amdlintuxos on 2008-05-19
[COLOR="Green"][B]ubuntu8.04 32bit, laptop toshiba A100, HDA, external microphone(works fine in mepis7.0)
microfone has low volume, checked in FF3b5, flash audio chat.
I need to speak very loud that person from the other side can hear me
Exist some way to fix this?[/B][/COLOR]

---

### Post by ajgreeny on 2008-05-19
Double click the volume icon in panel and make sure the microphone is set up high enough.  If it isn't showing go to Edit>>Preferences and enable it to show.  Also worth trying the Mic Boost (+20db) switch.

I hope that does the trick.

---

### Post by amdlintuxos on 2008-05-20
sorry for not detaled explanation
> **ajgreeny said:**
> Double click the volume icon in panel and make sure the microphone is set up high enough. 
[COLOR="DarkGreen"]**that was done.**[/COLOR]

[COLOR="Green"]**In additional, if i redirect sound from microfon to headphone (i talk to micro and hear via headphone it's good enought). So it's seems that sound API and sound driver is good, i became to thinking, maybe that is a flash non-free pluging issue. Sorry if wouold ubuntu contain skype aout of box i would checked also with it.**[/COLOR]


 > **ajgreeny said:**
> Also worth trying the Mic Boost (+20db) switch.
[B][COLOR="DarkGreen"]sorry could u so please give me a more detale information about this point. Actually i'm kde user,and really became gnome lover few days ago :D, all applets,API,GUI for driver are new for me. Maybe exist some way to make volume up under terminal, i remember case when i used some kind of this program in mandrake.When standart mixer doesn't help me i somehow made my volume louder

ajgreeny , but still thanks for u reply :)[/COLOR][/B]

---

### Post by pollywog on 2008-11-24
I was having the same problem (low mic volume) and I followed the instructions here [http://ubuntuforums.org/showthread.php?t=843012&highlight=low+volume]("http://ubuntuforums.org/showthread.php?t=843012&highlight=low+volume") to fix it.
Basically install all the pulse audio utilities (in synaptic) ie- manager, volume control, device chooser. Go to System>Preferences>Sound>Audio Conferencing>Sound Capture- change to "pulse audio". Applications>Sound & Video>Pulse Audio Device Chooser- this will start an applet running in the tray, select this applet, go to "volume control", select "input devices" and bump up the volume. It worked for me- Good Luck

---

