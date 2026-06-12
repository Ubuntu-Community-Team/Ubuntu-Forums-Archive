---
title: "No sound until I plug in headphones"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by OrionFyre on 2007-12-29
**NOTE: This has been solved! see last post for details.**
FIRST POST!!!!
*claps with glee and jumps up and down*

First let me say oh how I love Ubuntu. Three years ago I installed Suse (forgot what version) I never got any further than playing and tinkering around and somehow managing to completely destroy my entire mp3 collection (all 50GB) through some act i had no idea what i did... When I started playing something by nirvana it sounded fine then GLITCH and it would be in the middle of some NIN song... oh well :)

Let me tell you just how distraught I was over such a disaster...

I managed to get over it with time (3 years to be exact) and have now downloaded Ubuntu! YAY

I decided to go linux because my new laptop with Vista ate up 10% of my battery booting. I went from a 1.5 hour run time on battery to just shy of 3 hours. Even though nothing i want to do works the first time I love it! learning and doing.

Now on to my problem which really isn't a problem more than an enigma wrapped in a puzzle found within a quandry...

When I boot and login I play around and notice I have no sound. For two days I just went around with no sound and not worrying about why. I had sound while using the Live CD and thought that was wierd. Then it dawned on me when I was using the Live CD I was wearing headphones. So I plug in headphones and I'm suddenly listening to the farting preacher on youtube!!!!!! :guitar:

Then the puzzling quandry part of the enigma occured! I unplug the headphones and from my speakers emanates a loud flatulent reverberation.  :lolflag:

When I shut off the laptop and boot again I have no more sound until i repeat the headphone plug. how can I rectify the need to carry around a pair of headphones?

---

### Post by OrionFyre on 2007-12-29
D'OH

Sony Vaio VGN-CR120E

I'm running Ubuntu 7.10 tell me what other specs you need... and how ot figure them out! LOL

---

### Post by Furat on 2007-12-29
I had the same problem in my Toshiba laptop and when I double click on the volume control I found the "front" was muted .

---

### Post by OrionFyre on 2007-12-29
Nothing is muted

---

### Post by Furat on 2007-12-29
I found that this bug had been reported to Ubuntu Audio team 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132108](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132108)
the guy who report the bug said when he plug and then unplug the headphone it works, try that

---

### Post by OrionFyre on 2007-12-29
> **Furat said:**
> I found that this bug had been reported to Ubuntu Audio team 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132108](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132108)
the guy who report the bug said when he plug and then unplug the headphone it works, try that

Ok, unless I'm missing something on that bug report thats exactly what I've already said. That plugging in and unplugging my headphones makes the audio work. And I don't see anything on there on how to make it work WITHOUT carrying around a pair of headphones, or keeping track of a headphone plug...

????

Thanks for the link to the bug though! at least i know i'm not the only one.

---

### Post by mmb1 on 2007-12-29
Go into a terminal and type "alsamixer", then post the output please.

---

### Post by OrionFyre on 2007-12-29
> **mmb1 said:**
> Go into a terminal and type "alsamixer", then post the output please.

Card: HDA Intel
Chip: Realtek ALC262
View: [Playback] Capture All
Item:

PCM 65/65
Front 100/100
Mic 0/0
ATAPI Mic 0/0
Input So (blank with "mic" floating where the white part of the bar would be)
Input So
Input So

I assume this is what you need.:lolflag:

---

### Post by sstusick on 2007-12-29
I had the same issue, all I did was

in terminal:

> sudo nano /etc/modprobe.d/alsa-base

and add "options snd-hda-intel model=3stack" to the end of the file, and reboot.

After that, my sound was normal again.

Hope this helps!

---

### Post by OrionFyre on 2007-12-29
> **sstusick said:**
> I had the same issue, all I did was

in terminal:



and add "options snd-hda-intel model=3stack" to the end of the file, and reboot.

After that, my sound was normal again.

Hope this helps!

believe it or not! this noob had already tried that surprisingly... saw it somewhere else on another forum. I tried it again just to make sure i hadn't done a typo, and I still have no sound until I plug in headphones. Thanks sstusick!

Still need headphones, keep 'em comming guys.

---

### Post by OrionFyre on 2007-12-30
An update.

I was talking with a friend who had linux on an older laptop a few years ago with the same problem. He cannot recall his hardware or the like but remembers it had to do with the "jack sense" where the device thinks headphones are plugged in (but they aren't) so when you plug them in sound is going there, and when you unplug them the "jack sense" gets set to the proper setting "unplugged" so sound goes to the speakers like they should.

I've pressed him for details and he even took a peek around but nothing rang a bell.

---

### Post by OrionFyre on 2007-12-30
[http://ubuntuforums.org/showthread.php?t=650790](http://ubuntuforums.org/showthread.php?t=650790)

Thanks be to murmel and his delightfully succinct post. The two commands in particular that solved my problem were

```
options snd-hda-intel model=vaio
```
and
```
sudo apt-get install linux-backports-modules-$(uname -r)
```

After a complete reboot i was startled int he silence of the night and in this oh'so dark room by the wonderful Ubuntu drums at the login screen. (WITHOUT headphones)

I am however curious as to wether or not the first line would have worked on it's own. 

Further thanks are due to whose post set me to focus on searching for more options to place in alsa-base

---

