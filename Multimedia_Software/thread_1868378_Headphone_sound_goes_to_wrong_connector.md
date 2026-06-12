---
title: "Headphone sound goes to wrong connector?"
date: 2011-10-24
forum: Multimedia Software
---

### Post by TomCatFort on 2011-10-24
I had perfectly working audio in 11.04, but when I upgraded to 11.11 I got a problem. When I plug in a headphone, I get no sound from it. 
Then I did these steps to find the problem:
 - Removed headphone from jack. (sound comes from speaker).
 - Opened system settings, went to sound, output tab. Connector says "Analog Speaker".
 - Plug in headphone. Connector switched to "Analog Headphone" and sound goes away.
 - Manually switched it back to "Analog Speaker". Sound comes from the headphone as it should have been.

But I have to do this every single time I plug it in.

**Here is some info of my laptop:**
Type: Fujitsu Siemens AMILO Xi3650
Sound card: HDA-Intel.

/proc/asound/pcm: (from alsamixer)
[INDENT]00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-03: ALC888 Digital : ALC888 Digital : playback 1[/INDENT]

---

### Post by drdnl on 2011-11-02
Same, same workaround as well. 
(though this is the first time I notice I need a workaround)

Here is some info of my laptop:
Type: HP 8740W
Sound card: HDA-Intel.

/proc/asound/pcm: (from alsamixer)

00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 1

Laptop handles the internal switching just fine, any way of disabling the 'connector' switching? IE: 'keep output set to analog speakers'

---

### Post by Wbbswonder on 2011-11-02
I have excactly the same problem after upgrade with exactly the same workaround. I have filed a bug. Please go and click this bug affects you on Launchpad to raise its importance 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882170](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882170)

it seems to affect many users on many systems.

---

### Post by vangop on 2011-11-02
I had the [same problem]("http://ubuntuforums.org/showthread.php?p=11394884").
It appeared and vanished by itself.

---

### Post by vangop on 2011-11-03
I was playing with ubuntu/kubuntu/xubuntu 11.10 on the same laptop.
This problem happens in ubuntu/xubuntu, but in kubuntu it works like a charm - not only the output is directed to speakers/headphones correctly, but also the mic jack/internal mic are switched properly.
I'm noob at linux sound, but someone with more experience might shed some light on it.

ps in xubuntu the mic jack/internal mic are switched properly as well, but not in ubuntu - had to manually switch it all the time.
Also found [this thread]("http://www.linuxquestions.org/questions/ubuntu-63/no-sound-through-to-headphones-with-intelhda-892166/") - you may try, but it doesn't work for me (ubuntu/xubuntu)

---

