---
title: "skype sound issue's"
date: 2010-10-01
forum: Multimedia Software
---

### Post by tomski on 2010-10-01
yes i know skype on Linux is crap but i have no choice as i now have only Ubuntu installed on this pc & I NEED SKYPE

so with the new version how do i select a particular sound device
i ask because skype only lets me select a specific sound 'platform' (pulseaudio)

i have a motherboard with on-board sound & a USB voip phone (us robotics) and it the usb voip phone i want to use solely for skype

so is there something i can tell pulse audio that i want skype to ONLY use the usb phone or do i have to use the stupid sound preferences to change the system wide device to the usb phone which makes the whole thing a hindrance because i have no idea when someone calls me & when i have to quickly change the settings then turn off music then try to answer the call the person calling has gone!!!


i like to have music playing in the background out of my hifi & the error noises come out of the usb phone as well when this is selected & to be honest it makes having a pc setup with multiple devices pointless and a hindrance

---

### Post by kostkon on 2010-10-01
Install the *PulseAudio Volume Control* utility. Open Skype, start a call, open the volume control and select the *Applications* tab and then move the audio stream of Skype to the device you want. PulseAudio will remember your choice from now on.

And why do you say that it's crap :confused:

EDIT: sorry, I mean select the *Playback* or the *Recording* tab, to set your USB phone as the input and/or output device for Skype.

---

### Post by tomski on 2010-10-02
thnx Koston you fixed it

---

