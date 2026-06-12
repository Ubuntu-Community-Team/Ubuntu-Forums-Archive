---
title: "Recording from Vinyl Decks"
date: 2007-09-27
forum: Multimedia Production
---

### Post by simonfiction on 2007-09-27
Hi,
I have a pair of Technics 1200 with mixer and I'm looking to try and record my own mixes. I've done a bit of research but can't find a comprehensive guide on everything I need to do this. Am I right in saying that I basically need to install the low-latency package from the repo, install Audacity and I'm ready to go? Or is there much more tweaking involved? I'm running edgy eft. 

Thanks,
Si

---

### Post by djxcon on 2007-09-27
There really isn't much to it.  You need some type of input on your sound card to capture the audio from the outputs on your mixer.  Next you need software to record the data coming in through the sound card.  Audacity is a great choice however I prefer to record in Ardour (This is really an amazing piece of software!).  For more information about Ardour, visit [http://www.ardour.org/]("http://www.ardour.org/")

For the kernel, I believe the default kernel would work though I am using a low latency kernel packaged with Ubuntu Studio.  I am also using an M-Audio 2496 PCI sound card which works great.  

Finally, I am using ALSA (Advanced Linux Sound Architecture) which is the way to go if your sound card is supported.  For more about sound cards and compatibility, visit [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

So go ahead and download some software and rock out a mix or two.

---

### Post by simonfiction on 2007-10-01
Awesome. Thanks for the advice.

Si

---

### Post by dabl on 2007-10-02
> **simonfiction said:**
> Hi,

 Am I right in saying that I basically need to install the low-latency package from the repo, install Audacity and I'm ready to go? 

 It can be just about that simple.  :)

> 
Or is there much more tweaking involved? I'm running edgy eft. 

Or it can be as devilishly complicated, on both the analog and digital ends of the process, as you want to make it!  Have you Googled "cartridge and stylus" lately?  :lolflag:

I recently finished recording a collection of 78 rpm records from the 1930s and 1940s, which is WAY more complicated than 33.3s.  Then more recently I've been working through some of my vinyl from the 1960s and 1970s. It's amazing how much the quality varies, from one good-quality album to the next, played on the same analogue system.  If you're inclined to obsess about the quality, you might never finish the project.  My advice is to put some serious attention into the tonearm/cartridge/stylus setup, so you're getting the best possible signal through the pre-amp and into your "line in" port, and then just start capturing.  On the digital end, there is no end to the amount of time you can sink into de-clicking, de-noising, and de-crackling, but it never gets any better than the original signal you got off your vinyl, so that's where the real effort needs to go.

Good luck -- have fun!  :guitar:

---

