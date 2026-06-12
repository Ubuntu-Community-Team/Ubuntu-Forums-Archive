---
title: "Guide: How to replace Pulseaudio with ALSA and Set it up"
date: 2011-02-23
forum: Multimedia Software
---

### Post by SotaSystems on 2011-02-23
Okay, so here we're making a little guide on how to clean your system from pulseaudio and replace it with ALSA and how to set it up a little.

This has been tested on Ubuntu 10.04 LTS i386 and Ubuntu 10.10 amd64. Both have been confirmed to work great.

[COLOR=Red]Note: From this point on you're entirely on your own if something ends up in an malfunction. If damages to the system or hardware occur I won't be responsible for this.[/COLOR]

There will be two guides in this. The first guide explains how to remove the existing sound server (in our option pulseaudio) with Alsa. The second explains how to use alsa without actualy removing pulseaudio (for temporary use or whatever reason you like)1st Guide -> Replace Pulseaudio with Alsa and set it up:

First, we begin by removing pulseaudio from the existing system->
Open a Terminal (Ctrl+Alt+T)
Enter this:
> sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio And enter your password if promted and proceed.
(This removes Pulseaudio from the system.)

Next, enter this:
> sudo apt-get autoremove (This cleans the system from unused and unnecessary packages.)

Next we want to get some Alsa packages.
> sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui (This gets some of the Alsapackages we will need. (If you didn't have this already.))

Next, enter this:
> sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer (This gets some libraries we will need later.)

Now reboot, or enter this:
> sudo reboot (This will restart the system.)

After rebooting, again open a Terminal (Ctrl+Alt+T) and enter:
> gstreamer-properties (Opens the multimedia configuration application.)

Select ALSA from the dropdown if not already.

As you probably noticed, there is no panel icon for sound anymore and hotkeys don't work, so we will fix this little problem like so:
Open a Terminal (Ctrl+Alt+T), enter:
> sudo apt-get install python python-notify python-gtk2 python-alsaaudio python-eggtrayicon (This gets some python libraries we will need later.)

Then enter:
> wget [http://howto.blbosti.com/files/alsa/alsa_mixer_applet_1.1.tar.gz](http://howto.blbosti.com/files/alsa/alsa_mixer_applet_1.1.tar.gz) (This gets tools for the icon tray and the hotkeys.)

Next we want to extract this package. To do so, enter:
> sudo tar -C /usr/local/bin/ -xzvf alsa_mixer_applet_1.1.tar.gz (Extracts the package to /usr/local/bin/ .)

Next we need to make some of the extracted files executable, in order to make them executable, enter this:
> cd /usr/local/bin (Changes to that directory.)
> sudo chmod +x alsa* (Makes all files beginning with 'alsa' executable.)
> sudo chmod +x volbar.py(Makes volbar.py exectuable, so python can run it.)

Now we want the Alsa tools and the tray icon to boot at startup.
Go to System->Preferences->Startup Applications and add this:
> Name: Volbar
Command: /usr/local/bin/volbar.py> Name: alsavol
Command: /usr/local/bin/alsavol.pyFinaly, let's make the python plugin work with gstreamer:
> sudo gedit /usr/local/bin/volbar.py (This opens the file in the editor so you can edit it.)

Find the line 97 and replace xfce4-mixer to gnome-alsamixer:
> subprocess.Popen("gnome-alsamixer") (Replaced Line.)

Now to the hotkeys:
Go to  System->Preferences->Keyboard-shortcuts and add:
> Name:      ALSA Volume mute
Command:   /usr/local/bin/alsa_master_mute> Name:      ALSA Volume down
Command:   /usr/local/bin/alsa_master_down> Name:      ALSA Volume up
Command:   /usr/local/bin/alsa_master_up[/FONT]Then click on Disabled in the second column and map your hotkeys for these actions.
Reboot or enter:
> sudo reboot (This reboots the system.)

2nd Guide -> Use ALSA without removing Pulseaudio:

You can use ALSA over pulseaudio without removing it, to do so simply end it's server and prevent it from automatically restarting:
Enter this in a Terminal (Ctrl+Alt+T):
> echo autospawn = no|tee -a ~/.pulse/client.conf && killall pulseaudio

Then go to
System->Preferences->Startup Applications and add this:
> Name: Pulseaudiokill

Command: killall pulseaudio[/FONT]You will need the Alsa packages for also to actualy work, for a minimal or if you don't have alsa, you can enter this:
> sudo apt-get install alsa alsa-base[/FONT]Then enter:
> gstreamer-propertiesAnd select ALSA from the dropdown.

Now you can always enter
> alsamixerIn a terminal to control the Volume.

This is useful when you temporarily want to switch to alsa.

If you want to go back to Pulseaudio, do this:
Go to

System->Preferences->Startup Applications and delete this entry (The custom one you previously made):
> Name: Pulseaudiokill

Command: killall pulseaudioThen go to your home folder and make hidden files visible (Ctrl+H)
and go to .pulse and open the file client.conf and remove the entry
> killall pulseaudio

---

### Post by GlasgowPete on 2011-02-26
Thanks a lot. I didn't think I was ever going to get my volume back.

---

### Post by colobix on 2011-04-15
Thanks a lot.
I didn't understand the hotkey part so I have to do it manually, but it's way better than nothing.
The up, down and mute doesn't work for me, any suggestions?
Are there maybe other alternatives than the 3 alsa master files I can use to do these things?

---

### Post by Yellow Pasque on 2011-04-16
> **colobix said:**
> Thanks a lot.
I didn't understand the hotkey part so I have to do it manually, but it's way better than nothing.
The up, down and mute doesn't work for me, any suggestions?
Are there maybe other alternatives than the 3 alsa master files I can use to do these things?
[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
After you get updates from there, you can add the old mixer to your gnome panel and media keys will work. Just don't install the libcanberra from there (that's for OSS4 users).

---

