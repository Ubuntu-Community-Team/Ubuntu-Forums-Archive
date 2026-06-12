---
title: "Reverse stereo for speakers only"
date: 2018-09-11
forum: Multimedia Software
---

### Post by ikazama on 2018-09-11
Hi guys!

I'm trying to have stereo channels swapped (LR->RL) for speakers only so headphones are still LR.
I'd love it to be done with alsa or pulseaudio without a hardware adapter.

What is the current state of the problem? Is there any ready-to-go solution? It looks like I can't find any "this is a canonical way to do it" manual on the internets.

---

### Post by QIII on 2018-09-11
I don't see a "problem" here.

Have you thought about just simply swapping the physical positions of your speakers?

---

### Post by SeijiSensei on 2018-09-11
> **QIII said:**
> Have you thought about just simply swapping the physical positions of your speakers?

Or swapping the wires that connect them?

---

### Post by QIII on 2018-09-11
That, too, would seem an effective course of action.

Provided, of course, that the wires are not permanently attached.

---

### Post by ikazama on 2018-09-12
> **QIII said:**
> I don't see a "problem" here.


Have you thought about just simply swapping the physical positions of your speakers?


Swapping the physical position is what I want to do so the control knob (which sits on the the right channel speaker) goes to my left hand.



> **SeijiSensei said:**
> Or swapping the wires that connect them?

**I'd love to do it in software**. Surely stereo reverse for a particular output (speakers in my case) can be achieved easily in a hardware way even without soldering for example using a pair of 3.5mm to RCA splitters like these ones

[IMG]https://i.imgur.com/jI4m8Wf.png[/IMG]

---

### Post by Yellow Pasque on 2018-09-12
[https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index12h3](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index12h3)

---

### Post by QIII on 2018-09-12
Ah.  Left-handed operation does put a different face on your question.

---

### Post by ikazama on 2018-09-12
> **Temüjin said:**
> [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index12h3](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index12h3)

I've already tried that like the following:

0. Edit /etc/pulse/default.pa: add "restore_device=false" option to "load-module module-stream-restore", restart pulse.

1. Set the master sink to 100% volume so the remapped sink will have the same max volume as the master's.

2. Create a remapped sink (my master sink is alsa_output.pci-0000_00_1b.0.analog-stereo which is indexed **1**)

```
pactl load-module module-remap-sink sink_name=reverse-stereo master=1 channels=2 master_channel_map=front-right,front-left channel_map=front-left,front-right remix=no
```

3. Make the remapped sink a default one

```
pacmd set-default-sink reverse-stereo
```


As far new streams play on speakers as reverse stereo. Now I plug headphones and hear reverse stereo as well. To get it back to stereo I do the following:


4. Make the master sink a default one

```
pacmd set-default-sink 1
```

5. Set the headphones port for the master sink (so the headphones volume restores and overrides the master's 100%)

```
pactl set-sink-port 1 analog-output-headphones
```


Now new streams play on headphones as stereo.


To make it switch sinks automaticly I'd have to:

6. monitor "jack/headphone HEADPHONE plug"/"jack/headphone HEADPHONE unplug" acpi events

7. Switch sinks on an event AND move active streams (listed by "pacmd list-sink-inputs") to the new default sink (which "pacmd move-sink-input stream_id sink_id").

8. There are also corner cases like booting with headphones plugged, mby something more.


So after all what I think is: why such a simple task takes so much steps?? Isn't there some canonical way with pulseaudio config only without relying on acpi?

---

### Post by Autodave on 2018-09-12
What I find interesting is that every set of speakers I have ever had or used always had the volume control on the left speaker. Never had a problem.  I wonder why yours are backwards?

---

### Post by ikazama on 2018-09-12
> **Autodave said:**
> What I find interesting is that every set of speakers I have ever had or used always had the volume control on the left speaker. Never had a problem.  I wonder why yours are backwards?

I've got Logitech Z120 and some other speakers. Both have the controls knob to the right channel speaker.

UPD:* I've just dug out a rly old (produced in 1996) speakers in a closet. Same knob location. Lol.*

---

### Post by Autodave on 2018-09-13
> **ikazama said:**
> I've got Logitech Z120 and some other speakers. Both have the controls knob to the right channel speaker.

UPD:* I've just dug out a rly old (produced in 1996) speakers in a closet. Same knob location. Lol.*

Just went through my crates of spare parts: found a total of 6 sets: all with volume control on the left.  That is weird. :-)

---

