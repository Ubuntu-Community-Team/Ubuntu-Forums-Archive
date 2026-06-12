---
title: "TUTORIAL: How to run Jack &amp; Pulseaudio at the same time"
date: 2012-08-11
forum: Multimedia Software
---

### Post by Arightwizard on 2012-08-11
HELLO ALL!!!!!!
(Is this the correct place for this kind of thing? hopefully)
Anyway, I couldn't find any direct tutorials on this, so I figured it out from bits and pieces I found on the web and simple logic. Pardon my lack of references, I can't remember where I found most of this information. If I recall, most of it's from the same site, if anyone knows which, please post a link. I don't approve of plagiarism haha. 

Basically, what you'll be doing is routing PulseAudio through Jack.
I'm running Ubuntu 11.04, try this on other distros at your own risk.

If you're like me, and replaced pulseaudio with alsa, you're gonna want to undo that.
I don't know exactly what you did if you did it, so I'll leave that part to you.

ANYWAY,
First off, install QJackCtl (Available in Ubuntu Software Center) if you haven't already.
Then install pulseaudio and pulseaudio-module-jack if you haven't already.
Command: ```
sudo apt-get install pulseaudio pulseaudio-module-jack
```Next, open a terminal instance and type the following:

```
sudo gedit /etc/asound.conf
```Open up another terminal instance and type a similar thing:

```
sudo gedit $HOME/.asoundrc
```

And copy and paste:
  ```


pcm.pulse { 
    type pulse 
} 

ctl.pulse { 
    type pulse 
} 

pcm.!default { 
    type pulse 
} 
ctl.!default { 
    type pulse 
}

```Save, and exit.

Now, in the terminal:

```
sudo gedit ~/.pulse/default.pa
```And add the following:

```


load-module module-native-protocol-unix 
load-module module-jack-sink channels=2 
load-module module-jack-source channels=2 
load-module module-null-sink 
load-module module-stream-restore 
load-module module-rescue-streams 
load-module module-always-sink 
load-module module-suspend-on-idle 
set-default-sink jack_out 
set-default-source jack_in


  
```Terminal:
```
sudo gedit ~/.pulse/daemon.conf
```Add:[FONT=monospace]
[/FONT]```
default-sample-format = float32le 
default-sample-rate = 48000 
realtime-scheduling = yes 
exit-idle-time = -1
```Save and exit.

Now, open QJackCtl and open the Settings,
Change the sample rate to 44100,
Go to the MISC tab,
Check the box to start the server on application startup.

Go to the OPTIONS tab,
Check "Execute script after startup"
Copy and paste the following:

```
pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2;pacmd set-default-sink jack_out
```Check "Execute script after shutdown"
Enter:
```
killall jackd
```Now, open System > Preferences > Startup Applications
Click "Add"
For the name, type "JackAudio"
For the command, type "qjackctl"
Click "Add"
Make sure the command you just added is checked.
Now, make sure everything is saved and reboot to see if it's working.


The downside to this, is in a "Movie player" instance 
when the song or video finishes, you need to open the QJackCtl window, click "Stop" and then "Start"
in my eyes as a linux-preferring musician: Completely worth it. It doesn't take all that long to do, and I use VLC anyway.

ENJOY! No more stopping and restarting JACK and reconfiguring audio in your DAW whenever you go from your DAW to an mp3 file and back. BE GRATEFUL.

-Andrew

---

