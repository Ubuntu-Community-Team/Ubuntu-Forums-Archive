---
title: "Problem with gtk-recordMyDesktop &amp; Jack"
date: 2012-09-13
forum: Multimedia Software
---

### Post by mku1tra on 2012-09-13
Whenever I run recordmydesktop 
```

recordmydesktop -o /home/condor/Desktop/out.ogv --fps 15 -x 151 -y 163 --width 863 --height 562 --channels 2 --freq 48000 --v_quality 63 --s_quality 10 --workdir /tmp --use-jack vlc_12349

```I get the following:
```
Window size specification out of bounds!(current resolution:1280x1024)
```

Launching gtk-recordMyDesktop while selecting the same jack input (vlc_12349 = VLC audio out) I get the following when trying to capture a screen-cast:

```
Recording is finished.
recordMyDesktop has exited with status: 28
Description: Improper windows specification
``````
dpkg-query --list | grep recordmy
ii  gtk-recordmydesktop                      0.3.8-4.1ubuntu1                        Graphical frontend for recordMyDesktop screencast tool
ii  recordmydesktop                          0.3.8.1+svn602-1ubuntu3                 Captures audio-video data of a Linux desktop session
```

Another thing I;ve noticed is that I can't launch Jack using QjackCtrl. Only after I launch jack manually from cli I get to use apps like patchage and qjackctrl

```
/usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2
```

I can redirect/rewire audio to other apps like audacity selecting Jack vlc_12349 (audio out from VLC), so I know jack works. So I guess there has to be something wrong with recordmydesktop's Jack support as recordmydesktop seems to work fine for both front end and cli when Jack isn't selected as the audio source.

I'm using Precise 12.04 amd64

thanks

---

### Post by mku1tra on 2012-09-13
Is there an alternative to recordmydesktop that can use Jack ? I've looked in the most popular repositories but haven't found a single one app supporting Jack. I'm trying not to use Win/Mac for this job.
Thanks!

---

### Post by rofthorax on 2012-11-02
> **mku1tra said:**
> Is there an alternative to recordmydesktop that can use Jack ? I've looked in the most popular repositories but haven't found a single one app supporting Jack. I'm trying not to use Win/Mac for this job.
Thanks!

Ubuntu Studio usually comes with all the Jack supporting apps.. I'm coming up with similar errors on 12.10 of Ubuntu Studio... Seems to be a problem with recordMyDesktop and jack.. There has been times in the past I've had them working together, but GTKRMD doesn't like jack now.. I suppose it's cause I'm using the 64-bit Ubuntu instead of a 32-bit, but that doesn't make sense because Jack is designed to use Core2Duo's and later and everything since has been 64-bit...

---

### Post by wachin on 2013-04-13
the only way to work Recordmydesktop from Jack 

O.S. used UbuntuStudio 12.04.2 (32bits), Laptop Dell Inspiron 1750


Steps I did:

I uninstalled (via Synaptic):

recordmydesktop (this dont working)
gtk-recordmydesktop

Note: This uninstalled Kdenlive, but then returned to install.

I Download:

recordmydesktop_0.3.8.1 svn602-2 + + jackfix_i386.deb

from:

[http://www.remastersys.com/forums/index.php?topic=1608.0](http://www.remastersys.com/forums/index.php?topic=1608.0)

and install it from the terminal: sudo dpkg-i *. deb:

Then I installed (via Synaptic):

gtk-recordmydesktop

Ready now

I opened Jack Control (QjackCtl) and run Jack Server (Play button)

With Gtk-recordmydesktop opened, in Tab "Sound" Select the audio to be captured from Jack (crushing Ctrl):

system: capture_1
system: capture_2

I closed the window, and click Record buttom

STEREO MIX
You must configure your PC  in pulseaudio  Tab "Input devices" in "Port" record from the microphone of the laptop (if you have it) adjust the volume, I have to put such halfway to not sound ugly, or "Line In" if you use a external Mic. And Jack Control (qjackctl) you must click on the "Connections" tab "Audio" manually connect the music player that is playing to "recordmydesktop", you can use:

Audacious (must choose "File / Preferences / Output Options" JACK)
VLC (but must install from Synaptic vlc-plugin-jack


[IMG]https://dl.dropboxusercontent.com/u/83295394/Jack%20Connections/RecordMyDesktop%20%2B%20Jack%20Support.gif[/IMG]


and ready, that's all, ESTERO MIX WITH JACK FROM RECORDMYDESKCOP

Saturday 13 April 2013 10:12

---

