---
title: "This is getting completely STUPID. NO ANSWER?!"
date: 2009-09-06
forum: Multimedia Software
---

### Post by Marantz on 2009-09-06
There is no way that NOBODY knows how to increase the maximum volume on Ubuntu with laptops.

PCM is all ready all the way up. Everything is maxed out. There has to be a solution not everybody just deals with it. I can barely hear it myself. I'm ready to just say piss on Linux completely. This is exactly why this OS cannot be mainstream. This is why Linux was failing on netbooks. This is just stupid. XKCD said it best...   [http://www.xkcd.com/619/](http://www.xkcd.com/619/)


Now come on, I have all ready tried going to OSS and it is even quieter. There is no config file setting to boost the volume? ANYTHING?!

---

### Post by squenson on 2009-09-06
Two suggestions:

1. A more informative thread title could bring more visitors to your post and a gentler tone may invite more answers;

2. You are using 7.10 according to your signature. Could you update to 9.04, I am sure it has better support for multimedia.

---

### Post by theozzlives on 2009-09-06
Gutsy has reached "end of life" some time ago. Try a more current release.

---

### Post by 3rdalbum on 2009-09-06
Try writing your own sound card driver that solves this problem you complain of. When you've done that and it's been accepted upstream to ALSA, then you can start criticizing the people here who are using their free time to try and help people.

---

### Post by stinger30au on 2009-09-06
check its nothing simple like the laptop volume knob like on toshiba's and the likes is not turned down

try some external speakers as well

---

### Post by Ganymedes on 2009-09-06
> **Marantz said:**
> There is no way that NOBODY knows how to increase the maximum volume on Ubuntu with laptops.
...


Surely there is a way. It is called an amplifier with fitting loudspeakers.

If you prefer to use headphones, please check that the impedance of the headphones is not too high for the headphones output. Typically high-end headphones are not a match with laptops, which are very low-end sound devices. Alternatively, you can use an external USB device, like EMU 0202 USB, which has a proper headphones amplifier.

These are the solutions for regular human beings - also trolls use them.

---

### Post by Marantz on 2009-09-06
First off, I am using the latest Ubuntu, haven't been around much to update my profile.

Second, Why should I have to use external speakers? That takes away from the laptops portability. It is a Lenovo Thinkpad and everything is turned up as high as it goes, and it is still a whisper.


Third, that smartass answer about writing my own drivers is not needed. Not everybody can do this, and to answer a question like that just shows how immature the community is.

I have looked into every solution, and have dumped Linux and went to Windows 7. 

This audio problem and other problems is why I cannot convince people to change to Linux. It will just never happen I guess.

---

### Post by dynamics on 2009-09-06
Have you tried these ?
System --> Preferences --> Sound
Select 'Devices' tab and  select ALSA for 'Sound events' 'Music and Movies' and 'Audio Conferencing'

Next open Terminal and execute the following command

$alsamixer
 You will get the volume controlling GUI. Use 'right/left' keys to navigate between the volume controllers and use 'up/down' keys from your keyboard to change the volumes. 

This may work.

PS: Please don't abuse the forum members.

---

### Post by lildigiman on 2009-09-06
I find your attempt at asking for help to be more so immature than these answers. Next time you have a question do not bring your "opinion" of it being "stupid" in to play, just state the Facts, nobody is here to Rant about how good or bad something is, just how to make it better =]

---

### Post by chkneater on 2009-09-06
Well it could have been something real easy to fix but has just been overlooked or something that may need some work to fix, however we will never know since the OP has given up with out giving much info as to what he has tried and his hardware config.  Most likely it's something stupidly simple like having to mute or unmute one channel in the alsamixer.  He mentioned that PCM is all the way up so most likely he has fooled around with the mixer levels at some point.  Now the next person that has this problem will not know what to do.  This is the price of community software, it's not all "FREE FREE FREE!!"  If something is wrong, report it on Launchpad and look for similar bugs AFTER checking here for help.  This solves your problem (eventually anyways) and saves others from having the problem.  If OP hadn't given up on it this could have been a very good fix for a lot of other people.  He even mentions himself he can't convince people to switch to Ubuntu, maybe because the "community" is getting soft looking for their own answers and not bothering to help when they can.  Nobody is trying to get people to "switch" to Ubuntu.  Frankly I'd be happier off if Windows users stayed away from Ubuntu.  They are typically used to getting quick answers and fixes, while noone here is getting paid to help.

---

### Post by alejaaandro on 2009-09-06
just to comment that actually my dell mini 9 is louder on linux than it was on XP it came with...

---

### Post by fishbulb1022 on 2009-12-14
if you're dual booting, make sure you're volume isn't muted when you shut down windows

---

### Post by lisati on 2009-12-14
> **stinger30au said:**
> check its nothing simple like the laptop volume knob like on toshiba's and the likes is not turned down

try some external speakers as well

+1

---

