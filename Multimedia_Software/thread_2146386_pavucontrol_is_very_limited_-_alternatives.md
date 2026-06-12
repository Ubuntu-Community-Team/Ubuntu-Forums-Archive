---
title: "pavucontrol is very limited - alternatives?"
date: 2013-05-18
forum: Multimedia Software
---

### Post by jcoles on 2013-05-18
Running xubuntu 13.04 here. I'm talking about the volume control / sound settings app embedded in the Notification area in the top panel. 
As far as I can tell, this is pavucontrol. Its functionality is rather limited:

[LIST]
[*]Inputs such as Line In and Mic do not display unless something is actually plugged into the jack. (dumb!)
[*]Levels for Line In and Mic cannot be set separately. Set one input level, the other is changed too. (wrong! wrong! wrong!)
[*]User must choose one input (Line or Mic) and one output (speakers or headphone). (These are all separate channels, see alsamixer.)
[*]There is no way to listen to (send to speakers or headphone) the audio from Line In or Mic. (basic functionality missing)
[/LIST]
I can get around some of these limitations with the alsamixer console app. It's crude and ugly, but provides a clearer view of the sound system than the dumbed-down view of pavucontrol. 

Is there a mixer app/package that I can install to have comprehensive view and control of sound resources while retaining the master volume control function on the keyboard and top panel?

---

### Post by CatKiller on 2013-05-18
That's not pavucontrol.

---

### Post by jcoles on 2013-05-19
Starting pavucontrol from the command line, I see it is subtly different to the panel Sound Settings. But still you can choose one input, one output with no ability to monitor inputs like Line In or Mic. I suppose I should be looking for something called a mixer.

---

### Post by CatKiller on 2013-05-19
One of the PulseAudio utilities lets you set up monitoring. Can't remember which at the moment.

If you're doing Serious Business you probably want to be using JACK anyway.

---

### Post by Merrattic on 2013-05-22
Try alsamixer in a terminal

---

### Post by Atitudes on 2013-05-22
Hi, the pavucontrol is rather basic but it adds a lot more options than the "standard" one. If you run alsamixer from the terminal it will be rather "ugly" indeed but if you install the package it will be a lot easier to control, although imo the terminal one is more complete and versatile.

> **jcoles said:**
> Running xubuntu 13.04 here. I'm talking about the volume control / sound settings app embedded in the Notification area in the top panel. 
As far as I can tell, this is pavucontrol. Its functionality is rather limited:

[LIST]
[*]Inputs such as Line In and Mic do not display unless something is actually plugged into the jack. (dumb!) 
[/LIST]

Why do you need to control something that is not plugged in??? It seems dumb to me...

> 


[LIST]
[*]Levels for Line In and Mic cannot be set separately. Set one input level, the other is changed too. (wrong! wrong! wrong!) 
[/LIST]

I am having a lot of trouble with the Line In at the moment but I never had the same issue you refer; having two jacks' plugged the sound options are well separated and if your having trouble the terminal alsamixer does all the work .

> 


[LIST]
[*]User must choose one input (Line or Mic) and one output (speakers or headphone). (These are all separate channels, see alsamixer.) 
[/LIST]

[LIST]
[*]There is no way to listen to (send to speakers or headphone) the audio from Line In or Mic. (basic functionality missing) 
[/LIST]
I can get around some of these limitations with the alsamixer console app. It's crude and ugly, but provides a clearer view of the sound system than the dumbed-down view of pavucontrol. 

Is there a mixer app/package that I can install to have comprehensive view and control of sound resources while retaining the master volume control function on the keyboard and top panel?

Use QJack as mentioned by CatKiller and  I'm sure you will manage to control everything taking into account your referred needs!

Cheers!

---

