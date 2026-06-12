---
title: "connecting rakarrack with ardour and jack"
date: 2011-03-26
forum: Multimedia Software
---

### Post by petefan12 on 2011-03-26
I am new to using Ubuntu (3 days) so excuse me if my terminology isn't up to par. I downloaded and installed Ardour and Rakarrack. I want to record my guitar to the computer and use rakarrack for effects. I am using a Lexicon Alpha usb interface that is recognized by Ubuntu. Anyway, I start Jack and then open Rakarrack and Ardour. My headphones are plugged into the Lexicon Alpha interface and I can hear sound through the headphones, the meters move in Rakarrack, and the meters move in Ardour and I can record in Ardour. The problem is that I can't get the Rakarrack effects to work. I made sure the FX is turned on in Rakarrack, so I know that's not the problem. I tried plugging my headphones into the computer, but I don't get any sound at all. Also, I opened the connections in Jack and to my novice eyes, it looks like a bunch of lines of spaghetti to me. I must have a problem with the output connection from Rakarrack but I'm not sure. When I play it is the clean sound of the guitar and Rakarrack isn't influencing the sound. Any assistance would be greatly appreciated. One other thing, when I click on settings, file, etc in Rakarrack, there is no dropdown menus. Is this normal?

---

### Post by cchhrriiss121212 on 2011-03-27
Try using a program called patchage, it displays all the jack connections in a much easier way. Just connect the relevant blue boxes together.

---

### Post by petefan12 on 2011-03-27
Thanks for the tip dude. I downloaded patchage, then started all of my software. It looks like patchage shows how everything is hooked up already. I didn't see anything in blue boxes that wasn't connected. I tried connecting the rakarrack "aux" to several different things, but didn't get any positive results. You think it could be something with my usb interface? It will record in Ardour on its own, but I still can't get rakarrack to effect the sound.

---

### Post by cchhrriiss121212 on 2011-03-27
If the device works with Ardour, then it should be fine. Try using this:
system capture > rakarrack in
rakarrack out > system playback
The aux connection is not required.

Are you sure you have the FX on (the button in the top left)?

---

### Post by petefan12 on 2011-03-27
Yep, the FX light is turned on. Jack and patchage shows "system capture  1" going into rakarrack "in 1" and "in2" and ardour "audio 1/in 1".

Rakarrack "out 1" is going to system playback 1. Out 2 is going to system playback 2.

Could it be because of the mono signal from the usb interface and guitar? do I need to disconnect the "out 2" and/or the "in 2"? 

Thanks for your help.

---

### Post by cchhrriiss121212 on 2011-03-28
Try using another program for  FX, like guitarix, and connect it up like rakarrack is now. If that works, you will know the problem is specific to rakkrack.

> Could it be because of the mono signal from the usb interface and  guitar? do I need to disconnect the "out 2" and/or the "in 2"? 
No, that would not cause a problem.

---

### Post by petefan12 on 2011-03-28
Ok, I'm not sure what I did, but I managed to get Rakarrack running as far as being able to hear it through the headphones plugged into my usb interface. Checked a couple of the presets and they worked fine too. Tried to record a track with Ardour and it recorded. But, even though I can hear the distortion from Rakarrack through my headphones, the playback in Ardour is just the plain guitar sound without the Rakarrack influence. How do I fix this? Of note, in order for me to hear the Rakarrack effect through my headphones, my usb interface has to be dialed into playback mix vs. recording mix. Does that affect anything? If I have that dial directly into recording on the interface, I don't get any sound at all. Also, I downloaded JACKRack earlier today, how does that work with all this? Or, is it completely separate effects?

Thanks!

---

### Post by cchhrriiss121212 on 2011-03-28
To record the fx in ardour you just need to connect rakkarack output to the ardour input:
sys capture > rakkarack > ardour
Ardour will autoconnect to the dry input by default, I always disable this when starting a new project.
> in order for me to hear the Rakarrack effect through my headphones, my  usb interface has to be dialed into playback mix vs. recording mix. Does  that affect anything? 
I don't know what this is, is it physical control on your device? If it works, then I would leave it as it is.
> I downloaded JACKRack earlier today, how does that work with all this? Or, is it completely separate effects?
Yeah that is a separate effects tool. You just start it up then load whatever ladspa fx you want, if you search for ladspa in synaptic of software center you will find a few bundled together packages. Now you can use jack/patchage to add fx to anything you like.

---

### Post by transmogrifox on 2011-03-31
Maybe a good start is open qjackctl (or patchage, whichever you prefer) and disconnect all.  Once you have disconnected everything in Jack, you should hear absolutely nothing when you play or attempt to record guitar.  

Next, connect the audio input from guitar only to the first thing in your processing chain (rakarrack or jack rack).  Rakarrack should show the bouncing VU bars at that point, assuming you connected first to Rakarrack.  I don't think Jack-Rack has a VU bar plugin, so Rakarrack makes a good troubleshooting tool that way.

Next connect the output of that device to the system outputs.  You will then be able to hear the guitar, but won't be able to record in Ardour.

Next connect Rakarrack (or jack rack) outputs to the Ardour channel where you want to record.  

At that point you will be able to both hear what you're playing, and you will be recording what you hear.  When you play it back from ardour I don't expect you will hear any clean signal coming out.

I struggled with this problem when I first started learning about JACK and audio programs written for JACK in Linux.  Once you get to a point where are you are comfortable with the concept, then jack is really easy to use given the tools available like qjackctl and patchage.

I hope this is some help to you.  Take care.

---

### Post by petefan12 on 2011-04-09
Sorry for my delinquent response. Thanks to you guys for the help, I got everything going! Really cool how it all works together. Thank you so much!

---

