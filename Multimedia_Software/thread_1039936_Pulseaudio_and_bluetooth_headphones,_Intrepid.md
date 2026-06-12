---
title: "Pulseaudio and bluetooth headphones, Intrepid"
date: 2009-01-15
forum: Multimedia Software
---

### Post by John Jason Jordan on 2009-01-15
My Sony DR-BT50 bluetooth headphones worked fine in Hardy as long as I turned them on before launching a sound application. But after upgrading to Intrepid they no longer work at all.

Based on instructions received in other websites I have installed pulseaudio. But I still can't get sound to the headphones. The speakers work fine, it's just the headphones that I can't get working.

The headphones are properly paired in the bluetooth applet. When I turn them on the little power plug icon appears indicating that they are connected.

The problem exists for all sound applications. All send sound to the computer speakers perfectly, but none can send sound to the headphones. I have configured the settings in all applications over and over and have yet to hear one peep from the headphones.

I hope someone has a suggestion. I really want my headphones back!

---

### Post by John Jason Jordan on 2009-01-16
Bump.

Still no luck. Surely one can send sound to a bluetooth device with pulseaudio. Searching the forums and google reveals nada. Does anyone using pulseaudio have sound from bluetooth headphones?

---

### Post by markbuntu on 2009-01-16
I found this. It should work for Intrepid, the sound scheme has not changed very much from Hardy.

[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)

---

### Post by John Jason Jordan on 2009-01-16
> **markbuntu said:**
> I found this. It should work for Intrepid, the sound scheme has not changed very much from Hardy.

[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)

Thanks for the suggestion. I had already found the overclockers page a couple days ago. Unfortunately, it was written for Hardy and a lot of the options are no longer available (or accessed differently) on Intrepid.

I managed to get to item 18, but the pactl commands time out without doing anything. Also, the pulseaudio-device-chooser applet will not launch. It says "starting ..." and then nothing happens. From the command line it just takes a couple minutes and then I am returned to a prompt with no error messages.

---

### Post by markbuntu on 2009-01-16
Is pulseaudio running?
pactl will timeout if pulse is not running, same with padvechooser. An easy way to check that is to open the pulseaudio volume control and you will get an unable to connect error if pulse is not running. 

I noticed that pulseaudio has trouble starting in Intrepid after I installed KDE4 over gnome. You can start pulseaudio from the command line with

pulseaudio -D

which will start it with the defaults from etc/pulse/default.pa

Even though Intrepid and Hardy are both using pulseaudio 0.9.10 there have been some changes. I am still trying to figure out exactly what is screwed up this time. Meanwhile pulseaudio has just released version 0.9.14.

---

### Post by John Jason Jordan on 2009-01-16
> **markbuntu said:**
> Is pulseaudio running?
pactl will timeout if pulse is not running, same with padvechooser. An easy way to check that is to open the pulseaudio volume control and you will get an unable to connect error if pulse is not running. 

I noticed that pulseaudio has trouble starting in Intrepid after I installed KDE4 over gnome. You can start pulseaudio from the command line with

pulseaudio -D

which will start it with the defaults from etc/pulse/default.pa

Even though Intrepid and Hardy are both using pulseaudio 0.9.10 there have been some changes. I am still trying to figure out exactly what is screwed up this time. Meanwhile pulseaudio has just released version 0.9.14.

If I start it from Applications > Sound and Video > Pulseaudio Device Chooser it puts an icon in the Gnome panel. If I click on the icon I get all the options. But if I launch it from the command line I get:

jjj@Devil7:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.

And if I run the pactl commands from the command line I get:

jjj@Devil7:~$ pactl load-module module-alsa-sink device=bluetooth
Failure: Timeout

So I am assuming it is not running, in spite of the fact that I can get an icon in the Gnome panel and all the options seem to launch. Having said that, sometimes when I left click on the icon and then on Manager I see that the server is connected and the details about the server. Other times it launches the same window but the server information is all "n/a".

It sure would help if the developers had written some documentation for this thing.

I think it is not running at the moment.

---

### Post by John Jason Jordan on 2009-01-16
I should add that since it is not currently connected, the Connect button is active. But when I click on it I get "authorizing ..." for a minute or two, then "Failure: Timeout."

---

### Post by John Jason Jordan on 2009-01-17
Bump.

Can anyone tell me what modules must be installed for pulseaudio to run, and how to launch it after the modules are installed?

---

