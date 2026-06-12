---
title: "Suddenly can't play sound files"
date: 2009-07-15
forum: Multimedia Software
---

### Post by litlfrog on 2009-07-15
I had sound quality problems on an old computer that I installed Ubuntu 9.04 last week. After some failed attempts, I got OSS installed and running. It worked great for several days, but suddenly this morning I can't play any sound files with any programs. When I try to play mp3s, wav files, or a CD in Rhythmbox or Movieplayer, I get the red circle with a line through it (Movie Player often gives the message "Audio Playback Error.") I did a routine update this morning through Update Manager, but I'm afraid I don't remember what files were changed.

---

### Post by igorzwx on 2009-07-15
really?
I will try now!

---

### Post by igorzwx on 2009-07-15
Rhythbox play mp3s without problems.
Totem plays mp3s too.

I have ALSA here, but it is not used by any app

Perhaps, you are using ALSA drivers for OSS devices.
It was, perhaps, an upgrade in ALSA this days.

Try to remove ALSA, or disable it temporally

I wil try now on other boxes.

---

### Post by igorzwx on 2009-07-15
Everything OK on the old box with OSS4
All players play mp3.

I updated the system, and nothing changed.

Everything is OK here.

Was it an upgrade of the kernal.
modules
Drivers for your sound card?

---

### Post by litlfrog on 2009-07-15
I don't know, unfortunately. Is there a way to see what the most recent updates were? The big thing I saw was an update to sun-java6-bin. Is it safe to remove ALSA? I thought some components of it were necessary. If not, I'm happy to dump it since sound quality is far better with OSS.

---

### Post by igorzwx on 2009-07-15
This might be the difference:
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

### Post by igorzwx on 2009-07-15
I has java run time in Medibuntu!

Make it multimedia ready!

---

### Post by litlfrog on 2009-07-15
The steps from that website didn't make a difference. I didn't figure it was a codec problem since I can't even play a store-bought audio CD. When I go to System -> Preferences -> Sound, I can't even hear test sounds when I click the Test button.

---

### Post by litlfrog on 2009-07-15
Well, here's the problem! Here was my output of aplay-l last week.

> **** List of PLAYBACK Hardware Devices ****
card 0: nForce [NVidia nForce], device 0: Intel ICH [NVidia nForce]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: nForce [NVidia nForce], device 2: Intel ICH - IEC958 [NVidia nForce - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0 

Annnnd here's my output today: 
> aplay: device_list:217: no soundcards found...


So, any guesses as to how to get the onboard sound working again?

---

### Post by igorzwx on 2009-07-15
Clear it should not find it you have OSS4 installed

you should use 

ossplay

try 

osstest

I want to see output of these commands:

ossmix

ossinfo -v3
read pdf manual for OSS4,
hope you downloaded it with deb


this file (if you have) should be renamed
*/etc/asound.conf*

---

### Post by igorzwx on 2009-07-15
ossmix

ossinfo -v3

output of these 2 commands

---

### Post by litlfrog on 2009-07-15
Hah! Problem solved.

I initially got an input/output error from the ossmix command. I'd already restarted, but I tried restarting one more time and everything is working fine. I'm glad to know those oss commands. Sorry for the false alarm and thanks for the help.

---

### Post by igorzwx on 2009-07-15
I am happy to hear that you can relax now.
The pdf manual can be downloaded in the same place as deb.
Not much to read 1 page.

execute these commands:

man ossrecord

man ossplay

and other too.

Hope you use 

ossxmix


By the way, I have here Ekiga, which was not tested yet

[SOLVED: How do I make Ekiga work with OSS4?]("http://www.4front-tech.com/forum/viewtopic.php?t=3171&start=0&postdays=0&postorder=asc&highlight=")

[http://www.4front-tech.com/forum/viewtopic.php?t=3171&sid=fcca80bb5c0aba6e711535756774162c](http://www.4front-tech.com/forum/viewtopic.php?t=3171&sid=fcca80bb5c0aba6e711535756774162c)

One Ekiga is already tested (OK)
But I would like to test another one too.

---

