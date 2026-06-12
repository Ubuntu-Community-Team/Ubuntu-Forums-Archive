---
title: "Headphones and Alsamixer on an Acer Aspire 5738"
date: 2009-07-26
forum: Multimedia Software
---

### Post by Sennacherib on 2009-07-26
Hey all

I've been looking through the forums trying to get the headphone jack to work on my Aspire 5738 which is running Jaunty (i.e.: nothing happens).  When I brought up Alsamixer in the terminal the headphones option was zero with no bar to raise it.  Does this mean it isn't recognised by Alsa mixer?

---

### Post by lordL on 2009-08-09
I'm having the same problem, also on a 5738. So far I have found a number of ideas for solutions, but thus far none of them have actually worked. Here is some of what I've tried:

After a while I managed to get to the point where I do actually get sound in the headphones, but then there is also sound coming from the built-in speakers at the same time. I got thus far by following this guide: [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

The suggested solution that seems to pop up several places is that of editing */etc/modprobe.d/alsa-base*, by adding the line *options snd-hda-intel model=xyz* (where xyz is to be replaced with the correct magic word). See this thread: [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

The suggest value "ACER" does not seem to do the trick, I still have sound in both speakers and headphones simaltenously. 

I can however, by using the gnome-alsamixer, change the volume of the speakers and/or headphones indenpendently. Having to do this manually however is not an ideal solution, I would much more prefer to simply have all sound output automagically in the headphones whenever I plug them in.

Any ideas are welcome! I'll post back if I find a solution that works.

---

### Post by openware on 2009-08-10
Same problem here with Acer Aspire 5738 : )

---

### Post by openware on 2009-08-14
options snd-hda-intel model=auto 
seems to work fine for me : )
When i connect headphones they work and the built-in speakers are going mute.

---

### Post by aleivag on 2009-08-14
the option "ptions snd-hda-intel model=auto" in the alsa modprove config file worked on my acer 5738. now headphones and speakers work as two separated beast

thanx a lot

---

### Post by Celi* on 2009-09-04
'options snd-hda-intel model=auto' does not seem to work for me... My headphones don't work and sound keeps playing from the laptop's speakers.
Is there anything else you did for it to work, or you just added the line on the conf file?
Any chance it conflicts with something else I have installed or some configuration?
:confused:

---

### Post by temansetiaanda on 2010-05-18
'options snd-hda-intel model=auto'  works for my laptop, acer aspire 5051 on Ubuntu 10.04 fresh install..

thanks for the solution ! :P

---

### Post by hsmock on 2010-05-19
Asus G50V laptop.

My problem was slightly different. When plugging in my headphones, or external speakers into the audio jack. Internal speakers would mute, but no sound came out of the external audio device.  Pulling the plug out slightly would cause sound to play through my headset, or external speakers, but with a noticeable hum. 

Seems to be a sound routing configuration issue with the intel sound chips.

Placing the "**options snd-hda-intel model=auto**" in the options section of** /etc/modprobe.d/alsa-base** was the solution, as well. 

Thank you for the solution.

---

