---
title: "Sound card recommendation needed for Ubuntu 10.04"
date: 2010-05-26
forum: Multimedia Software
---

### Post by rick333 on 2010-05-26
Does anyone know of a sound card that works out-of-the-box with Ubuntu 10.04? I need speakers and microphone to work. 

I have already spent many hours with the various help guides trying to make my current sound card work (Creative SoundBlaster Audigy SE) to no avail. It works fine with the hated Windows, so the card isn't broken. With apologies to all the Ubuntu experts out there, I'm not interested in spending any more time messing with my configuration -- I just want to install a card and have it be recognized by the system -- and work. No drama, no hacking. Why is sound so hard to make work with Ubuntu? I love Ubuntu except for this.

Suggestions?

Thanks,

Rick

---

### Post by Royke on 2010-05-26
Hello Rick333 and fellow ubunteros.

There is proberbly nothing wrong with your soundcardsupport for linux. That means ubuntu can run it too. Your problem proberbly is PulseAudio related unless your card is not detected(?) I too had big systemproblems due to pulseaudio. The only thing i could do to have a stable ubuntu is to kill pulseaudio on login(it respawns, you have to disable that too!) Musicplayer-droppouts; latency too bad and a whole lot of other instabilaties that seem to be gone now. Only there is now another showstopper: no systemsounds.:( They seem to be somehow linked with pulse(i will find it, grrr:twisted:)
I hope there will be a better soundcard support or a fix for PulseAudio really soon and that your card plays music on Ubuntu now.:guitar:

---

### Post by rhinert on 2010-05-26
> **rick333 said:**
> Does anyone know of a sound card that works out-of-the-box with Ubuntu 10.04? I need speakers and microphone to work. 

I have already spent many hours with the various help guides trying to make my current sound card work



I ran into the same problem.  

I found a company on Ebay that sells used computer gear and I bought 3 different models of used sound cards for less that the price of 1 new one.  

I'm sure I can get one of them going.....

---

### Post by rick333 on 2010-05-26
rhinert, please let me know if you get any of them working with a standard installation. I'm not so much interested in hacking the installation to something non-standard because when I upgrade to the next Ubuntu release after 10.04, it'll probably just break again. No fun. 

Thanks.

---

### Post by rhinert on 2010-05-26
> **rick333 said:**
> rhinert, please let me know if you get any of them working with a standard installation. I'm not so much interested in hacking the installation to something non-standard because when I upgrade to the next Ubuntu release after 10.04, it'll probably just break again. No fun. 

Thanks.




Sure will.  

Just got an email that the cards were shipped out today via post office.  Most likely, I'll get them in early next week.  I'll update this thread then.......

---

### Post by desnaike on 2010-05-26
Sorry about your sound problems but that card I've used in all my linux installs and is known to be linux friendly So buying a new card might yield the same results no sound if the problem is not the card itself.

---

### Post by rick333 on 2010-05-27
Hi desnaike,

That's interesting information. Have you tried this sound card with Ubuntu 10.04?

Thanks,

Rick

---

### Post by rick333 on 2010-05-27
I tried a couple of other things with my Audigy SE card. 

1. I tried running the Ubuntu 10.04 LiveCD. Sound output works, but nothing from the microphone. Bummer.

2. I tried running Windows 7 in VMWare Player hosted on my Ubuntu 10.04 installation. When I tried to open the Windows recorder app, it says no sound cards recognized. I tried setting the VM's sound card to ALSA default sound card instead of Auto-Detect, and still no sound card recognized.

desnake, does your microphone work on your Audigy SE card?

Thanks,

Rick

---

### Post by rhinert on 2010-05-27
Rick333 -- I borrowed an audigy card, disabled the integrated sound card and did a fresh install.  It was recognized and configured perfectly, just like what the other poster was saying.  

Could you be struggling with a bad or intermittent soundcard?

---

### Post by rick333 on 2010-05-27
rhinert, so your microphone works with the Audigy SE?

In answer to your question, maybe I have a bad sound card. But it did work on Win 7 last time I tried (speakers and mic) -- I have a dual boot config.

My system has dual Opterons with on-board sound, but the system vendor informed me that I would need a separate sound card. Any chance the on-board sound could be interfering with the sound card? It doesn't show up in the sound preferences.

Rick

---

### Post by Royke on 2010-05-30
Mmm, as far as i know almost every soundcard needs configuration before you can record from the desired input. Once you did you can backup the settings for later use. 
Pulseaudio seems to work again here for output after some updates.
To my opinion the audigy card is well worth the trouble to learn to configure. Good luck:)

---

### Post by Royke on 2010-07-25
Dear rick333,

Just yesterday i bought the same audiocard 2nd hand in the computerstore here. On my machine i didn't succeed in getting the alc888onboard-card on a different IRQ. Therefore i bought this one and to be honest i thought of you in the store. I had to buy that one for sciënce and help also. But within a half hour(including building in) i was able to hear and record sound, without doïng more than clicking some settings. It has a very rich sound too, so i would say: stick to it!

Maybe you should select the correct input-output devices in system-preferences first or do a hardwaretest so you can view the ports it has? Look for the different devicenames it has. Then you now what to connect.

You can do it i believe..;)

---

