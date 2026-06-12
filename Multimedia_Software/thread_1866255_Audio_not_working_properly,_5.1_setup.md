---
title: "Audio not working properly, 5.1 setup"
date: 2011-10-21
forum: Multimedia Software
---

### Post by BWorld on 2011-10-21
Hello,

I am experiencing some issues with my sound setup.
I decided to buy a nice dolby surround system from Denon and everything is working fine on Windows after installing the drivers but for Ubuntu there seems to be no default driver..

After some digging I found out how to make my 5.1 setup work correctly in Xine.
The following tutorial allowed me to set this up properly: [http://www.halfgaar.net/surround-sound-in-linux](http://www.halfgaar.net/surround-sound-in-linux)

After doing this everything is working properly in Xine and I am able to play DVD's and my bass is also working now.
Problem is that when I am trying to play music in rhythmbox and/or banshee that I am having no sound at all. After running:

> sudo killall pulseaudioMy sound is working in the music player(s) but without bass so the sound is really really crappy.. 
After killing pulseaudio I am getting errors when trying to play a dvd again via Xine, the errors are:

> me@localhost:~$ xine "dvd:////media/somedvd.iso"
This is xine (X11 gui) - a free video player v0.99.6.
(c) 2000-2007 The xine Team.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
exec of JACK server (command = "/usr/bin/jackd") failed: No such file or directory
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
libdvdread: Encrypted DVD support unavailable.After logging out of the system and logging back on my dvd is playing correctly again but again no sound in the music players..

I have no ~/.asoundrc but the contents of my /etc/asound.conf is:

> #pcm.pulse {
 #   type pulse
#}
#ctl.pulse {
#    type pulse
#}
pcm.!default {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5

    hint.description "Default Audio Device PULSE"
}

#ctl.!default {
#    type pulse
#}

pcm.51to40
{
    type route
    slave.pcm surround51
    slave.channels 6

    # Front and rear, at 50% of original signal strength
    ttable.0.0 0.5
    ttable.1.1 0.5
    ttable.2.2 0.5
    ttable.3.3 0.5

    # Center channel routing (routed to front-left and front-right),
    # 6dB gaindrop (gain half of main channels) per channel
    ttable.4.0 0.25
    ttable.4.1 0.25

    # LFE channel routing (routed to front-left and front-right),
    # 6dB gaindrop (gain half of main channels) per channel
    ttable.5.0 0.25
    ttable.5.1 0.25
}Also I have changed some settings in /etc/pulse/daemon.conf:

> daemonize = yes
default-sample-channels = 6Rest of the file isn't modified.
Another strange thing is that in my sound settings I *must* choose for the profile *Digital Stereo Duplex (IEC958)* in order to make my music player work.
If I change this to *Analog Surround 5.1* *Output *I wont have sound anymore from my music player.

Strange thing is that I can only choose for ***Analog*** *Surround 5.1 Output* but a coax cable makes it digital or I am wrong at this point?

My soundcard is a **Club3D Theatron Agrippa**.

I really hope somebody has a solution for this anoying problem and could put some light on this..

FYI:
I have my sound card connected through a coax cable from my soundcard to my Denon receiver.

---

### Post by SlugSlug on 2011-10-21
with each install I do, to get my 5.1 up and running nicely I simply 

```
sudo apt-get remove pulseaudio && sudo apt-get install alsa alsa-mixergui
```then drag an icon to top bar for alsa-mixergui  so u have access to volume

I also bind F11 and F12  to PCM up/down  so I can use those keys to turn vol up and down

---

### Post by BWorld on 2011-10-21
> **SlugSlug said:**
> with each install I do, to get my 5.1 up and running nicely I simply 

```
sudo apt-get remove pulseaudio && sudo apt-get install alsa alsa-mixergui
```then drag an icon to top bar for alsa-mixergui  so u have access to volume

This means that you remove the pulse system, I wonder if this is the right way to do it, could you explain me why this would work?
And wich settings do you use in the sound preferences window, espacially I wonder which profile you are using and do you also use a coax cable for connecting the soundcard with your receiver?

> **SlugSlug said:**
> 
I also bind F11 and F12  to PCM up/down  so I can use those keys to turn vol up and down

Cool!

---

### Post by SlugSlug on 2011-10-21
> **BWorld said:**
> This means that you remove the pulse system, I wonder if this is the right way to do it, could you explain me why this would work?
And wich settings do you use in the sound preferences window, espacially I wonder which profile you are using and do you also use a coax cable for connecting the soundcard with your receiver?



Cool!


sound pref window wont work / apply after removing pulse.

try it you can always reverse it

---

### Post by BicyclerBoy on 2011-10-21
Your soundcard possibly has onboard DTS & AC3 encoders or uses windows software encoders.

This allows the card to encode discrete multi-channel audio & output digital S/PDIF matrix encoded multi-channel DTS AC3 (DD) or plain stereo PCM.

The stereo PCM could go up to 192KHz/24bit.
DTS has a max bitrate 1.5M ?
AC3 has a max bitrate 640K

But this may **not** be possible in Linux without specific driver support (alsa).
Linux alsa can encode AC3 realtime to output dig pass-thru' over S/PDIF.

If you use the surround5.1 on a normal soundcard, this is discrete "analog" channels output to 5.1 jacks. Your soundcard will likely encode to DTS/AC3 (if it works).

The IEC958 output on your soundcard is a direct dig pass-thru' for DTS/AC3/stereo PCM.
Can not use dmix on AC3/DTS.

All soundcards are mostly made superfluous by HDMI HDA & the fact there is no alternative digital audio interconnect.
Only HDMI is supported by consumer AVR HT amps.

A basic HDMI video card can output all S/PDIF & extra HDA formats including multi-channel LPCM.
HDMI audio is cheaper/easier/more flexible. Discrete digital multi-channel LPCM renders any soundcard deprecated.

You need to determine exactly what functions on your soundcard work with alsa.
Do you really want to upmix stereo to 5.1 ?
Do you want audiophile sound ? (alsa has a very good resampler).
Do you want system wide sound (sharing) ?

If you card uses windows software for AC3/DTS encoders then it is no more useful than mobo onboard sound.

Your DVD playback could be fixed by restricted extras medibuntu libdvdcss.

I have used dig pass-thru' S/PDIF with alsa & hq resampler (& with pulseaudio running) from 8.10.
Never needed to remove pulse.
Alsa AC3 encoding sort of works but questionable SQ & will not compile now.

---

