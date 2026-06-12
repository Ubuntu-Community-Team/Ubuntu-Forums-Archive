---
title: "Selecting Which HDMI Port to Use for Audio"
date: 2015-03-24
forum: Multimedia Software
---

### Post by matthew79 on 2015-03-24
Hello, I've run into a bit of a problem I was hoping someone out there may be able to help me with or at least point me in the right direction. Here is my setup: two desktop monitors with a set of desktop speakers using the standard stereo jack, I also have a TV across the room I have set as a third monitor so I can pull up videos on the big screen. I have a graphics card with three HDMI ports, two of which are connected to my two desktop monitors, the other, to the TV. I've been trying to things setup to where I could watch a video on the TV with audio of that video coming out of the TV speakers, and everything else out of my normal speakers. I was mostly succussful, I managed to get the video to display on the screen and get its audio to go through HDMI instead of my normal speakers. Except with one problem, the HDMI audio is coming out of my primary monitor on my desktop, and only that monitor. I can not find a way to change which HDMI port is used for audio output (or possibly make it just go to all if I have to, I can just mute the desktop monitor's speakers, I don't use them anyway). All the settings I can find on my computer just give me a single generic "HDMI/DisplayPort" option listed with the other outputs (like the stereo jack). I've been searching for a way to solve this problem, but I can't seem to find anyone else out there who has had this issue before. Any help or insight would be greatly apprieated.


My computer's info:

Kubuntu 14.4 LTS
Desktop enviroment: KDE
Graphics card: VisionTek 900574 Radeon HD 7750 (Offical drivers)
All software and drivers are up to date.

---

### Post by Yellow Pasque on 2015-03-25
So if you connect the TV to the HDMI port that is producing audio, does that work as intended? That's kind of a lame way to do it, but it's probably the easiest way if it works and you don't use the speakers on your other monitors.

Otherwise, this may help: [ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#_pulseaudio_default_device](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#_pulseaudio_default_device)

---

### Post by SeijiSensei on 2015-03-25
Try installing **plasma-widget-veromix** from the repositories, then adding it to the panel by right-clicking on the System Tray and choosing Panel Options > Add Widgets.  This should give you centralized control over all the audio inputs and outputs on your system.  I've taken to removing kmix from my systems with "sudo apt-get remove kmix" and just using the Veromix widget.  If you remove kmix, you'll get a scary warning that you'll also be removing "kubuntu-desktop".  Don't worry, though, that's just the name of a meta-package that includes all the KDE basics including kmix.  All the other applications will be left untouched when kmix is removed.

---

### Post by matthew79 on 2015-04-01
Thanks for the replies, I took some tinkering but I finally got it to work the way I wanted to. For audio, I just switched the cable to the port outputting audio, it just took a lot of work to get it to stop using that port as the primary monitor. Again, thanks for the help.

---

