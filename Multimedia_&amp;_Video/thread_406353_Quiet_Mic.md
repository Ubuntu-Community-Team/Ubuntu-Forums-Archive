---
title: "Quiet Mic"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by Pru on 2007-04-10
I know there's been alot of threads about quiet microphones in ubuntu, but people have always answered them by saying check the volume controls, this is not the problem in alot of cases including mine.

I need to find a way to make the recording volume of my microphone loud enough to actually use skype on ubuntu, at the moment I have to have the microphone almost in my mouth for the other person to hear it, this is also the case in other programs such as audacity.

If there is no fix for this bug, can someone tell me a soundcard/configuration that would definately work? I need my sound to work, I don't care if it means buying a new sound card.


Hope someone can help

---

### Post by aidanr on 2007-04-10
make sure capture and microphone are up and mic boost +20db is checked

---

### Post by Pru on 2007-04-11
idk where the mic boost is meant to be, but I said that I've checked everything in the volume controls, put all the mic inputs on full etc

---

### Post by aidanr on 2007-04-11
it's under switches, hit the little arrow that says show switches, it makes a big difference

---

### Post by Pru on 2007-04-11
There is no mic boost under switches, I have all the boxes checked in preferances

[IMG]http://img.photobucket.com/albums/v497/Prulie/Screenshot.png[/IMG]

---

### Post by aidanr on 2007-04-11
:-k go to edit -> preferences and make sure mic boost is checked, like [this]("http://img218.imageshack.us/img218/6812/via8237alsamixercz4.jpg")?

---

### Post by Pru on 2007-04-11
I don't have a mic boost option in there
[IMG]http://img.photobucket.com/albums/v497/Prulie/Screenshot-via8237alsamixercz4.png[/IMG]

---

### Post by aidanr on 2007-04-11
ok, what soundcard do you have?

---

### Post by Pru on 2007-04-11
It's built into my motherboard, it's a 'Realtek ALC885' but it only says that next to the OSS mixer, the alsa mixer says 'HDA Nvidia' I also have a X-Fi Xtreme Music in this computer but I haven't got that to work with linux

---

### Post by aidanr on 2007-04-11
well this is in the changelog for the latest alsa "- hda-codec - Missing Mic Boost on Realtek ALC882/883" not sure if the same applies for the 885 but it might be worth downloading and compiling the latest alsa from [http://www.alsa-project.org](http://www.alsa-project.org)

i don't really have any other ideas:-?

---

### Post by Pru on 2007-04-17
I tried to get the latest alsa drivers working but I couldn't do it, i read the instructions becaues I wouldn't know what to do and they kept refering the files that I couldn't find.

I'm now trying a differant sound card but still having no luck, this one has the Mic Boost but I still get almost no sound on Skype

---

### Post by p.herewini on 2008-02-13
I have the same problem, any resolution?

---

### Post by jii on 2008-02-23
I've had the exact same problem as Pru, but now it's solved thanks to Aidanr. What really made the difference was the "Capture" option.

I got to the Volume Control via double-clicking on my speaker icon.
I then clicked on Edit -> Preferences. 
I checked Mic Boost (+20dB), Microphone Capture, and Capture.
Back in the Volume Control window under the new Recording tab I turned Capture all the way up. 
Under the Switches tab I checked Microphone Capture and Mic Boost.
Under the Playback tab Microphone was already all the way up.
My microphone input is now working properly in Audacity and Skype.

Thanks Aidanr! I hope the rest of you get it working soon.

---

