---
title: "Problems with pulseaudio"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by sammydee on 2007-10-18
Hi all

Ok, here's what I want to try to achieve. I want to play a movie on my laptop, send the sound over the network to my main pc which will play it through my big speakers.

I have installed EVERYTHING in synaptic that has anything to do with pulseaudio. After hours of mucking around with avahi and firestarter, I managed to get the two pulseaudio daemons to form some semblance of communication with each other.

On both computers, I can select either computer to use the other as a "sink". I'm not entirely sure what a sink is, but I am assuming it is a soundcard, right?

Problem is, if I tell either computer to use the other as a sink, then play any sound it will crash and.or tell me that there is no sound output plugin or something to that effect.

I can't see any other servers or sources over the network.

This is on Ubuntu gutsy. Any help?

Sam

---

### Post by sammydee on 2007-10-19
Ok I finally managed to get it to work, but it's buggy and pusleaudio causes games like Quake 4 and Doom 3 to hard lock the system.

How do I remove all traces of pulseaudio and completely restore whatever sound setup ubuntu comes with by default?

Sam

---

### Post by sammydee on 2007-10-20
Nobody knows how to remove pulseaudio? I've tried getting rid of all the packages that rekate to it but I end up in dependency hell where I can't remove anything without also removing a load of other software like amarok and totem that worked just fine before.

What do I need to do to restore my system to a pre-pulseaudio state?

Sam

---

### Post by Capncruncky on 2007-10-21
I've been wondering this same thing. It seems to me that Pulse is not a very flexible program. 
Its pretty much ruined my OS to the point that i am having trouble even reinstalling my old drivers. I think when I unistalled Pulse through synaptic it removed a ton of other stuff I needed. Now i'm thinking of reinstalling Ubuntu all together. 
NEED HELP!

---

### Post by sammydee on 2007-10-21
Same problem as me then.

I managed to remove everything except libpulse0 without problems.

However, if I try to remove libpulse0, synaptic tries to, among others, remove amarok, gxine, totem-xine, totem, libxine1, libxine1-ffmpeg and mplayer.

Applications such as chromium or Doom 3 still give sound errors (chromium even says "error with audio module "pulse" or something like that) on startup.

All I want to do is get rid of it and restore whatever system was there before! Help!

---

### Post by sammydee on 2007-10-22
Still no help?

There must be somebody else that has had this problem! A lot of programs on my system are unusable because they either have no sound or cause segfaults when trying to initialise sound, quoting errors about pulseaudio.

A short but by no means exhaustive list of broken applications:

-Gens megadrive emulator
-Mupen64 N64 emulator
-Doom 3
-Quake 4
-Assualtcube first person shooter
-Gaim messenger
-Cedega

Do I really need to resort to removing the applications that depend on pulseaudio (listed in post above) then removing libpulse0 and reinstalling said programs? Will this even fix the problem?

At the moment I would call the sound on my pc completely broken, please can someone help me out here!

Sam

---

### Post by ridetheteapot on 2007-10-22
wow i was going to give pulse a try (there is a ubuntu wiki page saying that pulseaudio will soon replace esd)... guess i'll save the headache for another time

all i can tell you for sure is that libpulse0 is installed by defualt on ubunutu, so there is no need to remove it (or anything that depends on it) to get back to the original state.

make sure you have esound installed, and if you wanna go ahead and test if sound will work as it once did start up esd --maybe esd isnt starting by defualt anymore?-- and try out xmms or something simple.

---

### Post by sammydee on 2007-10-23
Well if libpulse0 isn't causing the problems I've no idea what to do. Practically every application that uses sound in some way spews out errors about pulseaudio.

Erm. There's no other packages other than libpulse0 left on my system that are in anyway related to pulseaudio.

Sound is still broken here folks, what do I need to do to fix it? Please somebody help me!?

---

### Post by rootkowski on 2007-10-23
Hi there!

I was only getting more and more scared reading this thread since I installed pulseaudio yesterday and can't set it so i have surround sound. I'm thinking of removing it if i can't fix this issue with surround.

Anyway, I wonder guys if you've changed the /etc/asound.conf and possibly ~.asoundrc so that they don't call for pulseaudio anymore. Check also in System/Pref/Multimedia System Selector and Sound. Check what system is set in amarok or other apps you use. There are a lot of things that pulseaudio changes.

Hope it was helpful :-)

---

### Post by rootkowski on 2007-10-23
I'm having really bad feelings here. I didn't find any way to get pulseaudio play surround so i uninstalled it, changed asound files, settings in Sound and Mulitmedia, but of course i forgot to change settings in amarok and now, even though i reinstalled amarok, it doesn't respond. It just goes grey, The same for another player that I had set to use pulseaudio. Totem plays without problems though and so does vlc. I installed exaile and it plays too, but with a lot of noises. I am actually considering reinstalling the system if someone does not get a better idea.

One more thing. When I wrote in the terminal sudo gedit /etc/asound.conf it gave me an error message: "/usr/bin/esd not found". That could of course be the thing. But i looked through synaptic and didn't find anything that would be suitable to install. I'm having some bad thoughts about this "compiz of sound"

---

### Post by sammydee on 2007-10-23
THANKYOU rootkowski!!!

Removing the driver calls for pulseaudio in /etc/asound.conf SEEMS to have fixed the problem. I haven't yet tested everything so I hope I'm not being premature here.

Let this thread serve as a warning to anybody who wants to give pulseaudio a try... It's hassle to get rid of the flippin thing!

rootkowski - have you tried finding the config files for amarok and changing the audio output plugin to gstreamer or xine or similar?

I know totem's config is in ~/.gnome2/totem_config

If you comment out the line that specifies the audio driver it should autodetect it and work nicely again - did for me anyway :-)

sam

---

### Post by rootkowski on 2007-10-23
I'm soo glad it worked for you :-D

Now, things worked for me as well. :-) First i checked only in .kde/share/apps/amarok and found nothing useful there. But after reading your post above i gave it another try and found something like this: .kde/share/config/amarokrc. And that was the thing! Replacing pulseaudio with alsa fixed it!

I'm so happy we could help each other :-) Thank you Sam!

ps: ye, i agree that pulseaudio thing is quite tricky. I hope it will improve before they put it into ubuntu.

---

### Post by JonathanRRogers on 2008-01-06
To get 5.1 output from pulseaudio, I had to add this line to the server configuration in /etc/pulse/default.pa:

```
load-module module-alsa-sink device=surround51:CARD=Audigy2
```

I have two different ALSA cards, which is why I had to specify CARD=Audigy2. If you only have one, just surround51 should suffice. Pulseaudio's HAL support enables it to automatically use devices HAL knows about, which doesn't seem to include surround51.

I also discovered that it's current a bad idea to put set pulse as the default device in /etc/asound.conf or ~/.asoundrc because quite a few ALSA apps still have trouble with the pulse plugin, though it is probably due to a bug in alsa-lib rather than pulseaudio. I do have the following lines in my /etc/asound.conf, which allows apps to use the alsa-lib plugin, but doesn't make it default:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}

```

---

