---
title: "Pulse audio not switching to headphones after upgrade"
date: 2016-01-25
forum: Multimedia Software
---

### Post by katoiam2 on 2016-01-25
Hello All,

I have recently upgraded from 14.10 (via 15.04) to 15.10.

Most  things went okay except pulse (or what ever internal mechanism!) is no  longer out putting the audio to the headphone jack when it is plugged  in. I can get it to play out of the headphones by going in to the pulse  mixer and choosing headphones from the drop down in the output devices  tab, but have to do this each time I plug in or out a jack! So there is  nothing wrong with the jack or the headphones!

I have tried to   remove the config files (rm -r ~/.config/pulse; pulseaudio -k (from  [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)) and purge pulse audio, which just  lead to having no mixer! So i installed kmix (thinking that was what was  missing), found out that it should be plasm-pa, which I then installed  (and purged kmix) but nothing has changed for the better, and I no  longer have a tray icon for pulse-pa just a blank space where it should  be!

Any ideas? This is driving me barmy!

Thanks in advance for any help

<snipped>

---

### Post by Bucky Ball on 2016-01-25
*Thread moved to **Multimedia Software**.*

Welcome. I have snipped your second support question from your first post as it has nothing to do with your other question and two questions on one thread gets confusing.  Please post a new thread for that issue. 

Have you installed pulse and pavucontrol again? Pulseaudio Volume Control is what I think you're referring to as the 'Pulse mixer' and what you're after to tweak the volumes and inputs/outputs for Pulse.

---

### Post by katoiam2 on 2016-01-26
Hello Bucky Ball,

I have installed both pulse and pavucontrol, you are correct in saying that I am referring to Pulseaudio Volume control, which is also what opens if I run pavucontrol from the commandline, however this only allows me to swap between either headphones or speakers, and only the one selected works, until I change selection. It also varies between telling me the headphones are unplugged or plugged, but not depending on whether they are actually plugged in!

---

### Post by katoiam2 on 2016-01-26
Update:

I have continued to search the web to no avail, but have found something else to add to the mix.

My  laptop is a XPS 15, 2012, which has a headphone jack (hole thing!) and a  headset jack (ie mic and headphones) I have never really used the  headset jack. I was looking at alsa mixer to see what happened when I  plugged the jack in. 

What I found was interesting. Pulse is  detecting the headphones when they are plugged into the headset hole. Or  what is happening when I have the output set to speaker, if I plug into  the headset hole the sound from the speakers stops, and the sound  levels change in the mixer, suddenly although no sound is coming out the  headphone bar is full and the speaker is at 0. If I then raise the  speaker+LO then sound comes out of the headset socket.

Edit: I attempted to add in images to show alsamixer during the 3 stages explained above, but they don't appear to have worked so I have removed them!

However  when I plug into the normal headphone socket nothing changes in the  mixer (ie it stays like the first image above), also the drop down list  in the Pulseaudio Volume Control, only shows headphones connected when I  put it in the headset socket(though will play out of them if I select  headphones from this list!). 

I hope this can help someone to work out whats going on!

Cheers,

Liam

---

### Post by katoiam2 on 2016-01-27
I have just realised these things:

The headphones socket isn't being detected
The headset socket is being detected as the headphone socket, but audio is routed to it as 'Line out'
When  a jack is inserted into the headset(line out) socket, the channel (in  alsamixer)  for speaker/ line out is muted, and the headphone one is  turned up/ on, which means no sound comes out until the speaker/ line  out channel is turned back up again.
The headphone socket does output audio, if it is set in Pulse Volume Control, but the jack when inserted isn't detected 

I  just did an interesting experiment, using two sets of headphones. The  out come is that when I put one in the headset (lineout) socket audio  stops coming out of the internal speakers and starts coming out of the  headphone socket! So I assume that there is something wrong with the  configuration, that is confusing the two sockets!

I have no idea where this config might be, whether its pulse or somewhere else, and then once found how I might fix it.

---

### Post by Bucky Ball on 2016-01-28
> **katoiam2 said:**
> ... when I put one in the headset (lineout) socket audio  stops coming out of the internal speakers and starts coming out of the  headphone socket! 

Isn't that what you wanted? Plug in headphones, sound output through headphones and not output through speakers?

---

### Post by katoiam2 on 2016-01-28
I was wondering if my description would be confusing!


No I have two sockets, headphone and headset. When I plug into the headset socket the sound comes out of the headphone socket, when I plug into the headphone socket no sound comes out! 


So my system seems to be confusing which one is plugged in, and sending the audio to a different one!

---

### Post by katoiam2 on 2016-02-03
Really, no one has an idea?

---

### Post by Bucky Ball on 2016-02-04
It really looks that way, but I'll bump the thread by posting this.

---

### Post by katoiam2 on 2016-05-30
bump

---

