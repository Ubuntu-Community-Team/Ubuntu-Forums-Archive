---
title: "Headphones and high definition"
date: 2009-03-30
forum: Multimedia Software
---

### Post by kumoshk on 2009-03-30
I just got a new laptop a while ago and it supports high definition audio. It sounds great if I plug my extra speakers into it (it's even loud enough). It does not sound great with the default speakers. I tried my headphones on it, and I was disappointed that they didn't sound very good, either, even though I thought them comparable to the speakers when used on my desktop.

Anyway, I was wondering if anyone has suggestions on some good headphones to get for this laptop—hopefully ones that are quite under $40 that will last a long time. My speakers I've been using weren't too expensive, and they've been around since before the high definition era, I believe.

I have the beta 64-bit version of Jaunty on the laptop. I have Conexant High Definition SmartAudio 221 nvidia HDMI audio. It doesn't really have an HDMI port, though, although there is a place where one could be with plastic over it. So, I'm not looking for something that requires an HDMI port.

---

### Post by aeiah on 2009-03-30
have you tested your speakers and headphones with another audio source? you may have perfectly good headphones and be wasting your money getting another pair you see.

what do you mean by high definition audio anyway?

---

### Post by kumoshk on 2009-03-30
> **aeiah said:**
> have you tested your speakers and headphones with another audio source? you may have perfectly good headphones and be wasting your money getting another pair you see.

what do you mean by high definition audio anyway?

To be honest, I don't really know what I mean by high definition audio—that's just what the computer says it has. Is there more than one thing referred to as high definition audio?

Thanks for the tip about other audio sources. Do you mean to go into the sound preferences and change from Autodetect to something else?

I actually should get another pair of headphones one of these days anyway, though—the current pair is somewhat broken as far as the plastic structure goes so that they can pop out of place while I'm wearing them (they function fine, though, sound-wise on other devices; it's not that they sound terrible on the laptop, but it is noticeably much lower quality than the speakers I have). I've tried super-glue and that works fine for a while, at least. Anyway, I'll have to try out that suggestion and let you know how it goes, but if you have any suggestions on headphones that aren't too expensive still, feel free to let me know.

Thanks!

---

### Post by kumoshk on 2009-03-30
> **kumoshk said:**
> Anyway, I'll have to try out that suggestion and let you know how it goes, …

Um, I went to test it out so that I could compare quality before changing anything and well, it sounds fine now. I don't know what the deal is. Maybe it's a program specific problem.

I don't remember what program I was using before, but this time I decided to use Rhythmbox with CD quality FLAC files, and it sounds just as well on the headphones as on the speakers. I don't think I've changed anything about the computer—not even updates—since my last comparison. It sounds fine with lower quality MP3s in Rhythmbox, too.

Maybe the problem was just that I had been listening to audiobooks too much that day and it made the headphones sound bad when I went to listen to music, but somehow I think it's something more. Let me try Totem now and see if it sounds fine. Yep, Totem sounds fine, too. Maybe it was me listening to the FLAC files over a daap share that caused the problem. Maybe it was even on PowerDVD. I'll have to check that out, but I'll have to reboot to try PowerDVD since I have a 64-bit OS, and I need to use my USB 32 bit Ubuntu for that.

Anyway, thanks for the help and for your faith in my headphones.

---

### Post by markbuntu on 2009-03-31
I have 3 or 4 pairs of headphones lying about and one thing is for sure, you get what you pay for.

---

### Post by logos34 on 2009-03-31
> **markbuntu said:**
> I have 3 or 4 pairs of headphones lying about and one thing is for sure, you get what you pay for.

well, maybe with big headphones, but as far as earbuds go, you don't necessarily have to spend a lot to get good quality.  I use a 5-yr old pair of Sony Walkman w/high-bass response ($15), and they sound fantastic--even compared to fancy Sennheisers (I hnestly can't tell the difference)

High-def audio means the sound card capability.  HD Audio sounds a LOT better.  But one way to make up for it if you don't have it is to pipe your audio through a stereo receiver/preamp (rca jacks will do just fine, don't even really need optical/coaxial).

---

### Post by markbuntu on 2009-03-31
Earbuds, meh. They really bother me.

Anyway, I do run my sound into a receiver with a nice pair of klipsch speakers. My c-media card says nothing about hd and it sounds better than the hd chip on the mobo, probably the 3D.

44.1k is 44.1k no matter how you slice it and my AC'97 has that. The hd designation is just marketing hype. If these chips really were HD they would be eight channel 196k. But then what would they play?

---

### Post by Xavier Oddmon on 2009-04-01
Doesn't the term the sound card companies use, "HD Audio," generally mean that the sound card has digital audio out?
[QUOTE]well, maybe with big headphones, but as far as earbuds go, you don't necessarily have to spend a lot to get good quality.
And i'll second that. My favorite pair of wired headphones were a cheap pair of 'noise canceling' ear buds I got at walmart for $25. The noise canceling worked surprisingly well, although it did distort the audio, but they sounded excellent when it was turned off. I bought them on a whim, and was quite pleased with them. (Unfortunately, they were mangled when I went under a tree while mowing the lawn, and they no longer resemble earbuds.) Now, however, i've got bluespoon spider A2DP headphones, and they're awesome.

---

### Post by aeiah on 2009-04-01
> **kumoshk said:**
> Um, I went to test it out so that I could compare quality before changing anything and well, it sounds fine now. I don't know what the deal is. Maybe it's a program specific problem.



it might have been something to do with volume. if i have everything set to max then the signal gets clipped and distorted and sounds crap on my speakers (with my speaker volume set to anything, loud or quiet). i usually make sure my volume sliders in ubuntu dont go beyond 80-90%, although for earphones you might need to break that rule since they havent got their own powersource like pc spearkers do.

HD in terms of video has a very specific quality to do with pixel resolution etc, but for audio, its really just a buzzword.

---

### Post by mcduck on 2009-04-01
Intel HD Audio (or Intel High Definition Audio) is just Intel's marketing term and rather loose standard that any manufacturer can print on their product if it has certain Intel chip and is able to produce multi-channel audio at certain bitrate (and the manufacturer pays Intel some money).

The "standard" is rather loose, and has nothing to do with the actual sound quality. It allows even replacing most of the hardware with driver software making your processor do the audio processing tasks instead of having proper sound chips to do the job.

In other words, just a buzzword that manufacturers can print on almost any hardware if they pay some money to Intel. :D

Edit for a quick example:

My previous desktop machine had rather nice audio features, using nVidia's SoundStorm chip to provide stuff like hardware-accelerated DolbyDigital encoding of all sound to digital sound outputs, and Realtek codec chip for ananlog outputs. Since the system had no Intel chips it didn't have "Intel HD audio-certificate".

At the same time my friend had a cheap Intel motherboard with most basic quality integrated audio, with the same Realtek codec chip and Windows driver to handle the Dolby Digital encoding (meaning quite high CPU usage if the DD output was enabled). The motherboard also had a rather high noise levels on audio. It, of course, had "Intel HD Audio" printed in every possible place.

---

### Post by logos34 on 2009-04-01
> **mcduck said:**
> 

The "standard" is rather loose, and has nothing to do with the actual sound quality. 
...
The motherboard also had a rather high noise levels on audio. It, of course, had "Intel HD Audio" printed in every possible place.

The Intel HD Audio chip on my Intel board (D915gav) sure sounds markedly better than that on my Realtek sound card.  Maybe it's just that the latter is *really* bad and makes anything else sound good by comparison...

---

### Post by mcduck on 2009-04-01
> **logos34 said:**
> The Intel HD Audio chip on my Intel board (D915gav) sure sounds markedly better than that on my Realtek sound card.  Maybe it's just that the latter is *really* bad and makes anything else sound good by comparison...

Sure, "Intel HD Audio"-certified setups can be good. Or bad. Or anything in between. The point was that only thing this sign on your hardware really tells is that it includes some Intel chip(s) and the manufacturer paid Intel to get the certificate.

---

### Post by kumoshk on 2009-04-02
I've decided to experiment and order some cheap earbuds that had some unusually nice-looking specs. I studied up on head phone specifications&#8212;that's something I would recommend doing, although I understand the only way really to know if I'll like them is to try them out. Anyway, if I forget, remind me to tell you how they turned out, since there weren't any product reviews. I'd like to tell how they work on and off high definition compared with my other headphones, and if they last very long. Some cheaper headphones sound great, but they don't last long.

Here's the link:
&#8226; [http://www.magoenterprise.com/simi-neck-strap-style-stereo-earphones-for-mp3-and-mp4_ep15.html?osCsid=8fbac0a864099c38a06fc1814ced1f39](http://www.magoenterprise.com/simi-neck-strap-style-stereo-earphones-for-mp3-and-mp4_ep15.html?osCsid=8fbac0a864099c38a06fc1814ced1f39)

I'd be careful if you use this store, though, as the number of items added to the shopping cart isn't always what you intend (I commented to them about this, so hopefully they'll fix it), and the default shipping is the most expensive (it can be lower). But, if you know that, it doesn't seem so bad. I used Google Checkout to make ordering more secure, though (i.e. no sign-ups and such).

Anyway, some things I considered were the following:
&#8226; The magnet metal used&#8212;neodymium is said to be preferred, as it is said to be the strongest magnet, and is supposedly good for bass; the amount and density of the metal should also be considered if possible (and perhaps the coating, as well)
&#8226; Impedance (Ohms)&#8212;lower means it takes less power (although I should note that many sets of expensive headphones have high impedance)
&#8226; Sensitivity (dB)&#8212;higher means it can get louder (sometimes even cheap headphones can get annoyingly loud, though)
&#8226; Response bandwidth (Hz range)&#8212;I believe a wider range means it can include a wider range of sounds (although this may or may not be noticeable to the human ear); an average headphone range is probably between 20 and 20,000 Hz
&#8226; Other random stuff

---

### Post by kumoshk on 2009-04-06
All right, so they've arrived and I'm testing them out.

They're definitely worth more than the $3 I paid for them, although there are some things you should know if you want to get some.

Anyway, they sound nice, good and clear. I don't know that I notice a 'huge' difference in quality between them and the headphones I had been using (there are some things about these I like more and some things about those I liked more), although they do sound significantly different in some ways&#8212;it's probably a preference thing more than anything.

They don't get nearly as loud as the specs might lead one to believe (at least on my laptop). The sound quality is probably best when turned up loud on these earbuds, although it does sound good. There is a lot of treble, although it's not bad-sounding treble with no bass&#8212;there is reasonable bass, and percussion sounds are quite audible. Sound-quality-wise, I like them more than the pair of Gumy earbuds I got for listening to audiobooks (these aren't the non-earbud headphones I had been using; those were Phillips brand, and they came with an MP3 CD player a few years ago; maybe I'd say they're about equal to the Phillips ones, although the things I like about them aren't same things I like about those; comparing earbuds to normal headphones is always an interesting process). The wires on it are made out of an atypical substance. It's like some sort of threaded/twisted metal surrounded in plastic, like they use on some bike locks (only thin); this could be a good thing, but I'm not sure. They didn't come with a neck strap&#8212;I don't mind, although they were advertised as coming with one (even on the box when I got them). There are two bead things to adjust the length where the wires divide, although they are quite loose and can slip, but I don't see it as a huge deal, since the cord isn't super long anyway, and the top one seems to hold, at least.

I have no idea how long they'll last. The materials don't appear the be the most expensive-looking sort, as for the tip that plugs in and some of the chrome-colored plastic on the headphones themselves, but I consider it possible that they could last a good while. I don't think they'll blow any time soon and make that permanent static-type sound soon that some headphones I've had in the past had, but you never know. The black plastic on the head pieces does seem to be high quality, though, and they do seem sturdy. They don't feel bad in my ears, but they are earbuds, and not the sort that sink further in, you should know. The ear pieces are bigger than the Gumy earbuds' though.

---

