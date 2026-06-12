---
title: "Sound problem ubuntu 9.04"
date: 2009-09-08
forum: Multimedia Software
---

### Post by haitham1 on 2009-09-08
[SIZE=3]Hi,

I had installed ubuntu three days ago and faced some difficulties configuring some things but everything went well eventually.  I am new to ubuntu, and linux altogether so bare with me.  

My problem is that there is no sound.  When I installed Ubuntu first, I could hear sounds from the system, like the sound when the desktop first opens, the message alerts from the messenger program,......etc.  Of course having to install plugins, and having to resize the hardrive, plus other things I have been doing the past three days required me to close Firefox and restart it again and on several occasions I shut down and restarted the machine it's self.  It seems like somwhere along that series of events my sound dropped.  I would like to trouble shoot but I don't know where to begin.  I would appreciate some help on the matter. 

Thank you very much.[/SIZE]

---

### Post by StefanSeo on 2009-09-08
Go to System -> Preferences ->Volume Control
Check the sound there, how its set

---

### Post by haitham1 on 2009-09-08
Hi Stephan and thanx for replying.

I went to "*system*" and then picked "*preferences*" but there was no "*volume contro*l" in the menu.  I hope that my OS is not terminally ill.

---

### Post by dynamics on 2009-09-08
System > Preferences > Sound

Go to 'Devices' and toggle the first 3 options to ALSA and the 'Default Mixer Tracks' > Devices : your sound driver (for ex : HDA Intel - STAC92xx in my system)

Open terminal and run

$ alsamixer

Adjust the volumes there and if you are luck you may enjoy music :-)

---

### Post by haitham1 on 2009-09-09
[SIZE=3]Hi Dynamics and thanx for your reply.

In the *"sound preferences*" window i changed the first three options to Alsa.  I am not sure where to find my "*sound driver*" information.  My computer is HP 530 laptop with an Intel Core Due processor.  Can you direct me to where I need to go to find that information?

Thank you much..[/SIZE]

---

### Post by haitham1 on 2009-09-09
[SIZE=3]Hi again Dynamics.. 

I tried that method you adviced but without luck.  Thank you for your help though.  If you have any other ideas I'd be happy to hear them.  

Thanx [/SIZE]

---

### Post by haitham1 on 2009-09-09
[SIZE=3]Dynamics, 

Thanks a whole lot man it works now.  I have a problem though hahahaha, the audio output comes through the built in speakers rather than the USB headset that i use.  The funny thing is that the system does recognize my headphones because when I adjust the volume from the volume control of the headset it appears on my screen, however when i turn it up or down it adjusts the sound comming out of the speakers rather then the headphones..

Any suggestions??[/SIZE]

---

### Post by vijaybilgoji on 2009-10-24
**How to fix ubuntu 9.04 sound problem.**__

sudo killall pulseaudio

sudo alsa force-reload

Make sure System>Preferences>Sound> Sound Capture to ALSA mode.

Restart System.

Enjoy Ubuntu :)

---

