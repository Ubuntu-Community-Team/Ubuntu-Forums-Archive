---
title: "Pulseaudio: no flash sound in Jaunty"
date: 2009-05-01
forum: Multimedia Software
---

### Post by DeadMetal on 2009-05-01
In earlier versions of Ubuntu Pulseaudio did not work for me, but since Jaunty I have everything working fine via Pulseaudio, except Flash player: I hear no sound in flash videos in Firefox.

I would like to request some help to get this working. What do I have to do to find a solution? How do I configure Flash to send its sound to Pulseaudio? That is currently not happening.

Besides Flash everything works fine after some tweaking. I have done the following: chosen Pulseaudio in the Ubuntu sound properties. The PulseAudio device chooser finds my two sound cards. I have chosen my Audigy 1 and not the onboard device. Skype and Rhythmbox worked fine out of the box. For Totem I had to run gstreamer-properties to select Pulseaudio and for VLC I had to install vlc-plugin-pulse and now it sends its sound to Pulseaudio.

---

### Post by kostkon on 2009-05-01
Since you already have the *PulseAudio Device Chooser*, then left-click on it and select the volume control. Put a *Flash* video playing in *Firefox* and then select the *Playback* tab in the volume control.

There you should see the audio stream of the *Flash* video (it'll be listed as *Firefox[ALSA*] or something like that) listed. Right-click on it and select *Move Stream* and in the list that will appear select your Audigy card.

Hopefully, *PulseAudio* will remember your choice from now on.

Hope that helps.

---

### Post by DeadMetal on 2009-05-01
Fixed, thanks a lot!

---

### Post by Laur1er on 2009-05-18
I'm having a similar problem but no stream is created in the pulse volume control for me to send to another sound card.

---

### Post by kostkon on 2009-05-19
> **Laur1er said:**
> I'm having a similar problem but no stream is created in the pulse volume control for me to send to another sound card.
What version of Ubuntu and Flash do you have?

---

### Post by The_Aviator on 2009-06-19
Hi, I have the same problem as above.

I'm using 9.04 amd64 with the adobe 64 bit plugin 10.0.22.87.

I tried with the 32bit version from synaptic first but this didn't work either.

I'm guessing that flash is simply using ALSA directly and not through PA as if everything else is closed then it works perfectly.

Cheers

---

### Post by The_Aviator on 2009-06-19
Hi.....I fixed it.

I simply installed asoundconf-gtk and then went System/Preferences/Default Sound Card and selected Pulseaudio.

Logged out/in and then all sound including flash worked together just fine!

Phew...

---

### Post by obieito on 2009-06-23
> **kostkon said:**
> Since you already have the *PulseAudio Device Chooser*, then left-click on it and select the volume control. Put a *Flash* video playing in *Firefox* and then select the *Playback* tab in the volume control.

There you should see the audio stream of the *Flash* video (it'll be listed as *Firefox[ALSA*] or something like that) listed. Right-click on it and select *Move Stream* and in the list that will appear select your Audigy card.

Hopefully, *PulseAudio* will remember your choice from now on.

Hope that helps.



Man oh man oh man Mr. Kostkon!!!

These have been the most beautiful words I've heard this week!!!

I have been fighting this issue for maybe 3 weeks... I was kinda lost, after having (almost) marked out system sound issues, plugin issues, flash issues, even firefox itself issues...

Today (I had a while to keep fighting :) I became convinced (again) that the issue should be with PulseAudio, and my 2 soundcards (I knew they were there someway too) but your advice with padevchooser finally worked!

You don't know how thankful I am, believe Im kinda old hacker, but got much less time in my hands today to debug stuff... Plus that nifty little app should be there by default, if PulseAudio is set up by default!!  
(It is by default now in my session of course!)

---

### Post by elgreengeeto on 2009-07-15
> **kostkon said:**
> Since you already have the *PulseAudio Device Chooser*, then left-click on it and select the volume control. Put a *Flash* video playing in *Firefox* and then select the *Playback* tab in the volume control.

There you should see the audio stream of the *Flash* video (it'll be listed as *Firefox[ALSA*] or something like that) listed. Right-click on it and select *Move Stream* and in the list that will appear select your Audigy card.

Hopefully, *PulseAudio* will remember your choice from now on.

Hope that helps.

Thanks a lot, worked for me!

---

