---
title: "Want to purchase new sound card, looking for Linux compatibility"
date: 2008-11-11
forum: Multimedia Software
---

### Post by das letzte einhorn on 2008-11-11
My Audigy2 sound card has provided me very good sound since it's purchase in 2003, however I feel now that I should move on with a new card which could allow me to plug my guitar signal into the computer and record with the Ubuntu Studio components, as well as getting sound quality which could match the quality of my actual headphones (SennHeiser HDR136).

From the research I have been doing, it seems sadly that there is only Creative Labs which produces a sound card which would be an interesting hybrid between capabilities for typical day-to-day music playback / gaming and recording. I had an X-Fi Platinum when Hardy Heron was released, and I did not manage to make it work with the HOWTO posted on this board at that time. Therefore I downgraded to my previous card (Audigy2) and got rid of the X-Fi platinum. I have noticed however that Creative Labs finally released a source driver compatible ([http://arstechnica.com/journals/linux.ars/2008/11/06/creative-releases-linux-x-fi-driver-under-the-gpl](http://arstechnica.com/journals/linux.ars/2008/11/06/creative-releases-linux-x-fi-driver-under-the-gpl)) but according to the article it is not ready to be used. There is also a HOWTO for that driver here ([http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)), but many users report that it does not work for them.

Hence, I am now wondering..

- Despite not being ready, with that driver released and probably further time invested on it, should I begin to look and invest into an X-Fi card? Are the Titanium Fatal1ty Champion & Pro cards worth the 200$ they are priced at?  What other recommendations within the non-discontinued X-Fi catalog do you have?

- Are there other alternatives to Creative Labs which I should invest and which are compatible with ALSA? I noticed HT Omega for example, but I have never heard of their products before. I would be glad to hear what you guys have tried; that could definitely help me to make my purchase more wisely.

Thanks!

---

### Post by markbuntu on 2008-11-11
M-audio and RME cards are professional quality cards that mostly work out of the box but tend to be expensive. If you are going to spend real money on a sound card thinking you might be using it for professional quality recording, you should really consider them. The difference between these companies and creative is that they have always put quality recording/playback capability first as opposed to creative which concentrates on gaming.

C-Media cards also work OOB and are dirt cheap compared to creative cards with the same specs. 

It also seems that some people are actually having success with the latest Creative driver release:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

You should check here for a comprehensive list of sound cards compatible with alsa:

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by Psychopsia on 2008-11-12
The problem of Creative X-FI, those cards are not working all the features like the console and the realtime effects on the card.

M-Audio is a good option, check this out: [http://www.linux.com/feature/126408](http://www.linux.com/feature/126408)

---

### Post by das letzte einhorn on 2008-11-13
> **markbuntu said:**
> M-audio and RME cards are professional quality cards that mostly work out of the box but tend to be expensive. If you are going to spend real money on a sound card thinking you might be using it for professional quality recording, you should really consider them. The difference between these companies and creative is that they have always put quality recording/playback capability first as opposed to creative which concentrates on gaming.

C-Media cards also work OOB and are dirt cheap compared to creative cards with the same specs. 

It also seems that some people are actually having success with the latest Creative driver release:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

You should check here for a comprehensive list of sound cards compatible with alsa:

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

Well, let's face it: I would like to be able to record demos of my stuff on the computer, but I also game a lot too. So a hybrid between both would be great. In terms of budget, I am not ready to invest more than 200$; I am not a power gamer nor a professional musician. I was looking for C-Media cards (the 8787 and 8788) on NCIX.com and Ebay, and they are not listed on their items list. Are they only available at special retailors? I already knew about the compatibility list; I wanted to check however if other users had experience with other retailers and how it went.

@Psychopsia: Do you use an M-Audio card? If yes which one? From what I have looked at on the M-Audio website, it might just be my ignorance, but I can't see any inputs for 1/8 jacks for either headphones or speakers. Example: [http://www.m-audio.com/products/en_us/Audiophile192.html](http://www.m-audio.com/products/en_us/Audiophile192.html) and [http://www.m-audio.com/products/en_us/Delta44.html](http://www.m-audio.com/products/en_us/Delta44.html) .

---

### Post by Cracauer on 2008-11-13
I bought this one this summer. Using under Debian with native kernel:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16829118109](http://www.newegg.com/Product/Product.aspx?Item=N82E16829118109)

I use it for recording, so good shielding is important. It has it.

The only issue is that although ALSA supports SPDIF input on this card the sound is distorted. A newer ALSA snapshot made it worse (and paniced the machine every now and then), so I guess some more waiting is in order.

Otherwise I'm very happy.

---

