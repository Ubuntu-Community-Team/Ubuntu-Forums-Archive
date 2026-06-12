---
title: "Changing PCM Output to Delta 1010 outputs? How?"
date: 2008-03-07
forum: Multimedia Production
---

### Post by dbsoundman on 2008-03-07
OK, so I have a Delta 1010 installed on my Ubuntu 7.04 machine here. I also have a basic, built-in soundcard. I had been using the built-in soundcard for listening to music, etc, but I'm getting tired of switching around all the time, so I'd like to set the Delta to be the default card for basically all types of sound output. I have tried a few things to get this to work, including setting the Delta to be the output device for music, video, and computer events in the sytem>preferences>sound menu, but it still doesn't seem to make a difference. If JACK is not running I can get the test tone from that dialog to come through the Delta, but that's it. I'm using Amarok to play music back and it's just going to the default soundcard. What do I need to do to make this work through the Delta? Any advice would be appreciated...

Thanks,
Dan

---

### Post by dbsoundman on 2008-03-07
Ok, here's a sort of mini-update that will hopefully shed some light to someone who might be able to help me...

I have some screenshots here of my volume control menus and Envy24 menus for the Delta.

[IMG]http://i200.photobucket.com/albums/aa62/dbsoundman/deltavolumecontrols.png[/IMG]

[IMG]http://i200.photobucket.com/albums/aa62/dbsoundman/deltaroutingsettings.png[/IMG]

The volume controls image shows the various controls and titles for each control when I am dealing with the Delta. One interesting thing of note is if you notice in the generic volume control panel, there is a "Multi" output, then a "Multi 1", etc. If I mute the PCM Out 1 in Envy24, which should correspond to Multi 1, instead, I mute the Multi out. If I do Out 2 in Envy, I get Multi 1 in volume control, etc. I'm thinking something is wrong here.

In the routing view, you can see my output patching options for both controls. What's interesting about the volume control panel is that it lists all the outputs with the same ambiguous title. I'm guessing they go from HW 1 to HW 8 though, because only the first two have the option of being routed to the Digital MIxer, which is the way it's laid out in Envy24.

I have played with all of these settings, trying to find that magical combination, but nothing works. Anyone have a clue as to what is going on here? I seem to think that there's a missing link between choosing a specific PCM output and routing it to the specific delta output, because in the control panel for the generic soundcard, there is no PCM 1, 2, etc.; only PCM. Ideas? Thoughts?

Thanks,
Dan

---

