---
title: "No sound in OpenAL programs"
date: 2011-12-14
forum: Multimedia Software
---

### Post by WBojangles on 2011-12-14
Hello!

I've been struggling to get OpenAL to work on my Ubuntu 10.04 install for some time now. The problem is usually a game which uses OpenAL, such as:
-Aquaria
-Super Meat Boy [the new Linux release, not on WINE]
-The Binding of Isaac
-Braid

Recently I have tried reinstalling OpenAL [libopenal.so.1.13 rather than libopenal.so.1.12.854] but the problem persists. Among the other solutions I have tried are:
-Uncommenting the "drivers" line in /etc/openal/alsoft.conf
-Setting "drivers" in /etc/openal/alsoft.conf to *only* oss
-Running with padsp
-Creating the file ".openalrc" in my home directory, and writing in it the line *(define devices '(oss))*

I can't figure out what could possibly be wrong after trying so many fixes that relate so closely to my problem. I'm running out of suggestions from internet searches, both general to OpenAL and specifying a problematic game. Any help would be greatly appreciated.

---

### Post by WBojangles on 2011-12-17
Good and bad news:

In the games I mentioned, sound is now working! All of the games I mentioned I can now play with music and all.

The bad news is, I'm not entirely sure why it is working. In my Sound Preferences, I have two options for a sound card output. "Internal Audio Analog Stereo" was selected, and I tried switching to the other, "VT1708/A [Azalia HDAC] ... Analog Stereo" [I'm sure this is relevant only to my setup, but if anyone else has the problem just assume another audio card]. I've had problems trying to use it before, so I've always kept Internal Audio selected - all applications I use from day to day with audio worked fine, except games. Selecting the VT1708 device somehow makes OpenAL-based programs work too.

I don't understand audio hardware at all really. If someone could explain *why* this worked, or what specifically it did in general and for OpenAL, I would be grateful [and help others with similar problems, I hope].

---

