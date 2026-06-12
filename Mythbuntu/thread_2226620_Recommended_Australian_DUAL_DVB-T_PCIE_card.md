---
title: "Recommended Australian DUAL DVB-T PCIE card"
date: 2014-05-28
forum: Mythbuntu
---

### Post by lmclaren on 2014-05-28
Hi,

As the title says, I a in need of some new tuner cards as my old Fusion DVB-T Dual Express cards are beginning to fail.

The replacement Fusion card is the -2 and as far as I can tell is not supported under linux.

I am trying not to spend more than $80 each per dual card.

Any suggestions?

thanks
Lee

---

### Post by Lester_Burnham on 2014-05-30
Hi,

I use Sony Play TV's. If you're not familiar, they're USB dual tuner, with single antenna input. You can pick them up for around $55 delivered from ebay.
[http://www.ebay.com.au/itm/PS3-Play-TV-Australian-model-/151309058014?pt=AU_Video_Game_Accessories&hash=item233ab8ffde](http://www.ebay.com.au/itm/PS3-Play-TV-Australian-model-/151309058014?pt=AU_Video_Game_Accessories&hash=item233ab8ffde)

Otherwise, I've used hauppauge hvr-2200 which are pci-e. You will need to check the revision of the card you are buying will work first, for newer versions.
I prefer the play tv.

Lester

---

### Post by lmclaren on 2014-05-30
Thanks Lester,

I will keep that in mind for an option. I was hoping for a card. Small children in the house and cables don't mix.

There are quite a few cheap cards available but it seems that there is no linux support.

Lee

---

### Post by Chris_Rowling on 2014-05-31
I took my sony playtv adapter out as was disappointed in picture quality compared to fusion dual express. will plug it in this week and report back as to comparison (will mean 6 tuner system)

I have two second hand PCI fusions in a new box. they work ok, not as good as my tuners in the old beyonwiz DP-2 beside it. 

by dying, what is happening to your card/s?

only local card is dntv quad and mixed results with mythtv on net and certainly over $120. aimed squarely at windows market, so is support.

---

### Post by blm-ubunet on 2014-05-31
Might be worth considering DVB-T2?

AFAIK As Australia is only using mpeg2 for HD over DVB-T, it is probable a change to H264 is on the cards.
It makes sense to combine this change with a change to DVB-T2 for **new** services.
Will there be any new services or just shopping channels.

All the existing set-top boxes & TVs sold in last x years will work fine with H264 decoding but not DVB-T2.
TVs tuners will start to support T2 because it is used in UK etc.

New Zealand started (7 years ago) with H264 over DVB-T & mpeg2video over dvb-s.
DVB-T2 exists in NZ only for a private encrypted network (Sky).
So not so likely to see T2 here in FTA use soon.

So I would consider a dual or quad DVB-T2 card from likes of TBS because they have supported closed source drivers, also there are open source drivers for some of their h/w.

Sadly TBS cards are not cheap down-under.
DVB-T2 USB tuners are cheap not yet well supported.

[http://www.linuxtv.org/wiki/index.php/Category:DVB-T](http://www.linuxtv.org/wiki/index.php/Category:DVB-T)
[http://www.linuxtv.org/wiki/index.php/DVB-T2_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T2_Devices)

---

### Post by Chris_Rowling on 2014-05-31
Crow eating time

Sony Play TV minor stutter in live TV in HD (so do my Fusions) but picture is perfect.
Have rejigged to make it primary recorder so pleased.

Sorry about dissing Sony...
Everything except cable tidy as you note. Is your box big enough to put the Play TV inside? (mine same size as AV amp for cooling reasons). Cheap solution.

Regards
Chris

---

### Post by blm-ubunet on 2014-06-01
The PlayTV tuner can not make the picture better or worse or cause frame jitter unless it is faulty or signal level/sensitivity problems (macroblocking/dropouts).
A DVB tuner outputs a transport stream, no decoding/encoding of video/audio.

---

### Post by gga96 on 2014-06-02
I have been using a DigitalNow Quad DVB-T tuner for over a year now with out any problems.
Ask support about the issues or link to [http://www.digitalnow.com.au/](http://www.digitalnow.com.au/)

---

### Post by lmclaren on 2014-06-03
Thankyou everyone for the recommendations.

gga96, how did you go with drivers, was it supported 'out of the box'? I suppose $180/4 is not a bad price per tuner.

The Sony's are not a bad idea and cheap enough for me to pick one up to play with.

---

### Post by gga96 on 2014-06-03
The tuner is supported from 2.7 onward. For a manual driver install follow [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0#readme](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0#readme)

---

