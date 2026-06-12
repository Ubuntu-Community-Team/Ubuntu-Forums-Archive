---
title: "DJplay and Jack"
date: 2008-03-11
forum: Multimedia Production
---

### Post by Nunu on 2008-03-11
Ok so I have one on board sound card and one Creative sound card. Both are working like they should. My problem is when i try to run DJ play through the on board sound card,  jack only detects the creative sound card. the idea is to run djplay through the on board card with 2 channels one for each CD jay, these goes into my mixing desk and from my desk i go into the line in on my creative card. so here is my question how can i force jack to use the via card that is on board and ignore the creative card?

---

### Post by GameGod on 2008-03-11
In QJackCtl, click "Setup", and on the right there's a box that says "Interface". Click the arrow beside it  and select whatever soundcard you want JACK to use.

---

### Post by Nunu on 2008-03-11
No Go Still pumps it through the Creative card for some reason.

Thanks for the reply though

---

### Post by Stochastic on 2008-03-11
GameGod was pointing you in the right place.  Which interfaces are listed?  Is the onboard soundcard even seen by JACK?  What about trying the input device list or output device listing?  Does ALSA know your onboard card exists, i.e. have you ever had sound through it?

---

### Post by Nunu on 2008-03-12
> **Stochastic said:**
> GameGod was pointing you in the right place.  Which interfaces are listed?  Is the onboard soundcard even seen by JACK?  What about trying the input device list or output device listing?  Does ALSA know your onboard card exists, i.e. have you ever had sound through it?

Yeah JACK sees it no problem and i can select it, but if I go to the connect option were you connect the four outputs from DJ play to your sound card. under ALS there are only two channels and both of them belong to the Creative card. 

Interesting thing that i noticed yesterday is that if you open Mixxx i can only get output from either or. i cant even point the CD jays to one sound card and the headphones to another. simply reloads none in the list once you select the second sound card. it does the same with both creative and Via. So i can have either the Creative or the Via play but can't point it to use the Creative as primary and the Via for the headphones or visa versa.

---

### Post by Stochastic on 2008-03-12
have you tried explicitly calling one soundcard as your input device and one as your output device in JACK settings panel?

---

### Post by Nunu on 2008-03-12
> **Stochastic said:**
> have you tried explicitly calling one soundcard as your input device and one as your output device in JACK settings panel?

I have done that yes. It seems to only want to use the Creative card. I also notice that i can set the VIA card in the volume control box to 2, 4 and 6 channel mode but neither Jack or Mixxx sees the additional channels only the primary channel of the VIA card is noticed, wonder if that is not the issue. Maybe the channel mapping is of in JACK.

---

### Post by Kyosama66 on 2008-05-02
I think I might be having the same problem...
I use a Dell D610 Notebook with an INTEL ICH6 - IEC958 (I think, that's what i have JACK configured to use) and i have DJPlay 0.5.0-2. JACK starts, and i can set it up to work with Mixxx, but i kinda hate the interface, so DJPlay was the alternative. I can get DJPlay to open, and i can get tracks into the players, the waveforms move, but i dont get any sound output, either through the headphone jack, or the pc speakers. Where can i configure the settings, or how do i patch DJPlay with JACK?

---

