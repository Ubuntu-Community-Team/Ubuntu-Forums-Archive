---
title: "How I fixed Flash and system sound audio problems..."
date: 2008-04-30
forum: Multimedia Software
---

### Post by brodae on 2008-04-30
What fixed everything for me was switching to PulseAudio. 

PulseAudio comes default with Hardy Heron, and I suggest upgrading if you haven't already. To download PulseAudio for Ubuntu, go to "Synaptic Package Manager", and select the following packages to install:

libpulse-browse0
libpulse-mainloop-glib0
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseaudio-module-x11
pulseaudio-utils

This next part I'm not completely sure about, and I only say that because I don't know if you need to restart before doing this because mine was preinstalled. However, my guts says it's possible you may need to restart.

To switch to PulseAudio, go to "System -> Preferences -> Sound"

In the "Sound Preferences" window, switch each device in the "Devices" tab to "PulseAudio Sound Server." Then, switch the Default Mixer Track to the device you want to be able to adjust with the speaker icon on your tray. This icon, by default, is near your clock. This part, however, gets tricky, because PulseAudio uses a myriad of different devices. And, it creates a monitor for each input device. Chances are, you need to either select one of the first devices there. I, personally, selected the PulseAudio version of my default device. It started with "Playback" rather then "Capture."

Note: This affects the device your mouse/keyboard affects with it's volume buttons. 

Make sure you install a graphical user interface for PulseAudio though, like pavucontrol. You can type in sudo apt-get install pavucontrol and that will help. 

Just run pavucontrol in a terminal when you want to run it. Or, you can make a launcher like I did. I recommend it because of the possible need to come back a few times. It's easier then opening a terminal each time you want to use it.

On your desktop, you can right-click your desktop and click create launcher. I did this:

Type: Application
Name: PulseAudio GUI   [The real name is PulseAudio Volume Control]
Control: pavucontrol
Comment: [I left it blank]

You can change the icon easiest if you change it at the creation rather then later. I clicked on the icon of the springboard and chose "gnome-sound-properties.svg"

At this point, you need to restart your computer so that the PulseAudio Sound Server will turn on. So, bookmark this page and restart.

Welcome back! :)

Using PulseAudio, you can use flash, system sounds, and Rhythmbox (for example) at the same time without any problems. When you open the Volume Control, you may need to reassign which sound device is default. Do so, by right-clicking the sound device you want to be the default device, and select "Default." Do this for both the "Output Devices" tab and the "Input Devices" tab. 

Also, you may need to reassign playback streams to the correct audio device.

Do so, by choosing the "Playback" tab and right-clicking the playback stream you wish to reassign. Then, click on the device you want to assign it to.

That should cover it. That got my sound devices to coexist and work with Flash and system sounds, as well as my already working Rhythmbox Music Player.

Some people have found complaints with PulseAudio.

For some people, the audio isn't in sync with video in Flash. People have found it to help when they let it go a few seconds, and then start the video over again. Yeah, it's annoying, but it's better then not having sound, no? I haven't ran into that problem at all, but it's possible you might.

I hope this was of help to anyone who was having problems with their sound.

I'm also going to post this into a new post.

B

---

