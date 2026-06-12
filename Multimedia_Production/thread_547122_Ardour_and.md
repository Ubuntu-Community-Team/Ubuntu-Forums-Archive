---
title: "Ardour and?"
date: 2007-09-09
forum: Multimedia Production
---

### Post by uputer on 2007-09-09
Okay, I am a newbie when it comes to Linux/Ubuntu but I was recently reading about Ardour and other music-oriented programs.

I was wondering about the current offerings:
Ardour, Rosegarden, and Audacity.  Is there any others?

I am somewhat familiar with Audacity having limited exposure.   Mostly with playing and editing mp3s.   

I am mostly curious and would like it if someone could compare these programs to those used in Windows and Apple systems (i.e. Cubase and Pro Tools).   If anyone could compare to Cubase and Pro Tools, that would be a bonus.  (Examples, ease of use, options, number of tools, etc. etc.).   

Does anyone use the Linux ones and do you know how they compare?  Which soundcards would be  good for them?   I am thinking of getting an M-Audio sound card in the future.  I know of a friend who got one.   

Also, is Ubuntu (well, preferably, Kubuntu) sufficient to use these programs with and/or is there distros which are suited for these  tasks?   I just want to experiment and I am just curious what the options are.   

Thanks in advance for any responses.

---

### Post by brummer on 2007-09-10
hello

there is a good page to start and find all interresting multimedia distros and apps for linux[http://linux-sound.org/]("http://linux-sound.org/")

brummer

---

### Post by Stochastic on 2007-09-16
Hi, just thought I'd toss my opinion into the ring.  

First a bit of my background: I'm a music composition student at Simon Fraser University (Vancouver Canada) and I've been working with audio programs on Windoze, Mac, and Linux (Debian and Ubuntu mostly) for many years, doing many different things (rock band recording/mastering, notation editing, DJing house parties, sample-based avant-garde music editng, etc...).  I'm currently running UbuntuStudio [http://ubuntustudio.org]("http://ubuntustudio.org")  as my one and only active OS.

In my opinion, pro audio and Linux are just beginning a seriously great relationship.  There is a long way to go, but it's really starting to come together.

- My favorite audio editor: Rezound
- My favorite audio mastering software: Jamin
- My favorite multi-track recorder: Ardour wins only because it's free and hardware independent, pro tools [non-linux software] has more functionality but I'm not about to pay for it and their silly soundcard.
- My favorite notation editor: Lilypond (Sibelius and Finale [non-linux software] are both more intuitive for the beginner though)
- My favorite music creation software: ChucK - This I don't expect many people to share with me.

You mentioned Cubase, if you're familiar with that style of working, I'd suggest trying Rosegarden.  It's not the same but its approach to music making is the same.  There are also a few newer progams such as Wired and Jokosher that are similar.
Overall I love the QJackCtl software patching interface, it makes many tasks extremely simple and hassle-free.

As for soundcards, do a google search for alsa then another for freebob and take a look at what cards those projects support.  The alsa cards are a little more hassle free right now.  I personally dislike the M-Audio sound quality, but for the average musician they're great.

Kubuntu should be okay but if you're really getting serious I'd suggest trying UbuntuStudio (they're very similar).  When I was running Ubuntu I did have some issues getting Jack set properly until I ran a few audio patches on my kernels (do your research if you want to go that route).

---

### Post by uputer on 2007-09-18
Hey, Stochastic, that is exactly the kind of info I'm looking for, thanks!

> **Stochastic said:**
> 

As for soundcards, do a google search for alsa then another for freebob and take a look at what cards those projects support.  The alsa cards are a little more hassle free right now.  I personally dislike the M-Audio sound quality, but for the average musician they're great.

Kubuntu should be okay but if you're really getting serious I'd suggest trying UbuntuStudio (they're very similar).  When I was running Ubuntu I did have some issues getting Jack set properly until I ran a few audio patches on my kernels (do your research if you want to go that route).
Okay, I will look into it.

About alsa and soundcards, I researched but I can't find anything recent yet.   So, which sound cards for Linux do you recommend?   I am wondering for the same functions you speak of, making/producing music.   I don't need it for gaming.  

MAudio and Creative are the only ones that come to mind but if there is something with better Linux support and better for musician/music manipulation/production, then I'd be interested in discovering that.

---

### Post by Stochastic on 2007-09-18
When it comes to soundcards for audio production the sky is the limit and the lower you go the more risk you have of poor audio quality.  Basically what it comes down to is what's your budget and what are your needs?

In the good to great audio range I'd recommend checking out the freebob (aka fado) driver [http://freebob.sourceforge.net/index.php/Main_Page](http://freebob.sourceforge.net/index.php/Main_Page) as firewire devices tend to be quite high quality for those on a budget.  The downside is that (from what I know - I'm sure there's hacks around this though) all audio has to go through the Jack driver.  This is fine for audio production software but when it comes to things like playing a youtube video you may need to end up using your comp's built in card.

The other issue to consider is what features do you need.  I personally don't do much recording of ensembles so I don't need too many ins but I do a lot of surround mixing and mastering so I need a full set of 8 outs.  Will you be needing MIDI? Is mic preamp quality something you're worried about? etc..

As a general rule, don't get anything that can't do 24bit 96khz recording - it's just become the industry standard now.

Other than that, I'd say in general the more you pay the better the card (this is NOT a rule, just simply a guideline for beginners).  Buy the card from a music store, not a computer store, and do your research before you buy to make sure it's supported.

A couple brands to check out (not all cards are supported): Mackie, Presonus, Focusrite, RME, Edirol, M-Audio, Tascam, Echo, Terratec

What do you plan to use the card for?

---

### Post by uputer on 2007-09-18
I'd like to experiment with recording from a musical instrument.  I own an electric guitar and amp and my brother owns a keyboard.  I might want to buy my own keyboard down the road.   I'd just like the options so I'm mostly looking at the M-Audio products since I researched and found some that might be good.  

Which is the best out of:  Delta 66, Delta 1010LT, Audiophile 2496?

Or is there other products that are as good or better?

How many pci slots should I go for regarding a motherboard?  Do I need firewire?   My current computer has firewire.   But, I haven't decided on the second computer's motherboard.   Perhaps, I don't need it?  

I am looking at the Gigabyte DS3R.   Anyway, I wasn't going to spend much on it for now.   But, some of the 'Delta' or M-Audio cards/hardware  look decent as I definitely don't need the best right now.   It would be enough to configure in Linux as it is (probably). ;-)

---

### Post by Stochastic on 2007-09-19
well if you're just starting an M-Audio would work fine.  There are many others around that same price range with similar features (check roland-Edirol out as an option).

Out of the cards you mentioned, here's the specs page:
[http://www.m-audio.com/index.php?do=products.list&ID=pciinterfaces](http://www.m-audio.com/index.php?do=products.list&ID=pciinterfaces)

I used to run a Delta 44 and it was quite nice though it lacked in features such as MIDI.  But an M-Audio UNO gave me that [http://www.m-audio.com/index.php?do=products.list&ID=usbmidiinterfaces](http://www.m-audio.com/index.php?do=products.list&ID=usbmidiinterfaces)
I've moved on from this setup now and actually still have the Delta 44 in a box.  If you make me an offer I'd sell you it for a reasonable price. (PM me)

You really only need to have 1 pci slot open for a soundcard.  as for firewire, it'd be a smart option to keep available if you chose to get a higher end card down the line.

---

### Post by qman_txun on 2008-06-20
Hi Stochastic, I'm in a rural area in Guatemala, close to the border of Mexico, it has been 2 years since I started to Record local music like Marimba, then some cothlic group with 3 to 5 persons but then it has getting growing, just last month I recorded a christian group of 8 where I couldn't get the sound I want and they want because they have recorded in Guatemala City. What I have done before, I just plug the instrument's cable to a behringer mixer to a M-Audio 2496 soundcard using Audacity either linux/windows (now 90% linux and would like 100% ubuntustudio) but sometimes they hit the instruments hard then it changes volume, so just this week I got the M-audio Delta 1010LT soundcard which you don't really like but that the only option in third country. Just today, I'm searching for informations how to record several tracks simultenously and the option that clears out is using Jack Server, Jack Control Kit and Ardour. Well I got one track figured out to record and I hope is the same with several tracks but mixing the tracks and mastering, I have been looking for informations for at least a year now and I haven't figured out how to do it, so I'm looking for somebody that could teach a little bit more about mixing and mastering (100% linux). How much could you charge to instruct me how to do it, should I need to travel there or you could come for vacation in my little town called Todos Santos Cuchumatan, Huehuetenango, Guatemala? My town is not that very poor but it is, so what my idea is to use the culture, traditions, religions, etc as my resources to make a living.

Thank you, Rosendo Pablo

---

### Post by qman_txun on 2008-06-20
Hi Stochastic, I'm in a rural area in Guatemala, close to the border of Mexico, it has been 2 years since I started to Record local music like Marimba, then some cothlic group with 3 to 5 persons but then it has getting growing, just last month I recorded a christian group of 8 where I couldn't get the sound I want and they want because they have recorded in Guatemala City. What I have done before, I just plug the instrument's cable to a behringer mixer to a M-Audio 2496 soundcard using Audacity either linux/windows (now 90% linux and would like 100% ubuntustudio) but sometimes they hit the instruments hard then it changes volume, so just this week I got the M-audio Delta 1010LT soundcard which you don't really like but that the only option in third country. Just today, I'm searching for informations how to record several tracks simultenously and the option that clears out is using Jack Server, Jack Control Kit and Ardour. Well I got one track figured out to record and I hope is the same with several tracks but mixing the tracks and mastering, I have been looking for informations for at least a year now and I haven't figured out how to do it, so I'm looking for somebody that could teach a little bit more about mixing and mastering (100% linux). How much could you charge to instruct me how to do it, should I need to travel there or you could come for vacation in my little town called Todos Santos Cuchumatan, Huehuetenango, Guatemala? My town is not that very poor but it is, so what my idea is to use the culture, traditions, religions, etc as my resources to make a living.

Thank you, Rosendo Pablo

---

