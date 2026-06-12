---
title: "[SOLVED] [How-to] Control both headphone and speaker volume from laptop buttons, etc"
date: 2008-12-07
forum: Multimedia Software
---

### Post by m-p{3} on 2008-12-07
I am a relatively new user of Ubuntu 8.10 (been testing Ubuntu since 6.10), and I faced some little problems that bugged me (probably some default settings that I don't feel right).

First of all, I currently use a test system (HP compaq nc6000) on which I explore the functionalities. When I plugged in my headphones to quietly listen to music, I found out that the speakers were still working while they were plugged, which could potentially disturb people when used in a library ;).

And by the way, I'm currently hooked on 8.10. The OS is getting very user-friendly in overall :).

**Auto-mute speakers when headphones are plugged**

[LIST]
[*]Go into the *Volume control* ([img]http://img376.imageshack.us/img376/4599/audiovolumehighvi8.png[/img]) applet by double-clicking on it.
[*]Click on *Preferences*
[*]Check the entry *Headphone Jack Sense*
[*]Press Close
[*]Click on the new tab *Parameters*, and check the entry *Headphone Jack Sense*
[/LIST]

At that point, when you will plug headphone in the audio jack, the laptop will system will automatically mute the speakers.

**Simultaneously control the volume of both speakers and headphone simultaneously with the laptop's buttons**

[LIST]
[*]Right click on the *Volume control* ([img]http://img376.imageshack.us/img376/4599/audiovolumehighvi8.png[/img]) applet
[*]Go in the *Preferences* menu
[*]Hold down the *Ctrl* key, and click on both entries *Main volume* and *Headphone* to make them both highlighted.
[*]Take note of the entry in the combo-box (mine is *Intel 82801DB-ICH4 (Alsa mixer)*)
[*]Press Close
[*]Go in *System* -> *Preferences* -> *Sound*
[*]On the last combo-box, select the same entry seen earlier (ie *Intel 82801DB-ICH4 (Alsa mixer)*)
[*]Hold down the *Ctrl* key, and click on both entries *Main volume* and *Headphone* to make them both highlighted.
[*]Press *Close*
[/LIST]

From there, if you press the buttons on the laptop to increase or decrease the volume, it will now affect both the speakers and the headphones.

I hope this can help new users who might face this issue, and feel free to leave comments if there is something that should be added or modified.

---

### Post by m-p{3} on 2008-12-09
After some testing with another laptop at the office, I've concluded the issue to be hardware-specific to the HP Compaq nc6000 I was initially using.

Can the thread be moved to the Hardware & Laptops section for better categorisation?

---

### Post by vtired on 2008-12-14
I have exactly the same problem with a HP Compaq laptop. In the HP support page they give they suggest to those with the problem (that seems common with their product) to dowload and install a given driver (that means the problem is a software one). But they only have drivers for vista and XP. Could there be a way of using that window driver in ubuntu?

---

### Post by m-p{3} on 2008-12-15
Actually I think it's just a problem with the default configuration of the drivers on the installation disk. The options are all there and work fine, but they are just not set as they should.

---

### Post by kartz on 2009-02-18
Actually my problem was i cannot able use the headphone and speaker simultaneously.i ve three jacks at the back 1,1,1 for speaker,headphone,mic
i ve enabled all the options in the volume control n preferences too still headphone is not working
if i connect the headphone to the speaker jack it s working perfectly
plz help me out to overcome this problem

thanks

---

### Post by mathisonej on 2009-02-18
I don't have a selection called 'headphone jack sense'. Am I missing something obvious?

---

### Post by m-p{3} on 2009-02-18
After some testing on different laptops, the Headphone Jack Sense feature seems to be specific to the HP Compaq nc6000 model. I renamed the thread to avoid any confusions.

---

### Post by claytronic on 2009-03-29
> **m-p{3} said:**
> 
**Simultaneously control the volume of both speakers and headphone simultaneously with the laptop's buttons**

[LIST]
[*]Right click on the *Volume control* ([img]http://img376.imageshack.us/img376/4599/audiovolumehighvi8.png[/img]) applet
[*]Go in the *Preferences* menu
[*]Hold down the *Ctrl* key, and click on both entries *Main volume* and *Headphone* to make them both highlighted.
[*]Take note of the entry in the combo-box (mine is *Intel 82801DB-ICH4 (Alsa mixer)*)
[*]Press Close
[*]Go in *System* -> *Preferences* -> *Sound*
[*]On the last combo-box, select the same entry seen earlier (ie *Intel 82801DB-ICH4 (Alsa mixer)*)
[*]Hold down the *Ctrl* key, and click on both entries *Main volume* and *Headphone* to make them both highlighted.
[*]Press *Close*
[/LIST]

From there, if you press the buttons on the laptop to increase or decrease the volume, it will now affect both the speakers and the headphones.


Thanks! The second part of your post solved the dual control problem I've had with my Dell Latitude D400. Now the volume controls above the laptop keyboard control the headphones as well as the master.

---

### Post by m-p{3} on 2009-03-29
Nice!

Good to know that my problem could also affect other laptop brands and models and that it can be fixed :)

---

### Post by claytronic on 2009-04-25
Quick update...

Just used the same second set of steps again successfully on my D400 for a fresh install of 9.04 Jaunty.  Thanks again, m-p{3}.  :guitar:

---

### Post by m-p{3} on 2009-04-26
I'm just wondering how this fix could get integrated into the official distro, or somehow detected/fixed automatically when using one of these laptop models?

---

### Post by FirstByté on 2009-08-17
> Quick update...

Just used the same second set of steps again successfully on my D400 for a fresh install of 9.04 Jaunty. Thanks again, m-p{3}.

Sadly, It seems there's something I'm not doing right to achieve this 'Mute' capacity on my:
[I]
[B]DELL Studio 14
Intel ICH8 Audio card (HDA Intel Alsa)
Ubuntu 9.04 Jaunty Jackalope[/B] [/I]

to work.

**I need some privacy :(** I can't listen to my music in public ](*,)

---

### Post by manojendu on 2010-05-12
Hi
I am using Dell Vostro 1014.
Ubunto 10.04
This problem persisted with all the various version of Ubuntu through 8.04 to present 10.04, and the solution provided doesn't work for me (unfortunately so) because the 'preferences' in my volume control have only the options Master and PCM, it doesn't have any control for Headphone jack or any such thing. I've tried Kmix but still the situation is the same. I've tried Alsamix and that has absolutely no effect on the sound system for my notebook.

Please help.

---

### Post by supergreatbirdman on 2012-01-09
i am in the same boat.
sony vaio using maverick 10.10
"sound preferences" lacks any such check box to disable speakers while headphones are plugged in.
Certainly there must be an easy fix for this in the terminal perhaps?

---

