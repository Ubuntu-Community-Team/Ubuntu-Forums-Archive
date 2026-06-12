---
title: "HDA Intel , mIcrophon issues?"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by cast0r on 2007-05-30
Hi,

Ubuntu 7.04 fresh installation and the microphone on HDA Intel card is not working :( Everything else apart of microphone works well.

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

The "Input Source" option in  alsamixer  is missing the "Front MIc" option. Only the "Line" is available.

What information do I need to provide more in order to get help with this  problem?


My previous  distributions (openSUSE,gentoo) didn't have problem at all with this sound card and its microphone in particular, but  all of them used older alsa driver.

Normally I set everything in gnome's sound preferences onto alsa, and set the Input source onto Front Mic and was fine. 
The problem with my current Ubuntu is that the Front Mic option is missing :(

 Kernel wise,in gentoo 2.19.5 I had only ALSA activated with no OSS and hasn't  been using the ESD. Microphone worked perfectly.

openSUSE, 2.6.18.8 with alsa 1.0.12rc1 worked fine too.


Regrads
castor



[UPDATE] --> [SOLVED]

OK. I got it work.:)

Append the "model" option onto the snd_hda_intel modul. my card required the "ref" value. 

For the values you may need referrer to the ALSA-Configuration.txt file. in alsa-kernel/Documentation directory of the alsa-driver tar.

---

### Post by Depressed Man on 2007-05-30
Hi, could you explain more about what you did? I have a similar problem, except line in and microphone are both missing.

---

### Post by cast0r on 2007-05-31
At first I append the "5stack" option. It gave me the "Front MIc", "Mic" and" Line"  but none of which was working:(.

The proper option for ma card is "ref". Although in alsamixer there is only "Line" option for "Input Source" the microphone is working and thats enough for me.



Have a look at the "Manually specify which model you are using" in this how-to: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

