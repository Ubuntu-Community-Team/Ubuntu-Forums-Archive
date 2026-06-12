---
title: "Recommed a simple drum machine/sequencer program?"
date: 2018-07-22
forum: Multimedia Software
---

### Post by neomadic on 2018-07-22
I've been pulling my hair out for three days trying to get Ardour to do....well anything really, and I must be too stupid.

I need to record a few click tracks that change tempo for the choruses and I just can't find a program that will work.  The drum machine programs only work with one tempo at a time and the DAW's are just too hard for a linux noob(been at it three years) to setup and operate.

I've found a few online options but most of them crash my browsers, pale moon, icecat, and waterfox, and they don't keep good time due to my internet connection.

Is there anything I can install where I can create a click track for 4 measures at 80 beats per minute, then 4 measures at 100, then back to 80?

Sorry if this is a dumb question but I just can't think of the necessary search terms to find what I want and there's so much irrelevant and outdated information out there that I keep getting lost in a sea of noise that doesn't apply to what I'm doing.

Any recommendations would be greatly appreciated.

---

### Post by neomadic on 2018-07-22
Sorry for sticking this post in the wrong spot.

I think I finally found a simple solution.

I discovered that Audacity works on Ubuntu!  

Then I followed the instructions here: [https://www.instructables.com/id/Drum-Beats-in-Audacity/](https://www.instructables.com/id/Drum-Beats-in-Audacity/)

It's an old post but it works perfectly and is super easy to use.  I can even program in poly-rhythms easily.  I got it set up and actually recorded a song in under an hour.  The only part that threw me for a bit was having to change the mic input level for the guitar track in ALSA instead of inside Audacity.

So pumped, no more random screeching Satan coming from Ardour!  Finally!

---

### Post by neomadic on 2018-07-22
I should add that I'm definitely still open to advice.  Adding in the drums one track at a time works but something like EZDrummer would be much faster.

---

### Post by deadflowr on 2018-07-23
It would help to know what other programs you tried.
So that others won't keep offering advice which you would already know does not work for your needs.

---

### Post by kazakore on 2018-07-23
If you want to do tempo changes I think you will need a sequencer really, rather than just a drum machine. I'd recommend trying Ardour and qtractor. You can manually create the drums tracks within the sequencer or you could use an external drum machine such as Hydrogen for the sounds. You're most likely going to want the Jack audio server installed, most easily done on Ubuntu through the control panel qjackctl.

```
sudo apt-get install ardour qtractor hydrogen qjackctl
```

See how well they do for you.

---

