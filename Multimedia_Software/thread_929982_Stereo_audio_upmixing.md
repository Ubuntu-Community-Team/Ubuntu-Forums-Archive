---
title: "Stereo audio upmixing"
date: 2008-09-25
forum: Multimedia Software
---

### Post by Zelandeth on 2008-09-25
Ubuntu Hardy Heron 64-bit

Using the onboard Realtek 7.1 surround sound card on my Gigabyte motherboard - which I can't remember the model of off the top of my head - if relevant I'll dig out the bit of paper with all that info on later.  Everything seems to work perfectly though.

Hooked up to my PC here for audio I've a Pioneer SA-610 amp and Pioneer CS-585 speakers on the front channel, and a Sanyo DCA-M15 amp and Kenwood speakers of indeterminate origin on the rear channel - giving me a quadrophonic setup...Sure I could go out and get a home cinema system, but this didn't cost me anything and sounds absolutely fantastic, despite the main component being 25 odd years old now.

One feature I find brilliant in Windows is the ability of the Realtek software to "upmix" stereo tracks to make full use of 4.0, 5.1 or 7.1 speaker setups - and contrary to my expectations it actually works really well.  Sure, if you just have the rear speakers on it sounds awful - but it does add a great deal of "depth" to music - especially orchestral or live tracks.  Clever bit of maths being used there I'm sure!  I should point out that all channels do work in Ubuntu - it just seems to duplicate the front channels on the rear when playing music though.

I've had a dig around, and thus far haven't managed to find anything similar for Ubuntu - does such a piece of software exist?

Just a bit of a shame that I have to bow my head in defeat and reboot into Vista when my flatmate's out and I want to crank the sounds up!

---

### Post by markbuntu on 2008-09-25
I have a 3D check box in the sound mixer for my C-Media sound card that does that, maybe you have one too.

I think VLC will also do that for you but I am not sure about that.

There is also an upmixing LADSPA effect in jackrack but you would need to send all your sound through jack. I have not tried the upmixer it so I can't really say how it works. 

There are directions to send all your sound through jack in my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

It may take some work to get it happening but once you get into jack, all sorts of effects are available to add depth to your sound. You should give it a try if you feel up to the challenge and let us know what you figured out.

For incentive, here is a screenshot of my Ubuntu internet radio player:

---

### Post by CholericKoala on 2008-09-26
In HH, I was able to upmix and use my 5.1 headphones.  It made the back turn on.  I opened up the volume control in the sound module in the top right corner and went to "edit", then "preferences."  In there is the option to turn on stereo upmixing.

---

