---
title: "[Solved]MIDI data via MIDIUSB adapter malformed"
date: 2019-01-09
forum: Multimedia Software
---

### Post by LucidNovelty on 2019-01-09
***************************************************************************
Solved/Update:  The MIDI adapter was faulty as in not compliant with MIDI specification. I got another different one and everything works perfect.


***************************************************************************
Running Ubuntu Studio with a Casio CK-900 connected through a MIDI USB adapter I run into a weird issue. I get the MIDI connection to work with any software (LMMS, Qsynt, virtual keyboards etc..) and I can use my Casio to play notes. That is, I can play almost all notes but a good number of them are not registered by any of the applications that listen to the MIDI in. This happens on different computers. I started to debug the MIDI input using Kmidimon and the suspect keys, where not registering). However, I notices the LED on the MIDI USB adapter flashing when I play the unresponsive keys so it looked some signal was coming through. 

Long story short: I started to dump the raw data from the MIDI in device using the command amidi -d -p hw:1,0,0 The keys that actually work show up like this:

90 24 32
90 24 00
90 25 34
90 25 00

Keys that don't work look like this:

90
97
E8

90
97
C0

90
9C
90

9C
C0
90

Somewhere for some keys the lines are split where they shouldn't be. I have no clue, I've been trying to get this work for the better part of today and have not been able to find any hint of what causes this problem. I suspect it's a problem with the Casio's MIDI implementation or that the very cheap MIDIUSB interface I just got is faulty. But then I would expect more intermittent failures and not specific keys behaving differently. 

Hope anyone has a clue what is going on here. 


Thanks in advance!

---

