---
title: "How I got JACK to work with PulseAudio (HowTo)"
date: 2012-03-19
forum: Multimedia Software
---

### Post by Splooshie123 on 2012-03-19
Running PulseAudio through JACK was very unstable for me. QJackCtl would crash half of the time when trying to connect to PulseAudio.

After some mucking about, I found out how to make it stable. So far, I have experienced ZERO crashes with my new settings (except that one time when Skype had a memory leak and crashed the system). I am posting this tutorial because I want to find out if this will work for others. My explanations are based on my observations. If you know the technical explanation, post in this thread and I'll try to add it to the tutorial. I am running Lucid so I don't know if this tutorial will work for later versions. Also, I don't know whether Jack and Jack2 are similar enough for this to work on the latter.

This tutorial uses content from [COLOR=Blue]***_[this Wiki page]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#PulseAudio_through_JACK_the_new_way")_***[/COLOR]. However, this tutorial has been modified because the I found the original article's instructions slightly incomplete. I don't have an account on that site so if you do, I encourage you to update it.

[COLOR=Red]_**WARNING: THE FOLLOWING INSTRUCTIONS INVOLVE  SETTING THE VOLUME TO MAXIMUM. PLEASE PAUSE/MUTE/QUIT ALL APPLICATIONS THAT PLAY SOUNDS  (SUCH AS MEDIA PLAYERS) BEFORE USING THE FOLLOWING SETTINGS. **_[/COLOR]_**[COLOR=Red]AFTER PRESSING "START" IN QJACKCTL, LOWER YOUR VOLUME NORMALLY.[/COLOR]**_
[COLOR=Red][U][B]       
TAKE OFF YOUR HEADPHONES. YOU'LL GO DEAF IF YOU FORGET TO LOWER YOUR VOLUME SETTINGS AFTER PRESSING "START".[/B][/U][/COLOR]

** You have to install JACK in the first place, so...**
```
sudo apt-get install qjackctl
```QJackCtl is a GUI for jackd.

** Now you need to install some modules for connecting PulseAudio to JACK:**
```
sudo apt-get install pulseaudio-module-jack pulseaudio-utils
```Now open up QJackCtl and click Setup.

In the configuration window that appears, look for **Force 16 bit** and tick the box.
You can try unticking it later if you get problems.

Move to the **Options** tab.
You will see a list of scripts that will run at specified times. Most are empty by default.
Use these settings:

** Execute script on startup:**
```
amixer set Master 100% ; a2jmidid &
```"*amixer set Master 100%*" sets the volume to maximum because for some reason the max volume for the virtual JACK output (more on that in a moment) is your current volume before starting jackd. "*a2jmidid &*" starts a program in the background. I think it is some sort of bridge for connecting ALSA and JACK MIDI ports. I had it by default so I left it alone.

** Execute script after startup:**
```
sleep 1 ; pactl load-module module-jack-sink channels=2 ; pactl load-module module-jack-source channels=2 ; sleep 1 ; pacmd set-default-sink jack_out ; pacmd set-default-source jack_in
```The *"pactl load-module module-jack-sink channels=2 ; pactl load-module module-jack-source channels=2" *command creates the virtual JACK input and output devices.

The problem with this setup is that it seems the modules are being loaded too soon after starting the jackd server. The solution is* "sleep 1"*. This makes sure that the jackd server has enough time to start up properly. Without it, QJackCtl will crash about 50% of the time when loading the modules.[I]

"pacmd set-default-sink jack_out ; pacmd set-default-source jack_in" [/I]sets the new virtual JACK input and output devices as the defaults (it will revert to normal when JACK is shut down). Again, there seems to be a problem where the commands are being run too early. Again, the solution is "*sleep 1*". Without it, you would have to enter the commands *twice* before they would take effect.

** Execute script on shutdown:**
```
SINKID=$(pactl list | grep -B 1 "Name: module-jack-sink" | grep Module | sed 's/[^0-9]//g') ; SOURCEID=$(pactl list | grep -B 1 "Name: module-jack-source" | grep Module | sed 's/[^0-9]//g') ; pactl unload-module $SINKID ; pactl unload-module $SOURCEID ; sleep 1
```Just to be tidy, this set of commands unloads the PulseAudio-JACK modules before shutting down the jackd server. Also, the "*sleep 1*" at the end prevents QJackCtl from crashing when you start, stop and start again the jackd server in the same QJackCtl session.

** Execute script after shutdown:**
```
killall jackd
```This makes sure that all instances of jackd are shut down. This is the default, so no need to change it.

[U][B][COLOR=Red]RUNNING JACK USING THE ABOVE-MENTIONED SETTINGS WILL RESULT WITH YOUR VOLUME SET TO MAXIMUM. AFTER PRESSING "START" IN QJACKCTL, LOWER YOUR VOLUME NORMALLY. AGAIN, FAILURE TO FOLLOW THIS WARNING MAY RESULT IN HEARING DAMAGE (AND, POSSIBLY, SPEAKER DAMAGE).

AFTER RUNNING JACK, QUITTING QJACKCTL AFTERWARD WILL STILL LEAVE YOUR VOLUME AT MAXIMUM. LOWER IT UNLESS YOU LIKE HAVING YOUR EARDRUMS BLASTED OUT.

YOU HAVE BEEN WARNED. DON'T BLAME ME IF YOU GO DEAF.
[/COLOR][/B][/U] 
You should be done. To test it, run QJackCtl with the above-mentioned settings and hit *Start*. Wait until the numbers start to change to make sure jackd has finished starting up. Now open an audio file or video file (except a silent video) in Totem (because Totem is not JACK-compatible by default). You should be able to hear the file now.

EDIT: espeak doesn't seem to work properly while jackd is running. The last few syllables get cut off for me. Then again, who uses espeak for songwriting?

---

### Post by Aveface on 2012-04-02
Hello There!

I followed your instructions, but no dice.  

All this stuff work great before I updated to 11.10, clean install.

here's what's in the message box:

20:14:40.962 Patchbay deactivated.
20:14:40.967 Statistics reset.
20:14:41.294 ALSA connection change.
20:14:41.390 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:14:41.829 ALSA connection graph change.
20:18:28.471 Startup script...
20:18:28.472 amixer set Master 100% ; a2jmidid &
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
amixer: Unable to find simple control 'Master',0
sh: a2jmidid: not found
20:18:29.081 Startup script terminated successfully.
20:18:29.347 D-BUS: JACK server could not be started. Sorry
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: driver "alsa" selected
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:18:29 2012: Starting jack server...
Mon Apr  2 20:18:29 2012: JACK server starting in realtime mode with priority 10
Mon Apr  2 20:18:29 2012: [1m[31mERROR: Cannot lock down memory area (Cannot allocate memory)[0m
Mon Apr  2 20:18:29 2012: control device hw:0
Mon Apr  2 20:18:29 2012: control device hw:0
Mon Apr  2 20:18:29 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
Mon Apr  2 20:18:29 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
Mon Apr  2 20:18:29 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|16bit
Mon Apr  2 20:18:29 2012: control device hw:0
Mon Apr  2 20:18:29 2012: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
Mon Apr  2 20:18:29 2012: [1m[31mERROR: Cannot initialize driver[0m
Mon Apr  2 20:18:29 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Mon Apr  2 20:18:29 2012: [1m[31mERROR: Failed to open server[0m
20:18:38.816 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:21:47.511 Startup script...
20:21:47.512 amixer set Master 100% ; a2jmidid &
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
amixer: Unable to find simple control 'Master',0
sh: a2jmidid: not found
20:21:47.924 Startup script terminated successfully.
20:21:48.027 D-BUS: JACK server could not be started. Sorry
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: driver "alsa" selected
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Saving settings to "/home/matthew/.config/jack/conf.xml" ...
Mon Apr  2 20:21:47 2012: Starting jack server...
Mon Apr  2 20:21:47 2012: JACK server starting in realtime mode with priority 10
Mon Apr  2 20:21:47 2012: [1m[31mERROR: Cannot lock down memory area (Cannot allocate memory)[0m
Mon Apr  2 20:21:48 2012: control device hw:0
Mon Apr  2 20:21:48 2012: control device hw:0
Mon Apr  2 20:21:48 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
Mon Apr  2 20:21:48 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
Mon Apr  2 20:21:48 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|16bit
Mon Apr  2 20:21:48 2012: control device hw:0
Mon Apr  2 20:21:48 2012: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
Mon Apr  2 20:21:48 2012: [1m[31mERROR: Cannot initialize driver[0m
Mon Apr  2 20:21:48 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Mon Apr  2 20:21:48 2012: [1m[31mERROR: Failed to open server[0m
20:22:07.472 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started.

Any clues?  Trying to use an RME multiface as I/O!

---

### Post by Splooshie123 on 2012-04-03
Hello.

Are you using jack2? Because this guide was written using jack1. I don't know whether it is applicable for jack2 or if its even necessary. Can you open Synaptic and check whether you have jackd2 or jackd1 installed?

EDIT: I'll try to help but I just replace Ubuntu with Arch Linux last week, so the only help I can provide is from memory and what you tell me.

---

