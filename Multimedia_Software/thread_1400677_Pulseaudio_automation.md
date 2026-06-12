---
title: "Pulseaudio automation"
date: 2010-02-07
forum: Multimedia Software
---

### Post by Joe of loath on 2010-02-07
Hi there

I have a simple question, which, knowing me, will become hideously complex. Anyway.

Basically, I want to make a GUI-less ubuntu variant, which just has pulseaudio. I want it to be able to connect to its network gateway (my ubuntu studio dell laptop set up as an ad-hoc wifi point), and become a client to any sound produced on there. So I can boot a computer, it will automatically connect to my laptop, and I can play music over the clients, all automatically.

Thing is, I don't know pulseaudio at all. In fact, I've never run any sound stuff from the terminal at all, so I'm starting from scratch on this front.

My question is, what kind of script would I have to write to get it to do this with no external effort? I'm planning to do this on 5-10 computers at a time, so having to type the same stuff in every time would be a drag. Looking at the pulseaudio wiki it shouldn't be too hard, as the GUI tools are add-on extras, so there must be some command I can punch in and set to run on boot.

Thanks in advance!
Joe

---

### Post by markbuntu on 2010-02-07
pactl and pacmd are the command lines for pulseaudio. You can look them up at the pulse site, I think there are some sample scripts there.

---

### Post by Joe of loath on 2010-02-07
Very helpful, thanks! I'll have a fiddle around (thank the FSM for two linux PC's :D) and come back if I need any help.

---

### Post by markbuntu on 2010-02-07
Well, due to your question I have been fooling around with getting pulse across my lan. It is pretty easy to get music playing on one machine to output on another. I just used Pulse Audio Preferences and turned on Network Access and Multicast Rtp on both machines.

It sort of works like that OOB but you might need to change the rtp module defaults etc. There is more info here and links to explanations of the modules.

[http://www.pulseaudio.org/wiki/FAQ](http://www.pulseaudio.org/wiki/FAQ)

You can also ask at the mailing list or IRC channel if there is something you need clarification on.

I think there is a how-to somwhere around the forums here also. You could try a search.

---

### Post by Joe of loath on 2010-02-07
Excellent, thanks! Once I figure out what to type in I can write a script, and have that execute at boot, and I'm sorted.

Computer department rickrolls here I come!

---

### Post by Joe of loath on 2010-02-07
Just for reference if anyone comes through search to get this, this is pretty much everything in one place:

[http://www.pulseaudio.org/wiki/FAQ#HowdoIusePulseAudiooverthenetwork](http://www.pulseaudio.org/wiki/FAQ#HowdoIusePulseAudiooverthenetwork)

---

### Post by markbuntu on 2010-02-07
You can start thr rtp server in /etc/pulse/default.pa by just uncommenting the load module-rtp send...  line so it starts automatically.
You can uncomment the load-module module-zeroconf-publish line so other machines running pulse can discover it automatically through zeroconf

I really do not think you need any scripts for pulse, just something in the rtp line to keep the stream confined to the local network. Even that is also a default you might want to limit it explicitly.

Basically if you do those things pulse will stream across the net without anything else. You might need a script just to start an app to actually play the music though.

---

### Post by Joe of loath on 2010-02-07
Bloody brilliant, thanks mate! I won't need a script to play any music, as I'll just use totem on my laptop (ubuntu is my primary OS). 

I guess I can do one USB stick manually (yay for persistence!) and DD the image to a dozen others. I can see many applications for this setup.

EDIT: Just two. Parties and rickrolling.

---

### Post by Joe of loath on 2010-02-10
EDIT: Ignore me, I replied before I'd done the right research...

---

