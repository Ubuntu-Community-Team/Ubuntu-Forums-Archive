---
title: "Record 24 tracks at once?"
date: 2007-11-16
forum: Multimedia Production
---

### Post by mojogil on 2007-11-16
Hello,
I am a non-pro live sound and recording guy.  I average about 2  gigs a month.  I'm considering migrating to linux, not because I'm dissatisfied with Windows, but because it seems as though there are some exciting things to learn with Linux and audio. It seems as though the Delta 1010 is the best bet for 8 channels of simultaneous audio from what I'm reading.  Has anyone had any luck using more that one device at a time?  If not is there any way to capture 24 tracks at once?

Thank you,
Gil

---

### Post by Stochastic on 2007-11-16
I have not done it myself, but there is some documentation on how use multiple soundcards as one big soundcard.  It does involve modifying a few configuration files etc.. but once it's setup then it should be no sweat to get 24 tracks recorded at once through ardour.  Here's an old link on how to set things up: [http://www.sound-man.co.uk/linuxaudio/ice1712multi.html](http://www.sound-man.co.uk/linuxaudio/ice1712multi.html) and if you do a google search for ALSA pcm_multi you'll find a variety of discussion on the topic.

here is an old bug report in Ubuntu's stream that looks to have fixed a duplex issue: [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/66657](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/66657) you might want to try contacting that developer to see if he/she still works with a multi-card setup.

If you're new to linux audio I'd grab ubuntustudio x86 as it's a nice hassle-free way to get most things up and running right out of the gates.  Let us know if you find any issues with multi-card setup.

---

### Post by mojogil on 2007-11-16
Thanks for the info.  I'll dig in and have a look.  I'm sure I'll have more questions as time goes on.  This is a great forum!
Take care,
Gil

---

### Post by kayosiii on 2007-11-18
The LInux Audio Users Mailing list might be a good place to find more info
  
[email]linux-audio-user@lists.linuxaudio.org[/email]

---

### Post by tgalati4 on 2007-11-18
Give dynebolic a spin:

dynebolic.org

I only have one Delta66 card that works well with it.  I'm under the impression it will work with multiple cards as the Delta series (envy24control driver) only requires an interrupt and IO address, no DMA, so as long as you can assign an interrupt you can install up to 4 cards.  There may be clock skew issues, but you can call one card the master and loop the spidf ports to the other cards and make them slaves to the master clock.  As I only have one card--I'm looking to purchase another--I can't comment on how well it works.

---

### Post by nalmeth on 2007-11-20
Just remember Delta 1010 don't have preamps (at least when I went to buy one), so you won't be using microphones.

Many devices allow you to daisy chain similar devices together, such as the firepod (with another firepod or firebox). With a workstation like Ardour, you should be able to handle many inputs simultaneously. 

If you are serious about live recording, I've heard the FireStudio is the best hardware solution for that. I think it costs money though :confused: lots of money :mrgreen:

---

### Post by Prefader on 2007-11-21
At one point, I had been using a 1010 and a Delta 44 simultaneously while dual-booting XP and Dapper (or maybe Edgy - don't recall).  I don't seem to recall having any problems with setting up both cards, but this was a while ago, and I'm not remembering well.  I do know that I did a test capture of all 12 tracks simultaneously without any issues.  This makes me think that multiple 1010's is well within the realm of possibilities.

---

### Post by mojogil on 2008-03-09
Thanks everyone for the heads-up.  I saw on the FFADO sight that the Focusrite Saffire Pro might be supported.  I'm going to check into perhaps getting 2 of these units working.  I see that it has 16 channels of lightpipe each unit.  I would only need a way to convert from audio to lightpipe but I know there are many devices that do that.
I've been diving into ardour and really liking it.  I don't quite like it as much as Samplitude on Windows but I'll get used to it.
After I solve this issue I'll need to be posting again as I dive into midi for the first time.
Thanks,
Gil

---

### Post by drunkmatador on 2008-05-06
> **nalmeth said:**
> If you are serious about live recording, I've heard the FireStudio is the best hardware solution for that. I think it costs money though :confused: lots of money :mrgreen:

Unfortunately, the Firestudio does not yet have linux support. I didn't know this when I purchased it, so now it is the reason why I still have xp installed on my system.

---

### Post by fgreenway@gmail.com on 2008-05-06
I use a Delta 44 with an external mic preamp.  No problem recording from a mic into Ardour

---

