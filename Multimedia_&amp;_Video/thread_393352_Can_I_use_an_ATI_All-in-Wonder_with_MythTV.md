---
title: "Can I use an ATI All-in-Wonder with MythTV??"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-03-25
Hi everyone,

I installed mythtv only to discover from the wiki that my video card (ATI Radeon X1300 All-in Wonder) is not supported.  Does anyone know of any fix I can use to get the two working together?

Thanks,
Douglas

---

### Post by djrobthaman on 2007-03-25
No fix???  :(

---

### Post by superm1 on 2007-03-26
Hi,

Sorry, there is no support for the ATI all in wonder cards.  There have been several strides made toward full V4L2 support from the gatos project, but nothing has materialized as of yet.

Alternatively, if you don't want to spend money on another tuner card, and you are in the US, you may be able to do firewire capture over a digital cable box.  Otherwise, start looking at other tuners if you want to do mythtv.

---

### Post by djrobthaman on 2007-03-26
Oh man, that's not cool at all.  I guess since mythtv is out of the question (at least for the moment) do you know of any other similar program that I can use with that video card?

Thanks,
Douglas

---

### Post by superm1 on 2007-03-26
Sorry, I can't comment much more on the topic.  Hopefully someone else around these forums can. :)

---

### Post by pedalwrench on 2007-03-26
Sorry to break it to you but the all-in-wonder function [TV-in] does not work and is not supported by ATI in Linux.  
I have been trying to get this to work for the last 2 years on my 9600 AIW.  There is GATOS, but it is a pain and barely works.  I am personally waiting for this card to die, then I will get a nvidia card and a hauppauge tuner.

Your best bet is to get a card that has driver support in Linux.  And never by ATI again.

References:
Mythtv Docs page
[http://www.mythtv.org/docs/mythtv-HOWTO-3.html#video_capture_device](http://www.mythtv.org/docs/mythtv-HOWTO-3.html#video_capture_device)

From the docs:
"NOTE:  The ATI TV Wonder series and the ATI All-in-Wonder series of cards
are not the same.  The All-in-Wonder cards will not work with MythTV.

NOTE: The ATI All-in-Wonder cards (which are not the same as the ATI TV Wonder, TV Wonder VE or TV Wonder Pro) will not work as a MythTV capture device because the GATOS [http://gatos.sourceforge.net](http://gatos.sourceforge.net) drivers that are available provide only a limited subset of the V4L API. The TV Wonder series of cards are supported by the Bt8x8 Video4Linux driver. "

---

### Post by djrobthaman on 2007-03-26
Those bastards....
Thanks for the info pedalwrench

---

### Post by djrobthaman on 2007-04-04
Hmmm.... I'm starting to have some more hope that maybe there is a mod out there somewhere.  The official mythtv wiki has an [ATI all in wonder how-to]("http://www.mythtv.org/wiki/index.php/ATI_All-in-Wonder_HowTo_%28English%29").

Does this mean I might be able to get this thing working??????

---

### Post by superm1 on 2007-04-04
Well that page is just explaining how to use the AIW for live purposes in xawtv.  No recording from what I see.

---

### Post by revaaron on 2007-04-08
you've got to be ******* kidding me.
the AIW doesn't work in mythtv?

why the **** am I bothering with this product them.
sucksucksucksucksucksucksucksucksucksucksuck.

sorry, I'm angry.

---

### Post by zolodon on 2007-05-02
Well...  This news stinks, but I'm glad to find some answers here before I started fighting my AIW card to get MythTV working.  Watching real-time TV with no other features on my PC is just not worth the effort IMO.

*adds another piece of hardware to the upgrade list*

---

### Post by prkfriryce on 2007-05-20
> **superm1 said:**
> Well that page is just explaining how to use the AIW for live purposes in xawtv.  No recording from what I see.

> **zolodon said:**
> Well...  This news stinks, but I'm glad to find some answers here before I started fighting my AIW card to get MythTV working.  Watching real-time TV with no other features on my PC is just not worth the effort IMO.

*adds another piece of hardware to the upgrade list*

It's worth it if you want to use your LCD as a joint desktop/live tv station. I will give xawtv a whirl and see if that works ;)

edit*

Has anyone tried gatos with AIW cards and the feisty build?

---

### Post by Minute on 2007-11-11
I was looking at the How To link above and I'm not sure I understand what it is saying about getting MythTV to work.  I'm trying to switch over to Ubuntu from Windows and I've never used Linux on my home computer before so I'm having a hard enough time trying to just figure out how to get MythTV working period.  Any help would be appreciated.

---

### Post by kamikazekarl on 2008-03-21
:popcorn:

 It appears that ATI/AMD/Radeon have been listening to the masses checkout this out 

Main driver page: 
 [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

OS of Choice page:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_83_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_83_linux.html)

---

