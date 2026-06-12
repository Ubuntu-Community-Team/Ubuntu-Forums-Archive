---
title: "Music production - where to start?"
date: 2007-05-13
forum: Multimedia Production
---

### Post by jondecker76 on 2007-05-13
I have used Cubase and my normal production app is FL Studio.  I want to transition over to doind my work in Linux, but I'm looking for some good tutorials. I currently have a fresh UbuntuStudio install, an MAudio Delta 1010, 2GB ram, p4 2.8ghz processor

I'm looking for:
1) Live recording (A guitar or two plus a microphone for acoustic recording)
2) Layered recording (record guitar, add vocals and drums etc later)

So my needs revolve around just recording guitar and vocals. I can use hydrogen pretty well already. I would like to get into some midi sequencing down the line, but not quite yet..

Where should I start? I've looked at Ardour, Rose Garden and Wired, and none of them have a familiar workflow or interface to me.

Can someone guide me to a tutorial that covers something simple first - like recording 2 tracks in ardour (a mic and an acoustic through a sound hole pickup)?

Also, can anyone recommend which app to use? (Rosegarden, Ardour, wired, etc)

thanks

Jon

---

### Post by Pocadotty on 2007-05-13
I like Using Ardour 2, Ardour 1 kind of sucked, but 2 is awesome.  It works great with JACK, which is something you will learn to love.

When you create an new audio track, Ardour 2 makes a JACK input for that track, which is nice because then you can record multiple tracks at once in real time.

For instance, lets say you wanted to record some guitar with effects and a drum program you made on hydrogen... here is how to do it.

for this you would want 3 programs, Hydrogen, Ardour 2, and Creox (real time effects).

first and foremost start JACK.

Start by creating two tracks in Ardour (right click in the left hand frame). Connect the output from creox to the input of one of the tracks you just made on Ardour using the options item under the Effector menu in Creox, also while your hear make sure the input on creox is the input for your guitar. Now turn the effects on by clicking on the gear looking icon in the main window.  Set the effects how you want and your done with that.

Then start hydrogen and load the song you want.  Here to manage the connection you will need to use Patchage to connect the output of hydrogen to the next Ardour track. Patchage is not pretty, but it works very well for managing connections graphically.

now that your connections are set up set ardour to record by clicking on the record button of each track and the record button on the top, when you press play in Ardour, it will start recording.

do your stuff and thats how it works.

At first it seams like a funky interface because there are is fair amount of fiddling to do, once you get used to it though you will see that the fiddling gives you a high degree of control over your PC studio.


for mixing I like to Use Audacity, because it has a ridiculous amount of plug ins and an easy interface.  I almost never record anything Using Audacity now because it doesn't work well with JACK in my experience.

I hope that has answered some of your questions.  That is a very basic run around of how to use a couple of the many apps in Ubuntu Studio.  Best advise is play around with the applications and find what you like best.

Linux works on modularity.  For music production that means having a variety of programs that work together through JACK, compared to the windows world where you have "complete" sound studio programs that are not compatible with one another. Most apps have a specific purpose, use the ones that fit your preference and purpose.


cheers :guitar:

---

### Post by Ananth on 2007-05-15
Thanks Pocadotty.

I've moved to Ubuntu for all generic tasks like browsing, editing photos, watching movies, ripping cds etc. Hoping to move my music production stuff to linux soon. 


* I have delta 1010LT. It shows up in the alsa mixer, but there are so many parameters so I don't know which are inputs and which are outputs. Is there a way to get an intelligible mixer? (It comes with a Delta control panel in Windows, which is kind of ok.)

* Are Ardour and Hydrogen in sync when we connect them thru jack, like master-slave. (So Hydrogen will take Ardour's tempo, Start playing when we hit record in Ardour, and will be rhythmically in sync)

* Is it possible to use (windows) VST plugins, particularly those come with installers and authorization.

Cheers!
Ananth

---

### Post by jondecker76 on 2007-05-15
I wouldn't use the Alsa mixer for your 1010LT (I have a 1010). Instead, use envy24control - just type envy24control into a terminal. Its almost exactly like the Delta control panel in windows.

---

### Post by Ananth on 2007-05-15
Super! Thanks.

ps: I had to install alsa-tools-gui to use envy24control.

> **jondecker76 said:**
> I wouldn't use the Alsa mixer for your 1010LT (I have a 1010). Instead, use envy24control - just type envy24control into a terminal. Its almost exactly like the Delta control panel in windows.

---

### Post by tgalati4 on 2007-05-15
If you search around the web, you will find instructions for installing VST plug-ins that show up in Audacity.

I use Audacity for recording simple projects, like a live 2-track performance.  You can also run Icecast to compress to mp3 on-the-fly for web-streaming or for a compressed backup of a performance (with some quality loss).  You won't need Jack for this type of production.

I've used Dynebolic 2.2 Live CD and it works well.  Haven't loaded UbuntuStudio yet.

---

### Post by kayosiii on 2007-05-24
> **Ananth said:**
> 

* Are Ardour and Hydrogen in sync when we connect them thru jack, like master-slave. (So Hydrogen will take Ardour's tempo, Start playing when we hit record in Ardour, and will be rhythmically in sync)



yes it is possible to do that either ardour or hydrogen be master and the other slave. I know that one way works better than the other but I can't remember which way around.

> **Ananth said:**
> 

* Is it possible to use (windows) VST plugins, particularly those come with installers and authorization.


Short answer no... Long answer yes but....

Owing to the licencing for the VSTSdk Programs with support for VST can be built but the binaries can't be redistributed. So you can have VST but only if you are prepared to build yourself from source. Steinberg (or whoever they are owned by now) have said that they are not opposed to changing the licensing but nothing of yet has changed.

The second part of the but is that because everything is running through an emulation layer some VST plugins work better than others and sadly those that require authorisation tend to fair poorly.

---

### Post by Ananth on 2007-05-24
Thanks kayosiii.

---

### Post by thunderkyss on 2007-06-09
> **jondecker76 said:**
> I wouldn't use the Alsa mixer for your 1010LT (I have a 1010). Instead, use envy24control - just type envy24control into a terminal. Its almost exactly like the Delta control panel in windows.

Is there anyway I can set up a Keyboard Shortcut to open the Envy24control Panel??

---

### Post by nalmeth on 2007-06-10
System - Preferences - Keyboard Shortcuts

---

### Post by pkslot on 2007-06-24
This is a great thread indeed!!

I've managed to set up Jack, Rosegarden, Hydrogen, Ardour2 and Patchage. I'm recording guirtartracks and stuff like that, but i kinda need some keyboard too. Only thing, i haven't got a keyboard (the musical kind ;)) so if anybody knows a good software substitute i'd be happy to try it out!

Thanks again for the great advice already written here.

---

### Post by eric71 on 2007-06-25
Look for vkeybd in Synaptic. Just what you need. Works great with Jack.

---

### Post by forrestcupp on 2007-06-25
About effects.  I know it's hard to substitute your vst effects, but you can use all of the free ladspa effects that are made for linux.  Type ladspa in synaptic search and there will be a few packages you can install that give you a lot of effects.

---

### Post by ricrac on 2007-06-25
You can also use jost for ported VST plugins  [http://www.anticore.org/jucetice/?page_id=4](http://www.anticore.org/jucetice/?page_id=4)
Posting from Linux journal  [http://www.linuxjournal.com/node/1000233](http://www.linuxjournal.com/node/1000233)

And wine asio with reaper or others for windows VST instruments as described here..
[http://www.linuxjournal.com/node/1000216](http://www.linuxjournal.com/node/1000216)

---

