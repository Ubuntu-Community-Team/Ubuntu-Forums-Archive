---
title: "Audio Disabled at Startup"
date: 2009-05-27
forum: Multimedia Software
---

### Post by dadrivr on 2009-05-27
I am running Xubuntu 9.04 and whenever my computer starts up, my sound is disabled and I have to go into Mixer to re-enable the audio devices.  The sound works, but it is a pain to have to configure it every time I boot up.  Any help would be greatly appreciated.  Thanks!

---

### Post by pmcchapman on 2009-06-01
dadrivr - I have just switched from ubuntu to xubuntu and have had the same issue. There is a workaround by CyrusCT located here: [https://answers.launchpad.net/ubuntu/+question/68564]("https://answers.launchpad.net/ubuntu/+question/68564"). (NB: you will need to open Thunar as root using the terminal in order to do stage 2.)

1.) Manually adjust the mixer settings to something that is a good default for your audio needs. These settings will be loaded every time you restart your computer.

2.) Change the file permissions for /var/lib/alsa/asound.state to enable read/write access for the group/others (open the folder in Thunar, then right-click the file, select properties, and go to the Permissions tab). If you don't do this, then the next step will give you a permission denied error.

3.) Open up a terminal and enter the command "alsactl store" (without the quotes). This stores your mixer settings in /var/lib/alsa/asound.state for later use.

4.) From The Xubuntu/Xfce menu, go to Settings and open Sessions and Startup. Go to the Application Autostart tab and click the Add button.

5.) Enter the command "alsactl restore" (without the quotes) and the name and description of your choice. This causes the "alsactl restore" command to automatically run when you start your computer. The command restores you mixer settings from /var/lib/alsa/asound.state where you saved them earlier.

---

### Post by Dean Crocker on 2010-02-16
Sadly, this advice disabled sound completely for my particular situation (Sony VAIO VGN-FZ340E; xubuntu Linux version 2.6.31-20-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010
All looks good. No audio.
Attempting to revert...

---

### Post by VertexPusher on 2010-02-16
Every time PulseAudio starts up, it "resets" ALSA's mixer settings. Unfortunately PulseAudio's idea of a default volume setup sometimes conflicts with reality. In my own case, it mutes the master volume channel.

Since PulseAudio has many other unresolved bugs, I recommend to uninstall it. You can do this by entering the following commands:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```
You can revert these changes at any time by entering this command:
```
sudo apt-get install ubuntu-desktop
```
This will bring PulseAudio back.

---

### Post by garvinrick4 on 2010-02-16
Audio mute fix
Works everytime for me, 
This issue may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore


Now set audio where you like and log-out on log-on to make
sure of fix.

---

